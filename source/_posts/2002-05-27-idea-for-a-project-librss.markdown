---
layout: post
title: "Idea for a project: libRSS"
---

I've been thinking for a few days, to begin development on a new <a href="http://mono.baselabs.org/CSAM/">CSAM</a> module, which would be called libRSS and be used for generating and consuming <acronym title="Rich Site Summary">RSS</acronym> feeds.

Coincidentally, Miguel sent today to the mono-list a link to the <a href="http://www.go-mono.com/index.rss">RSS feed for the Mono site</a>. It seems is auto-generated, but I haven't looked into it yet.

I plan to implement a <a href="http://www.hpl.hp.com/semweb/doc/tutorial/RDF_API/">Jena-like API</a> adaptation, but I'm not sure yet. It's been a long time since I last read documentation on RSS or <acronym title="Resource Description Framework">RDF</acronym>, so I don't even know which are the other APIs commonly used. I've been, however, reading some weblogs on the subject, and seems there's some controversy on the way to extend RSS. I'll try to implement the latest recommendations, if at all possible. It's always nice to be able to use up-to-date tools.
