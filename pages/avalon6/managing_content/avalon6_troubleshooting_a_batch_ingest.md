---
title: Troubleshooting Batch Ingest
summary: "Tips for locating errors in a failed batch ingest and instructions for replaying a manifest file."
sidebar: avalon6_sidebar
permalink: avalon6_troubleshooting_batch_ingest.html
folder: avalon6/managing_content
---

Batch ingest can fail for a variety of reasons, including errors with the manifest file and errors with individual items. Reports sent to the submitter can help pinpoint and correct errors, after which a manifest file can be replayed to rerun the batch ingest.

* For instructions on creating a simple manifest file and starting a batch ingest, see [Using Batch Ingest](avalon6_using_batch_ingest).
* For detailed information about the manifest file, see [Batch Ingest Package Format](avalon6_batch_ingest_package_format).

## Definitions

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

Upon detecting a new manifest file in the dropbox directory, Avalon validates the file for correct information. Manifest files fail validation for the following reasons:

* File is corrupt
* No username/email address listed
* The listed username/email address is not a manager, editor, or depositor for the collection

If the username/email address is in the Avalon system, the user receives an error message:
    
    User USER_KEY does not have permission to add items to collection: COLLECTION_NAME

If the username/email address is not in Avalon (i.e. username left blank, typed incorrectly, no associated email address), the error message is sent to Avalon's default notification account; contact an Avalon administrator if error messages are not being received.

### Valid Manifest File

Once a manifest file passes validation, the user receives a success message _regarding validation only_ :

{% include image.html file="doc_images/manifest_success.png" alt="Example success message for a validated manifest file" max-width="550" %}

This message does not imply a successful ingest, only a successful validation. At this point, the items in the manifest file have been queued for ingest and may begin appearing within the collection. Once the items have processed, the user receives a detailed report for both successful and failed items:

{% include image.html file="doc_images/ingest_report.png" alt="Example report for a processed batch ingest" max-width="850" %}

Use the report information to locate and correct item metadata; refer to [Batch Ingest Package Format](avalon6_batch_ingest_package_format) for detailed information and required syntax for each metadata field. After correcting any errors, the manifest file can be replayed.

## Replaying a Manifest File

Replaying a manifest file can ingest failed items with corrections, but can also revise successful items with updated information.

Batch ingest reports contain a replay name in the format _universally-unique-id_original_filename_. For example:

    2a29d341-7da8-44c1-a503-a0df44fd0337_example_manifest_file.xlsx

To replay a Manifest File:

1. Rename the original manifest file to the replay name provided in the batch ingest report.
2. Open the manifest file.
3. Enter new values for metadata fields that need updating:
   * Provide missing or incorrect data that caused an error.
   * Update data for successful items (i.e. the data didn't cause an error, but needs revision).
4. Connect to the collection subdirectory; see [Connecting to a Dropbox](avalon6_connecting_to_a_dropbox) for help with this process.
4. Upload the updated manifest file into the subdirectory.
5. Re-upload the content files into the subdirectory if they were removed for any reason.

Once Avalon detects the replayed manifest file, the updated items are requeued for ingest.

{{site.data.alerts.warning}}
Published items cannot be updated by replaying a manifest file. This method will always fail if Avalon is auto-publishing items. To turn off auto-publishing, set <b>Publish</b> in the manifest file to "No".
{{site.data.alerts.end}}