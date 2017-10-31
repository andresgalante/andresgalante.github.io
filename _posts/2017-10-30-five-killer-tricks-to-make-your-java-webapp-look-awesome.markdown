---
layout: post
title:  "5 killer tricks to make your Java webapp look awesome"
date:   2017-10-30 12:05:00
categories: css
tags: css design java app bootstrap patternfly
---


This article is based on my notes for the presentation I gave at JavaOne 2017. Here is a video of the same presentation:

<iframe width="560" height="315" src="https://www.youtube.com/embed/MGlYoBrZkFQ?start=128" frameborder="0" allowfullscreen></iframe>

During my years working with java developers, I’ve noticed they face two challenges:

- They have a hard time making UIs look good.
- And for the ones working with designers, they have bad experiences relating to them.

Don't take my word for it, Java Champion Bruno Souza once told me that:

> "We always do ugly things... always...""

And he is not alone: Gustavo and Bazlur, like many others java developers have problems either creating good UIs or relating with designers:

> "I find hard time with alignment."
Bazlur rahman, JUG leader

> "What frustrates me is the time I spend to get the layout the way I'd like it to be."
Gustavo Muniz do Carmo, Java Dev

But creating great UIs is not just about making them look great, but also about making them:

- Load fast.
- Work in every single device independent of their size and capabilities.
- Accessible for anyone disregarding of their abilities.

That’s why this article will cover 5 essential design principles to create amazing applications for java developer to follow:

## 1. Understand your user’s needs

Having empathy with your users is an essential part of design. We all talk about putting yourself in our user's shoes, but do we actually know what their needs are? How much time do we actually spend watching a user use their products?

Probably not much, and you’d be surprised to know that most developers I know have never seen a user using your product, and they end up taking decisions based on assumptions.

Assumptions are really dangerous! If you assume you will never be able to walk in their shoes.

Never assume you know what they need. I am 100% sure your user needs are not your needs.

How to know what are user needs? Here is a secret, the most meaningful type of user research is really easy!

- Sit down beside a user, give them a task to do watch them use your product! Don’t say anything, don’t ask anything, don’t help them.
- When they are done: Have a chat with them!

This exercise will be an eye opening experience for you and your team and I guarantee that you will never think about your product the same way.

This is extremely important to succeed, if you don’t understand what your users needs, everything else you do doesn’t matter.

My advice is to do this at least one hour a month.

Now that you know how to discover your users needs and you are ready to create content.

## 2. Create great content

Content, like text, images and data is the most important asset you own.

You structure it with HTML, style it with CSS and create interactions with JS. It’s the front end stack.

If you don’t know HTML don’t feel bad, Linus Torvalds once told that he doesn't have a website because he don't know html.

It doesn’t matter how beautiful your code and your style are, if your content stinks, your app will stink too.

Now, as Java developers you will probably use a UI framework to wrap your content, and there are many great well known options like Bootstrap, Foundation, and Material, or some less known ones such as Bulma or Tachyons.

Since I am a core team member of Bootstrap, I will write about Bootstrap.

Bootstrap is world's most popular front-end component library to build responsive, mobile-first projects on the web, and it will help you structure your content into semantic markup that’s accessible, style it with responsive CSS and give behaviours with JS.

## 3. Build accessible, responsive and performant UIs

Apart from a great set of UI components, Bootstrap ships a powerful responsive grid system to deal with layouts at the insane reality we live in.

### Responsive

This is the web today is insiane, we have devices with different screen sizes, different capabilities, different browsers and the web is even in places without screens like cars or refrigerators!

We don’t know where our content will land, will it be a tiny device with a stylus or a huge touch screen?

### Accessible

And then we need to think about the user, humans, like devices, comes in all sizes, shapes and capabilities too, and we need to take accessibility in consideration. Let me tell you a story: My second son’s name is Federico and he is one year and a half old. When he was born we’ve been told that his hearing test gave a negative result. That meant that he might have hearing problems. And as I was in the hospital with little Federico in my arms, I promise myself that I will do my absolute best to ensure that everything I produce is accessible.

When Federico was a year old, we tested him again and the results were positive, thank God he is ok now. But since then everything that my team or I do has baked in accessibility.

At the end of the day, there are way more disabled users than IE users, and we care a lot about making things look good on IE.

## Performant

On top of that, you need to think about performance, you only have users attentions for few seconds. In fact, according to the national center of biotechnology, the average attention span of a human dropped from 12 seconds in the year 2000 to 8 seconds in 2015. That’s one second less than the attention span of a goldfish!

So treat the web as if it was a [liquid Cat](https://www.google.com/search?tbm=isch&source=hp&biw=1364&bih=1252&q=liquid+cat&oq=liquid+cat&gs_l=img.3..0l10.960.2084.0.3268.11.9.0.0.0.0.262.1296.0j2j4.6.0....0...1.1.64.img..5.6.1295.0...0.pRXo5V9Maz0): Fast and fluid! It must be Responsive, Accessible and Performant.

In order to support this reality we structure our HTML in either be a component or a layout. Components will stretch out to the size of it’s container, and the grid (or layout) will regulate the placement and size ignoring completely what happens inside them.

Don’t ever mix grids with components in the same tag. Define your grid and then add components inside.

## 4. Establish a maintainable architectures

The way you architecture your CSS is critical for a successful application. If you fail, you’ll end up with brittle structure that will be impossible to maintain in the future.

The way to use a framework like Bootstrap wisely is to create isolated components instead of extending their components. You’ll end up with bootstrap on one side and your things in another.

Every component should be an island, nothing should depend on each other. Each thing should be it’s own thing, not an extension of another thing.

That way, when a new version of your framework comes up, you’ll be able to easily update and a component you build today to live side by side with one you build 5 years from now.

## 5. Keep Consistency across your UI

This is a hot topic nowadays with the era of design systems.
“Consistency is one of the most powerful usability principles: when things always behave the same, users don't have to worry about what will happen. Instead, they know what will happen based on earlier experience. “

Make sure to reuse the same variables for spacer, shadows, border, and animations. Define it once, use them everywhere

## Try it yourself

These are just 5 starting point that will be immensely helpful for your app.

Remember to understand your users to create great content, build responsive, accessible, and performant structures on a maintainable structure and keep consistency!

And if I can help in anyway please [contact me on twitter @andregsalante](https://twitter.com/andresgalante).


















[Una Kravets](https://twitter.com/Una) is absolutely right, you just can’t learn everything.

This is the list of things I would have liked to know if I had to start today:

## 1. Don’t underestimate how hard CSS is

CSS looks easy. After all it’s just a set of rules that selects an element and modifies it based on a set of properties and values.

It's so much more than that.

A successful CSS project requires the most impeccable architecture. Poorly written CSS is brittle and quickly becomes difficult to maintain. It’s critical you learn how to organize your code in order to create maintainable structures with a long lifespan.

But even an excellent code base has to deal with the insane amount of devices, screen sizes, capabilities and user preferences. Not to mention accessibility, internationalization and browser support!

**CSS is like a bear cub: cute and inoffensive, but when he grows he’ll eat you alive**. Experience, hard work and study will teach you how to tame the beast.

## 2. Share and participate

Sharing is so important! How I wish someone had told me that when I started. I've spent the first 10 years of my career ignoring the importance of sharing, and when I finally learned, it completely changed  how I viewed my work and working with others.

Learn git. [Git is the language of open source](http://andresgalante.com/design/2015/08/31/adopt-a-deisgner.html) and you definitely want to be part of the it.

Great developers are kind and generous. A healthy community is full of great developers and you want to be around them. The sooner the better.

Remember that you are as good as the people that surrounds you, so be kind and generous.

Share everything you learn. The path is as important as the end result, even the tiniest things can make a difference to others.

Write and read documentation. Remember that good development is documentation driven development.

## 3. Pick the right tools

Tools are very important, they allow you do your craft.

Learn your way around your code editor. It should be an extension of your mind.

It doesn’t matter if you use [Atom](https://atom.io/), [VSCode](https://code.visualstudio.com/) or old school [Vim](https://vim.sourceforge.io/), the better you shape your tools to your thought process, the better developer you’ll become. You’ll not only gain speed but also have an uninterrupted thought line that result in a fluid ideas.

The terminal is your friend.

There is a lot more about been a CSS developer than writing CSS. Things like building your code, compiling, linting, formatting and browser live refresh are just a tiny part of what you’ll have to deal in a daily bases.

Pick up your way around the terminal and learn CLI as soon as possible.

Don't forget that as a developer you are responsible to stay up to date with best practice. Follow resources like W3C and MDN to stay up to date.

## 4. Get to know the browser

The browser is not only your canvas, but also a powerful inspector to debug your code, test performance and learn from others. Become comfortable using the inspector.

Learn how the browser renders your code, what is its inner working and how to improve your work.

Every browser is different, embrace it. Love them for what they are. (Yes, even IE).

## 5. Learn to write maintainable CSS

It’ll probably take you years, but if there is just one single skill a CSS developer should have is to write maintainable structures.

This means knowing exactly how the cascade, the box model and specificity works. Master CSS architecture models, learn their pros and cons and how to implement them.

This is a hole you can dig for ever, the more you learn the less you’ll know. Keep up with the trends, **have an opinion and only follow the things that makes sense to you**.

Remember that a modular architecture leads to independent modules, good performance, accessible structures and responsive components (aka CSS happiness).

## The future looks bright

Modern CSS is amazing and the future is even better. I love CSS and I enjoy every second I spend coding.

During the following weeks I’ll write more about how to create maintainable CSS at scale going in depth on the topics that were mentioned on this post.

What do you think about those advices? Don’t be a stranger, <a href="https://twitter.com/andresgalante">tell me on Twitter</a>.
