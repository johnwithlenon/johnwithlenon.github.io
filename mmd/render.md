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
Update: That command could reduce the quality of the video. So I'm using this command with the curves file exported from photoshop:<br>
**ffmpeg.exe -i input.avi -vf curves=psfile=path/to/your/file.acv output.mp4**<br>
Link to the curves file: [file.acv](https://mega.nz/file/dUNgXTDC#0r3fzkc6mccffahHje7prH5276ugDdEBpctFy7iO0p0){: target="_blank" rel="noopener"}

FFmpeg also helps your video have less file size.
