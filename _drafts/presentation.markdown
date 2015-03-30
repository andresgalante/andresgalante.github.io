---
layout: post
title:  "Patternfly talk"
date:   2019-12-06 23:05:36
categories: howto
tags: Patternfly setup Bower
---

Patternfly DevNation

#### image of my beach house
Last year my wife and I decided to skip winter. We rent a house by the beach in Dominican Republic and we spent our days on the sand.

#### image of the beach
This is the story of how I went from there to been here talking about patternfly.

#### Pictures of Alan (my boss) and Paul (my other boss)
On August I had an interview to join Red Hat UX team.
It was odd: I was wearing swim suite, at the beach, having a job interview over hangout with Alan and Paul, two of my current bosses.

#### Pictur of me with a dialog box "You had me at hello."
During the interview Paul mention Patternfly and it was love at first sight. I was already using bootstrap on most of my projects, and Patternfly just click. A library of UI patterns makes sense and I wanted to be part of that.

#### Pictures of Paul(my other boss) with a dialog box "I'm gonna make him an offer he can't refuse."
4 month later I was a Red Hatter, part of the UX team and dedicated to jboss mobile effort: Aerogear.

#### Aerogear logo
That's where I met a fantastic group of people: The Aerogear team. It amaze me how Open source communities work together: everyone helps each other, if one fails the hole team fails. There is a sense of belonging, a sense a duty that makes you always do your best.

#### yay!
As a UX designer my main goal was to to help the team update and improve Aerogear Unified Push Console.
And to me that meant the perfect opportunity to put my hands on Patternfly for the first time.

#### Image of old UPS

This (the image) is how the UPS looked like. It was based on very early Patternfly, but its implementation was not following its guidelines correctly.

Jakob Nielsen says that consistency is one of the most powerful usability principles: when things always behave the same, users don't have to worry about what will happen. Instead, they know what will happen based on earlier experience.

A UPS user will probably use other Red Hat products and to keep consistency we follow patterns.

#### Design patterns are means of capturing useful design solutions and generalizing them to address similar problems. -- About Faces: Cooper, Reiman, Crionin, Noessel.
(read quote)

By taking advantage of existing work, we can focus on solving new problems, rather than reinventing the wheel.

Of course thats not easy. The Patternfly team spends a lot of time to identify which patterns to work on.  You wouldn't believe the amount of effort, discussion and testing behind each one. 

So when they approve a patterns you can be sure that it'll work.

#### Patternfly logo

As Robb mentioned earlier, they created a reference implementation of all of their Patterns. We’re talking working code -- login pages that looked good, widgets, perfect CSS.

And I think he’ll tell you that, at first, his team really didn’t expect anyone to use the reference implementation directly. They wanted their perfectly working, beautiful, amazing code to simply be an example for how to do it.

#### img: tool box with tools, maybe add some logos

There I was, ready to start: I had a library with patterns, amazing code bits and a Red Hat project to work on. 

#### img

First impressions are crucial and we weren't doing a great job on UPS. We set expectations high but we didn't help user achieve their goals.

That's why, for the new design, I wanted to take a user centric approach and add a wizard and create blank saltes to guide users.

But there weren't Wizard or blank slates patterns on Patternfly.

#### Give back

That's the beauty of open source projects: you can build uppon them and contribute back to the community.

So I created a wizard and implemented blank slates, did some gorilla user testing and send a draft for the Patternfly team to review.

My pattern was tested even more, and added to the library.

#### Angular + Boostrap + Patternfly

UPS is based on Angular.js, Angular plays nicely with boostrap and Patternfly is based on boostrap.

So implementation was straight forward.

#### Gregs patternfly RCUE

One more thing.

As Robb mentioned, internally in Red Hat we have the RCUE project, which is a fancied-up copy of PatternFly. aka the downstream project. Red Hat colors, logos, etc.

And Aerogear UPS downstream project is called Red Hat JBoss Unified Push.

If you think about it, by using PatternFly and RCUE, we can have almost the same codebase change its brand by very easily swapping out the look-and-feel library. Almost like an application skin.

It literally took me 10 minutes to go from Patternfly to RCUE on UPS.

#### UPS now image
I am really happy with how much better the end result is.
The new design saw the light on May, and initial user testing were very successful.

#### Lets be honest :)
Now lets be brutally honest

Design patterns are not recipes or plug and play solutions. Patterns are always context specific, they are design to be applicable to common design situations that share similar contexts, constraints, tensions and forces.

Each implementation of a pattern differs a little from the other, thats why to have a successful result you'll always need a UX expert or a designer.

#### Show, don't tell
Patternfly is organic, is alive and growing.
Come to our booth and we will show you how you can benefit and be part of it.

#### patternfly.org
questions?
