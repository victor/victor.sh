---
layout: post
title: Difficulties porting uptime.NET to linux
---

Bummer!
After #ifdefing out the Performance Counters, I successfully compile my classes... only to discover that in Mono, <code>System.Environment</code> is only stubbed, and its property <code>OSVersion</code> just returns <c>null</c>!!

Time to learn about <code>PInvoke</code> and implement it myself?

<b>Update @01.43:</b> Yet as I catched the <code>NullReferenceException</code> throwed by the incompleteness of <code>Environment.OSVersion</code>, I realize that <code>Single.Parse(string)</code> is unimplemented too :(
I've been looking into the <code>PInvoke</code> thing. The difficult part, is to have it do different things on different platforms. The funny thing is, this would serve to know in which platform is being called... Once you know which code you should call (a <code>PInvoke</code> into a <code>.dll</code> or a <code>.so</code>), you don't need it anymore! It's kinda like an uncertainty principle
mmmm does it ring any bells? why do I have the feeling I am overlooking something obvious?
