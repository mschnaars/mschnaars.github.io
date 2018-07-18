---
title: Troubleshooting Batch Ingest
summary: "Tips for locating errors in a failed Batch Ingest and instructions for replaying a Manifest File."
sidebar: avalon6_sidebar
permalink: avalon6_troubleshooting_batch_ingest.html
folder: avalon6/managing_content
---

## Introduction

Batch Ingest may fail for a variety of reasons, after which the Manifest File can be replayed with corrected information.

For help with creating an Ingest Package and starting a Batch Ingest, see [Uploading Content With Batch Ingest](avalon6_uploading_content_with_batch_ingest).

### Definitions

Batch Ingest
: {{site.data.definitions.batch_ingest}}

Collection
: {{site.data.definitions.collection}}

Content File
: {{site.data.definitions.content_file}}

Ingest Package
: {{site.data.definitions.ingest_package}}

Item
: {{site.data.definitions.item}}

Manifest File
: {{site.data.definitions.manifest_file}}

## Troubleshooting a Failed Ingest

### Invalid Manifest File

Avalon checks for new spreadsheets once per minute. Upon detection, the system opens the spreadsheet and attempts to validate it for correct information. Spreadsheets fail validation for the following reasons:

* File is corrupt
* No username listed
* The listed username account does not have permission to upload to the Collection

If the user account exists in the Avalon system, but the spreadsheet is invalid, the user receives a failure message from the system; multiple reasons may be listed.

Example error message:
    
    User USER_KEY does not have permission to add items to collection: COLLECTION_NAME

If the user account does not exist (i.e. username left blank, entered incorrectly, or no email address is associated with the account), the failure message is sent to the notification email address for Avalon. The default notification email address is "avalon-notification@example.edu", and is located in `Settings.yml`:

    email:
      comments: 'avalon-comments@example.edu'
      notifications: 'avalon-notifications@example.edu'
      support: 'avalon-support@example.edu'

{{site.data.alerts.important}}
If your instance of Avalon is running on AWS, default emails will need to be verified with AWS first (by clicking a verify link in a message sent to the email address).
{{site.data.alerts.end}}

### Valid Manifest File

When the spreadsheet passes validation, the user receives a message stating that the spreadsheet has been accepted:

    Your metadata package was validated and no errors were found. Your batch is now queued.
    Manifest file: example_manifest_file.xlsx

This message does not imply a successful ingest, only that the sheet was accepted and the rows have been queued for ingest. Once the Batch Ingest has finished, the user receives a Batch Ingest report with any reported errors:

{% include image.html file="doc_images/failed_ingest_message.png" alt="Example of a report for a failed batch ingest" max-width="850" %}

Reported errors always begin at Row 3. Use the row number and error description to locate and correct the object information causing the error. Refer to [Batch Ingest Package Format](avalon6_batch_ingest_package_format) for required syntax for each field. After correcting the errors, the Manifest File can be replayed.

## Replaying a Manifest File

Batch Ingest reports contain a replay name following the format _universally-unique-id_original_filename_. For example:

    2a29d341-7da8-44c1-a503-a0df44fd0337_example_manifest_file.xlsx

Using the replay name, Avalon reruns a corrected spreadsheet and ingests previously failed items. Replaying also updates any ingested and unpublished media objects that received changes. 

{{site.data.alerts.important}}
Published media objects cannot be corrected using a replayed Manifest File. This method will always fail if Avalon is auto-publishing media objects.
{{site.data.alerts.end}}

To replay a Manifest File:

1. Rename the original Manifest File to the replay name provided in the report email.
2. Change any data that needs to be updated:
   * Provide missing or incorrect data that caused an error.
   * Update data for successfully ingested media objects (i.e. if the data didn't flag an error, but needs to be edited).
3. DO NOT delete rows that receive no changes; leave them as is.
4. Upload the Manifest File using the normal process.
5. Re-upload the Content Files if they were removed for any reason (e.g. by automatic processes).

Once Avalon detects the uploaded Manifest File, the system requeues the rows for ingest. Upon reaching an altered row, Avalon takes the following actions:

* For previously failed rows, the row will rerun for ingest.
* For previously ingested items, AValon checks if the media object is currently published:
  * For published items, the row flags an error (published items may not be corrected using a replayed Manifest File).
  * For unpublished items, the previously ingested media object is deleted, and a new media object is created using the updated data.

After a Manifest File has been corrected and replayed, a user may make additional corrections and replay again immediately, but doing so will cause a changed media object to be processed twice (once for each replayed spreadsheet).