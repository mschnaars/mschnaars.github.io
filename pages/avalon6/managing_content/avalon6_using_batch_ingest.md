---
title: Using Batch Ingest
summary: "Instructions for adding large quantities of items simultaneously using Avalon's batch ingest functionality."
sidebar: avalon6_sidebar
permalink: avalon6_using_batch_ingest.html
folder: avalon6/managing_content
---

## Introduction

Avalon's Batch Ingest functionality allows for the creation of many media objects simultaneously outside of the user interface. Batch Ingest is useful for both well-documented collections and collections with minimal metadata. A Batch Ingest process is initiated by uploading an Ingest Package to an Avalon dropbox. This guide explains how to form an Ingest Package and upload it to Avalon using Batch Ingest.

For help with resolving issues related to a failed Batch Ingest, see [Troubleshooting a Batch Ingest](avalon6_troubleshooting_a_batch_ingest).

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

### Manifest Template

[manifest_template.xslx](/downloads/manifest_template.xlsx)

### Preliminaries

When a new collection is created, Avalon creates a sub-directory with the collection name (substituting underscores for any blanks) within the Avalon dropbox directory. Batch Ingest is initiated by uploading an Ingest Package to the collection subdirectory in the dropbox--all items in a single Ingest Package will be uploaded to the same Collection. To connect to the Avalon dropbox, see [Uploading Content to an Avalon Dropbox](avalon6_uploading_content_to_an_avalon_dropbox).

The Manifest File is a spreadsheet (xls, xlsx, csv, or ods) listing the metadata for the Items to be created; download the manifest template provided above for a blank template. The Manifest File provides many metadata fields, but only a few fields are required: 

* _Title_
* _Date Issued_
* _File_
* _Bibliographic ID_ : used in place of _Title_ and _Date Issued_.

 For a description of all allowable fields, as well as instructions for adding structure or captions, see [Batch Ingest Package Format](avalon6_batch_ingest_package_format).

## Creating a Basic Manifest File

1. Open the Manifest File that will list the metadata for the Content Files.
2. Enter a reference name for the batch in Column A Row 1; this field is only for reference and should be memorable or descriptive.
3. Enter the email address/username of the batch submitter in Column B Row 1; this name must match an existing manager, editor, or depositor for the collection.
4. Row 2 specifies potential metadata fields for each Item; if a field should be multi-valued (e.g. more than one subject, language, or Content file) duplicate the column using the same header.
5. Enter data for a single Item beginning in Row 3. The minimum required fields for each item include:
   * _Title_ :
     * Not repeatable: each item may only have one _Title_.
	 * _Title_ represents the name of a single item, which may consist of one or more Content Files.
     * If _Title_ is not available or known, create a title that describes the content of the item; this is necessary for identifying items in search results.
   * _Date Issued_ :
     * Not repeatable: each item may only have one date issued.
     * _Date Issued_ represents the item's primary publication date.
     * The simplest format should follow "yyyy-mm-dd"; see [EDTF](http://www.loc.gov/standards/datetime/pre-submission.html) specifications for other options, including date ranges or unknown dates.
   * _File_ :
   	 * Repeatable: for an item comprising multiple Content Files, duplicate the "File" and "Label" columns for each individual Content File; each "File" column should be immediately followed by a "Label" column.
	   * _Label_ represents a name or short description of each Content File (e.g. Part 1, Introduction, essay topic, musical movement, etc.).
	 * _File_ represents the name of a Content File, comprising two parts:
       * The path to the file, relative to the Manifest File.
       * The name of the file itself, including the file extension (e.g. video1.mp4, songB.aac).
       * Both path name and file name are case-sensitive; incorrect cases will result in a processing error.
     * Example _File_ : A Manifest File and a folder titled "video_content" (with .mp4 Content Files) are uploaded to the dropbox collection "MyVideos". Therefore, each _File_ would follow the format of `video_content/videoname.mp4`.
6. Enter data for all additional Items in the subsequent rows.

The following is an example Manifest File displaying batch reference name, username, _Title_, and _Date Issued_ fields:

{% include image.html file="doc_images/sample_manifest_1.png" alt="Manifest file displaying batch reference name, username, Title, and Date Issued" max-width="850" %}

Continued, with _File_ and _Label_ fields for an item with multiple Content Files:

{% include image.html file="doc_images/sample_manifest_2.png" alt="Manifest file displaying file paths and labels for an item with multiple content files" max-width="850" %}

## Uploading an Ingest Package to the Dropbox

1. Connect to the appropriate collection sub-directory; please see [Uploading Content to an Avalon Dropbox](avalon6_uploading_content_to_an_avalon_dropbox) for help with this process.
2. Upload the Manifest File and all Content Files into the sub-directory.

Once the spreadsheet passes validation, the users receives an email notification stating that the spreadsheet has been accepted.

{% include image.html file="doc_images/batch_queued.png" alt="Example message after spreadsheet has been accepted" max-width="850" %}

After all items listed on the Manifest File have been successfully ingested, the users receives an email notification  regarding completion of the Batch Ingest.

{% include image.html file="doc_images/batch_ingest_success.png" alt="Example message after successful batch ingest" max-width="850"%}