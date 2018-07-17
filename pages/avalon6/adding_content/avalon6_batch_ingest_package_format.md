---
title: Batch Ingest Package Format
summary: "Detailed formatting and syntax requirements for Ingest Packages used in Batch Ingest."
sidebar: avalon6_sidebar
permalink: avalon6_batch_ingest_package_format.html
folder: avalon6/adding_content
---

## Introduction

Avalon's Batch Ingest functionality allows for the creation of many Items simultaneously outside of the user interface. Batch Ingest is useful for both well-documented collections and collections with minimal metadata. A Batch Ingest process is initiated by uploading an Ingest Package to an Avalon dropbox. 

The instructions below provide detailed format and syntax requirements for Manifest Files and the metadata fields contained within. Follow the instructions to ensure a successful Batch Ingest.

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

When a new collection is created, Avalon creates a subdirectory with the collection name within the Avalon dropbox directory. Batch Ingest is initiated by uploading an Ingest Package to the collection subdirectory in the dropbox--all items in a single Ingest Package will be uploaded to the same Collection. To connect to the Avalon dropbox, see [Uploading Content to an Avalon Dropbox](avalon6_uploading_content_to_an_avalon_dropbox).

## Manifest File Format

The following is a simple package that has been uploaded to an Avalon dropbox subdirectory:

{% include image.html file="doc_images/batch_layout.png" alt="Layout of an uploaded Ingest Package" max-width="850" %}

The Manifest File is a spreadsheet (xls, xlsx, csv, or ods) containing the metadata for the Items to be created, as well as the names of the Content Files that make up each Item. In the above image, the Manifest File is named `batch_manifest.xlsx`. 

{{site.data.alerts.important}}
Neither the spreadsheet filename nor any directory/folder names can contain blanks--substitute underscores for any blanks.
{{site.data.alerts.end}}


Example Manifest File:

|----------------------|-----------------------|-----------|-----------|-----------------|
|     |A               |B                      |C          |D          |E                |
|----------------------|-----------------------|-----------|-----------|-----------------|
|**1**|Test Batch 1    |avalon_user@example.com|           |           |                 |
|**2**|Bibliographic ID|Title                  |Creator    |Date Issued|File             |
|**3**|123455          |Test Item 1            |Person Name|2012       |content/file1.mp3|
|**4**|789101          |Test Item 2            |Anonymous  |1951       |content/file2.mp4|
|----------------------|-----------------------|-----------|-----------|-----------------|

__Row 1, Column A__ contains a reference name for the batch; this field is only for reference and should be memorable or descriptive.

__Row 1, Column B__ contains the submitter's email address (or username, depending on the system's configuration) to be used for notifications and exceptions; this name must match an existing Manager, Editor, or Depositor for the Collection.

__Row 2__ specifies the names of the metadata fields supplied in the following rows. At minimum, _Title_, _Date Issued_, _and _File_ are required. Each subsequent row represents a single Item to be created in Avalon. Metadata values are specified first, followed by a list of Content Files to be attached to each Item. 

{{site.data.alerts.important}}
Make sure none of the field names in row 2 have leading or trailing blanks, or the field names will not be recognized by Avalon and will report an error.
{{site.data.alerts.end}}

Content Files listed in the Manifest File must have the correct path noted for where those files are located in the Avalon dropbox, relative to the Manifest File. Additionally, all Content Files must include a file extension. If necessary, include any directories or subdirectories (note the file paths listed in column E in the above example).

Multivalued fields are specified by multiple columns with the same header, e.g. _Topical Subject_ in the following example:

## Supported Field Names

### Descriptive Field Names
Required fields include (bolded below): 

* _Title_
* _Date Issued_
* _File_
* _Bibliographic ID_ : used in place of _Title_ and _Date Issued_.

* Bibliographic ID
  * MODS mapping: relatedItem@type="original"/identifier
  * Not repeatable
  * Editable after ingest in "Bibliographic ID" field of Resource Description form.
  * Used to identify the original MARC catalog record from which metadata was generated and import data from the catalog record into Avalon.
  * Inclusion of a bibliographic ID will cause any other descriptive metadata (including Required descriptive fields) entered into the spreadsheet besides the __Bibliographic ID Label__ to be ignored. The Required file fields will, however, be read and used.
  * Information about how the corresponding MARC record is mapped to Avalon MODS is found in the MARC record ingest section below.
* Bibliographic ID Label
  * MODS mapping: relatedItem@type="original"/identifier@type
  * Not repeatable
  * Editable after ingest in "Bibliographic ID" field of Resource Description form.
  * Identifies the type of bibliographic ID supplied in the __Bibliographic ID__ column. Valid types depend on system configuration and by default include "local", "oclc", lccn", "issue number", "matrix number", "music publisher","video recording identifier", and "other".
  * The value of "local" maps to "Catalog Key" in the Resource Description Form.
  * Batch will fail if value is not in the configured list of valid values.
  * Will be ignored if no Bibliographic ID value is present
* Other Identifier Type
  * MODS mapping: relatedItem@type="original"/identifier
  * Repeatable
  * Editable after ingest in "Other Identifier" field of Resource Description form.
  * Used to identify an external record that can connect the Avalon item to a catalog record or other record for the original item. This identifier differs from Bibliographic Identifier in that it is not used to retrieve a record from another system.
  * Must be paired with a value for Other Identifier Type
* Other Identifier Type
  * MODS mapping: relatedItem@type="original"/identifier@type
  * Not Repeatable within Other Identifier
  * Editable after ingest in "Other Identifier Label" field of Resource Description form.
  * Identifies the type of external record identifier supplied in the Other Identifier column.
  * Valid types depend on system configuration and by default include "local", "oclc", "lccn", "issue number", "matrix number", "music publisher","video recording identifier", and "other"
  * Batch will fail if value is not in the configured list of valid values.
  * Will be ignored if no paired Other Identifier value is present.
* __Title__ : _required_
  * MODS mapping: titleInfo/title
  * Not repeatable
  * __Required descriptive field__. Title is used for display in search results and single item views. Only the first 32 characters of a title are included in search results listings. Recommended use is to reflect the content captured in digitized media files (such as the title of the piece performed or a short description of the content of a home movie).
  * Editable after ingest in "Title" field of Resource Description form.
  * If title is not available or missing, create a title that describes something about the content of the item.  This is necessary for identifying items in search results.
* Creator
  * MODS mapping: name@usage="primary"/namePart (role/roleTerm set to "Creator")
  * Repeatable
  * No ability to specify Corporate Body in batch at this time
  * Main contributors are the primary persons or bodies associated with the creation of the content. Main contributors will be included in search results display and aggregated for browsing access. At this time there is no ability to specify a main contributor as a corporate body. When possible, use the [Library of Congress Name Authority File](http://id.loc.gov/authorities/names.html).
  * Editable after ingest in "Main contributor(s)" field of Resource Description form.
* Contributor
  * MODS mapping: name/namePart (role/roleTerm set to "Contributor")
  * Repeatable
  * Contributors are persons or bodies associated with the item but not considered primary to the creation of its content. Examples of this would be performers in a band or opera, conductor, arranger, cinematographer, and choreographer. At this time this is no ability to specify a contributor as a corporate body. When possible, use the [Library of Congress Name Authority File](http://id.loc.gov/authorities/names.html).
  * Editable after ingest in "Contributor(s)" field of Resource Description form.
* Genre
  * MODS mapping: genre
  * Repeatable
  * Genre can be used to categorize an item by form, style, or subject matter. For consistency and to allow for sorting and aggregating, use terms from the [Open Metadata Registry labels for PBCore: pbcoreGenre](http://metadataregistry.org/concept/list/vocabulary_id/148.html).
  * Editable after ingest in "Genre(s)" field of Resource Description form.
* Publisher
  * MODS mapping: originInfo/publisher
  * Repeatable
  * Publisher of the content of the item.
  * Editable after ingest in "Publisher(s)" field of Resource Description form.
* Date Created
  * MODS mapping: originInfo/dateCreated@encoding=”edtf”
  * Not repeatable
  * Creation date should only be used if Date Issued is a re-issue date. Then Creation date would contain the original publication date. Enter date information in a format consistent with the options shown in [Extended Date/Time Format (EDTF) 1.0](http://www.loc.gov/standards/datetime/pre-submission.html).
  * Editable after ingest in "Creation date" field of Resource Description form.
* __Date Issued__ : _required_
  * MODS mapping: originInfo/dateIssued@encoding=”edtf”
  * Not repeatable
  * __Required descriptive field__. Date should be the main publication date associated with the item to be used for sorting browse and search results. Enter date information in a format consistent with the options shown in [Extended Date/Time Format (EDTF) 1.0](http://www.loc.gov/standards/datetime/pre-submission.html).
  * Editable after ingest in "Publication date" field of Resource Description form.
  * If date issued is not available or missing, enter a date that is narrowed down as much as possible (by range of years) or enter a date for century (18uu, 19uu, 20uu), in accordance with [EDTF](http://www.loc.gov/standards/datetime/pre-submission.html) specifications.
* Abstract
  * MODS mapping: abstract
  * Not repeatable
  * Abstract provides a space for describing the contents of the item.  Examples include liner notes, contents list, or an opera scene abstract. This field is not meant for cataloger's descriptions but for descriptions that accompany the item. The first 15-20 words are included in search result listings.
  * Editable after ingest in "Summary" field of Resource Description form.
* Language
  * MODS mapping: language/languageTerm
  * Repeatable
  * Language should describe the language of the content. Only terms or codes from the [MARC Code List for Languages](http://www.loc.gov/marc/languages/) list may be used. Entering a language term not from the list will display an error when the page is saved.
  * Editable after ingest in "Language(s)" field of Resource Description form.
* Physical Description
  * MODS mapping: relatedItem@type="original"/physicalDescription/extent
  * Not repeatable
  * Physical Description provides a description of the original carrier for content that has been digitized from analog content.
  * Editable after ingest in "Physical Description" field of Resource Description form.
* Related Item URL
  * MODS mapping: relatedItem@displayLabel/location/url
  * Repeatable
  * Related Item URL provides a URL to related content, such as an adaptation or original version.
  * Editable after ingest in "Related Item(s)" field of Resource Description form.
  * Must be paired with a value for Related Item Label.
* Related Item Label
  * MODS mapping: relatedItem@displayLabel
  * Not repeatable within Related Item
  * Related Item Label provides a descriptive label for the Related Item URL field.
  * Editable after ingest in "Related Item(s)" field of Resource Description form.
  * Must be paired with a value for Related Item URL.
* Topical Subject
  * MODS mapping: subject/topic
  * Repeatable
  * Subject should be used for the topical subject of the content. For consistency and to allow for sorting and aggregating, use terms from the [Library of Congress Subject Headings](http://id.loc.gov/authorities/subjects.html). For temporal subjects (time periods), use Temporal Subject and for geographic subjects (locations), use Geographic Subject; see below.
  * Editable after ingest in "Subject(s)" field of Resource Description form.
* Geographic Subject
  * MODS mapping: subject/geographic
  * Repeatable
  * Geographic Subject should be used for the location associated with the content. For consistency and to allow for sorting and aggregating, use terms from the [Getty Thesaurus of Geographic Names](http://www.getty.edu/research/tools/vocabularies/tgn/index.html).
  * Editable after ingest in "Location(s)" field of Resource Description form.
* Temporal Subject
  * MODS mapping: subject/temporal
  * Repeatable
  * Temporal Subject should be used for the time period of the content (for example, years or year ranges). Enter date information in a format consistent with the options shown in [EDTF](http://www.loc.gov/standards/datetime/pre-submission.html).
  * Editable after ingest in "Time period(s)" field of Resource Description form.
* Terms of Use
  * MODS mapping: accessCondition@type="use and reproduction"
  * Not repeatable
  * Terms of Use describes the conditions under which content may be used.
  * Editable after ingest in "Terms of Use" field of Resource Description form.
* Table of Contents
  * MODS mapping: tableOfContents
  * Repeatable
  * Editable after ingest in "Table of Contents" field of Resource Description form.
  * Used to provide the titles of separate works or parts of a resource. Information provided may also contain statements of responsibility or other sequential designations. Titles of separate works or parts should be separated by “ – “ (space-hyphen-hyphen-space).
* Statement of Responsibility
  * MODS mapping: note@type="statement of responsibility"
  * Repeatable
  * Editable after ingest in “Statement of Responsibility" field of Resource Description form.
  * Used to provide information about primary persons or bodies associated with the creation of the content, along with details about their roles. This information can be transcribed from the credits listed in the resource itself or on its packaging.
  * Recommended use is to provide a separate Contributor field for each person or body listed in the Statement of Responsibility. Statement of Responsibility may be left empty if the use of Contributor fields alone is preferred.
  * Statement of Responsibility is displayed in the user interface appended to the Title field, following a “ / “.
  * Also may be included as a Note/Note Type pair with Note Type='statement of responsibility'.
* Note
  * MODS mapping: note
  * Repeatable
  * Editable after ingest in “Note" field of Resource Description form.
  * Used to describe aspects of the resource not accounted for in any of the other fields, such as creation or production credits, performers, venue/event date, historical or biographical information, language details, awards given to the performance or the work performed.
  * Recommended use is to provide a separate Contributor field for each person or body associated with the creation of the content and to use a Note to provide more information about such contributions or to provide information about secondary persons or bodies associated with the creation of the content.
  * Must be paired with a value for Note Type
* Note Type
  * MODS mapping: note@type
  * Not repeatable
  * Editable after ingest in "Note Label" field of Resource Description form.
  * Identifies the type of note and is used as a label in the user interface.
  * Valid types depend on system configuration and by default include:  general, awards, biographical/historical, creation/production credits, language, local, performers, statement of responsibility, venue.
  * Must be paired with a value for Note

### Operational Field Names

* Publish
  * Determines whether the item should be automatically published after ingest.
  * Default is "No".
  * To auto-publish, enter value of "Yes".
* Hidden
  * Whether the item will appear in search/browse results for end users. Use this field to prevent users from discovering items that would be confusing outside some externally-determined context (such as video figures for a research paper or audio clips contextualized in an Omeka exhibit). Hidden items can also provide "security by obscurity" when it is desirable to provide easy access but you don't want to publicize the availability of the items. 
  * Default is "No".
  * To trigger hiding, enter value of "Yes".
  * Hidden items will still appear in search/browse results for those with ingest privileges.
* __File__ : _required_
  * Repeatable
  * __Required file field__. Content files listed in the manifest file must have the correct path noted for where those files are located in the Avalon dropbox, relative to the manifest file. Additionally, all content files must include a file extension. If necessary, include any directories or subdirectories (note the paths listed in columns D and F in the above example).
  * Label, Offset, and Skip Transcoding can be listed in any order following the file they are describing. Absolute Location can only be used following Skip Transcoding if Skip Transcoding is included and its value is set to "yes".
* Label
  * Only repeatable following a file entry.
  * Label is used for display in single item views. Recommended use is to reflect the content captured in digitized media files (such as the Part 1 and Part 2 of the piece performed or titles of songs).
  * Editable after ingest in "Label" field of Manage Files page
* Offset
  * Offset is used to set the thumbnail and poster image for the display in search/browse results and single item views. Must be entered between 00:00:00.000 and length of file.
  * Excel will automatically format hh:mm:ss into time. To circumvent this, begin time offset with a single quote, for example: '0:10 for 00:00:10 and '1:06 for 00:01:06.
  * Only repeatable following an additional file.
  * Default is 2 seconds into playback. 
  * Only applicable to video files. Audio files have a default thumbnail, offset will be ignored.
  * If a record contains multiple files, the first offset listed will set the thumbnail and poster image for the Avalon record.
  * Editable after ingest in "Poster Offset" field of Manage Files page or on the item preview page.
* Skip Transcoding
  * Skip Transcoding is used if a pre-encoded derivative of the file is what is being uploaded to Avalon instead of the master version of the file. This presumes that the derivative(s) match the requirements explained in [Avalon Derivatives](avalon6_derivative_files). Master file location information should be included for complete object ingest. See Absolute Location (below) for further information.
  * Only repeatable following a file entry.
  * Valid values: “yes” or “no”
  * See section below for skipping transcoding with multiple quality levels of derivative.
* Absolute Location
  * Absolute Location is used with Skip Transcoding to indicate the location of the master version of a video or audio file when the file uploaded to Avalon is a pre-encoded derivative.
  * Only repeatable following Skip Transcoding if Skip Transcoding is included and its value is set to “yes”.
  * If Skip Transcoding is set to “no” or not included, Absolute Location will be ignored.
  * Absolute Location should be the full URI path of the server housing the master version of the file.
* Date Ingested
  * This represents the date the item was ingested into Avalon.
  * This date will not be visible within the user interface to normal users.
  * For system administrators and collection managers, a Limit By facet with these values will be available for search/browse.
  * If this column is not included, Date Ingested will automatically be set to the day on which the ingest process is completed by Avalon.
  * Include a valid date with format 2015-12-31 in this column to override the value being automatically set by the system. 