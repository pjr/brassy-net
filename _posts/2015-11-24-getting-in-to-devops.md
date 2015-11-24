---
layout: post
title: I want to be a Devops!
description: Learning how to apply continuous 
category: articles
tags: [devops, operations, sre, web operations]
image:
  feature: volcano.jpg

--- 

## Danger! 

My buzzer just went off when you used the word 'Devops'. Ewww! Devops is not
a moniker I'm fond of for many reasons. However, that's not your fault. Given
how prevalent the term is, let's ignore that for the time being.

One of the main challenges with this denomination is the variety of different
things people mean when they use it. Mostly somewhere between part-time build
engineer & part-time web operations engineer. So, you can take it that my
definition of what folks are looking for are Linux System Engineers who can
code. I wanted to be an engineer who can build maintainable, scalale systems
by either writing code, using 3rd party products or more often that not some
mixture of the two.

No matter what your definition is, whenever you want to be something in the
tech world, I have some generic advice. Make it your passion. Build your
craft. I gave a generic "career talk" for [CareerZoo](http://www.careerzoo.ie/)
previously which talks about [this idea of passion for your 
career](http://www.slideshare.net/PhilipReynolds4/your-career-a-hiring-managers-perspective).

In doing a bit of research for this blog post, I came across [this talk from
Theo Schlossnagle](https://www.youtube.com/watch?v=LAP1zaXUvAE). The idea of
having passion for what you do and becoming _obsessed_ with the craft is very
very key. Understand that success in an industry with so much to learn is
difficult and is becoming more difficult by the years with more technology.

## Forewarning

Some of these bullet points are weeks worth of effort. Some are months.
Some are years. To really master what I'm talking about, it's a slow journey.
The nice thing is it can be very practical and I think that's what is very
attractive to people who get in to stuff via this route.

The only thing I would recommand is starting the programming side as soon as
possible.

This is not meant to be exhaustive or comprehensive. You will have to join
plenty of dots yourself and you'll obviously pick up lots of other things
along the way. The key is to never stop learning and try to apply your
knowledge as quickly as you learn it. 

Pick a project or two at the bottom and try it out. 

## Systems Engineering
* Start learning how to install and administer Linux boxes
    * Pick your favourite distribution. If you don't have one, pick Ubuntu.
* Setup your own web servers, dns servers, email servers and run them on
the internet.
    * Not sure which ones? Apache, Bind & Postfix.
* Start learning how to use the shell like an expert.
* Pick up an editor - vim's fairly ubiquitous. Emacs is another alternative.
    * If you don't care, pick vim.
* Understanding networking
    * Know how IP's, gateways, netmasks all work. 
    * Understand CIDR.
    * Understand ARP, ICMP, traceroute
* Learn a monitoring system. 
    * Understand how to monitor your environment.
* Learn package management. 
    * Understand how your distribution of choice packages up software. 
    * Understand  
* Learn an RDBMS
    * If you're not sure, pick PostgreSQL.
* Understand filesystems
    * Start with simple local filesystems (ext3, ext4)
    * Learn NFS (as much as that is possible)
    * Look at distributed filesystems like Ceph, Gluster 


## Configuration Management
* Learn a config management system
    * If you don't care, use ansible
* Practice trying to deploy stuff with ansible
    * Use 3rd party stuff to start, but understand and learn how to write your
    own playbooks.

## Learning to code
* Learn how to write bash comfortably
    * You should be able to parse most log files fairly easily.
    * awk & sed should be second nature to you
    * Automate random duties (e.g. backups) using a config mgmt system
* [Learn python](http://learnpythonthehardway.org/)
    * You need to be a polyglot & know multiple languages. 
    * Powerful, dynamic scripting language. 
    * Often great for when bash isn't.
    * _Master the language_
* Learn C
    * You don't necessarily need to be a C master, but I think it helps.
    * Your underlying system is written in C and many common system software
    based applications are written in C.
    * Being able to patch systems, find bugs, root cause things to source code
    is jedi type stuff. Strong C skills give you confidence to do things
    around the system you won't get elsewhere.
* Learn a version control system
    * If you're not sure, use git.
* Learn how to develop and use HTTP based API's.
    * Interact with AWS to spin up VM's on demand
* Read and write lots of code!! 
    * Pick up simpler systems - I often look at the early versions of systems
    before they got complicated. First version of git. First version of nginx.
    First version of Openstack

## Internet / networked environment focus
* Understand common protocols and know how to debug them
    * SMTP - You should be able to execute an SMTP transaction by hand :-)
    * DNS - be intimately familiar with dig and how DNS requests work.
    * HTTP - be able to trace HTTP requests.
    * TCP/IP - there's so much to learn here, but learn to make tcpdump your
    friend
* Encryption
    * Understand PKI and learn how to use GPG
    * Understand one-way hashing 
* Understand time
    * What UTC is
    * What is NTP and how does it work?
* Learn LDAP
    * LDAP's a pain, but still very prevalent. Give OpenLDAP a whirl.
* Learn load balancing
    * Use HAproxy to distribute load to a bunch of webservers.
* Learn caching
    * Learn Varnish and the benefits to a caching layer 
* Learn Redis
    * A simple, very popular key value store. Write some code that uses Redis.

## Putting it all together - practical examples
* Write a small web application using whatever langauge or framework you know.
Make sure it uses an RDBMS (e.g. Postgres/MySQL). Write some code to spin up a
VM on AWS and deploy your application using your config mgmt system of choice.
* Setup an email address on your local email application that when you send it
an email with a secret key can add an entry in to your DNS system.
* Write code to be able to add and remove users / groups from an LDAP system
which is responsible for authenticating a whole series of systems.
* Build a system which automatically detects when your webserver is down and
automatically starts it back up again when it does.
* Generate load on your webserver and tune / optimize it so that it can handle
way more than what it does today.

## ... and

... here's the bad news. You're probably still not there. The next stage is
building these systems at scale and seeing where they break and knowing
where to put effort in to making them robust and reliable.

Here's the good news though. You have more of a foundation of knowledge than
90% of the folks out there practicing devops and you have a fantastic base to
build from.

## Resources

Read, read, read. Spend your spare time reading.

* Google is your friend obviously. You should be able to find oodles of
tutorials online
* Usenet - there's still a lot of activity online around Usenet and Usenet
groups.
* Mailing lists for popular / large pieces of software (e.g. Postfix / nginx).
I used to read a couple of hundred posts per day from these and you just pick
up things through osmosis.
* Stackexchange - go figure out how to answer questions on serverfault.
* Reddit - lots of subs related to Linux.
