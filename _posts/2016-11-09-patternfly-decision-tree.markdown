---
layout: post
title:  "The Tree of Wisdom"
date:   2016-11-09 11:00:00
categories: patternfly
tags: design patternfly decision maintenance
---

![PatternFly decision tree](/img/tree/tree.jpg)


Think about a design system as a [tamagotchi](https://en.wikipedia.org/wiki/Tamagotchi). To keep it alive once your turn it on, you need to take care of it: keep it clean, feed it and make it sleep, almost like a living creature.

That’s why supporting and maintaining a design system can be more challenging than initially creating it. A smart strategy, really good rules and a lot of love and patience is the only way to guarantee long-term success.

> "A critical part of design system maintenance is ensuring that UI patterns stay up to date, embrace evolving design and development best practices, and continue to address the real needs of the organization.” - [Brad Frost](http://atomicdesign.bradfrost.com/chapter-5/#making-changes-to-patterns)

To govern the [Vanilla Design System](https://docs.vanillaframework.io/), the Canonical web team developed a fascinating decision tree and PatternFly took a similar approach.

## The PatternFly Decision Tree

[![PatternFly decision tree](/img/tree/patternfly-decision-tree.png)](https://drive.google.com/a/redhat.com/file/d/0By4Lm65O5b3rTGhPZTVnSThyLWc/view?usp=sharing)

The goal for PatternFly is to deliver a set of common and modular UI components. The goal of the PatternFly decision tree is to identify common components and that we have all the parts to build them.

To define what makes a component common, we chose to follow a simple general rule: if more than two projects using PatternFly are asking for the same component, then it’s considered common.

To determine whether or not a component is modular requires deconstructing the component into smaller blocks to understand the underlying structure of that component. That way we can ensure we are building reusable parts instead of reinventing the wheel every time we introduce a new pattern.

The three outcomes are for a pattern to be modified, added, or removed from the design system.

## Practicing What We Preach

This process doesn’t only apply to new patterns. We are running our existing components through the decision tree.

> "A design system needs ongoing maintenance, support, and tender loving care for it to truly thrive.” - [Brad Frost](http://atomicdesign.bradfrost.com/chapter-5/#establishing-a-design-system-team)

We will have be having regular assessments to make sure components stand the test of time and modify or remove them as needed.

Just like PatternFly, the decision tree is not set in stone. Both are living resources that will evolve as we care for them and give them love.
