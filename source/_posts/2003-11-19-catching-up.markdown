---
layout: post
title: Catching Up
---

<h5>Let's start with Subversion</h5>

I've grown a taste for Subversion. Never have actually made much use of <acronym title="Concurrent Versioning System">CVS</acronym> or RCS either, so I can't really speak about their limitations, but the fact that it hasn't much of their limitations makes me feel good about using <acronym title="Subversion">SVN</acronym>.

I thougt about a better view of browsing the source trees, since the <a href="http://slunj.carotena.net/svn/mtplugins">normal view</a> isn't very appropiated for anything more than casual browsing, as it is intended for updating your local source trees rather than navigating around.

I settled for <a href="http://viewcvs.sourceforge.net/">ViewCVS</a>, which also has support for <acronym title="Subversion">SVN</acronym>. Or at least that's what I deducted from reading mailing lists and browsing the CVS tree at SourceForge. Unfortunately, the last released version of ViewCVS has been 0.9.2 for a long time, and it doesn't incorporate the support for SVN, and since the FreeBSD ports tree is mostly based on stable released versions, I got all kind of problems trying to browse <a href="http://slunj.carotena.net/cgi-bin/viewcvs.cgi/">my SVN repositories</a> with that version, until I was told to use the CVS version. Which I did, and finally I was able to browse them with a niftier interface.

One of the hurdles I had to jump was that the FreeBSD version of Subversion (which I got updated in the process) does not build the SWIG bindings (that is, the bindings for languages like Perl and <a href="http://python.org/">Python</a>) by default. I had to hack the Makefiles to got them to build, and it wasn't an easy feat. I won't post the details since they escape me after so many tests and because they seem to change from version to version. In the end, I could build them with no small effort, and it is no wonder that the current port maintainer prefers to disable them.

I looked for other uses I could put <a href="http://subversion.tigris.org/>Subversion</a> to. In its site I found a <a href="http://c2.com/cgi/wiki?WikiWikiClones">WikiClone</a> that used the Python bindings. Unfortunately, I couldn't get it to work.

While looking for documentation on the bindings, I fell upon the <a href="http://svn.elixus.org/svnweb/repos/browse/member/clkao/svn-perl/">SVN::perl</a> development tree, which were the basis for the perl bindings that now are integrated in Subversion. The tree can be browsed using a similar approach to ViewCVS, but using SVN::Web, which uses the Perl bindings themselves to access and serve a repository.

I had considered for a long time to install a wiki on this website. After the frustrating attempt to install subwiki, I decided I'd look for a wiki implemented in Perl.
Since I didn't wan't to spend too much time installing and configuring the WikiEngine, I looked into the ports tree. This reduced the choice to <a href="http://twiki.org/">Twiki</a> and <a href="http://kwiki.org/">Kwiki</a>. After reading some comments on the <acronym title="Barcelona PerlMongers">Barcelona.pm</acronym> mailing list, I decided to begin by installing Kwiki.

<h5>Kwiki</h5>

Kwiki is a simple Wiki that allows for an easy customization and extension. After a few hours playing with it,  I discovered it was the right choice. The CSS selectors in its default template match those of <a href="http://movabletype.org/">Movable Type</a>, that's why the <a href="/wiki">wiki</a> resembles so much the main site. There are also plugins, which I'll install in due time, to allow for wiki content to be pulled into a MT site.
I also discovered a nifty extension made by Taiwanese Perl hacker <a href="http://autrijus.org/">Autrijus Tang</a>, of <a href="http://par.perl.org/" title="Perl Archive Toolkit">PAR</a> fame (of the same perl programmers team as the author of SVN::perl ), that  allows for the metabase (the content and its changes) to be backed up by a SVN Repository.


As I said, Kwiki is easily extendable. I will be sending some patches soon.
I tried to configure Kwiki to be run as a mod_perl module, however, it is not quite ready for mod_perl 2, there are still some glitches to be ironed out. This is something that I'd like to improve, too.
