---
layout: post
title: Recent projects
---

In another order of things, since I couldn't participate in Rails Day, and since I don't have much free time lately, I've taken the time to get documentation and do small experiments with the next projects I'm incubating, to wit: 

* A javascript syntax highlighter (ie, client side). I'm using already existing code from <a href="http://blog.dotnetwiki.org/">Jonathan de Halleux</a>, but adapting it to Firefox (and, if some kind soul helps me, to Safari as well)
* A <a href="http://www.apple.com/macosx/features/bonjour/">Bonjour</a> plugin for rails
* A tool for population biologists (ie, demographs) to calculate the Mahalanobis distance between certain individuals and whole populations. Unfortunately, I'm stuck with the *pooled within-sample covariance matrix*. Anyone knows what's the algorithm for calculating that beast?

I wish I could do a Bonjour —aka Rendezvous aka Zeroconf— plugin for Firefox as well, but XPCOM doesn't do UDP, so I'd need to do a whole new component encapsulating the <a href="http://www.porchdogsoft.com/products/howl/">howl</a> library (perhaps, adapting code from Camino?). Which, unfortunately, is too much for my skills yet :P  I'd also like to experiment with the .NET bindings, but I haven't touched .NET in a looooong time (before all the latest betas, I'd say)

**Offtopic** Any reader from New York City?

**Update 2006-07-27** Now I know that XPCOM doesn't have to do UDP, I just need to contact a local mDNS dæmon. And TIMTOWTDI(there is more than one way to do it).
