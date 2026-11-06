# Sending files (30 MB limit in cloud sessions)

To analyze an edit I need accurate timing, not picture quality, so small exports work fine. **Never change the frame rate**: timing is measured in frames.

## A finished edit or raw clip, exported from Resolve

1. Go to the **Deliver** page.
2. In **Render Settings**, choose **Custom Export**.
3. Set **Format** to MP4 and **Codec** to H.264.
4. Set **Resolution** to 1280×720 for horizontal, or 720×1280 for vertical.
5. Leave the frame rate as it is.
6. Set **Quality** to *Restrict to* 2000 Kb/s, and set **Audio** to AAC.
7. Click **Add to Render Queue**, then **Render All**.

That comes to about 15 MB per minute, so clips up to about 2 minutes fit. For longer videos, use 1000 Kb/s or send them in parts.

## The timeline file (tiny, with exact cut points)

1. Open the timeline.
2. Go to **File → Export → Timeline…** and choose **FCPXML** as the format.
3. Send it together with the matching video export.

## Someone else's video, as a reference

1. Press **Cmd + Shift + 5** and choose **Record Selected Portion**.
2. Play the moment you care about, then stop recording.
3. Add a couple of lines on why it works. That explanation is the part I can't get anywhere else.

## Bigger files, or your whole library

If you run Claude Code on your Mac (the Claude desktop app, pointed at a folder), there's no upload limit, and I can read your exports directly. Everything in `editing-dna/` lives in GitHub, so it comes with you to any session, cloud or local.
