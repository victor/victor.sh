---
layout: post
title: "What I learned today: MTS Package export"
---

I am replicating a (win2k) server at work for balancing purposes. While doing it, I am also documenting all the little nuances of all the applications that run there, just in case I need to do it again in the future. Also, I'm trying to script all the procedures that can be scripted just to reproduce all the steps faster (like website creation and naming, filesystem permissions and so on).

While moving the packages that run in the MTS, I wondered whether the installation of packages could be scripted. It turns out that yes, <a href="http://msdn.microsoft.com/library/default.asp?url=/library/en-us/dnmts/html/msdn_install.asp">they can be scripted</a>, but best of all, and that's the thing I wanted to write about, is that you can generate an installer for the packages so that you just have to run it in the new server and voilÃƒÆ’Ã‚Â  the package and all its components are there (you just have to assing the identity under which the package should run).

To do that, just open the MTS Explorer, right-click the package and select <b>Export</b>. A wizard opens asking where do you want to put the installer and whether the package will run on its own or just proxy the calls to the original server. Check the first option and complete the wizard. Then, just copy the files to the new server and install them from there. Caveat: if you just run the installer you will have to configure the package later to indicate it the identity is should run under, but if you install it from the MTS using the installation wizard and pointing to the installer, the wizard will ask you for this data. Easy ain't it?
