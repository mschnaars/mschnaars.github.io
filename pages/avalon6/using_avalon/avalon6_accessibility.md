---
title: Accessibility
summary: "A description of Avalon's support for screen readers and instructions for navigating Avalon using the keyboard."
sidebar: avalon6_sidebar
permalink: avalon6_accessibility.html
folder: avalon6/using_avalon
---

## General Accessibility

* The default language (English) is declared on each page.
* The search field uses an associated label element to enhance screen reader support.
* Search terms are included at the beginning of the page titles for search result pages.
* Selected facet labels are included at the beginning of the page titles for browse result pages.
* The URL(s) provided to share specific media objects includes an appropriate title attribute.
* The "more >>" links leading to additional facet options on browse pages includes the appropriate facet label for screen readers, e.g. "more Collection >>", "more Language >>".

### Keyboard Access

Users can use the keyboard to navigate the Avalon Media System interface.

* `TAB`: move forward through each interactive element on the page (links, text fields, buttons, etc.).
* `SHIFT+TAB`: move backward through each interactive element.
* `ENTER`: trigger an element's behavior (e.g. pressing `ENTER` on a link will open the link in the browser).

When an element is focused it will be surrounded by an outline to enhance its visibility.

{% include image.html file="doc_images/accessibility_element_focus.png" alt="A focused element" max-width="200" %}

### Skip to Main Content

When using `TAB`, the first element of each page is a link titled "Skip to main content". This link immediately shifts focus to the main content of the page. When viewing an audio or video page, "Skip to main content" shifts focus directly to Play {% include inline_icon.html icon="play" %}.

{% include image.html file="doc_images/accessibility_skip_content.png" alt="Skip to main content link" max-width="850" %}

## Player Accessibility

### Keyboard Access

* `TAB`: move forward through each button/element on the player (see [Media Player Controls](avalon6_media_player_controls)).
* `SHIFT+TAB`: move backward through each button/element on the player.
* `ENTER`: trigger a button/element's behavior.
* `SPACEBAR`: when any of the player controls are focused, toggle Play/Pause.
* `LEFT/RIGHT ARROW`: when any of the player controls are focused, scrub forward/backward through the track timeline.
* `UP/DOWN ARROW`: when any of the player controls are focused, increase/decrease volume.

Stream Quality {% include inline_icon.html icon="stream_quality" %} allows the user to `TAB` between available stream qualities and `ENTER` the desired quality.

{% include image.html file="doc_images/accessibility_quality_selector.png" alt="Stream Quality selector when focused" max-width="200" %}

{% include links.html %}