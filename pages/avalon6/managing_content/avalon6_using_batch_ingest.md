---
title: Using Batch Ingest
summary: "Instructions for adding large quantities of items simultaneously using Avalon's batch ingest functionality."
sidebar: avalon6_sidebar
permalink: avalon6_using_batch_ingest.html
folder: avalon6/managing_content
---

Batch ingest allows the creation of many media objects simultaneously outside of the Avalon user interface. The process is initiated by uploading an ingest package to an Avalon dropbox.

For help resolving a failed batch ingest, see [Troubleshooting a Batch Ingest](avalon6_troubleshooting_a_batch_ingest). For detailed information about the manifest file, see [Batch Ingest Package Format](avalon6_batch_ingest_package_format).

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

## Manifest Template

Download a blank manifest file to use for a batch ingest:

* [manifest_template.xslx](/downloads/manifest_template.xlsx)

## Batch Ingest Basics

Whenever a new collection is created, Avalon creates a matching subdirectory (i.e. a folder) within the Avalon dropbox. Batch ingest begins when an ingest package is uploaded into that subdirectory.

The manifest file lists metadata for the items to be created; many fields are provided, but only the following are required: 

* __Title__
* __Date Issued__
* __File__

For detailed information and required syntax on all fields, see [Batch Ingest Package Format](avalon6_batch_ingest_package_format).

## Creating a Simple Manifest File

1. Open the manifest file that will list the metadata for the content files.
2. Enter a reference name for the batch in __Column A Row 1__; this field is only for reference and should be memorable or descriptive.
3. Enter the email address/username of the batch submitter in __Column B Row 1__; this name must match an existing manager, editor, or depositor for the collection.
4. __Row 2__ specifies potential metadata fields for each item; if a field should be multi-valued (e.g. more than one subject, language, or content file), duplicate the column using the same header.
5. Enter data for a single item beginning in __Row 3__. The minimum required fields for each item include:
   * __Title__ :
     * Not repeatable: each item may only have one __Title__.
     * __Title__ is the name of a single item, which may consist of one or more content files.
   * __Date Issued__ :
     * Not repeatable: each item may only have one date issued.
     * __Date Issued__ is the item's primary publication date; follow the format "yyyy-mm-dd" (see [EDTF](http://www.loc.gov/standards/datetime/pre-submission.html) for other options, including date ranges or unknown dates.
   * __File__ :
   	 * Repeatable: for a single item with multiple content files, duplicate the __File__ and __Label__ columns for each content file; each __File__ column should be followed by a __Label__ column.
	   * __File__ is the name of a content file, comprising two parts:
       * The file path, relative to the manifest file.
       * The file name, including the extension.
       * Both path and name are case-sensitive.
       * Example __File__ : `video_content/videoname.mp4`.
     * __Label__ :
       * Not required, but recommended when an item consists of multiple content files.
       * __Label__ is a name for each content file (e.g. Part 1, Disc 2, etc.).
6. Enter data for additional items in the subsequent rows.

Example manifest file with batch reference name, username, __Title__, and __Date Issued__:

{% include image.html file="doc_images/sample_manifest_1.png" alt="Manifest file displaying batch reference name, username, Title, and Date Issued" max-width="850" %}

Continued, with __File__ and __Label__ columns for an item with multiple content files:

{% include image.html file="doc_images/sample_manifest_2.png" alt="Manifest file displaying file paths and labels for an item with multiple content files" max-width="850" %}

## Uploading an Ingest Package to the Dropbox

1. Connect to the collection subdirectory; see [Connecting to a Dropbox](avalon6_connecting_to_a_dropbox) for help with this process.
2. Upload both the manifest file and all content files into the subdirectory.

Once the spreadsheet passes validation, the user receives an email notification confirming the manifest file was accepted.

{% include image.html file="doc_images/batch_queued.png" alt="Example message after spreadsheet has been accepted" max-width="850" %}

After all items on the manifest file have successfully ingested, the user receives an email confirming  completion of the batch ingest.

{% include image.html file="doc_images/batch_ingest_success.png" alt="Example message after successful batch ingest" max-width="850"%}

{% include links.html %}