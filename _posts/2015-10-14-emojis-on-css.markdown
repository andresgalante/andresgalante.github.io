---
layout: post
title:  "Spice up your CSS with Emojis"
date:   2015-10-14 23:05:36
categories: howto
tags: emoji jekyll css html setup
---

Jeff Atwood, creator of Stack Overflow and one of the best blogers there is, says that a blog without comments is not a blog. I'd like to add that a blog without [emoji](https://en.wikipedia.org/wiki/Emoji) is not a blog. But that's not the hole truth, emojis go way further. **A life without emoji is like the weekly PM meeting: boring**.

Andy Warhol said:

> I like boring things.

And Leo Tolstoy wrote: 

> Everything intelligent is so boring.” 

Which makes the weekly PM meeting an intelligent art masterpiece.

# Emijis on Jekyll

Adding emojis to a [jekyll](https://jekyllrb.com) blog is easy. Just add the [jemoji gem](https://github.com/jekyll/jemoji) to your site's `_config.yml`

{% highlight bash %}
# adds emoji
gems:
  - jemoji
{% endhighlight %}

Then you can go to [any emoji cheatsheet](http://www.emoji-cheat-sheet.com) to get the reference for the emoji.

For example here is a cute panda face :panda_face:

# Emijis on CSS

I've heard that you could use emoji as class names, but it blew my mind to actually test it. Ofcourse this is completely useless, but it's as cool as CSS can get.


For example, if I want to build a section for Funny Hot News, I can name it like this: :smiley: :fire: :newspaper:

<div data-height="220" data-theme-id="20015" data-slug-hash="jbGqXj" data-default-tab="html" data-user="andresgalante" class='codepen'><pre><code>&lt;div class=&quot;😃🔥📰&quot;&gt;
  This is the Funny Hot News section!
&lt;/div&gt;</code></pre>
<p>See the Pen <a href='http://codepen.io/andresgalante/pen/jbGqXj/'>Emoji CSS class names</a> by Andres Galante (<a href='http://codepen.io/andresgalante'>@andresgalante</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
</div><script async src="//assets.codepen.io/assets/embed/ei.js"></script>


These are just a few ways to use them, now go and [Spice Up Your Life](https://youtu.be/9wfpXI5PKlw) with emojis.


