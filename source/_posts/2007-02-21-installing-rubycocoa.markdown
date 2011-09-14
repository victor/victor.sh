---
layout: post
title: Installing RubyCocoa
---

Since the first exercise on the book - on chapter 2- consists merely on following along the instructions and build a simple application, I'm gonna start by doing this same exercise with Ruby. To that end, the [RubyCocoa](http://rubycocoa.sourceforge.net/doc/) bridge must be installed.

I use the ruby from  [MacPorts](http://www.macports.org/) (formerly known as DarwinPorts), so I can't use the binary that one can download from RubyCocoa's site, since that is for the ruby that comes with Mac OS X Tiger. If that were your case, just download the biinary, but be warned that Apple's ruby is buggy.

Installing the bridge is as simple as


    sudo port install rb-cocoa


The system will fetch and install the newest version available from the bridge. If a message like this appeared


>Error: Target com.apple.activate returned: Image error: /Developer/Documentation/RubyCocoa/build.en.html already exists and does not belong to a registered port.  Unable to activate port rb-cocoa.

it means that you already had the package installed for Apple's ruby and in trying to install it, it finds some conflicting files (while they are installed in different places, some files do indeed go to the same place, such as documentation and XCode templates). In that case, you will have to use the following command to activate the port:


    sudo port -f activate rb-cocoa

To check that it's working, we'll invoke the interactive interpreter:


    $ irb
    irb(main):001:0> require 'osx/cocoa'
    => true



