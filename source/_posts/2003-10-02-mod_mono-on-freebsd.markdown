---
layout: post
title: Mod_mono on FreeBSD
---

Notes on building:

<ul><li>FreeBSD's <code>make</code> utitlity is not the GNU version. Use <code>gmake</code> instead.</li>
<li>FreeBSD does not have the <code>signbit</code> macro. I've applied <a href="http://lists.ximian.com/archives/public/mono-devel-list/2003-August/001930.html">Rui Lopes' patch</a> and it does compile now.</li>
<li><strike>Either mcs takes a long time to compile or I have a setup problem. It's compiling since yesternight (it's a K6 @200Mhz with just 128MB, but still)</strike></li>
<li>I need to use a <a href="http://www.go-mono.com/daily/">monocharge</a> to use an updated <code>mcs</code> to compile mcs itself. Duh!</li>
<li>It's no use trying to use the releases straight from the web. Fortunately, the FreeBSD port has been updated. It seems mcs is version 0.27 though, but it can now build mcs-0.28 correctly. Yay!</li>
</ul>

Alternatively, see <a href="http://slunj.carotena.net/bugzilla/show_bug.cgi?id=2">Bug #2</a> for more info.
