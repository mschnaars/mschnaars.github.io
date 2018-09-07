---
title: Batch Ingest Package Format
summary: "Detailed formatting and syntax requirements for ingest packages used in batch ingest."
sidebar: avalon6_sidebar
permalink: avalon6_batch_ingest_package_format.html
folder: avalon6/managing_content
---

Batch ingest begins when an ingest package is uploaded to an Avalon dropbox. The ingest package--consisting of a manifest file and content files--must adhere to formatting and syntax requirements in order to process successfully.

* For instructions on creating a simple manifest file and starting a batch ingest, see [Using Batch Ingest](avalon6_using_batch_ingest).
* For help with resolving issues related to a failed batch ingest, see [Troubleshooting a Batch Ingest](avalon6_troubleshooting_a_batch_ingest).

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

## Manifest File Format

The following is a simple ingest package that has been uploaded to an Avalon dropbox subdirectory:

{% include image.html file="doc_images/batch_layout.png" alt="Layout of an uploaded Ingest Package" %}

The manifest file contains the metadata for the items to be ingested, as well as the names of the content files that make up each item. In the above image, the manifest file is named `batch_manifest.xlsx`. 

{{site.data.alerts.warning}}
Neither the manifest file name nor any directory/folder names may contain blanks&mdash;substitute underscores for any blanks.
{{site.data.alerts.end}}

Example manifest file:

|----------------------|-----------------------|-----------|-----------|-----------------|
|     |A               |B                      |C          |D          |E                |
|----------------------|-----------------------|-----------|-----------|-----------------|
|**1**|Test Batch 1    |avalon_user@example.com|           |           |                 |
|**2**|Bibliographic ID|Title                  |Creator    |Date Issued|File             |
|**3**|123455          |Test Item 1            |Person Name|2012       |content/file1.mp3|
|**4**|789101          |Test Item 2            |Anonymous  |1951       |content/file2.mp4|
|----------------------|-----------------------|-----------|-----------|-----------------|

__Row 1, Column A__
: Reference name for the batch; this field for reference only and should be memorable or descriptive.

__Row 1, Column B__
: Username/email address of the batch submitter; this name must match an existing manager, editor, or depositor for the collection.

__Row 2, All Columns__
: Metadata field names for items; at minimum, __Title__, __Date Issued__, and __File__ are required.

__Row 3, Row 4, etc.__
: Represents a single item in Avalon.

{{site.data.alerts.warning}}
None of the field names in <b>Row 2</b> may contain leading or trailing blanks&mdash;the field names will not be recognized by Avalon and will cause an error.
{{site.data.alerts.end}}

## Supported Field Names

### Descriptive Field Names
Required fields include: 

* __Title__
* __Date Issued__
* __File__
* __Bibliographic ID__ : used in place of __Title__ and __Date Issued__.

__Bibliographic ID__
: Identifies the original MARC catalog record from which metadata was generated and imports data from the catalog record into Avalon.
* MODS mapping: relatedItem@type="original"/identifier
* Not repeatable
* Editable after ingest in "Bibliographic ID" field of Resource Description form.
* Inclusion of a bibliographic ID will cause any other descriptive metadata (including Required descriptive fields) entered into the spreadsheet besides the __Bibliographic ID Label__ to be ignored. The required __File__ fields will, however, be read and used.
* Information about how the corresponding MARC record is mapped to Avalon MODS is found in the MARC record ingest section below.

__Bibliographic ID Label__
: Identifies the type of bibliographic ID supplied in the __Bibliographic ID__ column. Valid types depend on system configuration and by default include "local", "oclc", lccn", "issue number", "matrix number", "music publisher", "video recording identifier", and "other".
* MODS mapping: relatedItem@type="original"/identifier@type
* Not repeatable
* Editable after ingest in "Bibliographic ID" field of Resource Description form.
* The value of "local" maps to "Catalog Key" in the Resource Description Form.
* Batch will fail if value is not in the configured list of valid values.
* Will be ignored if no paired __Bibliographic__ ID value is present.

__Other Identifier__
: Identifies an external record that can connect the Avalon item to a catalog record or other record for the original item. This identifier differs from __Bibliographic ID__ in that it is not used to retrieve a record from another system.
* MODS mapping: relatedItem@type="original"/identifier
* Repeatable
* Editable after ingest in "Other Identifier" field of Resource Description form.
* Must be paired with a value for Other Identifier Type.

__Other Identifier Type__
: Identifies the type of external record identifier supplied in the __Other Identifier__ column. Valid types depend on system configuration and by default include "local", "oclc", "lccn", "issue number", "matrix number", "music publisher","video recording identifier", and "other".
* MODS mapping: relatedItem@type="original"/identifier@type
* Not repeatable
* Editable after ingest in "Other Identifier Label" field of Resource Description form.
* Batch will fail if value is not in the configured list of valid values.
* Will be ignored if no paired __Other Identifier__ value is present.

__Title__ : required descriptive field
: Used for display in search results and single item views. Only the first 32 characters of a title are included in search results listings. Recommended practice is to reflect the content captured in digitized media files (such as the title of the piece). If title is unavailable or missing, create a title that describes something about the content of the item. This is necessary for identifying items in search results.
* MODS mapping: titleInfo/title
* Not repeatable
* Editable after ingest in "Title" field of Resource Description form.

__Creator__
: Primary persons or bodies associated with the creation of the content. Creators will be included in search results and aggregated for browsing access. At this time, there is no ability to specify a creator as a corporate body. When possible, use the [Library of Congress Name Authority File](http://id.loc.gov/authorities/names.html).
* MODS mapping: name@usage="primary"/namePart (role/roleTerm set to "Creator")
* Repeatable
* Editable after ingest in "Main contributor(s)" field of Resource Description form.

__Contributor__
: Persons or bodies associated with the item but not considered primary to the creation of its content. Examples of this would be performers in a band or opera, conductor, arranger, cinematographer, or choreographer. At this time, this is no ability to specify a contributor as a corporate body. When possible, use the [Library of Congress Name Authority File](http://id.loc.gov/authorities/names.html).
* MODS mapping: name/namePart (role/roleTerm set to "Contributor")
* Repeatable
* Editable after ingest in "Contributor(s)" field of Resource Description form.

__Genre__
: Used to categorize an item by form, style, or subject matter. For consistency and to allow for sorting and aggregating, use terms from the [Open Metadata Registry labels for PBCore: pbcoreGenre](http://metadataregistry.org/concept/list/vocabulary_id/148.html).
* MODS mapping: genre
* Repeatable
* Editable after ingest in "Genre(s)" field of Resource Description form.

__Publisher__
: Publisher of the content of the item.
* MODS mapping: originInfo/publisher
* Repeatable
* Editable after ingest in "Publisher(s)" field of Resource Description form.

__Date Created__
: Used only if __Date Issued__ is a re-issue date; __Date Created__ contains the original publication date. Enter date information in a format consistent with the options shown in [Extended Date/Time Format (EDTF) 1.0](http://www.loc.gov/standards/datetime/pre-submission.html).
* MODS mapping: originInfo/dateCreated@encoding=”edtf”
* Not repeatable
* Editable after ingest in "Creation date" field of Resource Description form.

__Date Issued__ : required descriptive field
: Main publication date associated with the item to be used for sorting browse and search results. Enter date information in a format consistent with the options shown in [Extended Date/Time Format (EDTF) 1.0](http://www.loc.gov/standards/datetime/pre-submission.html). If date issued is not available or missing, enter a date that is narrowed down as much as possible (by range of years) or enter a date for century (18uu, 19uu, 20uu), in accordance with [EDTF](http://www.loc.gov/standards/datetime/pre-submission.html) specifications.
* MODS mapping: originInfo/dateIssued@encoding=”edtf”
* Not repeatable
* Editable after ingest in "Publication date" field of Resource Description form.

__Abstract__
: Used for describing the contents of the item. Examples include liner notes, list of contents, or an opera scene abstract. __Abstract__ is not meant for cataloger's descriptions but for descriptions that accompany the item. The first 15-20 words of __Abstract__ are included in search result listings.
* MODS mapping: abstract
* Not repeatable
* Editable after ingest in "Summary" field of Resource Description form.

__Language__
: Used for describing the language of the content. Only terms or codes from the [MARC Code List for Languages](http://www.loc.gov/marc/languages/) list may be used.
* MODS mapping: language/languageTerm
* Repeatable
* Editable after ingest in "Language(s)" field of Resource Description form.

__Physical Description__
: Description of the original carrier for content that has been digitized from analog content.
* MODS mapping: relatedItem@type="original"/physicalDescription/extent
* Not repeatable
* Editable after ingest in "Physical Description" field of Resource Description form.

__Related Item URL__
: A URL to related content, such as an adaptation or original version.
* MODS mapping: relatedItem@displayLabel/location/url
* Repeatable
* Editable after ingest in "Related Item(s)" field of Resource Description form.
* Must be paired with a value for __Related Item Label__.

__Related Item Label__
: Descriptive label for the __Related Item URL__ field.
* MODS mapping: relatedItem@displayLabel
* Not repeatable within Related Item
* Editable after ingest in "Related Item(s)" field of Resource Description form.
* Must be paired with a value for __Related Item URL__.

__Topical Subject__
: Used for the topical subject of the content. For consistency and to allow for sorting and aggregating, use terms from the [Library of Congress Subject Headings](http://id.loc.gov/authorities/subjects.html). For temporal subjects (time periods), use Temporal Subject and for geographic subjects (locations), use Geographic Subject; see below.
* MODS mapping: subject/topic
* Repeatable
* Editable after ingest in "Subject(s)" field of Resource Description form.

__Geographic Subject__
: Used for the location associated with the content. For consistency and to allow for sorting and aggregating, use terms from the [Getty Thesaurus of Geographic Names](http://www.getty.edu/research/tools/vocabularies/tgn/index.html).
* MODS mapping: subject/geographic
* Repeatable
* Editable after ingest in "Location(s)" field of Resource Description form.

__Temporal Subject__
: Used for the time period of the content (for example, years or year ranges). Enter date information in a format consistent with the options shown in [EDTF](http://www.loc.gov/standards/datetime/pre-submission.html).
* MODS mapping: subject/temporal
* Repeatable
* Editable after ingest in "Time period(s)" field of Resource Description form.

__Terms of Use__
: Describes the conditions under which content may be used.
* MODS mapping: accessCondition@type="use and reproduction"
* Not repeatable
* Editable after ingest in "Terms of Use" field of Resource Description form.

__Table of Contents__
: Used to provide the titles of separate works or parts of a resource. Information provided may also contain statements of responsibility or other sequential designations. Titles of separate works or parts should be separated by “ – “ (space-hyphen-hyphen-space).
* MODS mapping: tableOfContents
* Repeatable
* Editable after ingest in "Table of Contents" field of Resource Description form.

__Statement of Responsibility__
: Used to provide information about primary persons or bodies associated with the creation of the content, along with details about their roles. This information can be transcribed from the credits listed in the resource itself or on its packaging. Recommended practice is to provide a separate __Contributor__ field for each person or body listed in the Statement of Responsibility. __Statement of Responsibility__ may be left empty if the use of __Contributor__ fields alone is preferred.
* MODS mapping: note@type="statement of responsibility"
* Repeatable
* Editable after ingest in “Statement of Responsibility" field of Resource Description form.
* __Statement of Responsibility__ is displayed in the user interface appended to the Title, following a “ / “.
* May be included as a __Note__/__Note Type__ pair with __Note Type__='statement of responsibility'.

__Note__
: Used to describe aspects of the resource not accounted for in any of the other fields, such as creation or production credits, performers, venue/event date, historical or biographical information, language details, awards given to the performance or the work performed. Recommended practice is to provide a separate __Contributor__ field for each person or body associated with the creation of the content and to use a __Note__ to provide more information about such contributions or to provide information about secondary persons or bodies associated with the creation of the content.
* MODS mapping: note
* Repeatable
* Editable after ingest in “Note" field of Resource Description form.
* Must be paired with a value for __Note Type__.

__Note Type__
: Identifies the type of note and is used as a label in the user interface. Valid types depend on system configuration and by default include "general", "awards", "biographical/historical", "creation/production credits", "language", "local", "performers", "statement of responsibility", and "venue".
* MODS mapping: note@type
* Not repeatable
* Editable after ingest in "Note Label" field of Resource Description form.
* Must be paired with a value for __Note__.

### Operational Field Names

__Publish__
: Determines whether the item should be automatically published after ingest.
* Not repeatable
* Default: "No"
* To auto-publish, enter value of "Yes"

__Hidden__
: Determines whether the item will appear in search/browse results for end users. Use this field to prevent users from discovering items that would be confusing outside an externally-determined context (video figures for a research paper, audio clips contextualized in an Omeka exhibit, etc.). Hidden items provide "security by obscurity" when it is desirable to provide easy access but undesirable to publicize the availability of the items.
* Not repeatable 
* Default: "No"
* To trigger hiding, enter value of "Yes"
* Hidden items still appear in search/browse results for collection staff.

__File__ : required operational field
: The file path and file name for content files listed in the manifest file and located in the Avalon dropbox, relative to the manifest file. Additionally, all content files must include a file extension. If necessary, include any directories or subdirectories (see the example manifest file above for a __File__ value).
* Repeatable
* __Label__, __Offset__, and __Skip Transcoding__ can be listed in any order following the file they are describing. __Absolute Location__ can only be used following __Skip Transcoding__ if __Skip Transcoding__ is included and its value is set to "Yes".

__Label__
: Used for display in single item views. Recommended practice is to reflect the content captured in digitized media files (such as the Part 1 and Part 2 of the piece performed or titles of songs).
* Only repeatable following a repeated __File__ entry.
* Editable after ingest in "Label" field of Manage Files page.

__Offset__
: Used to set the thumbnail and poster image for the display in search/browse results and single item views. Must be entered between 00:00:00.000 and length of file.
* Only repeatable following a repeated __File__ entry.
  * If a record contains multiple __File__ entries, the first __Offset__ listed will be used for the item thumbnail displayed in search results.
* Only applicable to video files; audio files use a default thumbnail.
* Default: 00:00:02:000 seconds into playback
* Editable after ingest in "Thumbnail" field of __Manage Files__ page.
* Excel will automatically format hh:mm:ss into time. To circumvent this, begin time offset with a single quote, for example: '0:10 for 00:00:10 and '1:06 for 00:01:06.

__Skip Transcoding__
: Used if a pre-encoded derivative of the file is to be uploaded instead of the master version of the file. __Skip Transcoding__ presumes that the derivative(s) match the requirements explained in [Avalon Derivatives](avalon6_derivative_files). Master file location information should be included for complete object ingest. See __Absolute Location__ (below) for further information.
* Only repeatable following a repeated __File__ entry.
* Accepted values: “Yes” or “No”

__Absolute Location__
: Used with __Skip Transcoding__ to indicate the location of the master version of a video or audio file when the file uploaded to Avalon is a pre-encoded derivative.
* Only repeatable following __Skip Transcoding__ if __Skip Transcoding__ is included and set to “Yes”.
* If __Skip Transcoding__ is set to “No” or not included, __Absolute Location__ will be ignored.
* __Absolute Location__ should be the full URI path of the server housing the master version of the file.

__Date Ingested__
: The date the item was ingested into Avalon. Follow the format yyyy-mm-dd to override the default value.
* Not repeatable
* Default: day on which the ingest process is completed by Avalon
* Not visible within the user interface to normal users.
* For administrators and collection managers, a "Limit By" facet with these values will be available for search/browse.

{% include links.html%}