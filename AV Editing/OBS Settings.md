check also my [[AV Editing/OBS Cheatsheet]] for shortcuts

We also need a [[Templates/Recording Checklist]] that I need to  check before I hit start. (This checklist is now a template that we can inherit from)

Additionally the following OBS Plugins are installed : StreamElements and ChapterMarker

Capture comes straight from the [[AV Editing/Audio Routing/MiraBox]] Capture Card, so we ignore Game Capture and Desktop Capture in OBS.

For the [[AV Editing/Hardware/M$ Livecam]] **&** [[AV Editing/Hardware/FiFine Mic]] we're grabbing stream-data from [[AV Editing/Audio Routing/NVidia Broadcast]] instead of the actual hardware devices.

Ideas to try out for future recording/streams to make failures less likely [[Streaming/Best Practices]]

There's also a new tool from NVidia called "Broadcast" it allows you to apply camera and microphone filters before obs ever sees the media-stream
So instead of applying filters in OBS/StreamLabs you can simply set up your cam/mic with NV's technologies and feed those sources into OBS as-is :D
