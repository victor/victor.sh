---
layout: post
title: A rails-based photo gallery
---

Ever since I moved from my home server to TXD, I've been wanting to move my photo gallery as well. However, TXD does not support mod_perl which is a requirement for <a href="http://apachegallery.dk">Apache::Gallery</a>, the software that powers my gallery. And, not wanting to use PHP again, I've been pondering for a while now to start a new project in Rails for displaying photo collections, with added features like tagging (I don't really like comments on pics, but I could consider adding that as well). The design would be quite similar to A::G, that is, a template based representation of the contents of a folder, with caching, EXIF interpreting and on-the-fly rotation and scaling. Would anyone be interested apart from me?
