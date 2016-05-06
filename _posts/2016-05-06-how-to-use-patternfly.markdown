---
layout: post
title:  "How to setup a PatternFly 3 project"
date:   2016-04-20 16:34:20 -0300
categories: random
tags: argentina ignitetalks redhat
---

![Patternfly Charts](/img/patternfly-set-up/patternfly-new.jpg)

[PatternFly](https://www.patternfly.org/) is an open interface project that promotes design commonality and improved user experience across enterprise IT products and applications.

A successful set up of the framework will help maintain, organise and grow a project. It will also allow to customize the default patternfly styles.

## Create a project folder

Using the command line navigate to the folder where the project will be nested:

{% highlight css %}
cd path_to/projects
{% endhighlight %}

Then create a directory with the project name:

{% highlight css %}
mkdir myProject
{% endhighlight %}

And `cd` into your project folder:

{% highlight css %}
cd myProject
{% endhighlight %}

## Use Bower (or npm) to install Patternfly

[Bower](http://bower.io/) is a package manager. For this example we are going to use bower to install PatternFly, but you can also use npm and the process would be almost the same.

You'll need npm to install bower, make sure you have [node installed](https://nodejs.org/en/) on your system.

The first step is to install bower globally. On the terminal type:

{% highlight css %}
npm install -g bower
{% endhighlight %}

Sometimes it's require to run this command as root/Administrator. To do so add `sudo` before `npm` and run it again.

Now make sure you are in the project folder `path_to/projects/myProject` and install patternfly:

{% highlight css %}
bower install patternfly
{% endhighlight %}

*TIP* There are lots of command line basics tutorials.  [This excellent video series](https://www.youtube.com/playlist?list=PLLnpHn493BHGmEYzbjWPJsnRMhvs-PSYG) will teach you the basics.

## File structure

Bower will create a folder called `bower_components/` where it will install `patternfly` and all its dependencies.

Your project folder should now looks like this:

{% highlight css %}
MyProject/
└── bower_components/
    ├── bootstrap/
    ├── bootstrap-combobox/
    ├── bootstrap-datepicker/
    ├── bootstrap-select/
    ├── bootstrap-switch/
    ├── bootstrap-touchspin/
    ├── bootstrap-treeview/
    ├── c3/
    ├── d3/
    ├── datatables/
    ├── datatables-colreorder/
    ├── datatables-colvis/
    ├── eonasdan-bootstrap-datetimepicker/
    ├── google-code-prettify/
    ├── jquery/
    ├── font-awesome/
    ├── matchHeight/
    ├── moment/
    ├── moment-timezone/
    └── patternfly/
{% endhighlight %}

*TIP* Remember never to change /bower_components so patternfly can be easily updated.

## Add styles

Patternfly is based on bootstrap. I recommend to use of a CSS pre-processor to extend patternfly instead of overwritting it. There are Less and a Sass versions of patternfly, in this case I'll use less.

Lets create a folders one for /less and add a file called styles.less

{% highlight css %}
MyProject/
├── bower_components/
│   ├── bootstrap/
│   ├── bootstrap-combobox/
│   ├── bootstrap-datepicker/
│   ├── bootstrap-select/
│   ├── bootstrap-switch/
│   ├── bootstrap-touchspin/
│   ├── bootstrap-treeview/
│   ├── c3/
│   ├── d3/
│   ├── datatables/
│   ├── datatables-colreorder/
│   ├── datatables-colvis/
│   ├── eonasdan-bootstrap-datetimepicker/
│   ├── google-code-prettify/
│   ├── jquery/
│   ├── font-awesome/
│   ├── matchHeight/
│   ├── moment/
│   ├── moment-timezone/
│   └── patternfly/
└── less/
    └── styles.less
{% endhighlight %}


## PatternFly CSS setup

PatternFly has splitted its styles to cope with Internet Explorer 9 rule that only reads 4,095 CSS line of CSS.

`patternfly.css` has bootstrap and all the styles to customize bootstrap, and `patternfly-addions.css` has all the styles for the new components patternfly adds to extend bootstrap functionalities.

We are going to build our styles ontop of `patternfly-addions`

## Set up styles.less

Open your favourite text editor and open `styles.less`.

On styles.less, first import `patternfly-addions`:

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

By importing patternfly-addions.less you can use all the mixins built in bootstrap and patternfly, like clearfix or grandients. Plus you can take advantage of patternfly and bootstrap variables under /variables.less for colors, sizes and more.

For example if you want on your project to change the default blue for red, and change the font size from 12px to 13px, you would write:

{% highlight css %}
@brand-primary:     red;
@font-size-base:    13px;
{% endhighlight %}

## Compile

To create a css file from the less file, you'll need to compile your less file. [There are several ways to compile less](http://lesscss.org/#using-less).

It is very usefull to set up [Grunt](http://gruntjs.com) or [Gulp](http://gulpjs.com) for live results. I've wrote instructions on [how to set up a `gulpfile` to compile less and do browser refresh](http://blog.andresgalante.com/howto/2015/02/09/gulp-guide-for-designers.html).

This will generate a styes.css file under /css:

{% highlight css %}
MyProject/
├── bower_components/
│   ├── bootstrap/
│   ├── bootstrap-combobox/
│   ├── bootstrap-datepicker/
│   ├── bootstrap-select/
│   ├── bootstrap-switch/
│   ├── bootstrap-touchspin/
│   ├── bootstrap-treeview/
│   ├── c3/
│   ├── d3/
│   ├── datatables/
│   ├── datatables-colreorder/
│   ├── datatables-colvis/
│   ├── eonasdan-bootstrap-datetimepicker/
│   ├── google-code-prettify/
│   ├── jquery/
│   ├── font-awesome/
│   ├── matchHeight/
│   ├── moment/
│   ├── moment-timezone/
│   └── patternfly/
├── css/
│   ├── styles.css
└── less/
    └── styles.less
{% endhighlight %}


*TIP:* Do not edit the css file, changes should always be made on the less file.


## Set up HTML

Call `styles.css` and `patternfly.min.css` on the HTML head:

{% highlight html %}
<link href="/bower_components/patternfly/dist/css/patternfly.min.css" rel="stylesheet" media="screen, print">
<link href="css/styles.css" rel="stylesheet" media="screen, print">
{% endhighlight %}

*TIP:* For a full guide of how to load the js for all patternfly dependencies, check the [quickstart guide](https://github.com/patternfly/patternfly/blob/master/QUICKSTART.md).

{% highlight css %}
MyProject/
├── bower_components/
│   ├── bootstrap/
│   ├── bootstrap-combobox/
│   ├── bootstrap-datepicker/
│   ├── bootstrap-select/
│   ├── bootstrap-switch/
│   ├── bootstrap-touchspin/
│   ├── bootstrap-treeview/
│   ├── c3/
│   ├── d3/
│   ├── datatables/
│   ├── datatables-colreorder/
│   ├── datatables-colvis/
│   ├── eonasdan-bootstrap-datetimepicker/
│   ├── google-code-prettify/
│   ├── jquery/
│   ├── font-awesome/
│   ├── matchHeight/
│   ├── moment/
│   ├── moment-timezone/
│   └── patternfly/
├── css/
│   ├── styles.css
├── index.html
└── less/
    └── styles.less
{% endhighlight %}

## Enjoy!

For a production you'll probably want to seup a gulp or grunt task to take patternfly.min.css out of bower_components (or node_modules) and as well as all the other dependency js you are using.

I highly recommend fully reading [Bootstrap 3 documentation](http://getbootstrap.com/) to understand how the grid system and components works and how to change them.

Everything is where it should be, next is for you to check out [PatternFly](https://www.patternfly.org/) recomendations and specifications and start coding.

If you have questions please contact [Patternfly Mailing List](https://www.redhat.com/mailman/listinfo/patternfly).
