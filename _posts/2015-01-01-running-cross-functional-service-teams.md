---
layout: post
title: Running Cross Functional Service Teams
description: "Learn about running a cross functional team with both developers and operations people"
modified: 2015-01-01
category: articles
tags: [management, operations, development, teams]
image:
  feature: ateam.jpg
---

## Preamble

This is, in written form, [something I talked about at Velocity Europe
2014](http://velocityconf.com/velocityeu2014/public/schedule/detail/37211).
Based on the feedback on the talk, I've decided a blog post might be a nice way
for people to refer back to this.

The idea of cross functional teams is that the team can be autonomous to do
what it needs to do to develop, build, test, qa, deploy, release, monitor &
maintain it's product or service. This means one team which has the entire
skillset required to own the *full lifecycle* of your service. You need to
either hire or grow a skillset that is often foreign to traditional development
teams with respect to areas like deployment & monitoring. 

From a technical perspective, if you've got a small product (like a small LAMP
stack in a startup), then this can be straight-forward. As your architecture
grows, you need to figure how to compose your application so it becomes more
manageable and maintainable. One popular way of doing this is breaking down
your application in to services ala [a service orientated
architecture](http://en.wikipedia.org/wiki/Service-oriented_architecture). 

The [topic of
microservices](http://martinfowler.com/articles/microservices.html) has been
particularly prominent recently and the principles here align very nicely with
microservices if that is how you choose to grow your application. 

I'll continue to use the word "service" as the item to organise around. If
you're small, that service may be your entire application.

This idea is particularly suited towards cloud software where you run your own
infrastructure. If you are shipping mobile software to a 3rd party device, or
selling on-premise software to your customers this article may not as relevant
to you. However, as food for thought, it may be interested to think about any
organisational inefficiencies in these areas.

Typically, the three main protagonists in any cloud software company for
building and running the software are Developers, QA & Operations. Increasingly
we start to see Security (SecOps / AppSec / Infosec) as part of this story
also. Historically, those organisations have been siloed with their own
reporting and management chains. Developers would develop stuff, often times
working closely with QA and then the proverbial "throw it over the wall" moment
would happen as they deliver to Operations. However there has been a tremendous
push recently towards
["DevOps"](http://www.jedi.be/blog/2010/02/12/what-is-this-devops-thing-anyway/)
led by Patrick Debois. It will be difficult for me to write this without
repeating some of the DevOps mantra, but I'll do my best to try and focus on
the specifics of running a cross functional team. Most of the DevOps principles
are abstract notions and I hope I describe one concrete implementation of these
principles.

As we develop more rapidly, deploy more often and maintain ever larger pieces
of infrastructure our ineffiencies become exacerbated. The goal we are striving
towards is the ability for the team who is building a service to own their own
destiny and be autonmous where they need to be.

## What's wrong with the traditional model?

Firstly, most of what I'm defining refers to a specific landscape. These
symptoms appear in large cloud software companies who have multiple
development groups producing part of the product(s). Separately, you have an
operations group which is responsible for running the stuff the developers
have built.

Over time your operations group grows bigger and bigger but with a bigger
application their application knowledge spreads thin. You've introduced a
throw it over the wall mentality where developers introduce new things that
are decided on in a sprint that they don't understand the full consequences of
in production. You've got lack-lustre monitoring with an ops team clamouring
to figure out what to monitor where. Your development teams & managers need
qualifications in project management to now manage all of the cross team
dependencies when they have new stuff to deploy or have to make changes. Those
cross team dependencies often manifest as meetings and as a development
manager you'll find yourself in meetings constantly with managers from other
groups talking about what is it you're putting in to production and how that
works.

The key metric for cloud software is *delivery*. You've given developers
autonomy over everything that happens before they deliver (build, test etc.),
but their delivery channel is non-existant or extremely manual. Delivery or
deployment becomes a path fraught with peril. 

Another interesting part of this is scaling the organisation. As the developer
or operations organisations grow, resourcing becomes much more tricky. The
development organisation grows independently from the operations organisation.
In theory, both could equally outgrow the other but my experience here
suggests development gets the resourcing and so you have more and more
developers and development teams co-ordinating with one or more central,
overloaded, operations groups. All evidence seems to point to operations as a
bottleneck in most companies as opposed to development. It feels like that
should only happen some of the time given the law of averages, so something
else is at play here. Seems like we're playing with a stacked deck - stacked
against operations.

New folks in operations start to have increasingly less familiarity with the
systems. They don't have all the tribal knowledge of the older folks and as the
system grows it becomes increasingly difficult to understand all of the moving
parts together. 

The siloing of the teams means often developers and operations folks only ever
talk when something new is about to get in to production or something is on
fire. Building a relationship in emergencies is certainly a bonding
expeirence, but then the only way those relationships get built is if you have
a lot of fires. Don't think that's something we want to encourage.

Simply, *done isn't done until it's delivered*. If a team can't own 'done',
then they don't own their service. You now have a shared ownership model
between operations and development and to coin a cliché, "if everyone owns it,
no one owns it". This manifests itself in many many ways, most of which are
covered more appropiately in other devopsy related topics you can read
elsewhere.

## Embedded in the scrum team

"*You build it, you run it*" was the phrase coined by [Werner
Vogels](http://www.allthingsdistributed.com/) to describe Amazon's model. This
has more benefits than just empowering the development team. It starts to make
operational issues front and center. It forces them to understand their service
running in production more but likewise that allows them to make better
decisions. 

[The principle of least
effort](http://en.wikipedia.org/wiki/Principle_of_least_effort) suggests that
once you've established an organisation that has now introduced significant
friction in to the delivery process that your developers, who are trying to
deliver, will often choose paths that reduce their friction even if that's not
the straighest path to victory. That can often mean making bad architectural
choices rather than going through the slog of introducing more delivery
artifacts. Suddenly, adding something new to the mix, becomes a tradeoff
discussion as you talk about the logistics of co-ordinating that. 

So, here's my proposal, embed all of the knowledge required in the scrum team.
Set that as a goal.
