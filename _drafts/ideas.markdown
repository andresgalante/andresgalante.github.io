---
layout: post
title:  "IDEAS"
date:   2019-12-06 23:05:36
categories: howto
tags: Patternfly setup Bower
---

Jeff Atwood, creator of Stack Overflow and one of the best blogers there is, says that a blog without comments is not a blog. I'd like to add that a blog without [emoji](https://en.wikipedia.org/wiki/Emoji) is not a blog. But that's not the hole truth, emojis go way further. **A life without emoji is like the weekly PM meeting: boring**.

Andy Warhol said:

> I like boring things.

And Leo Tolstoy wrote: 

> Everything intelligent is so boring.” 

Which makes the weekly PM meeting an intelligent art masterpiece.

# Emijis on Jekyll

Adding emojis to a [jekyll](https://jekyllrb.com) blog is easy. Just add the [jemoji gem](https://github.com/jekyll/jemoji) to your site's `_config.yml`

{% highlight bash %}
# adds emoji
gems:
  - jemoji
{% endhighlight %}

Then you can go to [any emoji cheatsheet](http://www.emoji-cheat-sheet.com) to get the reference for the emoji.

For example here is a cute panda face :panda_face:

# Emijis on CSS

I've heard that you could use emoji as class names, but it blew my mind to actually test it. Ofcourse this is completely useless, but it's as cool as CSS can get.


For example, if I want to build a section for Funny Hot News, I can name it like this: :smiley: :fire: :newspaper

<div data-height="220" data-theme-id="20015" data-slug-hash="jbGqXj" data-default-tab="html" data-user="andresgalante" class='codepen'><pre><code>&lt;div class=&quot;😃🔥📰&quot;&gt;
  This is the Funny Hot News section!
&lt;/div&gt;</code></pre>
<p>See the Pen <a href='http://codepen.io/andresgalante/pen/jbGqXj/'>Emoji CSS class names</a> by Andres Galante (<a href='http://codepen.io/andresgalante'>@andresgalante</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
</div><script async src="//assets.codepen.io/assets/embed/ei.js"></script>


These are just a few ways to use them, now go and [Spice Up Your Life](https://youtu.be/9wfpXI5PKlw) with emojis.




I work at Red Hat, that means that I get paid to  contribute to open source communities, but to be honest, until lats week I've never done a selfish commit to any project.



Saturday nights are usually busy. But on rare occasions when there are no plans and my wife and son go to sleep early, there is a strange window of quietness in my life.

Last weekend I had one of those special moments, and of course, since I am a big nerd, I spent it coding.

A few weeks ago I bumped into an article written by [Una Kravets](http://unakravets.com) about [hacking :visited](http://una.im/hacking-visited/) psudo-class, and I had to try it myself.

The idea is to display an `"unread"` label to represent links that haven't been read yet, plus I wanted to add a `"new"` tag to the newest post and for extra css fun I changed the text for `:hover` and `:active` states.

If you really want to learn this technique, stop reading now, go to Unas posts, enjoy her article and come back. If you are like Bruno and you are here just for the joy of reading my words, then continue reading.

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

Then on the `sass` I add the content of the label after the `h2` title, and to make it disappear I set the same colors as the background color on `:visited`.

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


You can check the complete code here.

## One more thing...

On related news, I've also added comments to the blog. Not because I expect to get any comment, I honestly don't think anyone reads these words, or that they deserve a discussion, but [Jeff Atwood](https://en.wikipedia.org/wiki/Jeff_Atwood) says on his excellent [blog](http://blog.codinghorror.com) that a blog without comments is not a blog.

Now I have a blog. :smile: 



My son Leon is two and a half years old, and he shares the same passion every single kid in the world has: Peppa Pig.

Kids comes in all sizes and shapes and they have different personalities. Some talk a lot, others are more physical, some sleep others (like my son Leon) don't, but they all agree in one thing, Peppa Pig is the best.

What visual magic is behind a rudimentary drawn phallic shape pink pig goes way beyond my comprehension.

I am sure that the bright colors, the high pitch of the voices, the simple music and animations and a bit of luck have a lot to do with its success. To me it all comes down to George.

George is Peppas little brother, he love dinosaurs and he is a cool guy. I'd hang out with George any day.

## 99% of Cartoons are crap :poop:

[Sturgeon's Law](https://en.wikipedia.org/wiki/Sturgeon%27s_law) says that 99% of everything is crap.

There are about 1.5 billon children in this world, that many little people can't be wrong.

Creating something as successful as Peppa doesn't happen by accident, it takes a lot of time, research, resources, talent and skill.

The same happens in design.

## 99% of Design is crap :poop:

A [guy on the internet](https://www.quora.com/If-we-all-agree-design-is-important-why-does-so-much-design-suck) said:

> It's easier and cheaper to create bad designs. Because of that, bad designs will be more plentiful in any free market than good design.

I think that it goes beyond good vs bad. We work in an industry where good is not enough. Only the exceptional succeed. Bing is a very good search engine, Google is excellent. Google Plus is a good social network, Facebook is excellent. There is no room for just good.

On his [Incomplete Manifiesto for Growth](http://www.manifestoproject.it/bruce-mau/), [Bruce Mau](http://www.brucemaudesign.com/) motivate us to push the limits:

> Go deep. The deeper you go the more likely you will discover something of value.

Excellency doesn't come easy. To get the finest quality we should go outside our comfort zone and **studying as much as we practice**.

## Cue Peppa song: :musical_keyboard: Tu turu tu tum tu turu tu tu tum

Excellent design is honest. There is no cheating, no shortcuts. It requires an attention to detail that is really hard to achieve. 

That craftsmanship goes to build any excellent thing. There is elegant coding, excellent music and even great accounting.

Sometimes we, the adults, can also agree that some things are superlative.

Meanwhile I'll join Leon and all the children in the world and surrender to the excellent Peppa Pig.



 

Andres Galante wrote this on date
// poner comentarios
get a logo?
agregar tweeter
next and prev posts
// categories


- pattenrfly?
- redhat demo
- house of cards, all charpters at once == ux behavior ?
- homepage aerogear website, first 1 second
- My new monitor sucks
- the js learning curve
- the perfect mouse
- iphone, go back to my first love
- why i love working at red hat
- choosing a bumper for my phone
- Rehersal until bla bla, like clowns
- start with design
- spend money on good shit
- designers open source community
- Pre procesadores de CSS
- language http://ilanguages.org/bilingual.php
- Font paring
- PatternFly Jekyll
- basic jekyll static page for project pages
- jekyll blog template














If there is one thing I regret from my trip to QConRio is not having spent enough time talking with [Felippe Nardi](https://twitter.com/FelippeNardi). He has been developing on remote server for more than a year and he enter to the list of "Heroes". 

To be honest it's a quite large list that includes Michael J Fox for Back to the Future and Raphael turtle ninjas because he can kick ass.

That doesn't take away the fact that he has done something I always wanted to do and, ofcourse, always failed. I work on a very nice macbook pro (which I love) attached to a stupid and very bad samsung monitor that never gets colors right (which I hate). And although I like working on a mac, I don't want to be attached to it. If I travel, or if I want to work somewhere else I always need to take my large 15' computer. It's the only place where I have all my tools and envioments and files to work.

Felippe replaced his laptop for an ipad for a year and he proves that your development machine can be on the cloud, but what happen with designers. Can we replace my computer for a tablet or even a smart phone?

The answer is no completely.

What have I done?

I've look into a normal workweek and learn about my workflow. I've list the tools I use and cure to know which ones are really necessary.

My main concern is photoshop. Although I would prefer to work on Sketch, the team I work on uses photoshop and we share psd files. Even though a look a lot for it, I couldn't find a app replacement for desktop photoshop.

That been said there is no reason why I couldn't start coding on virtual machines. Well, actually there is, I don't know ssh or vin good enough.

And there are 2 solutions to that issue:

The first is to learn Vin, which is probably what I am going to do because I am big nerd and I am sure I'll brake things up in the process... and we all know there is no better way to learn something than to fix what we've broken. Plus I get to use the command line, and nothing feels better than successfully using the command line.

The second one is to use [Cloud9](https://c9.io/). Which is awesome and easy to use, and although I should use it I won't... because well, I've just said it, I am a big nerd.

Practice makes the master. If I blog again about this in a few month then you'll know I succeed 


Felippe



What if I know ssh or vin


the ipad only designer setup

This is a something I've always wanted to achieve: get rid of my computer. I've tried to do it with a smart phone





https://medium.com/@felippenardi/start-coding-from-an-ipad-d942ebe44c63


Three tips to build a design guide

Keep consistency

Create components and not webpages

Write good documentation. It would probably very very hard for a new person to do anything inseide the system, you have to teach them whever everything is. removes friction. improve comonnucation,s share knowlage and documented in a style guide.
Build the documentation within the product, use the style guide to build the tool.

dont buid one of. build a library of components.

well documented and arpochable.

reuse and refactor.

coding startdanrds. it should feel like ne person write it. Rules.

live examples, copy paste, no change anyone can screw things up.

dont write more css.

brake things into ocmponents and docs should rule everything. Docs driven development.


Make it easy to jump in and help each other. no matter what knowlage level



distributed teams work 

Patternfly is a Design systems.

everything that makes out your product open source framework

the aproach to open source treat it as open durce even though it isnt

cmponents and assets

What did we learn from patternfly HTML,CSS and JS components to build stuff on the web.

remove friction and help peoeple get things done.

we use our products to buils patternfly and we use patterfly to build our products




A few monthes ago I've got a Sam




If there is one thing I regret from my trip to QConRio is not having spent enough time talking with Felippe Nardi. He has been doing for a year something I always wanted to do.
 
Today, and after 8 month of waiting, I finally got an extra monitor.

the ipad only designer setup

This is a something I've always wanted to achieve: get rid of my computer. I've tried to do it with a smart phone

I've been listening about Red hat Summit since I've started working at Red hat last November, and now is around the corner.

Apart from the PatternFly talk I am co presenting with Robb this Tuesday, and the Patternfly booth I'll be hosting during wendesday and thusrday, I've also been helping build the Red Hat Middleware Keynote.

It's been a long jurney from when we started till now and I have the pleasue to work with an amazing group of super talented people lead by Burr Sutter.  Today we had rehsresal and after seen the demo on a small screen both monthes, watching it in real life was a shock. The sheer size of the screens we are presenting it blew my mind.

you feel dirty. your kid will hug you and you have to wash first
if youwork at home you have a eew secnds to close the computer is not he will never want to be a designer


o desneho tem que estar envilvido em cada passo do desenvolvimento , design thinking

vou fazer o que os argentinos sabemos fazer de melhor




- Presentação
- andresgalante
- @andresgalante
- blog.andresgalante.com
- redhat
- redhat mobile: aerogear and feedhenry
- patternfly
- outclass

- O problema 
- A quantidade de interfaces da redhat
- Novas adquirições
- Developer drive thinking
- Developers communities
- Design stardards?
- grande grupo de ux distribuido

- porque investir em UX http://www.fastcodesign.com/1669283/dollars-and-sense-the-business-case-for-investing-in-ui-design
- dar o proximo passo, dev hardcore to devops

- Research
- Boostrap
- transformar bootstrap (mostrar código)
- mudanças e porque fizemos cada uma delas. (mostrar componentes e razao por eles)
- user testing (mostrar lab)
- Criar algo que os developers possam consumir
- Reducir a distancia entre desenvolvedores e designers

- Consistency
- Design Patterns
- Design thinking (example: thonet)

- Aerogear e UPS
- O problema (mostrar old UPS)
- A solução (Mostrar novo)
- wizard
- peixe
- primeiras impressoes (http://www.fastcodesign.com/1663500/with-apps-first-impressions-are-king-heres-3-keys-to-getting-them-right)
- numeros mais numeros
- concistency

- Porque falhiu?
- meu processo e porque é um sucesso. 37 signals

- Demo
- install with bower (but also rpm etc)
- templates out of the box
- 


## Acesse este endereço:

## Olha só!

## Nooooossa

## WOW!

## andres galante

Ola, meu nome é Andrés Galante, eu sou Argentino, moro em Buenos Aires e trabalho na Red Hat.

Estou muito feliz de estar aqui, adoro o Rio, é sem duvida uma das cidades mais bonitas do mundo.

Perguntei para um amigo meu carioca se eu deveria dar esta palestra em ingles, e ele me falou que os Brasileiros valoram muito quando um estrangeiro tenta falar português, assim que pelos próximos 40 minutos é exatamente isso que vai acontecer: Eu vou tentar falar português.

Eu morei no Brasil durante um tempo e minha experiencia foi excelente, até achei legal aquelas coisas que ninguém gosta de falar, tipo o Programa do Ratinho o a Banda Calypso.

E é disso que vou falar: da Banda Calypso. 

Não, mentira, vou falar da experiencia dos usuarios e como na Red Hat construimos um framework para ter coherencia entre todos nosso produtos.



A great UI framework is the perfect intersection between aesthetic, behavior and implementation.
Patternfly make sure to look great, we user test every thing and have a beautiful implementation guid. We do the design so developers can focus on what they do best.




Só estou mostrando um mapa da Argentina porque da ultima vez que estive nos Estados Unidos, um colega meu achava que Buenos Aires fica na California.


## Red Hat



Apresentação
Mapa
CSS geek funny transformers (.autobots{transform: transform3d})
O problema, design standards?
artigo silicon valley hire more designers
Não é sua culpa mente do developer vs mente do designer
exemplo (mostrar algo foda de design)
cosnsietncia - jacob nielsen
Memoria cache
chache = Consistencia
Bootstrap
Mudanças sobre o bootstrap
Patternfly
Design vs UX
como não sabemos o caminho do usuario, we test everything
















Hello my Andres, I am a designer and code html and css

I live in Buenos Aires in Argentina.

And I am part of the User Experience Team.

Apart from working with you on Aerogear and RHMAP I also contribute to PatternFly. 

Patternfly is the solution we've created to have a consistent user experience across all Red Hat products. And since we work at Red Hat, PatternFly is Open Source.

What do I actually do?

"You make our shit look less shitty! In fact it actually looks good!"

Summers once said me that I make things look good.

And although those are super kind words, the truth is that making things look good is really easy.

I am here to help users achieve their goals. And if you think about it, thats everyones jobs. 

We are all here to help our users achieve their goals, right?

UX designers are lawyer defending the user.

My job is to make sure we all understands our users. And keep them front of mind as we do all of our design decisions , and product decisions and productisation decisions all away though the process.

And here is a first tip: our users are human beens. And dealing with human beens it's very hard.

According to the National institute of Biotecnolgy the attention spam of a human been has drop from 12 seconds in 2000 to 8 seconds in 2013. 

That's one second less than the attention span of a gold fish.

Thats why we always need to keep consistency. 

Jacok Nielsen says that Consistency is the most powerful usualbility principal, when things always behave the same, users don't have to worry about what will happen. Instead, they know what will happen based on earlier experiences.

And at Red Hat we keep constancy by following PatternFly styles and patterns.

PatternFly is our ring to rule them all.

If we change our current studio to PatternFly styles we will have a look and feel consistent with the rest of Red Hat. But as I told you, making things look good is easy and that is not our goal.

Remember: we want to help the users achieve their goals, and makeup doesn't do it.

The RHMAP studio has been growing organically and feature driven. I want to change that to a user centric approach.

First we need to really understand who our users is and their goals.

Once we understand it, we build personas and scenarios and use cases to design solutions.

For example:

One of our main personas is a Front Developer, lets call him Peter.
 
One of the main reasons Peter comes back again and again to the studio is to Build his app.

Hows does he do it?

He logs in.

Goes to Projects

Search and finds his project

Selects the project

Then selects the app he wants to build

And finds the build link on the side bar, which is the 7th link on the list. 

I don't think that app Details, Docs, Editor, Analytics, Configurations or Push are more usefull to him than building the app. 

Chances are that Peter will edit the code on his local IDE, and that he'll never change the info, configurations or push settings after his initial set up.

We have this, and I need to find a way to get him from here to here as effective as possible.

Now, the studio also has some very good design choices, like the 3 column view for projects.

But we have some structural problems that can only be address if we review the information architecture.

And that's where I fail.

I fail to the users, I fail to my goals, and to the team. I am currently not helping the users achieve their goals or helping the team understand our users.

The design of this product is something that involves all of us. 

We all know that design is important, but I know there are more urgent things to. And the urgent always beats the important.

Thats why I'll need the help of all you to create a clear vision of where the end to end User experience of the mobile platform should go.

To make na impact on the market we really need to think about Design and UX is what can take our product from where it is, to where it can be. 

















The only way to mkae this big change happend is to Design thinking.


But changing the current studio to patternfly styles










User centric products are usually way more successful than feature drive ones.

But our 




PatternFly is the 
A few years ago Red hat created the UXD team as part of an initiative to make all our products work better together and have a consistent look and feel.

It wasn't easy, but keeping consistency is key to a good user experience.


And that's critical because we are deailing with human been, and 

Thats right, the attetion span of a gold fish is 9 seconds, one second more than any of us.


Thats why at Red Hat we follow the patterns and styles of patternfly.

Patternfly is our ring to rule them all.

It was created to promote design commonality and improved user experience across enterprise IT products and applications.

And since we work at Red Hat, Patternfly is of corse Open Source.








An effective UX solution is the perfect intersection between Research, Design and Teconlogy.

Thing about with a good reserach we will understand what is the problem we need to solve

Understanding the problem we can design solutions for it.

And those solutions would be lost without a perfect implementation.

One of best examples of this process is Thonets chair number 141

It was designed in 1859 a way that you can fit 36 chairs in a square meter for shipment.

This allowed to produce them at eastern europe and send to places as far a NY keeping the price low.

More than 50M 141 were sold since 1859, a feat that wouldnt be possible if the design wasn't involced in every step of the process.

Thats what we called Deisgn thinking: Beguin with design and not end with it.

My goal is to help our users achieve their goals.

And after doing a design reserach to get to know our users I 

I fail. I need your help. Its not only my goal to help the users acheve their gaols.

That the job of every one of us.

We always talk about features when we should be talking about users. User centric products are usually way more successful than feature drive ones.

And just a a glimps of where we are standing let me show you something.

One of our main personas is a developer. 
And one of the main reasons that developers will visit our studio is to Build his app.

Hows does he do it?


He logs in.

selects projects

search and finds his project

Selects the project

Selects the app he wants to build

Finds the build link on the side bar, which by the way is the 5th link. 

Then be gets to building his app.

I don't think that app Details, Docs, Editor, Analytics, Configurations or Push are more important to him than building the app. 

Changes are that he'll edit on his IDE, and that he I'll never change the info and confiurations after they are set up for the first time.

We have this, and I need to find a way to get him from here to here in the lest amount of time.

I do get why things are the way they are. FH was a startup and it grown organically.

Whats next? Re think the information architecture. Building a huge map of the console, identify the main use cases and reacomodate things tohelp te users acheve their goals. 

UX designers are lawyers defending the user.


My goal is to help our users achieve their goals.

And after doing a design reserach to get to know our users I 

I fail. I need your help. Its not only my goal to help the users achieve their gaols.


That the job of every one of us.





I wasn't a Red Hat employee at the time, but I know that it wasn't easy to catheard a bunch of independent Open Source communities to follow the same design styles.
 





20 seconds

History of the UXD team
Duck
Fish
that's why we follow patternfly
Patternfy = RING
What is patternfly



