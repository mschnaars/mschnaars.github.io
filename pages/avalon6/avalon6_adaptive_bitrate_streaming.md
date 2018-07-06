---
title: Adaptive Bitrate Streaming
summary: "A description of adaptive bitrate streaming and its use by Avalon."
sidebar: avalon6_sidebar
permalink: avalon6_adaptive_bitrate_streaming.html
folder: avalon6
---

## Adaptive Streaming in the Media Player

Avalon 6.4 and above can use [adaptive bitrate streaming](https://en.wikipedia.org/wiki/Adaptive_bitrate_streaming) to offer an "auto" quality level during playback. Adaptive streaming works by monitoring network bandwidth and adjusting playback quality automatically. This results in minimal buffering time (i.e. waiting for a video to partially download before playing) and consistent playback for both high- and low-quality connections.

The adaptive streaming option can be viewed using the Playback Quality selector in the media player, and can be seen alongside the other quality options that correspond to each streaming derivative.

{% include image.html file="doc_images/adaptive_bitrate_streaming.png" alt="the adaptive bitrate option in the quality selector" %}

## Embedded Audio

{{site.data.alerts.important}}
When embedding audio files from an Avalon instance, the playback quality selector has been removed from the audio player (see image). The playback quality is set to "auto" by default, and the removal of the selector only occurs in an embedded context.
{{site.data.alerts.end}}

{% include image.html file="doc_images/embedded_audio_selector.png" alt="the quality selector is missing in the embedded audio player" %}

{% include links.html %}