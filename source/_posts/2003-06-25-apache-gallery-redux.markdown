---
layout: post
title: Apache::Gallery redux
---

OK, so I read a little about porting <a href="http://perl.apache.org/">mod_perl</a> modules to mod_perl 2 and realized that I wouldn't need to run <a href="http://victor.carotena.net/weblog/archives/000299.html#000299">two copies of Apache in parallel</a> if I used <code>Apache::compat</code>. I tried it, to no avail, but just saw <a href="http://www.nowhere.dk/A::G/msg00361.html">an interesting post</a> at the ApacheGallery list, which pointed to the development version of a mod_perl2 enabled A::G.

So I tried it and  <a title="Index of: /gallery" href="http://slunj.carotena.net/gallery/">it works!</a>. It uses <code>Apache::compat</code> too (which precludes it from being a proper <a href="http://www.cpan.org/" title="Comprehensive Perl Archive Network">CPAN</a> module) but in time it will be fully ported. I'll try to do it myself, too, just to see how far I can get.

