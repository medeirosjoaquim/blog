---
title: youtube-dl for session-cookie // embeded files
date: 2017-12-10
---

ok, first, you need a netscape formated cookie.

to do so, use curl -b file.txt (it writes the cookie down);

next

youtube-dl --cookies file.txt videoURL --refer siteItcameFrom

ex;;;

videoURL= some vimeo/video

--refer = site where you took the link
