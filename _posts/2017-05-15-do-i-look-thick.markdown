---
layout: post
title:  "Do I look thick?"
date:   2017-05-15 08:00:00
categories: css
tags: css design patternfly
---


![Border width makes no sese](/img/border/border.jpg)

You know that feeling when you use an obscure color name? There is something special about using CSS keywords... or maybe there’s just something really wrong with me.

This week I massaged my ego by trying to use keywords for border width on [PatternFly](https://www.patternfly.org/). My reasoning was that since nowadays we use relative units for everything except from borders, maybe by using keywords we can achieve cleaner results and ditch fixed units once and for all.

I couldn’t be more wrong.

## Thin, Medium, Thick, what is it it good for? Absolutely nothing!

The [CSS Backgrounds and Borders Module Level 3](https://www.w3.org/TR/css3-background/#the-border-width) defines `border-width` as the property that sets the thickness of the border. Where:

> “The lengths corresponding to ‘thin’, ‘medium’ and ‘thick’ are not specified, but the values are constant throughout a document and thin ≤ medium ≤ thick. A UA could, e.g., make the thickness depend on the ‘medium’ font size: one choice might be 1, 3 & 5px when the ‘medium’ font size is 17px or less. Negative <length>values are not allowed.”

After testing these keywords on different browsers we’ve got consistent results:

- 1px for `thin`,
- 3px for `medium`,
- and 5px for `thick`.

High density screens like a retina display or an iPhone renders 2 times value, as expected. For example a `thin` line will render 2px on an iPhone.

I’ve also noticed that the thickness is not attached to the font size since, meaning it doesn’t change when I modify the font size.

## Awesome! so, what’s the matter?

The problem is that the spec is so loose that renders these keywords useless.

The fact that a browser is allow to display `thin`, `medium` and `thick` the exact same width or even change following other measurements like font-size makes using these keywords unpredictable.

Building with `thin`, `medium` or `thick` would be the same as building over quicksand. Today ‘thin’ means 1px, tomorrow we don’t know.

## The px to rems Sass converter mixin

If you do want to write relative units based on pixels, there are [many sass mixings](https://css-tricks.com/snippets/css/less-mixin-for-rem-font-sizing/) you can use. I wrote a small Sass function to translate `px` to `rem` too:

{% highlight sass %}
$font-size-root: 16; // Most browsers font size base is 16

@function px-to-rem($px-value) {
  @return ($px-value / $font-size-root) * 1rem;
}

.one-px-border { border-width: px-to-rem(1) }
{% endhighlight %}

And you can [read all about it on this blog post](http://blog.andresgalante.com/css/2017/01/27/font-size.html).

Although this is still quicksand, it’s a better solution. The browser font size base can vary and the border will change when the root font size changes, but  hey, maybe that’s what you are looking for anyway!

## What did I learn?

<iframe width="560" height="315" src="https://www.youtube.com/embed/emHSO5dr6dk" frameborder="0" allowfullscreen></iframe>

CSS, much like life and the TV show “Friends” teaches us that the answer to the questions “Do I look `thick`?” doesn’t really matters since it’s always a lie.

I’d love to hear what you think about this. Should I just use pixels and stop whining about it?
