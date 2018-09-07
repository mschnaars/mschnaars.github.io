---
title: Reference Guide for Avalon Media System Documentation
summary: A short guide to authoring and formatting documents on Avalon's documentation site. External links for more information are also included.
date: 2018-09-7
creator: Matthew H Schnaars
---

## Directory Layout

Most important/useful directories and pages within the site structure:

__`_data _`__
: `.yml` files containing frequently reused data across the site.
  * `sidebars` contains the page titles and URLs for every user-facing document; make sure to add new pages here after they are created.
  * `alerts` contains pre-formatted UI alerts for warnings, danger signs, helpful tips, and more.
  * `definitions` contains a list of terms that can be reused when defining terms on user-facing documents; this helps ensure consistency across documents.
  * `tags` contains a list of pre-defined tags that get attached to a document's frontmatter, enhancing search and SEO; tags must be defined added here before they can be used.
  * `topnav` contains the links for items within the top navigation bar; when a new version of Avalon is released, add the new version subdirectory here.

__`_includes`__
: Most of the items here are only used by Jekyll when building the site, but a few of them are utilized to include images, icons, and links. See more on this below in __Formatting__.

__`_posts`__
: The documentation site has a blog-style section that can be used for time-based updates and information. Adding a page here to announce a new major version of Avalon, forthcoming documents, etc., would be useful and signify to users that the site is being maintained. The filename for posts must follow the format `yyyy-mm-dd-title_of_post.md`. 

__`downloads`__
: Place resources here for users to download. Provide the download link using the following format:

    [Download this item!](/downloads/this_item.csv)

__`images`__
: Place visual resources here to display on documents. Images in this directory will be added to documents when the appropriate `include` is used. See more on this below in __Formatting__.

__`pages`__
: The main directory containing almost all of the user-facing documents. Each major version of Avalon will have a subdirectory of documents within this area. Additionally, there is a subdirectory for `News` within this area; static pages for the news section (not posts) can be placed here.

## Formatting

Check out the following resources for more in-depth explanations on formatting:

* [Kramdown](https://kramdown.gettalong.org/)
* [Tom Johnson's documentation theme](https://idratherbewriting.com/documentation-theme-jekyll/)

Also, writing documents in a clear and consistent style greatly helps with readability. Check out [Microsoft's style guide](https://docs.microsoft.com/en-us/style-guide/procedures-instructions/) on technical writing, especially when referring to onscreen UI elements like buttons or icons. For a quick summary:

* Use words that are interface-neutral--i.e. say "Select" instead of "Click" or "Touch"
* When referencing an onscreen element, such as a button, menu, or heading, emphasize the element using `<b>Bold</b>` or `__Bold__`. 

### Frontmatter

Pages in Jekyll are written and saved as markdown files (`.md`), and each page need to have frontmatter in order to be published correctly. Example frontmatter for the `avalon6_accessibility.md` page:
    
    ---
    title: Accessibility
    summary: "A description of Avalon's support for screen readers and instructions for navigating Avalon using the keyboard."
    sidebar: avalon6_sidebar
    permalink: avalon6_accessibility.html
    folder: avalon6/using_avalon
    ---

Each of these variables in the frontmatter is required. Note that the permalink is the same as the file name, but the extension is changed to `.html`. Please follow the established filename scheme in place, i.e. `avalon#_page_name.md`. Adding the `avalon#` to each document prevents name conflicts when more versions of Avalon are included at a future date.

### Links

Adding web links to a document is identical to normal markdown:

    (display text)[link_address.com]

### Images and Icons

#### Working with Images

Screenshots don't need to be fancy; I don't use anything other than the Print Screen function and MS Paint to edit images. However, it can be visually pleasing to leave a small margin of white space around the outside border of an image. MS Paint makes this really easy:

1. Crop the image to just slightly larger than necessary.
2. Add a rectangle with no fill and a thick white border around the edges of the cropped picture.

If elements of the screenshot should be emphasized, do the following:

* If the background is light, create a black arrow pointing at the element.
* If the background is dark, use a yellow rectangle to outline the element.

#### Includes

Using `includes` within documents is the best way to achieve consistent and stylized formatting with images and icons--it also promotes code reuse! There are only three `includes` that should be used frequently: images, inline images, and inline icons. The `includes` for images and inline images both look within the `images` folder (don't add `images` into the file paths).

__images.html__
: Use this for screenshots and large images. Don't include `px` after the pixel width; just enter the number. 850 is the best for full-width screenshots, otherwise leave it blank or use a smaller number to find the best resolution.

    {% include image.html file="file.path" alt="Alt text" max-width="" %}

__inline_image.html__
: Use this for smaller images that should appear inline. However, I have rarely found this `include` to be a useful way of presenting images.

    {% include inline_image.html file="file.path" alt="Alt text" %}

__inline_icon.html__
: Use this to display SVG icons when referring to onscreen icons--visual examples are always better than referring to a "button" or an "icon"! All the SVG code for every icon is located within avalon_icons.svg. If more icons are used in the future, add the code to the file, and give it an ID. It should look like this within the file:

    <symbol id="play" viewBox="0 -10 93.434 110">
		<path d="M84.94 46.5L0 100L0 0L84.94 46.5Z"></path>
	</symbol>

The icon would then be referenced using the following:

    {% include inline_icon.html icon="play" %}

### Definitions and Alerts

Information in the `.yml` files in the `_data` folder can be called on each page. This promotes code reuse and helps achieve consistency across documents. The info can be called using the following format:

    {{site.data.yml_file_name.yml_term}}

#### Definitions

Kramdown provides a nice formatting option for definitions; please use this format when defining _any_ terms in a document (either common Avalon terms stored in the `definitions.yml` file or terms unique to a singel page), as it is more readable than using a bulleted or numbered list. See the following:

    Batch Ingest
    : {{site.data.definitions.batch_ingest}}

    Playlist
    : Collection of playlist items.

#### Alerts

Alerts provide a visually distinct way of highlighting important information. I use alerts on documents to highlight when a higher level of permission is necessary for an action, when an action might cause an error, when syntax rules are easy to miss, etc. There are four types of alerts:

* Success (green checkmark)
* Info (blue question mark)
* Warning (yellow exclamation)
* Danger (red exclamation)

Call an alert using the following format:

    {{site.data.alerts.info}}
    Here is some text. I can't use Kramdown here, so if I want to style anything I need to use <b>Bold</b> or <em>Italics</em>.
    {{site.data.alerts.end}}
    
