---
layout: post
title:  "The RGBA to feColorMatrix converter"
date:   2016-07-09 23:05:36
categories: random
tags: howto patternfly setup npm bower
---

![Red Hat Summit Keynote Demo](/img/rgbtocolor/rgba-to-color-matrix.jpg)
This year I've been lucky enough to be part of the team building the Red Hat keynote demo at [Red Hat Summit](https://youtu.be/tPqbM3buK8M).

The presentation ended up dynamically building a picture mosaic of the Red Hat logo out of selfies taken by the audience. It was an impressive visualisation that I helped [Brian Leatheam](https://twitter.com/brianleathem) create.

<!-- You can check the complete story in this DevNation talk: -->

## Process
Mapping an image and building a mosaic following some CSS filters and blend modes took about 3 days to a skilful DOM manipulator like Brian.

But we've spent at least a moth iterating on designs details, trying new animations and optimising the performance.

During one of those iterations, and aiming to achieve good performance and smooth animation we've tried SVGs instead of HTML images. That also implied changing our CSS blend modes to an SVG filter, in this case the `feColorMatrix` filter.

## The feColorMatrix SVG filters

> The [feColorMatrix](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/feColorMatrix) is an SVG filter that changes colors based on a transformation matrix. Every pixel's color value (represented by an [R,G,B,A] vector) is [matrix multiplied](https://en.wikipedia.org/wiki/Matrix_multiplication) to create a new color.

This filter is really powerful and allows granular per channel color manipulation, kinda like editing the channels on Photoshop.

[Una Kravets](http://una.im/) wrote an [excellent list apart article](http://alistapart.com/article/finessing-fecolormatrix) explaining how to use it.

## RGBA to feColorMatrix

Color manipulation with `feColorMatrix` seems limitless, I could colorise an element any way I wanted. But what I needed for the mosaic was to reproduce an exact RGB value into the color matrix, and that was tricky.

It's not a common problem to have, no one was asking about it on [StackOverflow](https://stackoverflow.com/).  But the answer was simple.

Since RGB are based on a 255 scale, I just needed to divide the RGB value by 255 and I get the matrix value for each channel.

![RGBAtoFeColorMatrix preview](/img/rgbtocolor/preview01.jpg)

For example RGB `255, 255, 255` becomes:

```
1 0 0 0
0 1 0 0
0 0 1 0
0 0 0 1
```

![RGBAtoFeColorMatrix preview red](/img/rgbtocolor/preview02.jpg)

Pure red `255, 0, 0` becomes:
```
1 0 0 0
0 0 0 0
0 0 0 0
0 0 0 1
```

![RGBAtoFeColorMatrix preview pink](/img/rgbtocolor/preview03.jpg)

And a pink `255, 30, 150` becomes:
```
1     0     0     0
0     1.22  0     0
0     0     0.59  0
0     0     0     1
```

Now that I had the math sort out it was easy to colorise our mosaic.

## Sharing is caring

In the very odd chance that there is someone else out there trying to transform an an RGA value into a color matrix, I set myself to build an RGBA to feColorMatrix converter.

Of course I couldn't do it by myself, my javascript knowledge is still very basic. So I designed the layout, [Brian Leatheam](https://twitter.com/brianleathem) made the magic happen and [Patrick Riley](https://twitter.com/priley86) took it to the next level.

## Webcomponent

Once the tool was working, Patrick forked it and built a polymer webcomonent out of it.

Thanks to Patrick this converter is now an even cooler project.

## Open Source

This project is open and you can do whatever you want with it.

The source code for the [webcomponent is here](https://github.com/andresgalante/RGBAtoFeColorMatrix).

And you can [use it here](http://blog.andresgalante.com/RGBAtoFeColorMatrix/).
