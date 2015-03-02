---
layout: post
title:  "Colorblindproof syntax highliting"
date:   2015-02-18 23:05:36
categories: howto
tags: Patternfly colorblindness Syntaxhighliting
---

A few years ago I worked with a client that was [color blind](http://en.wikipedia.org/wiki/Color_blindness). 

Eight percent of Caucasian men are color blind, this is made of mostly Deuteranope (Green-blind), follow by Protanope (Red-blind) and very rarely Tritanopia (Blue-blind). What is even more rare is Monochromatic, total color blindness.

My client was the totally color blind. He saw in shades of greys and I can only wonder how the world looks through his eyes.

That was a huge problem to him. From little things like depending on his wife to dress to go work every morning, to more dangerous one, like not knowing if a traffic signal was red or green when he was travelling in a place where the traffic lights where horizontal instead of vertical. 

And of course he sent me to talk to his wife when I arrived at his office with pantone samples.

Although I did study color theory and light physics is something that always interest me, I must confess that until then I've had never really though about color blindness. You could say I was a bad designer.

Joseph Albers said:

>Every perception of color is an illusion...we do not see colors as they really are. In our perception they alter one another.


## What is color bliness

A normal color vision person is capable of perceiving all three primary colors of light: Red, Green, and Blue.

**Color blindness is the complete inability to perceive one or more of the three primary colors of light.**

With color deficient vision, it is more difficult to discriminate all three dimensions of color: hue, value, and chroma. The severity of color vision deficiencies ranges from a little difficulty in distinguishing similar hues to the inability to perceive any color at all. **But all people with color-deficient vision can perceive differences in value and most can see a fairly wide range of hues.**

In general, if the Red value is greater than the Blue, it appears in the yellows group, and if Red is less than Blue it appears in the Blues group. A color generally appears neutral when Green equals Blue, more or less regardless of the value for Red.


## Syntax highliting

Last week I've been involved in [implementing syntax highlighting](https://github.com/patternfly/patternfly/commit/33bafaab0950847893d3b784dbcd40eec0bd453f) on [Patternfly](https://www.patternfly.org).

There are lots of [themes](http://vimcolorschemetest.googlecode.com/) and [although it's almost never an issue for color blind users](http://gotoanswer.stanford.edu/?q=Syntax+Coloring%3A+Is+it+harder+for+color-blind+coders+to+program%3F), to proof this concept I decided to create one for this blog.

With that in mind and using colors picked from Googles [Material Design color pallete](http://www.google.com/design/spec/style/color.html#color-color-palette), I came up with this theme:

#### HTML

{% highlight html %}
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
    <title>A Tiny Page</title>
    <link href="css/styles.css" rel="stylesheet" media="screen, print">  
  </head><!-- real comment -->
  <body>
    <script language="javascript" type="text/javascript">
          function changeHeight(h) {
            var tds = document.getElementsByTagName("td");
            for(var i = 0; i < tds.length; i++) { 
              tds[i].setAttribute("height", h + "px");
          }}
    </script>
    <p>Testing page</p>
  </body>
</html>
{% endhighlight %}

#### JAVA

{% highlight java %}
import java.util.Map;
import java.util.TreeSet;

public class GetEnv {
  /**
   * let's test generics
   * @param args the command line arguments
   */
  public static void main(String[] args) {
    // get a map of environment variables
    Map<String, String> env = System.getenv();
    // build a sorted set out of the keys and iterate
    for(String k: new TreeSet<String>(env.keySet())) {
      System.out.printf("%s = %s\n", k, env.get(k));
    }
  }
}
{% endhighlight %}


Side by side, the first image is the original, second is a Protanopia view, next is a Deuteranopia view and last is Monochromatic.

![color theme comparison](/img/colorblind/compare.jpg)

This blog is based on [jekyll](http://jekyllrb.com/) and it has built in support for syntax highlighting thanks to [Pygments](http://pygments.org/). In case you want to use this colorblind friendly theme for Pygments, [the source is here](https://github.com/andresgalante/andresgalante.github.io/blob/master/_sass/_syntax-highlighting.scss).


## How to test it

There are several tools to test color blind images. After trying a few of them, I found that these two come in handy:

#### 1. Photoshop

To test images, Adobe Photoshop under **View > Proof Setup > Color Blindness**, has an option to view images with Green-blind or Red-blind filters.

![adobe photoshop view option as color blind](/img/colorblind/ps.jpg)

#### 2. Chrome

On the browser, [Spectrum](https://chrome.google.com/webstore/detail/spectrum/ofclemegkcmilinpcimpjkfhjfgmhieb?hl=en) is an excellent plugin for Chrome to test your colors.

![Spectrum to test color blind on the browser](/img/colorblind/rh.jpg)


## The translator

Last year, while doing the first steps with my startup [Outclass](http://www.outclassapp.com), we've been invited to a pre acceleration program called [Startup SC](http://www.startupsc.com.br). We share that experience with other startups, one of them was [True Vision](http://www.truevision.io).

They have wichcraft a way to "translate" colors for color blind people. A small device is plug into your TV or computer, the user sets up it up and it adjust hue and saturation of the image. They even developed a mobile app.

Until all devices come with this kind of solutions as default there will be a need to always test colors.


#### References:

- [uxmatters.com/mt/archives/2007/02/ensuring-accessibility-for-people-with-color-deficient-vision.php](http://www.uxmatters.com/mt/archives/2007/02/ensuring-accessibility-for-people-with-color-deficient-vision.php)
- [nngroup.com/articles/accessible-design-for-users-with-disabilities/](http://www.nngroup.com/articles/accessible-design-for-users-with-disabilities/)
- [bconnelly.net/2013/10/creating-color blind-friendly-figures/](http://bconnelly.net/2013/10/creating-color blind-friendly-figures/) 
- [safecolors.rigdenage.com/colors.pdf](http://safecolors.rigdenage.com/colors.pdf)
- [zingdesign.com/web-design-guidelines-for-color-blind-users/](http://www.zingdesign.com/web-design-guidelines-for-color-blind-users/)
- [optional.is/requiRed/2011/06/20/accessible-color-swatches/](http://optional.is/requiRed/2011/06/20/accessible-color-swatches/)




