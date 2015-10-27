---
layout: post
title:  "IDEAS"
date:   2019-12-06 23:05:36
categories: howto
tags: Patternfly setup Bower
---


This is the story of how I tried to make a pattern using css background and I failed.

If you are looking for a nice CSS story with a happy ending stop reading now. 

On the other hand, if you are like Douglas, and you also think that writing about my sad wasted of hours during the weekend is a perfect blog post, then stay and read on. 

First things first: Lets face it, you have a problem. I understand that Douglas wants to read about unsuccessful CSS experiment, after all he is crazy enough to get married in a Castle in São Paulo. But you, my dear reader, should consider stop reading now or a psychology session.

Now that we've got the important out of the way, I'll start with a story.

## The Story

I am part of the Red Hat UXD team. Internally the team has a site where we publish our weekly status reports, blog about work in progress, ask questions, and look for shared UXD assets, and we call it **UXDepot**.

The guys that build the UXDepot did an amazing job. It has some nifty features that make me smile every week, you wouldn't believe the pleasure I feel every time I click the "Insert Last Status Report" button.

The UXDepot has an image on the header following the [Red Hat brand guidelines](http://brand.redhat.com/elements/pattern/).

So I set myself to rebuild that image as proper HTML/CSS header.

<img src="../img/dumb/UXDepot_Banner_Template.jpg" alt="UXDepot_Banner_Template" width="2910" height="270" />

## The Process

At first it seems simple. I've created a `header` with multiple background for the image, the red stipe and the shadow on the right. I've multiplied the red stripe and the shadow with CSS background blend modes, added the logo as an svg image and more of less set the font sizes.

That was easy enough, but then I found two roadblocks: the typeface and the pattern.

## The Problem

The font Interstate is not open source, I could have replaced it with an image but it is better to use a webfont. So I decided to change it with [Overpass](http://overpassfont.org/).

The second issue is the pattern. After trying for a few hours I found out that I couldn't reproduce the pattern with CSS backgrounds.

It's either impossible or I don't know how to do it. 

If it is impossible, then I am dumb for not having realize it before I stared. On the other hand if it is possible then I am too dumb to do it. Either I am dumb.

So I chose to use an svg pattern and clip it with a CSS polygon shape.

But I couldn't match the exact location of the pattern because the positioning of the red background is relative to the center of the box and not the top.

## The Conclusion

If anyone can solve this, Robb can. I asked him and he told me that since I am already using an image, he’d be inclined to make both background part of the same image.

But he is a fun killer, there is no awesomeness on using background images.

During this weekend I learn that I am dumb.


- 

## The Failure

 
http://brand.redhat.com/elements/pattern/

You enjoy 

You enjoy Hello reader, you like I hate you. Im a way, it seems that 



I am aware that 

 the timing is bad for UX changes to studio.  On-prem and OSS are all-consuming business priorities.



Mobile team. 
- I though it was going to change but same same.
- Still working on WFM
- Really bad, lots of issues everywhere.
- Mark Little ask them to stop doing new features and make the product stable.
- To me its a time bomb.
- Fh was bought by RH, but they are not RH.
- Not open sourcing.
- Developer team working constantly on client issues.
- developer team became support for clients
- Good developers thinking of leaving the team.



Company culture is something abstract that I only got to know when I experience it. I've worked by myself or in very small team for most of my professional life, and it wasn't until recently that I've got the chance to see how crucial it is.

According to [forbes](http://www.forbes.com/sites/williamcraig/2014/10/24/what-is-company-culture-and-how-do-you-change-it/) the "culture" is the Company vision, values, norms, systems, symbols, language, assumptions, beliefs, and habits.

It's basically about people. A talented smart team with good leadership can embrace, follow and create good culture. And I've been lucky enough to have find all of that when I join Red Hat.

I also learn that it takes much more time and effort to build a culture than to destroy it.

I don't think that for large companies there is such thing as a company culture. Each team has its own dynamics that creates ecosystems, and that of courses depends on the people working and leading each team.

Clash of titans

What happens when 

Lead on maestro

There is a need for developers on the market and few good ones. Good developers can choose where to work.


Adapt or die





On Friday I received the opening and closing slides to include on my presentation for the upcoming talk at Interaction South America 2015 in Cordoba, Argentina.

The opening slide has the title of the talk, the authors name inside an hexagonal shape with rounded corners in the middle of the screen and some information at the footer. Everything is laid over a two color background spilt horizontally in the middle. There is also a transparent pattern and a stripe at the top.

They sent keynote and powerpoint options, and I though: "what if anyone want to use [reveal](http://lab.hakim.se/reveal-js/#/), there should be an HTML version of this... How hard can it be to build it?"

There is only one way to answer that question, by doing it.

## The HTML

The HTML is simple, with a title on an `h1` tag, the name of the author on a `p` tag and a `footer`, but framing the authors name on a rounded corner hexagonal box that is horizontally and vertically centred end up been a mathematical challenge.

{% highlight html %}
<body>
  <h1>Keynote title</h1>
  <p>Authors Name</p>
  <footer>This is an HTML version of the opening slide for ISA 2015 presentations.</footer>
</body>
{% endhighlight %}



## The SCSS

There are two challenges I face here. The background and the rounded corner hexagonal box.


### Background

For the background I am applying CSS mutiple background on the `body`:

- I start with a linear gradient to generate the stripes at the top.
- Then there are 2 svgs to generate the pattern. It has a blend more of multiply.
- I am adding a little shadow at the top
- and finally I paint half of the screen with a gradient stripe.

{% highlight scss %}
  background-color: $color-background-bottom;
  background-image: 
    linear-gradient(to left, 
                    $color-background-stripe-01, $color-background-stripe-01 200px, 
                    $color-background-stripe-02 200px, $color-background-stripe-02 360px, 
                    $color-background-stripe-03 360px, $color-background-stripe-03 600px, 
                    $color-background-stripe-04 600px, $color-background-stripe-04 800px, 
                    $color-background-stripe-05 800px, $color-background-stripe-05 960px
                    ),
    url(../img/pattern.svg),
    url(../img/pattern-bottom.svg),
    linear-gradient(to bottom, rgba(0,0,0,.1), transparent 100%),
    linear-gradient(to bottom, $color-background-top, $color-background-top 50%, transparent, transparent 50%);
    background-size: 960px 10px, 700px,700px, 100% 20px,  100%;
    background-repeat: repeat-x, repeat-x, repeat-x, repeat-x, repeat;
    background-blend-mode: normal, multiply, multiply, normal, normal;
    background-position: 0 0, 0 0, -330px bottom , 0 0, 0 0, 0 0;
{% endhighlight %}


### Rounded corner hexagon

To explain how I created this hexagon I have to take you back to school.

The hexagon is a rectangle with two 45º rotated squares on each side. This means that if the height of the squares is **x**, the rectangle should be **x times the square root of 2**.

But its not that easy, I also need to consider the rounded corner of the squares. Trigonometry to the rescue. First we discover the size of the hypotenuse and we subtract the diference of the border radius.

I did all this math, so you don't have to. This sass mixing will generate a rounded corner hexagon and absolute position it at the center of the screen. You are welcome.


{% highlight scss %}
@mixin rounded-hexagon($hexagon-height: 5rem, $hexagon-radius: .5rem, $hexagon-bg-color: white, $hexagon-font-size: 1.6em, $hexagon-color:#515F67 ) {
  margin: 0;
  color: $hexagon-color;
  background: $hexagon-bg-color;
  height: calc((#{$hexagon-height}  * 1.414213562373095) - (((#{$hexagon-radius} * 2) * 1.414213562373095) - (#{$hexagon-radius} * 2)));
  line-height: calc((#{$hexagon-height}  * 1.414213562373095) - (((#{$hexagon-radius} * 2) * 1.414213562373095) - (#{$hexagon-radius} * 2)));
  position: absolute;
  top: calc( 50% - (((#{$hexagon-height}  * 1.414213562373095) - (((#{$hexagon-radius} * 2) * 1.414213562373095) - (#{$hexagon-radius} * 2))) / 2));
  left: 50%;
  margin-left: -9em;
  min-width: 18em;
  text-align: center;
  font-size: $hexagon-font-size;

  &:after, &:before{
    content: " ";
    transform: rotate(45deg);
    transform-origin: 0px 0px;
    background-color:$hexagon-bg-color;
    width: $hexagon-height; 
    height:$hexagon-height; 
    top: calc(((#{$hexagon-radius} * 1.414213562373095) - #{$hexagon-radius}) * -1);
    left: 0px;
    position:absolute;
    border-radius: #{$hexagon-radius};
    z-index: -1;
  }
  &:before{
    left: 100%;
  }
}
{% endhighlight %}


[Here is the result](https://cdn.rawgit.com/andresgalante/isa2015cover/master/index.html).

And here is the code altogether:

<div data-height="500" data-theme-id="20015" data-slug-hash="wKPPPZ" data-default-tab="html" data-user="andresgalante" class='codepen'><pre><code>&lt;h1&gt;Keynote title&lt;/h1&gt;
&lt;p&gt;Author&#39;s Name&lt;/p&gt;
&lt;footer&gt;This is an HTML version of the opening slide for ISA 2015 presentations.&lt;/footer&gt;</code></pre>
<p>See the Pen <a href='http://codepen.io/andresgalante/pen/wKPPPZ/'>CSS Hexagon Rounded Corner</a> by Andres Galante (<a href='http://codepen.io/andresgalante'>@andresgalante</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
</div><script async src="//assets.codepen.io/assets/embed/ei.js"></script>

## Will I use it?

Of corse not. Keynote is awesome to build presentations, plus it has the way underused flame effect that I alway try to sneak in all my talks.

I am sure there are way better ways to do hexagonal rounded corner shapes, this one doesn't feel elegant enough. But it was good fun to build it.


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



