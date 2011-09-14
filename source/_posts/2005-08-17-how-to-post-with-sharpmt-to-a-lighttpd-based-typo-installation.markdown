---
layout: post
title: How to post with SharpMT to a lighttpd-based typo installation
---

Allright? Ok, let's continue. Since the expect header *is not strictly needed*, we can manipulate the request to drop it. What is fiddler then? Fiddler is the tool that will allow us to massage the request before it is actually sent down the wire. Fiddler is a tool, useful for debugging, that sits as a proxy on our side, allowing us to examine and manipulate the HTTP streams as they co&#109;e in and out of our machine. For our purposes, we need SharpMT to tunnel its request through this proxy, which can be accomplished in two ways: either we set up SharpMT to use a proxy, or we instruct fiddler to act as a system proxy, which has the inconvenient that all requests will go through it, obscuring a bit what we are trying to see.

Fiddler, by default, uses port 8888, so the proxy we'd need to configure is at 127.0.0.1:8888.

I'll assume you've already configured SharpMT, however you want it. You can try a few requests (for example, refresh categories on your blog) to have a feeling of how fiddler works. What's the next step then? Well, the good thing about fiddler is that it is scriptable, so that we can automate manipulations to the requests and responses without needing to intervene. If you go to Rules/Customize rules, an editor window will open with the default scripts. Let's add the following code:

below
	public static RulesOption("Request &Japanese Content")
	var m_Japanese: boolean = false;

add:

	public static RulesOption("Chomp Expectations")
	var m_ChompExpect: boolean = false;

This instructs fiddler to add a new menu option, to enable and disable our automatic manipulations. The actual manipulation is done a bit further down the code. In the `OnBeforeRequest` function, just before the closing curly bracket, add:

		if (m_ChompExpect) {
			oSession.oRequest.headers.Remove("Expect");
		}

Save the script and exit the editor. Now, you should have, under the Rules menu, a menu option called "Chomp Expectations". If you enable it, the `Expect` header will be dropped if it is present, allowing you to post successfully to your Typo based blog.

Since I have only tested this on two computers, please leave your feedback using the comments below if you try it. Thanks.

**PS** I actually had my request blocked, but because some filthy words I inadvertently used which made the anti-spam filter my hosting provider uses to overreact. Apparently, having requests come to your machine is frowned upon by the powers that be when you refer to said requests as *they*. Fortunately, the filter is a bit lame and with some entity hacking is easily bypassed.
