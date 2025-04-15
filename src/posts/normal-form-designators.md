---
title: Normal Form Designators
date: '2023-04-12'
tags: [programming]
description: 
permalink: posts/{{ title | slug }}/index.html
---

*Brian Cantwell Smith* is one of the many people who are far smarter than I am, their [MIT thesis Procedural Reflection in Programming Languages](https://publications.csail.mit.edu/lcs/pubs/pdf/MIT-LCS-TR-272.pdf), which is something else, is how I first became aware of them.

As usual, I learned the concepts presented in this post from the aforementioned paper. As such, I'm not sure if I should give credit to Brian for these concepts, but I will since I'm not sure to whom to give credit otherwise.

Acquiring knowledge is a collaborative endeavor, and I extend my gratitude to all those who contributed.

## DISCLAIMER
I may be misusing terminology here. If so, please substitute made up words that accurately convey the meaning I've given here for any instances of phrases that appear in Brian's book.

*pripl is about the development of LISP-3, which is a scheme endowed with reflective capabilities.

The extent of this is beyond my brain capacity to cover in one blog post, but rest assured that I will do so in the future.

On the other hand, Normal Form designators were a frequently suggested idea, and I thought they were a neat idea.

At its core, an NFD is the semantic grouping of the result of evaluating a statement, regardless of how far it has been evaluated.

As such, the following scheme statements all relate to the same Normal Form Designator:

```
(if true
    (* 23 (+ 4 2))
    0)

(* 23 (+ 4 2))
(* 23 6)
69
```

Note that the following is included in the same **NFD** set as the following, so there's no need to include every step of a single evaluation:

`(- 70 1)`

I liked this idea for several reasons, but the main reason I'm writing this post is to use it as an opportunity to vent my frustrations about software.

In my opinion, all of the so-called *progress*, particularly with regard to the modern web, falls short of actually improving the NFD groups that the technology claims to improve.

We still use the internet to do a few basic things:
- Send messages to each other
- Distribute files
- View media

And instead of coming up with effective, context-focused methods to accomplish this, we just keep creating ever-larger expressions that amount to the same thing, calling it "progress" because it's harder for the typical person to understand.

We continue to assert that *"operating system improvement"* consists of repeatedly creating an additional abstraction layer on top of the same meaningless signifiers of what users should expect from an operating system, or reinventing them.

Rather than building something different, we just keep building.

## Fin
I'm simply sick of seeing the newest technology to be some incredibly bloated piece of software that needs a corporation in the middle and ever-more-powerful computers to implement features that have been around for ages.

I'm sick of seeing people trained in what the same tool industry decided is this month's fad and never trying anything truly unique.

I wish to find new Normal Form Designators and make their distinctiveness a positive attribute in and of itself.

`C-c C-x`

