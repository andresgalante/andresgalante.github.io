---
layout: post
title:  "Gulp guide for designers"
date:   2015-02-09 23:05:36
categories: howto
tags: Patternfly, setup, Gulp, BrowserSync
---

[Gulp](http://gulpjs.com) is a Task / Build runner. It's easy to use, has a simple api, and is efficient. Gulp.js makes use of pipes for streaming data that needs to be processed.


But as designer you don't actually need to know any of that. What you do need to know is that **Gulp will make your life much easier**.

This tutorial will setup Gulp to do 3 things:

- Compress js
- Compile [Less](http://lesscss.org)
- Browser livereload

## Installing Gulp and Gulp plugins

#### 1. Install gulp globally:

{% highlight bash %}
npm install --global gulp
{% endhighlight %}

You'll probably need to `sudo` this one. 

Now `cd` to your project directory and install the dependencies and plugins

#### 2. Install gulp in your project devDependencies:

{% highlight bash %}
npm install --save-dev gulp
{% endhighlight %}

#### 3. Install gulp less plugin

{% highlight bash %}
npm install --save-dev gulp-less
{% endhighlight %}

#### 4. Install gulp uglify plugin for js

{% highlight bash %}
npm install --save-dev gulp-uglify
{% endhighlight %}

#### 5. Install gulp plumber to output errors

{% highlight bash %}
npm install --save-dev gulp-plumber
{% endhighlight %}

#### 6. Install gulp browsersync for live reload

{% highlight bash %}
npm install browser-sync gulp --save-dev
{% endhighlight %}

## Create gulpfile.js

On the root of your project create a .js file name `gulpfile.js`, and paste this snippet

{% highlight js %}
var gulp = require('gulp'),
    uglify = require('gulp-uglify'),
    less = require('gulp-less'),
    plumber = require('gulp-plumber'),
    browserSync = require('browser-sync'),
    reload = browserSync.reload;

// Uglyfies js on to /js/minjs
gulp.task('scripts', function(){  
  gulp.src('js/*.js')
    .pipe(plumber())
    .pipe(uglify())
    .pipe(gulp.dest("js/minjs"));
}); 

// Compiles less on to /css
gulp.task('less', function () {
  gulp.src('less/**/*.less')
   .pipe(plumber())
   .pipe(less())
   .pipe(gulp.dest('css'))
   .pipe(reload({stream:true}));
});

// reload server
gulp.task('browser-sync', function() {
    browserSync({
        server: {
            baseDir: "./"
        }
    });
});

// Reload all Browsers
gulp.task('bs-reload', function () {
    browserSync.reload();
});

// watch for changes on files
gulp.task('watch', function(){ 
  gulp.watch('js/*.js', ['scripts']);
  gulp.watch('less/*.less', ['less']);
  gulp.watch("*.html", ['bs-reload']);
}); 

// deploys
gulp.task('default',  ['scripts', 'less','browser-sync','watch']); 
{% endhighlight %}

## Magic!

Open terminal and run `gulp`!
{% highlight bash %}
gulp
{% endhighlight %}

And now the magic starts. This will do:

- Compress any .js files on /js folder and store them on /js/minjs
- Compile any .less files on /less folder and create a .css file on /css
- Open a browser with your index.html
- Watch for changes on your js file and compress it every time you save it
- Watch for changes on your less file and compile it every time you save it
- Auto reload the browser every time the less file is updated.


## More magic! Awesome livereload with Browsersync

You've just installed [BrowserSync](http://www.browsersync.io/), its a time-saving synchronised browser testing.

[BrowserSync](http://www.browsersync.io/) makes your tweaking and testing faster by synchronising file changes and interactions across multiple devices. It’s wicked-fast and totally amazing.

You'll be able to view your project at this address `http://localhost:3000/` and you'll find browser sync configurations at `http://localhost:3001/`. On that seetings page you'll find a IP address to sync on your mobile device among other amazing features.



## Enjoy!

There are also [Gulp plugins](http://gulpjs.com/plugins/) for Sass or Stylus and with little changes on this code you can implement them.

Once you save your less file, it will overwrite any change you do directly on the css. So remember to **do styling changes on less** and never edit the css file and you'll be fine.