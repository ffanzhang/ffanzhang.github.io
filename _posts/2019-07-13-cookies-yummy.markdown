---
layout: post
title: "Cookies - Yummy"
---

Finally graduated and had been in the job hunting club for a while. What's interesting about cookies is I got asked about them at least twice, and I used to work in a "cookie factory".

My first attempt at answering this question was short
and simple, "a cookie is a piece of data that the server wants the browser
to keep track of." The interviewer looked discontent, and by the exponential increase in intensity of voice the interviewer,
I can feel the room air getting colder, "if the browser keeps
track of the cookies, how does the server know the what the client is doing?" "Well,
you see, in any of the following requests, the browser attaches the cookies with the
request." Then follows a long awkward silence... What I attempted next to break
this silence was, "in any modern framework, the process of setting cookies and obtaining cookies is abstracted away in
library calls and I might not have the perfect picture of what's going on." Then another panel member changed the topic, and the interview
continued. For story telling purposes, this is roughly what happened with a bit
of exaggeration.

A few days ago, I got asked the same question. Having had a similar experience,
my attempt was, "a cookie is a piece of data that the server wants
the browser to keep track of, then the browser attaches that piece of data for
every subsequent request." "It's not how it works!", one of the interviewers
protested. In a flash of insight, I thought, "hmm, maybe using library calls as an excuse
might not be a good idea because it shows I'm shirking responsibility as a
developer to dig things a bit more, let me try it another way." So I went,
"this is what I know so far, if I needed the details of cookies while coding in
production, I understand it's part of the HTTPS protocol and would resort to
RFC documents and I know where to look (note the mix up between HTTPS and HTTP protocol :))."
Note this is a slightly better response, but the interviewer still thinks I'm an
idiot. As you can see, I still need a good, thorough answer in the first place to dodge the
confrontational tactics needed once the interviewers deemed it unsatisfactory.

So what went wrong? In an ideal scenario, the server is supposed to
keep track of the resources not what goes on the client side, whereas the client
should keep track of state (REST in one sentence). Cookies are designed to keep track of client side state.
Traditionally, on the contrary, the server needs also keep
track of cookies in the database in the form of sessions, a database table
literally called sessions would be dedicated to keep track of cookies and maintain some client information. Each cookie would also have
a reference to the database entry in the sessions table. But the existence of
sessions are due to technology limitations and not supposed to happen! Using
sessions goes against REST principles!
But, you may ask, "how do you keep track of who is logged in?" Well, the answer is use tokens! This is not a technical blog
about how cookies work. This is a post about random complaints :) Maybe
a lot of the interviewers are still used to legacy code base where sessions are
bundled with cookies, so they deemed my answer incomplete.

Having learnt my lesson. So my next attempt would be, "a cookie is a piece of
data that the server wants the browser to keep track of, the browser would try
to send what it has in its cookie jar along with every request. In a
session-less server environment, this brief description suffices to describe the
basic functionality of a cookie, I would be very happy to elaborate any details
about sessions or types of cookies." 

What did I get out from those two interviews? A slightly better
understanding of cookies, and a rare self entertaining post :)
