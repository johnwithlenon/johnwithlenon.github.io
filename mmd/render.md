---
layout: default
title: Render Tips
description: "MMD Render Tips"
parent: MMD
---

# MMD Render Tips
{: .no_toc }


If your hard disk cannot handle large file size, then you can render with ffdshow codec (by installing K-Lite Codec Pack). BUT it's maybe a bug because the contrast of the output video is wrong, which makes your video become a bit darker (and color white become gray). To fix this, I use ffmpeg with this command:<br>
~~**ffmpeg.exe -i input.avi -vf eq=contrast=1.16:brightness=0.025 output.mp4**~~<br>
Update: The above command could reduce the quality of the video. So I'm using this command with the curves file exported from photoshop:<br>
**ffmpeg.exe -i input.avi -vf curves=psfile=file.acv output.mp4**<br>
Link to the curves file (place it in the same location as ffmpeg): [file.acv](https://mega.nz/file/dUNgXTDC#0r3fzkc6mccffahHje7prH5276ugDdEBpctFy7iO0p0){: target="_blank" rel="noopener"}<br>

To prevent quality loss, and with recommended settings for YouTube, use this ("**-b:v 15M -r 60 -g 30**" is 1080p60fps. For 4K60fps, change **15M** to **67M**):<br>
**ffmpeg.exe -i input.avi -c:v libx264 -b:a 384k -ac 2 -preset slow -crf 18 -profile:v high -bf 2 -pix_fmt yuv420p -movflags +faststart -threads 4 -cpu-used 0 -b:v 15M -r 60 -g 30 -coder 1 -vf curves=psfile=file.acv,scale=out_color_matrix=bt709 -color_primaries bt709 -color_trc bt709 -colorspace bt709 output.mp4**<br>
If you want to use GPU for faster encoding, replace "**libx264**" with "**h264_nvenc**" (for NVIDIA) or "**h264_amf**" (for AMD).<br>

FFmpeg also helps your video have less file size.

More information about recommended YouTube settings:<br>
[https://www.reddit.com/r/ffmpeg/comments/r1qwyy/best_streaming_settings_for_youtube/](https://www.reddit.com/r/ffmpeg/comments/r1qwyy/best_streaming_settings_for_youtube/){: target="_blank" rel="noopener"}<br>
[https://gist.github.com/mikoim/27e4e0dc64e384adbcb91ff10a2d3678](https://gist.github.com/mikoim/27e4e0dc64e384adbcb91ff10a2d3678){: target="_blank" rel="noopener"}<br>
[https://support.google.com/youtube/answer/1722171](https://support.google.com/youtube/answer/1722171){: target="_blank" rel="noopener"}<br>
