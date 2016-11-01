---
layout: post
title:  "Dance to the new PatternFly flow"
date:   2016-10-22 23:05:36
categories: patternfly
tags: news patternfly spacing CSS
---

![PatternFly new visuals](/img/spaces/spaces.jpg)

If you follow this blog you should know that for the past two years I’ve been a contributor to [the PatternFly project](https://www.patternfly.org/). Five month ago, I've joined the PatternFly team and I am working full time to push the boundaries of open source design.

We are currently working on PatterFly 4, a major release that will include design and code improvements. The two main design changes that we are introducing are around typography and spaces, including a much necessary [font size base bump](https://medium.com/attack-the-front/your-body-text-is-too-small-5e02d36dc902#.o9y3t6r40) to 14px and moving our font family from [Open
Sans](https://fonts.google.com/specimen/Open+Sans) to [Overpass](http://overpassfont.org/).

You can read all about these typography revisions on [Kyle Bakers](https://github.com/orgs/patternfly/people/kybaker) [article on the PatterFly blog](https://blog.patternfly.org/choosing-the-best-font-for-application-design/).

## Spacing, Rhythm and Flow

One of the key elements of both print and web design is the way the typography flows, we call it Rhythm.

There are several books and articles explaining what Typographic Rhythm is. If you are looking for an in depth detail about typography you should read [The Elements of Typographic Style](https://www.amazon.com/Elements-Typographic-Style-Robert-Bringhurst/dp/0881791326) else, I recommend [this article by Shelly Wilson](http://typecast.com/blog/4-simple-steps-to-vertical-rhythm) on the [typecast blog](http://typecast.com/):

> Rhythm is just a repeated pattern. The more consistent the pattern, the better the rhythm. In music, it’s the structure that ties all the different instruments together. Even if the notes are correct, a song with an inconsistent rhythm is pretty hard to listen to.

> In design, vertical rhythm is the structure that guides a reader’s eye through the content. Good vertical rhythm makes a layout more balanced and beautiful and its content more readable.

> The time signature in sheet music visually depicts a song’s rhythm, while for us, the lines of the baseline grid depict the rhythm of our content and give us guidelines to align text and objects to.

Therefore the typographic change we are introducing to PatternFly 4 would be incomplete without an overall adjustment of spaces.

## Relative spaces

To define spaces on PatternFly 4 we will use [CSS relative units](https://developer.mozilla.org/en/docs/Web/CSS/length).

Each one of these units are relative to a different base, some are based on the viewport size, others to the size of the container element, and others to the size of the font.

In our case we will use `rem`. The [W3C CSS specs](https://www.w3.org/TR/2016/CR-css-values-3-20160929/#rem) define `rem` as:

> Equal to the computed value of font-size on the root element. When specified on the font-size property of the root element, the rem units refer to the property’s initial value.

Since PatterFly 4 root font size is `14px`, then `1rem = 14px`, `2rem = 28px`, `0.5rem = 7px`... well you get the idea.

This system will define all our spaces, from typography, paddings and margins to grids and gutters.

## Variables and utility classes

To ensure consistency we are delineating spacing with Sass variables and utility classes.

Since PatterFly 4 is based on [Bootstrap 4](http://v4-alpha.getbootstrap.com/), we will be able to [take advantage](http://v4-alpha.getbootstrap.com/utilities/spacing/) of the [nifty utility sass variable](https://github.com/twbs/bootstrap/blob/v4-dev/scss/_variables.scss#L79-L100) to build our spacing.

Using sass variables to set the utility classes will keep our code DRY, maintain consistency and allowing users to easily create spaces on their implementations.

## Work in progress

As a start point we are basing our components on a set of default spaces:

{% highlight sass %}
$spacer:   1rem;
$pf-spacer-xxxs:   ($spacer * .25);   // ~3px
$pf-spacer-xxs:    ($spacer * .5);    // 7px
$pf-spacer-xs:     ($spacer * .75);   // ~10px
$pf-spacer-sm:     $spacer;           // 14px
$pf-spacer-md:     ($spacer * 1.25);  // ~17px
$pf-spacer-lg:     ($spacer * 1.5);   // 21px
$pf-spacer-xl:     ($spacer * 1.75);  // ~24px
$pf-spacer-xxl:    ($spacer * 2);     // 28 px
$pf-spacer-xxxl:   ($spacer * 2.5);   // 35 px
$pf-spacer-xxxxl:  ($spacer * 3);     // 42 px
{% endhighlight %}


But I am sure that as we move forward adding components to the [new PatterFly Atomic repo](https://github.com/patternfly/patternfly-atomic), we will need to adjust removing or adding variables.

## Want to dance with us?

This is without a doubt the best CSS project I've ever work with.

If you want to join the talented **UXD CSS Army:heart:** send an email to [the PatterFly mailing list](mailto:patternfly@redhat.com), contact us on the [Slack](http://patternfly.slack.com) or [IRC channel](http://webchat.freenode.net/?channels=#patternfly), or just [fork the repo](https://github.com/patternfly/patternfly-atomic) and send us a PR :smile:
