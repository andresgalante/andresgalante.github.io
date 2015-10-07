---
layout: post
title:  "CSS pseudo class playground"
date:   2015-10-06 23:05:36
categories: howto
tags: design howto css
---

![Visited](/img/visited/visited.jpg)

Saturday nights are usually busy. But on rare occasions when there are no plans and my wife and son go to sleep early, there is a strange window of quietness in my life.

Last weekend I had one of those special moments, and of course, since I am a big nerd I spent it coding.

A few weeks ago I bumped into an article written by [Una Kravets](http://unakravets.com) about [hacking :visited](http://una.im/hacking-visited/) [pseudo class](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes), and I had to try it myself.

The idea is to display an `"unread"` label to represent links that haven't been read yet, plus I wanted to add a `"new"` tag to the newest post and for extra css fun change the text for `:hover` and `:active` states.

If you really want to learn this technique, stop reading now, [go to Unas posts](http://una.im/hacking-visited/), enjoy her article and come back. If you are like Bruno and you are here just for the joy of reading my words, then continue reading.

## The HTML

It all starts with Unas code. Since for security reasons `:visited` is limited to just changing the color, she wisely changes the color of the font to match the background, making it disappear. Pretty nifty.

On my Jekyll `HTML` I make sure the `<a>` is around the `<h2>`.

{% highlight html %}
{% raw %}
<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">
        <p class="post-meta">{{ post.date | date: "%B %d, %Y" }}</p>
        <h2>
          {{ post.title }}
        </h2>
      </a>
    </li>
  {% endfor %}
</ul>
{% endraw %}
{% endhighlight %}


## :visited is where the magic happens

Then on the `sass` I apply a content for the label after the `h2` title, and to make it disappear I set the same colors as the background color on `:visited`.

{% highlight sass %}
{% raw %}
.post-list{
  a {
    &:link h2:after {
      //Creates the content of the label
      content: 'unread';
      //Defines color and backgorund color
      color: #fff;
      background: $grey-color;
   }
    &:visited h2:after {
      //Here is where the magic happens, changes the background and color to make it disappear
      color: $background-color;
      background: $background-color; 
    }  
  }
}
{% endraw %}
{% endhighlight %}


## CSS fun with :hover and :active

I've also added different messages for `:hover` and `:active` states

{% highlight sass %}
{% raw %}
.post-list{
  a {
    &:link h2:after {
      //Creates the content of the label
      content: 'unread';
      //Defines color and backgorund color
      color: #fff;
      background: $grey-color;
    }
    &:hover h2:after {
      content: 'unread, read it!';
    }
    &:active h2:after {
      content: 'click!';
    }
    &:visited h2:after {
      //Here is where the magic happens, changes the backgound and color to make it dessapear
      color: $background-color;
      background: $background-color; 
    }  
  }  
}
{% endraw %}
{% endhighlight %}


## The new kind on the block

And since the first `h2` on the list is the newest post, I tagged it as "new".

{% highlight sass %}
{% raw %}
li{
  &:first-child h2 {
    &:after {
      content: "new!";
    }
  }
}  
{% endraw %}
{% endhighlight %}


You can check the [complete code here](https://github.com/andresgalante/andresgalante.github.io/blob/master/_sass/_hack.scss).

Now go and check the homepage to see the result!

## One more thing...

On related news, I've also added comments to the blog. Not because I expect to get any comment.

I honestly don't think anyone reads these words, but [Jeff Atwood](https://en.wikipedia.org/wiki/Jeff_Atwood) says on his excellent [blog](http://blog.codinghorror.com) that a blog without comments is not a blog.

Now I have a blog. :smile: