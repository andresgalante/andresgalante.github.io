---
layout: post
title:  "Migrating PatternFly from 1.x to 2.0"
date:   2015-08-12 23:05:36
categories: patternfly
tags: uxd design html css code patternfly upgrade migrate 2.0
comments: false
---

![Migrate to Patternfly 2.0](/img/migrate/migrate-patternfly.png)




This week we've [release PatternFly 2.0](https://github.com/patternfly/patternfly/releases). This guide will go step by step on how to upgrade from PatternFly 1.x to our latest version.

## PatternFly 2 is (almost) backwards compatible with v1.x

There are three major changes that you should know about:

- We don't support Internet Explorer 8 anymore.
- We've split the CSS into two files (`patternfly.*css` and `patternfly-additions.*css`) to avoid a limitation of Internet Explorer 9 where [only 4095 selectors are recognized in a single stylesheet](https://support.microsoft.com/en-us/kb/262161).
- and we've moved `components/boostrap-select/bootstrap-select.min.js` to `components/boostrap-select/dist/js/bootstrap-select.min.js`.

## First: Get PatternFly 2.0

The first step is to upgrade the PatternFly codebase. This process will be different depending on how your project manages its depencies.

##### Upgrade using Bower:
{% highlight bash %}
$ bower upgrade patternfly —save-dev
{% endhighlight %}

##### Upgrade using Npm:
{% highlight bash %}
$ npm upgrade patternfly —save-dev
{% endhighlight %}

##### Upgrade using Git:
Add PatternFly as a remote repo, fetch it and rebase
{% highlight bash %}
$ git remote add upstream git@github.com:patternfly/patternfly.git
$ git fetch upstream
{% endhighlight %}

##### Get the ZIP:
Or just [Downloading the zip file](https://github.com/patternfly/patternfly/archive/master.zip) from github

## Changes on the HTML

#### IE8 support
Since we no longer support IE8, you can remove IE8 utilities (html5shiv and respond) from all your pages.

#### Link two CSS instead of one
We've split PatternFly styles into two style sheets. The links to the styles will look something like this:

{% highlight html %}
<link href="PATH_TO_PATTERNFLY/dist/css/patternfly.*.css" rel="stylesheet" media="screen, print">
<link href="PATH_TO_PATTERNFLY/dist/css/patternfly-additions.*.css" rel="stylesheet" media="screen, print">
{% endhighlight %}

#### Boostrap select
If you are using [Boostrap Select](https://www.patternfly.org/widgets/#bootstrap-select) you should change the path to the javascript. It'll look something like this:

{% highlight html %}
<script src="PATH_TO_PATTERNFLY/components/patternfly/components/bootstrap-select/dist/js/bootstrap-select.min.js"></script>
{% endhighlight %}

## Dependency Upgrades
We've upgraded most of our dependencies. You can see the [complete list on the release](https://github.com/patternfly/patternfly/releases/tag/v2.0.0). If you need a version other than what is checked into patternfly/components, you'll have to pull it yourself.


## Changes on LESS

If you are [extending PatternFly styles using less](http://blog.andresgalante.com/howto/2015/02/06/patternfly.html), import patternfly-additions.less as a base to your styles, and compile again. Remember to load both `patternfly*.css` and your styles on the HTML.

{% highlight css %}
@import "PATH_TO_PATTERNFLY/patternfly/less/patternfly-additions.less";
{% endhighlight %}

For more information on upgrading to v2.0, send an email to the [Patternfly Mailing List](patternfly@redhat.com) or join the IRC channel #patternfly on Freenode.


