---
layout: post
title: Cross-browser transparent headers with CSS
---

Well, since you're reading this, I assume you are interested in the method because you know the goodness that comes from using PNGs, but are frustrated because the mainstream browser does not correctly support alpha blending.

You may say (as some people does) "who gives a damn? if you visitor is clueless enough to come visit your site with IE, he/she doesn't deserve to experience the joys of alpha blending!" and you might (or might not) be right, however, you can only afford to say so if you are not worried that the majority (and concrete stats depend on your site's subject matter) of users does not use standards-compliant browsers (and, to the best of my knowledge, no single browser supports 100% of the specs). While, at the same time, you are concerned over users with disabilites and their ability to access your site (yes, I'm referring to accessibility).

Well, I consider the IE users group as a group with a disability, and a majority group at that. Why not implement accesibility measures for your CSS-impaired users? So, if you care enough for your users, you may want to know how do I serve transparent headers to my visitors, regardless of which [graphical] browser they are using.

You may have read <a href="http://www.alistapart.com/stories/pngopacity/">Michael Lovitt's article at <acronym title="A list apart">ALA</acronym></a> and came, as I did, to the conclusion that implementing the AlphaImageLoader filter is not worth it if you want to serve content compatibly. If you specify the AlphaImageLoader filter in your CSS, the content is non-accesible to the standards-loving visitors. And, I prefer not to use DHTML if I can avoid it, specially when I have to implement browser detection, I'm too lazy to ensure that the contents is usable for ALL browsers (and besides, don't have the resources to do so).

Since I want to be able to change the logo and pixel art-cartoon independently from the landscape behind it, I have 2 options: either prepare the images so as to simulate transparency and fading, or devise some way to use alpha-blended images.

I do want to different styles and change them on the fly in the near future, so option A is not really an option. So, after too much time <strong>knowing</strong> exactly what I'd do if I had to, I've decided I'd do it today, since I couldn't wait more to have my decorated header. I don't want others getting the glory I deserve for being the first to describe how it's done. I haven't searched the web exhaustively, but I think no one has come up with this yet.

So, after this lengthy introduction, let me explain how it is done:

First, we'll care for the standards-respecting browsers. Let's say we have this code at the beginning of our pages:

<code class="css">&lt;div id="header">
&lt;img src="/images/header.png" alt="Syntactic Saccharose" />
&lt;/div>
</code>

Pretty straightforward, isn't it? How would you proceed to give it a background, transparent or not?

Well, by putting this in the CSS:

<code class="css">#header {
background-image: url(http://victor.carotena.net/images/ThinkDifferent.png);
background-repeat: no-repeat;
}
</code>

If your overlapping logo happens to be alpha-blended, you're done (if not, load your image-manipulation app of choice and clear the background, resave, and reload the page).

Now, what about Internet Explorer?

OK, let's decide what needs to be done. We need to apply an image filter, AlphaImageLoader to be specific, which loads the image as it is intended to be. Since this tecnique only applies an image over an existing element, we need to be sure of two things: that the existing element is already clear, and that we can apply a second filter to load a second image on top of the first. Let's first see how would this be done, if we weren't caring for standards-compliant browsers:

<code class="css">#header img {
visibility: hidden;}
#header {
height: 50px;
background: #666699;
filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(
src='http://victor.carotena.net/images/ThinkDifferent.png',
sizingMethod='image') progid:DXImageTransform.Microsoft.AlphaImageLoader(
src='http://victor.carotena.net/images/header.png',sizingMethod='image');
}
</code>

Yes, I'm reapplying the background property, just to make sure IE does not load an  image on it. You can also see what's the correct manner to chain two consecutive filters, and that I'm using the <code>image</code> scaling method to be able to use two differently-sized images, without specifying an explicit size.

However, how do you have IE apply this CSS, while at the same time have other browsers ignore it? That is, how did I make it cross-browser? Well, if you have been impatient, you'll already seen the CSS for this page. It exploits a IE-only CSS parsing bug, which makes it override the previous style definitions and apply the later ones:

<code class="css">/* IE-ONLY */
* html body div#header img {
visibility: hidden;}
* html body div#header {
height: 50px;
background: #666699;
filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(
src='http://victor.carotena.net/images/ThinkDifferent.png',
sizingMethod='imagee') progid:DXImageTransform.Microsoft.AlphaImageLoader(
src='http://victor.carotena.net/images/header.png',sizingMethod='image');
}
</code>

What's all this? If you look at the selectors, you'll see that I specify all these properties for a concrete set of elements, that is, all <code>div</code> tags marked with the header identifier, and the <code>img</code> tags within, that happen to be inside a <code>body</code> element tag, inside an <code>html</code> tag (up to here, perfectly normal) inside any other tag. But wait a moment! How many such elements do exist, in a normal (x)html page? 

Actually, zero such elements. However, a bug in IE makes the <code>star html</code> selector incorrectly select the root <code>html</code> element, and thus unmistakably make IE reveal itself. While there is no such element in a well formed, valid XHTML document, the selector is itself still valid, which gives us the additional benefit of exploting a browser specific bug while having the CSS be perfectly valid (or as much as it can be, using the filter property). The credits for discovering this bug go to <a href="http://www.info.com.ph/~etan/w3pantheon/style/starhtmlbug.html">Edwardson Tan</a>.

And that's all, it is really that simple. I hope I made myself clear with the explanation. If not, or you care to comment on the tecnique, please leave some feedback, either a comment or a trackback will do. I'd like to write more posts like this, and I'm sure some feedback would encourage me still more to do so. Write also if you decide to use this method, no credits are needed, it's just that I'm curious as to where it ends up being used.
