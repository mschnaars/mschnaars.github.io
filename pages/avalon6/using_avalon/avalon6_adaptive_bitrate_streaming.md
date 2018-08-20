---
title: Adaptive Bitrate Streaming
summary: "A description of adaptive bitrate streaming and its use by Avalon."
sidebar: avalon6_sidebar
permalink: avalon6_adaptive_bitrate_streaming.html
folder: avalon6/using_avalon
---

## Adaptive Streaming in the Media Player

Avalon 6.4 and above uses [adaptive bitrate streaming](https://en.wikipedia.org/wiki/Adaptive_bitrate_streaming) to offer an "auto" quality level during playback. Adaptive bitrate streaming monitors network bandwidth and adjusts playback quality automatically, resulting in minimal buffering time (i.e. waiting for a video to partially download before playing) and consistent playback for both high- and low-quality connections.

The adaptive bitrate streaming option can be viewed within Stream Quality {% include inline_icon.html icon="stream_quality" %} in the media player, alongside the other quality options that correspond to each streaming derivative.

{% include image.html file="doc_images/adaptive_bitrate_streaming.png" alt="The adaptive bitrate option in the quality selector" %}

## Embedded Audio

{{site.data.alerts.important}}
When embedding audio from an Avalon instance, the playback quality selector has been removed from the audio player (see image). The playback quality is set to "auto" by default, and the removal of the selector only occurs in an embedded context.
{{site.data.alerts.end}}

{% include image.html file="doc_images/embedded_audio_selector.png" alt="the quality selector is missing in the embedded audio player" max-width="500" %}

{% include links.html %}