---
title: Current Release
summary: A summary of features from the latest Avalon release.
sidebar: home_sidebar
permalink: current_release.html
toc: false
folder: news
---

## Avalon 6.3.0

Avalon 6.3 is a significant update including a new media player, rewritten batch ingest functionality, and support for cloud deployments.

### Media Player Upgrade

Avalon's media player has been upgraded to the latest release of MediaElement.js. Highlights of this change include:

* Adobe Flash Player no longer required for media playback
* A loading indicator displays while media content is loaded into the player
* Updated icons within the media player

### Playlists

* Tags can be created and associated with playlists, providing improved organizing, searching and sorting for users with large numbers of playlists
* User preferences for sorting on the playlist index page are saved

### Improved Batch Ingest Functionality

* Replay batch ingests: update metadata for newly ingested items by updating spreadsheets
* Ingests with large numbers of items run more successfully
* System emails about batch ingest statuses are improved

### AWS Support

* Avalon components have been updated to work with Amazon Web Services
* For more information, see the [avalon-aws repository](https://github.com/avalonmediasystem/avalon-aws/) and accompanying [documentation](https://github.com/avalonmediasystem/avalon-aws/wiki)

### Bug Fixes and Minor Changes

* Playlist items no longer intermittently skip
* Issues with LTI login have been resolved