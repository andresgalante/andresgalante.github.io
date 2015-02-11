---
layout: post
title:  "Patternfly: Set up instructions"
date:   2015-02-06 23:05:36
categories: patternfly howto design
---

[PatternFly](https://www.patternfly.org/) is an open interface project that promotes design commonality and improved user experience across enterprise IT products and applications.

A successful set up of the framework will help maintain, organise and help you grow a project.

**HEADS UP:** This document will use the command line. If you feel uncomfortable with it you can install  [CodeKit](https://incident57.com/codekit/). It does Bower, live reload and less compilation without having to type any command.

## Create a project

With the Finder, create an empty folder where the the project will live.

**Add Image: Finder**

Or do it the hardcore way, use the command line. Open the terminal and navigate to the folder where the project will be nested:

{% highlight bash %}
cd path_to/projects
{% endhighlight %}

Then create a directory with the project name:

{% highlight bash %}
mkdir myProject
{% endhighlight %}

## Use Bower to install Patternfly

Bower is a package manager. We are going to use bower to install patternfly framework. The first thing to do is to install bower globally. On the terminal type:

{% highlight bash %}
npm install -g bower
{% endhighlight %}

Sometimes it is require to run this command as root/Administrator. To do so add `sudo` before `npm` and run it again.

Make sure you are in the project folder `path_to/projects/myProject` and install patternfly:

{% highlight bash %}
bower install patternfly
{% endhighlight %}

**TIP:** There are lots of command line basics tutorials.  [This excellent video series](https://www.youtube.com/playlist?list=PLLnpHn493BHGmEYzbjWPJsnRMhvs-PSYG) will teach you the basics. 

## File structure

The folder now looks like this:

**Add Image: Finder**

- myProject
  - bower_components
    - patternfly

****TIP:**** Remember never to change /bower_components so patternfly can be easily updated.

## Add styles

Patternfly is based on bootstrap. We recommend the use of a CSS pre-processor. This case uses Less, but there is also Sass version.

Now create 2 folders, one for /less and another for /css

**Add Image: Finder**

- myProject
  - bower_components
    - patternfly
  - less
  - css

Leave the /css files empty, it is to place the compile css file there. 

****TIP:**** Do not edit the css file, changes should always be made on the less file.

## Create styles.less

Open your favourite text editor and create a new file, call it styles.less.

**Add Image: Finder**

- myProject
  - bower_components
    - patternfly
  - less
    - styles.less 
  - css

On styles.less, first import patternfly:
{% highlight css %}
@import "../bower_components/patternfly/less/patternfly.less";
{% endhighlight %}


Then change path of the fonts:
{% highlight css %}
@fa-font-path:      "../bower_components/patternfly/components/font-awesome/fonts/";
@font-path:         "../bower_components/patternfly/dist/fonts";
@icon-font-path:    "../bower_components/patternfly/components/bootstrap/fonts/";
{% endhighlight %}


Now the less file is set up, you can write your styles here.

****TIP:**** By importing patternfly.less you can use all the mixins built in bootstrap and patternfly, like clearfix or grandients. Plus you can take advantage of patternfly and bootstrap variables under /variables.less for colors, sizes and more.

## Compile

To create a css file from the less file, you'll need to compile your less file. [There are several ways to compile less](http://lesscss.org/#using-less).

It is very usefull to set up [Grunt](http://gruntjs.com) or [Gulp](http://gulpjs.com) for live results. 

[Here are very easy instructions on how to set up Gulp](https://gist.github.com/andresgalante/e4170f60f05630bbd402)

Or just use [CodeKit](https://incident57.com/codekit/)

This will generate a styes.css file under /css:

**Add Image: Finder**

- myProject
  - bower_components
    - patternfly
  - less
    - styles.less 
  - css
    - styles.css 

## Set up HTML

Call styles.css on the HTML head:
{% highlight html %}
<link href="css/styles.css" rel="stylesheet" media="screen, print">
{% endhighlight %}


**TIP:** By calling just one CSS you avoid making unnecessary requests.

**Add Image: Finder**

- My_Project
  - bower_components
    - patternfly
  - less
    - styles.less  
  - css
    - styles.css
  - index.html 

## Enjoy!

Everything is where it should be, next is for you to check out [PatternFly](https://www.patternfly.org/) recomendations and specifications and start coding.

If you have questions please contact [Patternfly Mailing List](https://www.redhat.com/mailman/listinfo/patternfly).