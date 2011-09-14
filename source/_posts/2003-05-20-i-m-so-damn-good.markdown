---
layout: post
title: I'm so damn good...
---

I've been for the last few days fighting my way with my little FreeBSD server. I'll probably be self-hosted in the near future, due to some long lasting issues with tech support everywhere. I have decided that it's in my best interest to buy an <acronym title="Uninterrutible Power Supply">UPS</acronym> and host all my websites through my ADSL line. I don't know abot the performance (maybe I'll have to ask for a higher bandwidth cap) but I can try it.

I have my FreeBSD server configured to <a href="http://uptime.netcraft.com/up/graph/?host=slunj.carotena.net">run Apache 2</a>, and <a href="http://apachegallery.dk/">Apache::Gallery</a>, one of my requirements, doesn't work with mod_perl 2 yet. I had the option then to modify A::G to run under mod_perl 2 (and I don't know that much perl yet) or install side-by-side Apache 1.3 on the server to run mod_perl 1.27 and thusly A::G, which is what I did.

The tricky part is not have the two Apache versions runnning side-by-side oh no, the tricky part has been to convince mod_perl to run under perl 5.6.1 instead of the system-suplied 5.003. This has taken me the best part of the last few days...

Well, you can see <a title="don't go slashdotting it now eh!" href="http://slunj.carotena.net:81/gallery/">the results, of course!!</a> Performance is nothing to be proud of, of course, but take into account that this is just a humble AMD K6 with 128MB of RAM!

