---
layout: post
title: Further toying with FreeBSD
---

Now that I've got a decent internet connection at home, I have begun to play again with my old K6 machine, which I put FreeBSD onto. I can now do a <code>cvsup</code> to update the ports collection and install new software.

Since I also (for the time being) have a fixed IP address, I have pointed the <code>slunj.carotena.net</code> subdomain to it. I installed the latest version of Apache, but can't install mod_perl with it, which means no Apache::Gallery yet. I have, however, being able to use <a href="http://www.openssl.org/" title="OpenSSL suite">OpenSSL</a> to create my own <acronym title="Certification Authority">CA</acronym> and have a secure communication with it (which will be of use when using webmail) besides <acronym title="Secure Shell">SSH</acronym>.

So, now my trusty old K6 runs <a href="http://uptime.netcraft.com/up/graph/?host=slunj.carotena.net">Apache mod_ssl</a> :)
