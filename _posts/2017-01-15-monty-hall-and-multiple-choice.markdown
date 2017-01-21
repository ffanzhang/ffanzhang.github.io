---
layout: post
title: "Monty Hall's Problem and its application to guessing Multiple Choice
Questions"
date: 2017-01-15 22:55:25 -0800
---
At some point in your life, you probably have heard about monty hall's
problem. Here's a [link](https://en.wikipedia.org/wiki/Monty_Hall_problem) to
the wiki page about it. Let me summarize the problem. You are in a game show
with 3 doors. Behind one door is an awesome car, and the other two doors have
goats behind. Now you pick a door, and the host reveals another door with a goat. The
question now becomes, should you switch the door, or stick with your original
choice? What is mind boggling about it is the fact that switching will allow
you to have $$\frac{2}{3}$$ probability to win the grand prize. This is not
another post about explaining why switching will allow you to win, there are
plenty of excellent resources on the net and there is no point of reinventing
the wheel. This is a post about given this result, can we use this fact to do something useful?

Suppose you are writing a multiple choice exam that is made of 3 option
multiple choice questions. If there is a question that you don't know how to
answer, the probability of getting it right is $$\frac{1}{3}$$. So pretend to
be a contestant and circle a random choice first. But don't give
up yet. What if, at this point, you pretend to be the host. So that out of the
other two options, you are able to pick the other goat. After pretending to be
host, by pretending to be the contentant and switch the door, you can get the answer right 
$$\frac{2}{3}$$ of the time! Realistically you won't be able to boost your
probability up to $$\frac{2}{3}$$ because I'm assuming that your ability as a
host to eliminate a bad answer given 2 answers is 100%. However, any attempt to
eliminate an answer will improve your odds getting a question right! 
So my proposed strategy for guessing a 3 choice multiple choice question is as
follows:

1. never choose a.
2. if not b, choose c, else choose b.

An even better one, if you have a fancy calculator to generate random numbers:

1. randomly generate a number out of 1 to 3, that number is not the answer.
2. eliminate one, and choose the other. 

You may ask, well this is not practical, because most multiple choice questions
have 4 or 5 answers. Well now that you know how 3 answered multiple choice question
works, it is time for you, the reader to figure out how to improve the odds of
answering those questions correctly :)
