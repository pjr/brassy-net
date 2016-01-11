---
layout: post
title: Management, decision making and cutting the baby in half
description: Tips and tricks for management
category: articles
tags: [management, engineering, management patterns]
image:
  feature: cliffjump.jpg

--- 

## Decisions, decisions

One of the things that struck me most about moving in to management
originally was just how many decisions you were involved in. Whether it was
decisions you were personally making for yourself, or your team, team
decisions that you are helping to make or decisions your team have an opinion
on but you ultimately have a casting vote on.

In a busy environment, you often don't have the required time to simply sit
and think ad nauseum about every decision you need to make. Retrospectively
looking at every decision is also typically a luxury.

Moving quickly on decisions, where possible, is absolutely necessary. That
means using established patterns to enable yourself and your team to make
decisions more confidently.

## Reversibility

There will be a number of times where you find yourself or your team in a
decision making quandry. One of the first questions I try to ask is how easily
can we reverse this? If the answer is quickly, then we try to move past that
quickly. Don't be afraid to introduce this concept to your teams either. By
simply introducing that concept in to a discussion, dogma often quickly
disappears. 

Decisions that aren't reversible - the metaphorical ['cutting the baby in
half'](https://en.wikipedia.org/wiki/Judgment_of_Solomon#.22Splitting_the_baby.22)
- and have high impact may need to be given more consideration. 

Hiring? Not easily reversible.
Architecture choice? Not easily reversible.
Workflow? Easily reversible.
Button colour? Easily reversible.

The next time you end up in a discussion that seems like it's going nowhere,
ask yourself and your team can you easily reverse a decision and if so, try
and move forward quickly.

## Introducing reversibility

There are times where you can introduce the property of reversibility to a
decision making process. 

A technical example of this is using a
[Facade](https://en.wikipedia.org/wiki/Facade_pattern) on a third party library.
Leaky abstractions aside, the ability to reverse that decision later by
replacing the underlying concrete implementation can be beneficial. 

This doesn't eliminate the effort in reversing that decision, but it may
significantly reduce it.

A vendor example, might be hiring a consultant or firm to do a once off
smaller job, before making a decision to enter in to a longer term
higher-value agreement.

Don't just hope for reversibility to be present. You can often introduce it.

## Reversibility and Agile

I should note that this idea of reversibility is very present in all [agile
methodologies](http://agilemanifesto.org/). Deliver in small increments,
allowing us to change course once we receive feedback on a small, delivered
piece of product or functionality. 

It's not always possible, but it's one tool to put in your decision making
toolbelt! 
