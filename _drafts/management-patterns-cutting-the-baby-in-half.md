---
layout: post
title: Management patterns - Decision making and cutting the baby in half
description: Tips and tricks for management
category: articles
tags: [management, engineering]
image:
  feature: cliffjump.jpg

--- 

## Decisions, decisions

One of the things that struck me most about moving in to management
originally, was just how many decisions you were involved in. Whether it was
decisions you were personally making for yourself, or your team, team
decisions that you are helping to make or decisions your team have an opinion
on but you ultimately have a casting vote on.

In a busy company, you often don't have the time to simply sit and think about
the decisions you need to make, never mind retrospectively assessing every
decision you've made.

One of the keys I've found is to move quickly on decisions and that means
trying to use established patterns and tricks to enable yourself to make
decisions confidently. 

## Reversibility

One nugget I picked up was the notion of not spending any time on decisions
that could be reversed easily.

There will be a number of times where you find yourself or your team in a
decision making quandry. One of the first questions I try to ask is how easily
can we reverse this? If the answer is quickly, then we try to move past that
quickly. Don't be afraid to introduce this concept to your teams either. I've
found on a number of occasions that by simply introducing that concept in to a
discussion, dogma often quickly disappears. 

Decisions that aren't reversible - the metaphorical ['cutting the baby in
half'](https://en.wikipedia.org/wiki/Judgment_of_Solomon#.22Splitting_the_baby.22)
- and have high impact should be given a due process and consideration. 

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

A concrete technical example of this is using a third party library.
Proprietary library, potentially risky? Want the ability to reverse that
decision later? Define your own API that has a provider specific
implementation.

This doesn't eliminate the effort in reversing that decision, but it may
significantly reduce it.
