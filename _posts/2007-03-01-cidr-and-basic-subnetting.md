---
layout: post
title: CIDR and basic subnetting
description: "Explaining the basics of CIDR and subnets and how they work"
modified: 2015-01-01
category: articles
tags: [networking, cloud]
image:
  feature: networks.jpg
---

This particular aspect of networking/computer affects everyone with a network.
It's so unbelievably necessary for anyone who deals with networks (at any
level) to understand. I cannot stress this enough! :) That said, so many
people have serious problems with it and I can kind of understand why. Every
single site I've seen goes into the detail straight away with binary
arithmetic. Yes, binary arithmetic is how you work these things out, but are
these people doing this binary arithmetic in their head when they know a /26
has a subnet mask of 255.255.255.192? Well, yes and no. They're using a
shorthand variety, they are not ANDing 1 and 0's. Well, if they are, they're
wasting braincells.

Do you even know what I just said? No? Well read on...  Warning : There's very
little point skimming this. It might be time to open up your calculator and
grab a piece of paper and a cup of coke (ugh, I hate coffee).

So, a computer network is basically just a way for my computer to talk to
another computer. If you need this part explained, it might be time to start
reading somewhere else before continuing here. So on our IP based networks,
machines have IP addresses. So, yadda yadda yadda, this uniquely identifies a
machine on the network. I'm hoping noone needed that to be explained. If so,
go read some background first. Of course, machines can have multiple IP
addresses and even one IP address can represent multiple machines, but let's
keep it simple for the time being (if you don't put these things in, the
anoraks get very animated).


So back in the good ol' days, when networks were easy we had what is known as
... Park Life ... ok, sorry, bad habit ... classful networks. It's surprising
how many texts and papers (mostly out of date) still refer to Class A, B & C
networks. These are obsolete and have been since about 1993 (ref: wikipedia -
it's great isn't it?). So basically, these classful networks, i.e. what is
commonly referred to as Class A, B & C have been out of date since anyone
actually used the Internet. What the hell is up with people still referring to
them then? I don't know either. What is used now is CIDR - Classless
Inter-Domain Routing. Don't get too bogged down remembering it, just associate
network segments with the slash terminology - /16, /24, /28 (pronounced "slash
16", "slash 24", "slash 28") etc.

So what were classful networks about and why do we now have CIDR? Well, a
network is great, but although we have one big network (the Internet) it's
actually divided up into many small segments. This is to facilitate many
things. There have probably been many papers written on the benefits and right
and wrong ways to segment networks but at the end of the day it makes logical
sense that in some way the big network containing 2^32 IP addresses is broken
up into smaller chunks that are more manageable. In the before time (i.e.
before 1993) you (as a person who wanted an allocation of public IP addresses)
could have three types of allocations. A class A (big allocation - like really
big), a class B (medium sized) and a class C (small sized). These were fixed
sizes, so a Class A was 16777216 (or 2^24 - that's 2 to the power of 24) IP
addresses, a class B was 65536 IP addresses (i.e. 2^16) and a class C was 256
IP addresses (i.e. 2^8).

Now, what about if someone wanted something in between a class C and a Class B
(like say 20,000 ip addresses) ? Well, they'd either have to get allocated
approximately 78 class C's (20,000 divided by 256) or use a class B and waste
40k IP addresses. What if someone wanted 12 IP addresses? Well, they'd get a
class C as well ... eek. Ok, so we moved away from this technique to stop
WASTING IP addresses. Why don't we hand out IP addresses one at a time?
Because that isn't feasible & it makes sense to use logical blocks for a lot
of reasons but especially routing ones. There's a long winded explanation for
that as well, so just ignore that question! 

So, the CIDR format was used in order to facilitate chopping up network
segments into smaller more configurable chunks.
Now, this is the bit where we will need to start using some binary arithmetic,
but don't worry, I'll try and guide you through it.

First and foremost:
An IP address is 32 bits. In fact in networking, most things are represented
in 32 bits as most computers can natively (or at least were, we're moving
towards 64 bit architectures now) store 32 bits. What does that mean? It means
that the IP address 89.234.64.66 (the IP of this website) is stored as 32 1's
and 0's.

IP addresses are composed of four parts (octets), so if an IP address is 32
bits, each octet is how many bits? (octet should give you a clue as well) ...
yup, ok it's 8 (again, simple arithmetic, 32 divided by 4).

So, in 1's and 0's, the IP is broken up into:
{% highlight c %}
    89      234       64       66
01011001 11101010 01000000 01000010
{% endhighlight %}

Why is that useful? Well, it's nice in theory, but in practice, I'll never
convert an IP address to it's binary form, so yeh, take note of it, but I
won't pretend you'll ever need to use that. That's what machines are for,
making calculations and converting between base 10 and base 2.
Still, base 2 and powers of 2 are important, so don't think you're going to
get away with doing no math here.

Ok, so if you're configuring your network settings on your PC and you entered
that IP address first, the next thing you'd (probably) enter is the subnet
mask. So, this seems to be the BIG confusion. What the hell is a subnet mask,
why do you need one, and how do you tell what one to use?

Quite simply, the subnet mask represents how big your local network is. What's
your local network? Normally stuff that's PHYSICALLY connected to you. In a
simple scenario, that's basically it. i.e. you don't go through any "hops" to
get to a machine on your local network. If two machines are plugged into the
same hub, they're on each others network. Switches are different, because they
use VLANs (Virtual LANs), but again this is just a logical separation.

So who decides? Well, whoever is designing the network decides. Now for home
networks, it doesn't matter, most people just choose easy things to remember,
but for corporate / business / large networks or anyone who has to deal with
public IP addresses (i.e. IP addresses reachable by anyone on the internet) oh
it SO matters. It SO does. Like.

When we talked about classful networks (i.e. class A, B & C) most people (or
certainly a large number of people) seem to know that  
Class A - subnet mask 255.0.0.0  
Class B - subnet mask 255.255.0.0  
Class C - subnet mask 255.255.255.0

Notice how a subnet mask is in the dotted quad format like an IP address,
split up into four parts. Now the easy way most people go is with a Class C,
the last octet (quad) can change, i.e. if my ip address is 89.234.64.66, then
everything from 89.234.64.1 up to 89.234.64.255 is in my network. If it was a
Class B, then everything from 89.234.1.1 up to 89.234.255.255 is in my range.
If it was a Class A, then everything from 89.1.1.1 up to 89.255.255.255 is in
my range. Now I can kind of see why the classful stuff stayed around ... it's
like a mnemonic ... a handy way of understanding subnetting, even if it's
outdated and wrong nowadays. Well, it's not quite wrong, but it's not quite
correct. You'll certainly get a lot of anoraks excited using that terminology.

So, let's explain CIDR a bit more so we can decide what CIDR mask to use
(remember the slash 16, slash 24 stuff from up above?) for a size network. Ok,
so back in the old days, a Class C network was 256 IP addresses. That was the
smallest network segment you could use. What's the equivalent in CIDR if any?

Well, the equivalent is a /24. What does that mean? It kind of means that
everything past the 24th bit is in my network. Now that doesn't really make
sense, but bear with me. First of all, remember these IP addresses and subnet
masks are 32 bits, so four by 8 bits. 24 bits (3 times 8 is 24; 4 times 8 is
32. Therefore 24 is 3/4 or three-quarters of 32) basically means that the
first three octets are non-variable in our network.
{% highlight c %}
    89      234       64       66
01011001 11101010 01000000 01000010
                          ^
{% endhighlight %}
Take everything past the arrow (in bold) and that can change and still be in
our network. If anything changes BEFORE the arrow, then our computer will
consider that to be outside our network. Ok, so maybe you're asking what the
hell happens if it's outside our network? Well, our computer sends it to the
gateway (sometimes referred to as the default gateway). So when you're
manually entering IP information, that's normally the third setting you're
asked for.

To Summarize (don't worry, there's lots more, but let's take a bit of a break
here for a second):

1. IP address - 32 bits. Must conform to the dotted-quad notation and when
handing out multiple IP addresses to machines on the same network segment,
they need to be decided carefully. How? We'll look at that later.
2. Subnet Mask - 32 bits. Decides what we consider local and what we consider
foreign.
3. Gateway - It's an IP address too. It's the IP of a computer (most likely a
router) that will forward your packets onto anything outside of your network.
OK, so we've stated that a Class C is equivalent to a /24. How can we say
that? Well, the largest number possible slash-anything is /32. Also, the
larger the CIDR mask, the smaller the subnet. So a /32 is actually a single
solitary IP address. Why is it a /32 ? Because all 32 bits are set to 1.
e.g.
11111111 11111111 11111111 11111111

So, how do we tell how big a /24 or a /16 or a /whatever is? Well the variable
part of the address is everything after the 24th bit in a /24. It also means
as we noted above that the first 24 bits are set to 1 and the next 8 are set
to 0. So, 2^32 / 2^24 = 2^8 (that's 2 to the power of 32 divided by 2 to the
power of 24 equals 2^8 ... that's the last time I'll write that out). If
you're thinking that all that needs to be done is subtract 24 from 32 and
raise it to the power of 2, that's correct. 2^8 is 256.

Another example: a /28 would be 32 - 28 = 4. Raise 2 to the power of 4 (2^4),
which is 2 * 2 * 2 * 2 which is 16.  
2^4 is 16  
2^8 is 256

Most other operations can be divised easily if you remember those two. So, 2^5
is 2^4 multiplied by two. You can do that in your head, it's 32. 2^6 is 2^4
multiplied by two multipled by two. That's easy, 64. 2^7 is 2^8 divided by two
or 2^6 multiplied by two, which is 128. So remember those two important ones
above and you can multiply up or down to suit then! Even if you can't, just
remember 2 to the power of 4 is 2 by 2 by 2 by 2. Even that only takes a few
seconds.

As with lots of things got to do with computers, counting starts from 0, so
256 addresses actually turns into a maximum number of 255. Again, remembering
2^8 is the maximum that can fit in one octet and again is part of the reason
why 255 appears in subnet masks so much. It's basically the maximum number
that can be there.

So, again we have a /24. Now, the first IP is used to identify the network,
and we're starting counting from 0.

So, our subnet has 256 hosts, which means that for example, the IP address we
were using earlier was 89.234.64.66 in a /24. This /24 would start at
89.234.64.0 and would go up to 89.234.64.255. Now the .0 address is used to
identify the network, i.e. the network identifier would be:
89.234.64.0/24

The LAST address of the network is typically used as a broadcast address. You
can look that up somewhere else, but basically that means that the usable IP
addresses are actually now down by 2, so we've got 254 usable IP addresses.
Yeh, sorry, I kinda lied above, but it seems less complicated now right?
So, our usable IP space is from 89.234.64.1 to 89.234.64.254. ( worth bearing
in mind that typically your gateway address, if used, is either the first or
last IP address on the network also. I've always seen the first used as best
practice.). Our subnet boundary is 89.234.64.0 to 89.234.64.255. 

Ok, so that was a /24, that was easy because a /24 occurs on an octet
boundary, so it makes life really easy and in fact that's why so many people
use it (a /16 and a /8 also occur on boundaries as they represent the old
class B and A respectively) for home networks.
Let's have a look at a /26. Ok, so the first thing we do here? 32-26 raised to
the power of 2. 2^6 = 64

So now, that means that our subnet is broken up into blocks of 64 IP
addresses. Now the math gets a bit harder to do in our head (if you're not
used to dealing with powers of 2). In this case, the subnet boundaries occur
at multiples of 64 (minus 1 as we start at 0) i.e. the start of the subnet
boundaries occur at:  
( 64 * 0 ) = 0  
( 64 * 1 ) = 64  
( 64 * 2 ) = 128  
( 64 * 3 ) = 192  

The end of the subnet boundaries occur 1 before the next one, so
89.234.64.0/26 goes from 89.234.64.0 -> 89.234.64.63. Now we lose the first IP
address to the network identifier and the last one to the broadcast address
(this is the case for every network over a /31), so our usable IP addresses
are 89.234.64.1 to 89.234.64.62 (with 89.234.64.0 being the network identifier
and 89.234.64.63 being the broadcast).

Ok, so our IP address we were using doesn't actually fit into that subnet. Our
example IP was 89.234.64.66. We need to mentally sort out the boundaries in
order to find the network. In this case, the boundary it fits in is 64->127.
Now, let's show you how to find out the subnet mask:

The subnet mask is calculated by taking the multiple we used above and taking
it away from 256 on the relevant octet. Ok, so in this case with a /26 we're
ALWAYS working on the last octet (octet 4), so take the multiple we used above
(64) away from 256 to get 192. 192 is the last octet of the subnet mask, with
the rest being set to 255.
i.e.  
255.255.255.192  

If we were operating on the third octet (e.g. the equivalent of a /26 on the
third octet is a /18), then everything AFTER that octet gets set to 0.
i.e.
255.255.192.0

Now, we can cheat a little here also. We were working on the premise that
/whatever means you subtract it from 32 and work away there. Well, we can
reduce the math for ourselves here. 2^14 isn't something I can calculate in a
couple of seconds in my head (32 - 18 = 14), but we can operate on the octet
boundaries (a bit like the way we operated on the subnet boundaries above).
So, the end of the octet boundaries are 8, 16, 24 and 32. Identify the octet
the /whatever comes in and then start by using the same principles as above.

Let's take a /5. Ok, so the nearest octet boundary is 8 (remember the 1st
octet), 8-5 is 3. 2^3 = 8. Ok, so now unlike above, because we're operating on
the 1st octet, this doesn't mean that the IP addresses are being allocated in
blocks of 8. There are three octets after this remember. However, we can use
the same trick of subtracting from 256.  256 - 8 = 248. 

Everything before the current octet is set to 255 and
everything after the current octet is set to 0. This is the first octet, so
the subnet mask is 248.0.0.0

Let's take a /15 as another example. The nearest octet boundary after the
number 15 is 16, so 16-15 = 1. 2^1 = 2. So, subtract 2 from 256 to get 254 and
the subnet mask is 255.254.0.0

Let's have a look at the binary arithmetic going on here, just to be sure to
be sure. So we'll present the binary version of 255.254.0.0 and the easiest
way is to count the number of 1's. That basically tells us the / number also.  
255 is 11111111 in binary  
254 is 11111110 in binary  
0 is 0 (or 00000000) in binary  

So our subnet mask is in binary format as:  
11111111 11111110 00000000 00000000

Counting the number of 1's in the subnet mask, gives a direct result to the
CIDR. All we've done above is use a little shorthand to actually convert to
these results.

Why are subnet masks used in these convaluted fashions? Well, because an IP
address is stored in 32 bit format as well, storing a subnet mask like this
means to tell whether a computer is in a foreign network or not, is an
extremely quick operation. For anyone familiar with binary arithmetic, it
might be obvious already.

Let's take the example IP we've been using all along on a /24 network (i.e.
subnet mask of 255.255.255.0)
{% highlight c %}
IP    01011001 11101010 01000000 01000010
Mask  11111111 11111111 11111111 00000000
{% endhighlight %}

If we bitwise AND the two, we get a result. For bitwise AND, the rules are, 1
AND 1 is 1. 1 AND 0 is 0. 0 AND 1 is 0. 0 AND 0 is 0.
{% highlight c %}
01011001 11101010 01000000 01000010
11111111 11111111 11111111 00000000
-------- -------- -------- --------
01011001 11101010 01000000 00000000
{% endhighlight %}

What is this binary number? It's actually the network identifier, i.e.
89.234.64.0

Now, any IP address on this network that we bitwise AND with the subnet mask
above should output exactly the same result

The following is the result of a bitwise AND operation between 89.234.64.2 and
the subnet mask 255.255.255.0

{% highlight c %}
01011001 11101010 01000000 00000010
11111111 11111111 11111111 00000000
-------- -------- -------- --------
01011001 11101010 01000000 00000000
{% endhighlight %}

As you can see the result is exactly the same as above. However, let's take an
IP address like 88.234.64.1 (note that is 88 not 89)

{% highlight c %}
01011000 11101010 01000000 00000001
11111111 11111111 11111111 00000000
-------- -------- -------- --------
01011000 11101010 01000000 00000000
{% endhighlight %}

Again this is different and you need to look at the first octet to tell the
difference.

Bitwise operations like AND can be performed extremely quickly so when a
computer receives information from a new IP address it has never seen before,
it can tell extremely quickly whether that machine should be available on the
local network or not.

So, when you are choosing a network layout for your own home use, you can
probably use a /24 or /16 (i.e. subnet masks of 255.255.255.0 and 255.255.0.0)
no problem, but remember to choose carefully when segmenting a larger network.
Be especially mindful of all of these things when you start using publically
addressable IPs.

NB please make sure all private networks use the RFC 1918 properly designated
private network subnets
