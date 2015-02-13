---
layout: post
title:  "On-boarding new users is like parenting"
date:   2015-02-02 23:05:36
categories: design
---
This is my son, his name is Leon and he is an artist.

![Leon](/img/onboarding/leon.jpg)

He is two years old, which means that I haven't been sleeping well (or at all) for the last two years. He is the most time consuming, attention sponge, energetic creature I have ever met. Don't get me wrong, I love him more than anything and he is the joy of my life. Love comes built in babies, it's the way mother nature found to make us survive childhood.

[UX Designers](https://developer.jboss.org/en/gatein/blog/2012/05/28/user-experience-what-is-this-about-anyway) are much like parents. We are always thinking about our users. We observe them and try to get into their minds to help them achieve their goals.


Children and users need care, patience, attention, love and guidance. It is our job to provide that. Nobody really teaches us how to be parents and we don't have second chances. We just do our best and, of course, we fail. Luckily for our users, UX designers are very well prepared. We get many second chances, we can test, learn and iterate.

At Red Hat our users are usually developers. They are hackers who are always looking for ways to alter their surroundings to find methods to increases productivity and efficiency. They are just fantastic, in my opinion the best kind of users to work with.

##Aerogear Unified Push Console

I've been given the challenge to [redesign Aerogear Unified Push Console (UPS)](http://www.nngroup.com/articles/radical-incremental-redesign/).

This server allows sending native push messages to different mobile operating systems, such as Android, iOS, Windows or Firefox OS/SimplePush.

Push notifications can be a pain, and Aerogear team has done an amazing job. It is a powerful tool that has all kinds of sorcery and Jedi tricks that i cannot begin to grasp. 

![Old UPS console](/img/onboarding/post-image-old-page.png)

Currently users count on extensive documentation to set up Unified Push Console. On this redesign we seek to improve the UI to direct the set up without the need to go through the documentation.

###Lead the users to success

One key aspect of this redesign is how to guide new users to get on-board.

In order to make the server work, the user will have to successfully complete 5 steps:

1. Create an application
2. Add at least one Variant
3. Install client code
4. Send a test push notification
5. Set up the sender API

Expectations are high. It isn't an easy job, and we need to help them succeed.

### Focus

We set the expectations early, we promise that there is gold at the end of the rainbow. If they follow the (not so simple) steps, they will be able to easily send push notifications and we will make sure they are delivered. 

But the [average user attention span is 8 seconds](http://tinyurl.com/l6t5sts), that's one second shorter than a goldfish[2]. 


We only have a fraction of a second to make a good first impression and just a couple of seconds to grab their attention.

Now the countdown begins! we have only a few minutes to show them how they can achieve their goals. If we fail, they will assume the console doesn't work, and second chances are rare.

We need to [grasp our users attention instantly and show them how to use the console fast](http://www.nngroup.com/articles/powers-of-10-time-scales-in-ux/), but how?

### Can I buy you a drink?

There are several methods to have a [first date with our users](http://www.dtelepathy.com/blog/design/ux-flows-onboarding). 

**Better than show how it works is to make them actually do it**. Tumblr does an amazing job on first interacting, the new user is prompted to input important information to ensure a customised user experience.

![Tumblr on boarding](http://assets-www-dtelepathy-com.s3.amazonaws.com/wp-content/uploads/2014/02/UXflows_GifGraphic_Tumblr.gif)

For the UPS console, we also built an interactive wizard that guides the user to complete the 5 steps to get push notifications up and running. 

![UPS On boarding Set Expectations Early](/img/onboarding/post-image-welcom-page.png)

![UPS On boarding](/img/onboarding/post-image-step1.png)

Without been intrusive, we never leave them alone. Even if they decide to skip the wizard, they still get a blank slate waiting to guide them.

![UPS blank slate](/img/onboarding/post-image-blank-page.png)

Setup is done but our job is not over, we have to make sure that the rest of their experience is up to their expectations. Users spend most of their time on other websites and we always follow patterns and keep consistency.

### One ring to rule them all

[Jakob Nielsen says](http://www.nngroup.com/articles/top-10-mistakes-web-design/):

> Consistency is one of the most powerful usability principles: when things always behave the same, users don't have to worry about what will happen. Instead, they know what will happen based on earlier experience.

To keep consistency we build the UI based on [Patternfly](https://www.patternfly.org/) recommendations. 

Patternfly is an Open Source community that promotes design commonality and improved user experience across enterprise IT products and applications.

It is based on Bootstrap, so implementation is easy and straight forward.

And to keep the karma flowing we are contributing a blank slate pattern and syntax highlighting back to Patternfly.

## The results

This UI hasn't been implemented yet. Basic user testings with the prototype show that this user-centric interaction is very successful.

A successful on boarding strategy is like teaching something new to your children. As parents we need to encourage them to  teach themselves and learn their own way. They have to drive. But you're there as bumpers to make sure they don't fall off the edge.

[Alan Cooper](http://www.amazon.com/About-Face-Essentials-Interaction-Design/dp/1118766571/ref=dp_ob_image_bk) teaches us that the main goal of a UX design is to never make the user feel stupid. **It's in our hands for that to happen**.