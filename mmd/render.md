---
layout: default
title: Render Tips
description: "MMD Render Tips"
parent: MMD
---

{: .fs-9 }

If your hard disk cannot handle large file size, then you can render with ffdshow codec (by installing K-Lite Codec Pack). BUT it's maybe a bug because the contrast of the output video is wrong, which makes your video become a bit darker (and color white become gray). To fix this, I use ffmpeg with this command:<br>
**ffmpeg.exe -i input.avi -vf eq=contrast=1.16:brightness=0.025 output.mp4**

FFmpeg also helps your video have less file size.
