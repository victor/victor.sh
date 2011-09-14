---
layout: post
title: Could not access 'CDO.Message'
---

We've been having this problem intermitently when trying to send mail from within an ASP.NET application. Today, while looking for other info on the documentation, I came across a precious nugget which has helped us solve the problem.

The thing is, the .NET framework is trying to access a mail server and is not possible to connect to it (yes, the error message is misleading). Why can't it connect to the mail server? well, because of the proxy settings. As we have to access from time to time servers which the proxy cannot reach, we are constantly enabling and disabling the proxy. The framework also uses the proxy, and by default will connect to it using the configuration found in the Internet Options dialog box.
Since we develop our apps using the local IIS server, the framework is also affected by our intermitent proxy info availability.

So, either you make sure the options are right, or (and here's the secret) edit your <c>machine.config</c> file, and in the <c>/configuration/system.net/defaultProxy</c> node set up your preferences. You can also set a list of servers which the framework will bypass the proxy when connecting to.

Also, this option is configurable on an application level, too. More info on <a href="ms-help://MS.VSCC/MS.MSDNVS/cpgenref/html/gngrfdefaultproxyelement.htm">ms-help://MS.VSCC/MS.MSDNVS/cpgenref/html/gngrfdefaultproxyelement.htm</a> or, if you have not the documentation installed locally, <a href="http://msdn.microsoft.com/library/en-us/cpgenref/html/gngrfdefaultproxyelement.asp">on the MSDN library</a>.
