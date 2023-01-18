Takes exclusively [[AV Editing/Audio Routing/MiraBox]] and [[AV Editing/Audio Routing/NVidia Broadcast]] inputs

That way all the stream data is pre-filtered before ever hitting OBS, and you can pretty much ignore all that crud in OBS.
The only thing left here is to arrange it all into a scene and then setting your Audio levels.

Also note, in OBS we only need 1 audio input:
![[AV Editing/Audio Routing/attachments/Pasted image 20230118114154.png]]

The webcam is literally just this:
![[AV Editing/Audio Routing/attachments/Pasted image 20230118114319.png]]

And in case you're wondering how we're doing the actual desktop audio:
![[AV Editing/Audio Routing/attachments/Pasted image 20230118114554.png]]
That way we're grabbing essentially [[AV Editing/Audio Routing/VoiceMeeter]]s desktop audio (the A2 channel)