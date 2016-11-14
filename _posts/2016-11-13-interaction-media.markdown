---
layout: post
title:  "Just because a device is large, he doesn't mean he doesn't want to be touched"
date:   2016-11-13 10:00:00
categories: css
tags: css design patternfly
---

![Touch screens media query](/img/touch/touch.jpg)

Let’s face it, front end development is a bitch.

As we started discussing how to design enterprise application UI element on mobile environments, the talented ladies working with me (yes, I am talking about you Jenn and Sarah) pointed out that touch devices should not be judge by their size.

Assuming that a small viewport device has a touch screen and a large doesn’t is a mistake since the twisted minds in the hardware industry have created massive touchscreen TVs, really large tablets like the iPad Pro and even a huge touch desktop PCs like the new (and jaw dropping) Surface Studio.

This adds a new layer of complexity to the already complicated world of interaction design and front end development.

Responsive viewport media queries are great to accommodate our UIs elements, but designing small clickable areas on large screens guessing that our users will have a mouse pointer is a mistake.

We know we can detect touch screens with tools like [modernizr](https://modernizr.com/), but I want to keep our [PatternFly](http://www.patternfly.org/) CSS efforts away from javascript. Is there a way to query a touch screen with CSS? Spoiler alert: the answer is yes!

## Interaction Media Features

[The nice people at the W3C CSS Working Group](https://www.w3.org/Style/CSS/members.en.php3) have been guiding the CSS community to a solution.

On the [Media Queries Level 4 Working Draft](https://drafts.csswg.org/mediaqueries/) there is a spec for [Interaction Media Features](https://drafts.csswg.org/mediaqueries/#mf-interaction) that includes three definitions: [Pointing Device Quality](https://drafts.csswg.org/mediaqueries/#pointer), [Hover Capability](https://drafts.csswg.org/mediaqueries/#hover) and [Rare Interaction Capabilities](https://drafts.csswg.org/mediaqueries/#any-input).

Together they allows a media query to be set based on the presence and accuracy of the user's pointing device, and whether they have the ability to hover over elements on the page.

Let’s take a close look at each one of them.

### Pointing Device Quality: the pointer feature

> “The pointer media feature is used to query about the presence and accuracy of a pointing device such as a mouse. If a device has multiple input mechanisms, the pointer media feature must reflect the characteristics of the “primary” input mechanism, as determined by the user agent.” - W3C

The key word here is “accuracy” of the pointing device.

* A mouse or a drawing styluses is very accurate and it takes the value of `fine`.
* A finger or a Kinect peripheral isn’t, and it takes the value of `coarse`.


Therefore we can detect if a screen is touch with a simple media query. This is useful for example to make hit areas larger if the user has a touch screen.

{% highlight css %}
@media (pointer: coarse) { ... }
@media (pointer: fine) { ... }
{% endhighlight %}


### Hover Capability: the hover feature

> “The hover media feature is used to query the user’s ability to hover over elements on the page. If a device has multiple input mechanisms, the hover media feature must reflect the characteristics of the “primary” input mechanism, as determined by the user agent.”

It’s important to notice that it only evaluates the primary input device. A device with multiple input mechanisms that’s able to hover will query as “none”.

> “For example, a touchscreen where a long press is treated as hovering would match hover: none.”

* A touch screen device where the primary point system is the finger and can’t hover will take the value of “none”
* A device where the primary input is mouse and can easily hover parts of the page takes the value of “hover”

{% highlight css %}
@media (hover: hover) { ... }
@media (hover: none) { ... }
{% endhighlight %}

A classic example to use this query is a dropdown menu.

### Rare Interaction Capabilities: the any-pointer and any-hover features

> “The any-pointer and any-hover media features are identical to the pointer and hover media features, but they correspond to the union of capabilities of all the pointing devices available to the user. More than one of their values can match, if different pointing devices have different characteristics. They must only match none if all of the pointing devices would match none for the corresponding query, or there are no pointing devices at all.”

This is rarely used. An example can be a touch TV that also has a pointer device.

### Device examples

Typical examples of devices matching combinations of pointer and hover:

|   | `pointer: coarse` | `pointer: fine` |
| `hover: none` | smartphones, touch screens | stylus-based screens (Cintiq, Wacom, etc) |
| `hover: hover` | Nintendo Wii controller, Kinect | mouse, touch pad |

This is really cool, right? I hear you shouting: what about browser support?

## Browser support isn’t :poop: at all!

Even though this is a working draft it has [pretty good support](http://caniuse.com/#feat=css-media-interaction).

[My simple test](http://codepen.io/andresgalante/pen/bBEJKg?editors=0100) proved successful on Chrome, Chrome for Android, Safari, Edge, Opera, Samsung browser and Android Browser but it didn’t work on FireFox, Opera Mini or IE.

<iframe height='300' scrolling='no' title='Touch screen test' src='//codepen.io/andresgalante/embed/bBEJKg/?height=300&theme-id=20015&default-tab=css,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>
</iframe>

FireFox and IE [represent only a bit more than 2% mobile/tablet browser market share](https://www.netmarketshare.com/browser-market-share.aspx?qprid=0&qpcustomd=1). I couldn’t find information about touch TVs or other touch screens devices that are not mobile or tablets.

I think we are ready to take the progressive engagement approach with this feature, and as FireFox adds support for it and IE dies once and for all we will have full support.

## Have I mention that front end development is a bitch?

This exponentially opens the door to exciting new challenges (and by “challenges” I mean “problems”).

The obvious immediate enhancement on our UIs are around click zones with `pointer` and dropdowns with `hover`. But I am sure there are nifty mysterious ways to use these features that people smarter than me (and I am pointing at you Jenn and Sarah again) will discover.
