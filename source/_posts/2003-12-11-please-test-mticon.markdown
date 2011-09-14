---
layout: post
title: Please test MTIcon
---

I just hacked together a few modifications to MT which allow the favorite icon for the user commenting on this weblog to appear in the comments next to their name.
Please add a comment with the URL of your weblog so as to test it. If there's interest I'll probably release the code this weekend.

For the moment, the limitation is that your weblog (or website) must use the `rel="shortcut icon"` way of indicating the favorite icon, and the URL must be absolute, because the URL is included as-is. No other ways are supported yet. The information is re-gathered each time the page is rebuilt, so if you add support *a posteriori* the icon will appear once the page is rebuilt.

I hope no spammers post to this entry...
