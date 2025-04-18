---
title: Rust and C
date: '2023-05-03'
tags: []
description: 
permalink: posts/{{ title | slug }}/index.html
---

I'm seeing too much comparison on the internet about why C is unsafe and Rust is safe. True. But they are NOT even the same class of language.

C is minimal. The compiler is easy to write. Even nicknamed **portable assembler** for how low-level it is. Rust on the other hand, is a big, complicated language with many features. And a massive standard library. It's not even close. Here's a short list of features Rust have but C does not.

- Generics
- Traits
- Pattern matching
- Containers
- Reference counting
- Object oriented programming
- First class functions
- Multithreading primitives
- Slice
- Resizible string

C++ is a much fairer comparison. However, it is not C-with-classes, not in the past decade. It supports most Rust does support. With the noticiable exception of the borrow checker, context free grammar and a built-in build system. Also, no one is using raw pointers in C++ anymore.

No one writes this in 2023:

```c
Label* label = new Label();
label->setText("Hello World");
```

Instead we do this:

```c
auto label = std::make_unique<Label>();
label->setText("Hello World");
Make valid arguments next time.
```