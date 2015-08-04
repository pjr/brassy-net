---
layout: post
title: Running Cross Functional Service Teams
description: "Learn about running a cross functional team with both developers and operations people"
modified: 2015-08-01
category: articles
tags: [management, operations, development, teams, devops]
image:
  feature: ateam.jpg
---

## Preamble

This is, in written form, [something I talked about at Velocity Europe
2014](http://velocityconf.com/velocityeu2014/public/schedule/detail/37211).
Based on feedback from the talk, I've decided a blog post might be a nice way
for people to refer back to this.

The idea of cross functional teams is that the team can be autonomous to do
what it needs to do to develop, build, test, qa, deploy, release, monitor &
maintain it's product or service. This means one team which has the entire
skillset required to own the *full lifecycle* of it's deliverable. You need to
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
to you. 

Typically, the three main protagonists in any cloud software company for
building and running the software are Developers, QA & Operations.
Increasingly we start to see Security (SecOps / AppSec / Infosec) as part of
this story also. Historically, those organisations have been siloed with their
own reporting and management chains. Developers would develop stuff, often
times working closely with QA (or not!) and then the proverbial "throw it over
the wall" moment would happen as they deliver to Operations. However there has
been a tremendous push recently towards
["DevOps"](http://www.jedi.be/blog/2010/02/12/what-is-this-devops-thing-anyway/)
led by Patrick Debois. It will be difficult for me to write this without
repeating some of the DevOps mantra, but I'll do my best to try and focus on
the specifics of running a cross functional team. Most of the DevOps
principles are very abstract and I hope to espouse some more of the concrete
benefits I've seen.

As we develop more rapidly, deploy more often and maintain ever larger pieces
of infrastructure our inefficiencies become exacerbated. The goal we are striving
towards is the ability for the team who is building a service to own their own
destiny and be autonmous where they need to be.

## What's wrong with the traditional model?

Firstly, most of what I'm defining refers to a specific landscape. These
symptoms appear in cloud software companies who have multiple development
groups producing part of the product(s) that typically lives on an ever
growing and more complex infrastructure. Separately, you have an operations
group which is responsible for running the stuff the developers have built.
They're often also responsible for building the stuff that the stuff the
developers built runs on.

Over time your operations group grows bigger and bigger. With a bigger
application their application knowledge spreads thin. You've introduced a
throw it over the wall mentality where developers introduce new things that
are decided on in a sprint that they don't understand the full consequences of
in production. You've got lack-lustre monitoring with an ops team clamouring
to figure out what to monitor where. Typically after it goes in to production.
Your development teams & managers need qualifications in project management to
now manage all of the cross team dependencies when they have new stuff to
deploy or have to make significant changes, particularly where there's
deployment impact. Those cross team dependencies often manifest as meetings
and as a development manager you'll find yourself in meetings constantly with
managers from other groups talking about what is it you're putting in to
production and how that works.

The key metric for cloud software is *delivery*. What do we mean by delivery?
Running in production. You've given developers autonomy over everything that
happens before they deliver (build, test etc.), but their delivery channel is
non-existant or extremely manual. Delivery becomes a path fraught with peril. 

Another interesting part of this is scaling the organisation. As the
development & operations organisations grow, resourcing becomes much more
tricky. The development organisation often grow independently from the
operations organisation. In theory, both could equally outgrow the other but.
All anecdotal evidence seems to point to operations as a bottleneck in most
companies as opposed to development. It feels like that should only happen
some of the time given the law of averages, so something else is at play here.
Seems like we're playing with a stacked deck. Stacked against operations.

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

## Embed in the scrum team

"*You build it, you run it*" was the phrase coined by [Werner
Vogels](http://www.allthingsdistributed.com/) to describe Amazon's model. This
has more benefits than just empowering the development team. It starts to make
operational issues front and center. It forces them to understand their service
running in production more but likewise that allows them to make better
decisions. 

[The principle of least
effort](http://en.wikipedia.org/wiki/Principle_of_least_effort) suggests that
once you've established an organisation that has now introduced significant
friction in to the delivery process, that your developers, who are trying to
deliver, will often choose paths that reduce their friction even if that's not
the best path. That can often mean making bad architectural choices rather
than going through the slog of introducing more artifacts which complicates
deployment and makes them end up in meetings. Suddenly, adding something new
to the mix becomes a tradeoff discussion as you talk about the logistics of
co-ordinating that. 

So, here's my proposal. Embed all of the knowledge required in the scrum team.
Set that as a goal. The scrum team needs to own all aspects of their service.

Delivery is a feature.
Upgrade is a feature.
Performance is a feature.
Monitoring is a feature.
Uptime is a feature.

If you do not own those areas in your scrum, then those features are owned
outside of your scrum team. You've now created dependencies. Uh oh.

## Dependency vs Redundancy

There is a natural inclination for every engineer to try to re-use as much as
possible. Everything we're taught in software engineering lends itself to
re-using code. Well written, well designed code following [DRY
principles](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself). 

The engineering groups natural inclination is, _"Shouldn't a build team take
care of our builds? Shouldn't a deployment team take care of our deployments?
Shouldn't a monitoring team take care of our monitoring?"_. We then centralize
those resources. Organisational efficiency at it's finest. Those are
specialized skills that are consolidated within those groups. Easier to hire
for. Easier to manage. Dedicated manager. On-paper perfection. 

Unfortunately, reality bites and, in most cases, no-one really understands
what we've created from a project delivery standpoint. First of all, you need
to accept that your _definition of done, is delivered_. Now start to draw the
dependency tree of teams that it takes to deliver small features & changes for
just one engineering team & you start to see the challenges. That dependency
diagram continues to get more and more complicated as the organisation grows.
Typically those same groups have multiple other groups that depend on them
also. Once you end up in this situation you end up in resource contention
hell. A lot of developers can actually relate to this and have experienced
this intimately in their job. It's called [Dependency
Hell](https://en.wikipedia.org/wiki/Dependency_hell). Who knew, it existed
within organisations too! 

So, the alternative to dependency is redundancy. We end up with multiple teams
potentially inventing the same solution to a similar-sounding problem (e.g.
caching services, queueing services). So, the idea is not to deal with
redundancy up-front by trying to eliminate everywhere there is redudancy.  The
idea is, to bludgeon more development metaphors, refactor as and when you see
it.

Embrace redundancy! Then figure out how to remove it long term. Don't make
removing redundant services or functions dependencies on delivering.  Embrace,
potentially, reinventing a slightly less-round wheel. You can get to make it
rounder over time.

So, hold on a minute, you say, if we brought this thought to a logical
conclusion & every team did everything themselves, they'd run their own IT
infrastructure, build data centers, build their own laptops.  That's obviously
not a runner. How do we know when to choose redundancy over dependency? Simple
answer... when it's a problem. When it's stopping you getting things done.

*The goal should be to minimize as many external dependencies as possible.*

## Organisational Growth

One of the side benefits to traditional development teams now owning more of
their delivery pipeline is headcount planning. 

Often, resources that own different parts of the delivery chain live in
different parts of the organisation. When that happens you now have
complicated resourcing strategies as different parts of the organisation grow.
Inevitably, you end up with capacity constraints somewhere and inevitably
those constraints end up on the teams that are the most contended i.e. have
the most dependencies. 

Owning your build & delivery chain and minimizing those external dependencies
makes headcount planning a lot easier. The dev team owns the headcount, one
manager makes a decision and a business case. The decision therefore can be
made at the closest point to the actual resourcing problem - at the team
level. 

## The people

The last set of benefits I'll talk about is on the people side. 

The first and most important trait of having all of this knowledge on one team
is growing a deeper understanding of the system with your engineers. If your
delivery chain, build pipeline or your infrastructure is complicated and/or
nuanced this becomes more important. Having the engineers understand these
areas allows them to dive deep in the belly of the beast, where necessary.
Even if you only have a few people who can do that, that knowledge tends to
spread when it's _within the team_.

Second on my list is autonomy. Suddenly, when you own more of the system, you
are free to make different choices. You genuinely become more agile. If you
need to upgrade to a newer version of your language framework, test harnass
etc. you can do that. Turning on a dime is difficult in any software company,
but owning more of your process is the key to make sure you're not trying to
turn the titanic. Co-ordination with other groups is difficult. One of the
consequences is that you find over time, people hesitate to suggest things
that require large amounts of effort. Now you're free to try new things, to
experiment and iterate towards better solutions for your builds, delivery
pipeline etc. When small changes take large amounts of co-ordination and
logistics, iterating towards a solution is always painful & risky. This type
of perceived red-tape actually starts to penetrate developers well-being.
Moaning & griping can often happen as teams complain about how long simple
things take to do. Let them own it.

Last is cross training. You'll find that having e.g. ops and dev folks on the
same team means knowledge starts to filtrate between the two groups of people.
The developers and ops folks often end up blending in to the same role where
it can often become difficult on the surface to even know you have different
skillsets within the group.

*As we scale, we figure out new and imperfect practices that hamper our
ability to grow & sell product. Sometimes these changes are fundamentally
different ways to execute and require huge buy-in. Don't underestimate the sea
of change within your organisation required to make this happen.*
