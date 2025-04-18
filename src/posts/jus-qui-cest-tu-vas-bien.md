---
title: Jus qui c'est, tu vas bien
date: '2025-04-18'
tags: []
description: 
permalink: posts/{{ title | slug }}/index.html
---

I was cleaning up my disk partition to free up some of the space all those auto-generated files, created by makefiles and other confidential stuff, took up. Then I open up a new terminal tab and suddenly I see this:

```bash
-bash: home/laude/src/utils/oracle.utils.sh: No such file or directory
```

Fuck. This is it.

I have to actually write down the full commands now. At this point, I gave up on the bug I was working on and was about to go 

While trying to make a mental note of each of the aliases and functions I wrote, I realized one thing. 

The terminal I used while cleaning the disk was still open.

## What does that mean?
It means that my scripts are still loaded there. I just needed to find a way to get to it. A quick little google search pointed me to the declare method.

You want your functions back? Here you go:

`declare -f`

You erased your variables? Use this:

`declare -x`

You want to recover your aliases? You will need this:

`alias`

## Lesson
Always back up your scripts.