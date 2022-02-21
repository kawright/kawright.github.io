---
layout: post
title: New Blog, New Testing Framework
description: First blog post; announcement about new project, wrench.
tags: news wrench
---
New Blog, New Testing Framework
===============================

Hey everyone, and welcome to the first of what I hope are to be many posts on
my new personal blog.

Initially, when I purchased the domain *kriswrightdev.com*, I figured I would
use it for a portfolio site where I could put my resume, a list of my socials,
and a link to my github account. While I still think that it is a good idea to
do those things, I've realized that it could also be a place where I can talk
about all of the things I am working on and learning about. I think that having
a platform to talk about my struggles and triumphs will be theraputic in some
kind of way, but I also hope that perhaps it will also benefit others as well.

Other than that, I really don't have too much to say specifically about this new
blog format for my personal website, so let's get to some news about the latest
project I have been working on:

wrench: A Simple Unit Testing Framework for C
----------------------------------------------

Not too long ago, I was in the very early stages of another C project (which I
will be posting about soon), and I was trying to figure out what framework
I would use for unit testing. After much research, I came to the following
conclusions:

1.  Most of what is available out there is way too bloated for what I needed.
2.  I surely cannot be the only developer who feels this way.
3.  It would be fun to take a small diversion from my current project to work on rolling my own unit testing framework.

Thus, my latest project *wrench* was born. *wrench* is an easy-to-use unit
testing framework which has a simple API and supports TAP (Test Anything 
Protocol) output. It gives you everything you need to test your code, without
forcing you to learn a whole bunch of stuff you mostly don't need.

Unfortunately, as of the time when this post goes up, I don't have a GitHub repo 
up for this project, but as soon as I finish up the API documentation, which 
should be in another day or two, I will spin up a new repo and make the first
commit and release. The initial release will be marked as a pre-release version,
as I am currently working on writing unit tests for the entire library
(normally I would have the unit tests written before the implementation, but
since I plan to use *wrench* to test itself, I decided to flesh out the API
first). Once all of my tests are written and passed, I will release a *1.0.0*
tag.

Once I have version *1.0.0* released, I will go ahead and post some tutorials
on installing and using *wrench*.

More updates on this project should be coming up very soon, so keep your eyes
peeled!