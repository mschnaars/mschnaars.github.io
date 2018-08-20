---
title: Playlist Items
summary: "Instructions for adding and editing playlist items within a playlist."
sidebar: avalon6_sidebar
permalink: avalon6_playlist_items.html
folder: avalon6/using_avalon
---

## Introduction

Playlists in Avalon are limited to Authenticated Users only.

### Definitions

Authenticated User
: {{site.data.definitions.authenticated_user}}

Item
: {{site.data.definitions.item}}

Playlist
: {{site.data.definitions.playlist}}

Playlist Item
: {{site.data.definitions.playlist_item}}

Marker
: {{site.data.definitions.marker}}

## Adding Items to Playlists

### Adding A Single Item

1. View an item in Avalon.
2. Select Add to Playlist {% include inline_icon.html icon="add_to_playlist" %} in the media player.
3. In the dropdown, alter any of the following fields:
   * _Title_ : customize this Item's title that displays in the Playlist.
   * _Playlist_ : select a Playlist for this Item, or create a new Playlist for this Item.
   * _Start_ : edit the timestamp marking the beginning of this Item's playback.
   * _End_ : edit the timestamp marking the end of this Item's playback.
   * _Description_ : add an optional description for this Item.
4. Click "Add".

{% include image.html file="doc_images/add_to_playlist.png" alt="Adding an item to a playlist" max-width="850" %}

### Adding A Multiple-Section Item

1. View an Item in Avalon.
2. Select one of the Add to Playlist {% include inline_icon.html icon="add_to_playlist" %} options located in the structure below the media player.
3. In the modal window, choose a Playlist for the Item(s) and select one of the following options:
   * _Create single item for section_ : one Playlist Item for each section.
   * _Create multiple items from subsections, if available_ : one Playlist Item for each subsection within a section.
4. Click "Add to Playlist".

{% include image.html file="doc_images/add_section.png" alt="Adding multiple-section items to a playlist" max-width="850" %}

{% include image.html file="doc_images/add_modal.png" alt="Modal window for adding multiple-section items to a playlist" max-width="850" %}

## Using Markers

Markers locate specific timestamps in an Item; they are similar to bookmarks in other applications. Markers can only be added while viewing Playlist Items within a Playlist, and they can only be added by the Playlist creator. 

To add a marker:

1. Select Add Marker {% include inline_icon.html icon="marker" %}.
2. Add a title to the Marker.
3. Adjust the timestamp offset, if necessary.
4. Click "Add".

Markers can be edited or deleted by using the drop-down list of Markers when viewing the playlist item. If the playlist's visibility is shareable (by link or public), Markers will be usable by other viewers.

{% include image.html file="doc_images/marker.png" max-width="850" %}

## Editing Playlist Items

1. Select the Playlist feature.
2. Click the "Edit" button for the respective Playlist.
3. Edit Playlist Items in the following ways:
   * Drag Reorder{% include inline_icon.html icon="reorder" %}  and move an Item manually to reorder individual Playlist Items.
   * Enter new values in the order field adjacent to Reorder{% include inline_icon.html icon="reorder" %} to reorder all Playlist Items simultaneously.
   * Select an Item(s) and use the "Copy to..." or "Move to..." drop-down menus to move or copy a Playlist Item(s) to another Playlist.
   * Select Edit <i class="fa fa-edit"></i> for a Playlist Item to edit its Title, Start Time, End Time, or Description.

{% include image.html file="doc_images/edit_playlist_item.png" alt="Editing playlist items" max-width="850" %}

{% include links.html %}