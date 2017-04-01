---
layout: post
title: "Getting &lt;bits/stdc++.h&gt; header on a Mac"
date: 2017-01-07 07:32:25 -0800
---

If you've stumbled on this post and just looking for a solution, you can skip all the mumbo jumbo and just try the snippet.

A bit of background story on how I ended up getting a Mac. I owned an acer
laptop for about 5 years. Because I carried it around too much and must have
caused some wires and connections to deteriorate, the screen started to appear green when the lid is opened.
My usual solution was, rip the plastic cover in front of the screen out,
wiggle the bus going into the back of the screen, and the green screen of death will
hopefully disappear. One day last September, I was fed up with this trick. 
Raged, I had decided to try to get a Mac. 
You may ask why the heck was the acer laptop working last September?
Moores law indicates if it's 5 years old, it must have been 4 times slower.
There are a couple things you can do to squeeze the performance out of a laptop.

- on a black friday or boxing day, pick memory sticks and ssd drives that update
  your hardware, but do read specifications and make sure the stuff you bought works.
- install a bare minimum linux distro.

During Christmas break, I finally had the time to fully take apart this acer
laptop and ended up using pliers to squeeze the metal connector to fix the loose
grip, and yes a variant of the duct tape is used as well, except this time it is double sided
tape that will hopefully keep the connector in place.

I now use this acer laptop as a stationary computer at home and writing this
post with it. I can even claim that after using a Mac for 4 months, this acer laptop
bought in 2011 still feels way faster and responsive than a Mac bought in 2016. I also occasionally run a hp laptop dated back in 2007, still works pretty awesome.

Back to school season, it's time to do some practice coding on this luxury toy!
I naively thought since I already had g++ command in terminal, it must have
been the case it includes all the default headers. But I was wrong, first compile
with this header gave me tons of errors! 

After a bit of digging, the rough explanation is that
g++ on a Mac is actually llvm/clang, which is really confusing because I do not
understand the rationale for a program pretend to be some other program. (maybe
same reason as symbolic linking?)

I found some stackoverflow posts, they are mostly along the lines of, "oh, copy this
header file from a random github gist." But doing so is not really a
sustainable solution, things can horribly break. Another stackoverflow solution involves installing 
gcc. But my major concern was whether would the g++ command would override the
existing g++ and potentially break the existing toolchain. The following is what I ended
up doing after referencing a couple of stackoverflow posts. Just a heads up, this solution
might not work in a year or two from now. If it stops working, try "brew install gcc[1-9]+" where "[1-9]+" is the version.

- Fire up the terminal.
- And if you have homebrew, type

```
brew install gcc6
```
- The process took about an hour, just minimize the window and do something else.

### Compiling with C++11
```
g++-6 -std=c++11 sourcefile.cpp
```
