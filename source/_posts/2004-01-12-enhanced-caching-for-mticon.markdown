---
layout: post
title: Enhanced caching for MTIcon
---

I have commited to SVN an improvement to the caching system of <a href="http://victor.carotena.net/projects/mtplugins/mticon.php">MTIcon</a>. Now it uses <code>MT::PluginData</code> for storage, which is a table in the MT system designed for plugins to store their own data.

Also, now it also caches unsuccesful icon retrievals, which means that every URL will only be scanned once trying to find a shortcut reference. Even if it is not found, MTIcon will remember the URL and never ask for it again, unless you delete the specific row pointing to that URL (is very easy to spot if you need to) in the <code>mt_plugindata</code> table.

Since I want to make another change prior to the 0.8 release, you might get it from <a title="Subversion log for trunk/mticon/extlib/MTPlugins/icon.pm" href="http://slunj.carotena.net/cgi-bin/viewcvs.cgi/trunk/mticon/extlib/MTPlugins/icon.pm">http://slunj.carotena.net/cgi-bin/viewcvs.cgi/
trunk/mticon/extlib/MTPlugins/icon.pm</a> if you want to try it. Just download <code>icon.pm</code> and copy it in <code>extlib/MTPlugins/icon.pm</code>. You need to do no further changes (supposing you are already using a version newer than 0.5)

