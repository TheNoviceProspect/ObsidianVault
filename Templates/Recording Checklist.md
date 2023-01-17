---
creation date: <% tp.file.creation_date() %>
modification date: <% tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %>
---
<% tp.file.rename("Recording Checklist - " + tp.date.now("MMMDD-YYYY")) %>
## <% tp.file.cursor(1) %>Name of the Recording/Series & Episode #
### Pre-Recording
- [ ] Hydration available
- [ ] Visibility/Glare
- [ ] W/C?

### Recording setup
- [ ] At least 2x space available on D:
- [ ] Check Mic is set to VoiceMod
  - [ ] (Optional:) Check that VoiceMod has the Clean voice enabled
- [ ] Check Mic audio levels
- [ ] Check MiraBox Capture Audio level
- [ ] Check Camera is enabled and visible
- [ ] Check video capture is enabled and visible
- [ ] StreamCtrl on Android running and connected
- [ ] Game Loaded
  - [ ] {Multiplayer} Loaded into world
  - [ ] {Single player} Loaded into save and paused

### Streaming
- [ ] Have you scheduled a stream?
- [ ] Ensure you've selected and setup the stream in OBS as a Broadcast

**This checklist need to be check before *EVERY* recording/stream**
-smzb