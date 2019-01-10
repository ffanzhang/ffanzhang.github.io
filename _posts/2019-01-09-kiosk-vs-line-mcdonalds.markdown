---
layout: post
title: "Line vs. Kiosk: optimize the time for that burger to get into your stomach"
date: 2019-01-09 22:34:17 -0800
---
Mcdonalds has been equipped with self serve kiosks for a while now.
As hungry student I want my stomach to be filled as soon a possible.

Let's estimate how much time it takes for a person to order in line.

- "May I get a big mac meal with a medium coke?"
- "For here or to go?"
- "To go."
- "How would you like to pay?"
- "Credit card."
- "$x.xx please."
- "Beep"
- "Here is your receipt, number xxx"
- "Thanks."

Here is around 40 words. This roughly translates to 40 seconds.

Now comes the kiosk.

- touch to start
- select take away
- select burgers
- select big mac
- select medium meal
- select coke
- select add to order
- select done
- select proceed to checkout
- pay here
- beep
- take receipt

What is the theoretical fastest time we can order from a kiosk? We can
safely assume that there is at least 1 second of animation between each step.
So if we have memorized the location of each button, and able to move our finger
right in front the button just in time when the transition animation finishes, we can finish that order in 12 seconds 
if we use our non-dominant hand to reach our wallet while our dominant hand is busy performing the order.
I don't think anyone would spend the time to memorize the location of every
button, so each person has around 0.2s of reaction time to locate the next
button and another second to move to the next button. So for a seasoned veteran
who orders a big mac all the time, it will take around 2.2 seconds per step for
a total of 27 seconds. Multiplying it by a safety factor of 1.5, we get around 40s.
Why the fudge factor? Because not everyone is super fast at ordering. Also keep
in mind we are computing the average time people in front of you are taking. 

Now we can appreciate the elegance of the kiosk system. As cumbersome as it might seem, it is probably designed to
to approximately match cashier performance. But without taking actual data, it is
pretty safe to assume a kiosk and a cashier are probably same. I have a bias
towards kiosks being slower. Reason being cashiers spent more time and practice
on taking orders efficiently and they have a more efficient software interface.
The reason I pointed out this is probabably a bias is that I have failed to account for a cashier can also hold up a line by being away from desk to complete other tasks,
while a kiosk cannot hold up a line.

Although there is an efficient market hypothesis that probably implies trades are
carried out in an optimized manner. Judging by the trade of a mcdonalds meal, we can tell not everyone is making rational decisions
when lining up. Sometimes we see huge lines at the cashiers, but
each kiosk has only 1 or 2 person. Other times we also see huge lines at the
kiosks, but only a few people at the cashier. If the lines sizes are
self regularizing, the ratio between the sizes of cashier lines and kiosks lines would have been more
stable. 

So how to fill our stomach fast? Quickest rule of thumb is to go to the shorter line.
A more cumbersome rule is to statistially compute the average time an average
person spend on cashier vs kiosk, and go to the line that will get your order
the fastest. Yes I know bummer :) Chances are, we are probably not gonna die if we lose a
few minutes to eating, water is probably more critical when we are in this situation.
