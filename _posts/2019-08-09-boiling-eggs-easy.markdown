---
layout: post
title: "Estimating the Amount of Time Needed Boiling Eggs, the Easier Way"
date: 2019-08-09 08:02:00 -0800
---

After several days rigorous driving around the Island looking for housing,
my car had an check engine indicator came on. I had my car checked today in the
morning. I was expecting an hour check, but the service technician called me saying that the part he needed is not gonna be
ready until the end the day. So I ended up in a mall having fun computing the amount of time it takes to
properly cook an egg.

The way I learnt how to boil eggs is as follows:
1. place the eggs in a pot of cold water on a range.
2. turn up the the heat to maximum.
3. as soon as the water boils, start the timer.
4. as soon as the timer reaches 5 minutes, transfer the eggs into cold water.

I was pretty happy with this method, until it failed on me a couple of days ago. The major problem with this recipe is, the amount of time it takes to
getting the water to boil varies a lot from stove to stove, the eggs are already
cooking even before the water is boiling! Imagine having
a really powerful stove that instantly boils the water, it will have a shorter
cook time compared to a regular range, and will produce undercooked eggs than expected. On the other hand,
we can have a really weak range that can only heat water up to 70C, but we can still
end up with fully cooked eggs. In addition, there are more minor issues such as initial water temperature and pot type.

An alternative version of this recipe involves turning off the heat after
the water boils. As a result, water temperature becomes unpredictable depending on room temperature, the type of pot, and type of range, bringing more variance
to the quality of cooked eggs.

The best recipe I can find online that minimizes the different
things that could go wrong involves placing the eggs into the
boiling water, and start the timer after. I am most satified with this recipe, but now the issue with this recipie is that,
it failed to take into account the size of each egg.

I tried to search for the exact formula online, all I found was some research paper with
partial differential equations that I used to understand :( So I simplified my
calculations to high school physics :)
This forumla, $$Q = Mc\Delta T$$ means $$Energy\ Transfer = Mass\ of\ Object \times
Constant \times Change\ In\ Temperature$$, this formula is sort of deceiving
because I learnt later in life the constant is not a constant. 

Since everyone knows how to cook egg whites properly, I'm using the constant(Specific Heat) of the egg yolk $$3120 J\ kg^{-1} C^{-1}$$. So my current model of an egg is a blob of egg yolk of unknown shape,
the goal is to calculate the amount of energy to fully coagulate the egg yolk, which
means bringing up the egg temperature to 70 Degree Celsius. Also I assumed that
it only takes a few seconds to bring the egg shell to reach thermal equilibrium with
the boiling water. I'm also using
a initial temperature of 4C, which means the egg is right out of the fridge.
I'm using 50g as the mass of the egg for demostration purposes, and later we
can use the mass as a variable to compute the time needed to cook the egg.

$$ Q = 0.050\frac{kg}{egg} \times 3120 \frac{J}{kg C} \times (70C - 4C) \approx 10300 \frac{J}{egg}$$

Now the hard part is, given energy needed in total, how do we get the amount of time needed to
cook the egg? If we know the rate of energy needed per unit time,
then time = enegy / rate! Unfortunately, this only works if the rate is
constant. Initially, the egg is super cold, the energy
transfer is super fast because of the huge temperature difference between the water and the egg. As the egg gets warmer, the heat transfer slows down.
This summarizes Fourier's law of thermal conductivity:
$$q = -k \nabla T$$, which means bigger temperature difference leads to faster
heat transfer rates. (q = energy transfer rate per unit area, k = constant, $$ \nabla T $$ =
slope of temperature vs position at a particular position)

Another problem remains to be solved, law of thermal conductivity is hard to
solve if we assume this blob of egg yolk is a sphere. A more accurate
representation would an ellipsoid, which makes things even harder. What we need to approximate
is the amount of time for the egg center to reach 70C, which is on average
around 22mm away from the shell. To simplify the calculations, I have flattened the egg into a disk
with 22mm thickness. The circular section of the disk has an area equilvalent to a 22mm radius sphere.

So what is a reasonable estimation of average $$\nabla T$$? One of them is $$ (100C -
4C) / 22mm$$, this is a global average after a few minutes after we placed the egg into the
boiling water. What happens before that? Well, it's a bit complicated, I might
write a post computing a harder version of this estimation if I feel like it in the future.
Another reasonable estimation of $$\nabla T$$? The other is $$ (100C - 70C) /
22mm $$, where the center of the egg reaches 70C, this represents the slowest heat transfer rate we can achieve just before
the egg is ready. If you search online, the temperature profile is a lot more
complicated. Here, the simplification we made is that the temperature drops linearly towards the center of the egg.

$$ A = 4 \pi R^2 = 4 \pi \times 0.022m^2 = 0.00608 m^2$$

$$ q_1 = \frac{\dot{Q_1}}{A} = 0.40 \frac{J}{s\ m\ C}\times \frac{100C - 4C}{0.022m} $$

$$ \dot{Q_1} = 0.40 \frac{J}{s\ m\ C}\times \frac{100C - 4C}{0.022m} \times A = 10.6 \frac{J}{s}$$

$$ t_1 = \frac{Q}{\dot{Q_1}} = 10300 / 10.6 = 972\ s = 16\ min $$

$$ q_2 = \frac{\dot{Q_2}}{A} = 0.40 \frac{J}{s\ m\ C} \times \frac{100C - 70C}{0.022m} $$

$$ \dot{Q_2} = 0.40 \frac{J}{s\ m\ C}\times \frac{100C - 70C}{0.022m} \times A = 3.32 \frac{J}{s}$$

$$ t_2 = \frac{Q}{\dot{Q_2}} = 10300 / 3.32 = 3102\ s = 52\ min $$

As you can see, $$t_1$$ seems like a reasonable estimation,
while $$ t_2 $$ is too much off. This is because I skipped the hard part of solving the heat differential equation and assumed that the egg is a flat disk.

Let's use $$ t_1 $$ for now for a fully cooked egg. let's see how we have
arrived at the conclusion:

$$ t = \frac{Q}{\dot{Q}} = \frac{Mc\Delta T} {k \nabla T \times 4  \pi R^2} $$

Here the known variables are $$ c = 3120 \frac{J}{kg C} $$, $$ k = 0.40 \frac{J}{s\ m\ C}$$, $$ \Delta T = 66 C$$, $$ \nabla T = \frac{96 C}{R}$$

$$ t = \frac{3120 \times 66 \times M} {0.40 \times 94 / R \times 4  \pi R^2} $$

$$ t = \frac{3120 \times 66 \times M} {0.40 \times 94  \times 4  \pi R} $$

$$ t = \frac{436M}{R} $$

Where m is the mass of the egg in kg, and r is the average radius of the egg in meters, and t is in seconds.
Now if the egg is a sphere, radius of the egg is related to the mass of the
egg.

$$ M = \rho V $$

$$ M = 1000 \frac{kg}{m^3} \frac{4}{3} \pi R^3$$

$$ R = \left(\frac{3 M} {4000\pi}\right)^{1/3} $$

So substitute the equation above into $$ t = \frac{436M}{R} $$

$$ t = \frac{436M}{\left(\frac{3 M} {4000\pi}\right)^{1/3}} = 7028 M^{2/3}$$

So for a fully cooked egg, we have arrived at:

$$ t = 7028 M^{\frac{2}{3}} $$

Where M is the mass of the egg in kg, and t is in seconds

Let's try some values according to wikipedia:
- Small: 42g -> 0.042kg -> 849s = 14min
- Medium: 49g -> 0.049kg -> 941s = 15.6min
- Large: 56g -> 0.056kg -> 1028s = 17min
- Extra Large: 63g -> 0.063kg -> 1113s = 18.5min
- Jumbo: 70g -> 0.070kg -> 1193 = 20min

Are we done? The answer is no. Because a lot of people prefers the egg yolk to be
runny. So let's compute the amount of time it takes for that to fully cook the
egg white portion.
So 33% of the weight of the egg is yolk, it's corresponding radius is

$$\frac{V}{3} = \frac{4}{3} \pi r^3 $$

$$ V = \frac{4}{3} \pi R^3 $$

$$ r = \left(\frac{V}{4\pi}\right)^{1/3}  $$

$$ R = \left(\frac{3V}{4\pi}\right)^{1/3}  $$

$$ \frac{r}{R} = 0.69 $$

$$ d = R - r = 0.31R $$

Where d is the distance from the shell where temperature has reached 70C.

$$ t = \frac{Q}{\dot{Q}} = \frac{Mc\Delta T} {k \nabla T \times 4  \pi r^2} $$

$$ t = \frac{3120 \times 66 \times M} {0.40 \times 94 / d \times 4  \pi R^2} $$

$$ t = 0.31 \times 7028 M^{\frac{2}{3}}$$

$$ t = 2179 M^{\frac{2}{3}}$$

Again, running those numbers
- Small: 42g -> 0.042kg -> 263s = 4.4min
- Medium: 49g -> 0.049kg -> 292s = 4.9min
- Large: 56g -> 0.056kg -> 319s = 5.3min
- Extra Large: 63g -> 0.063kg -> 345 = 5.7min
- Jumbo: 70g -> 0.070kg -> 1193 = 6.2min

What if you want something in between? One thing we can do is boil a bunch of
eggs. Starting from the lower bound minus a minute. We take out an egg every
minute and label the time until the upper bound plus a minute. Sort the
eggs in increasing time label. Crack open the middle egg, if overcooked, pick the egg
between the middle egg in the left region you narrowed down to, else pick the middle egg in the right region you narrowed down.
Repeat this until you have narrowed down your pick to one or two eggs.
You might end up picking 2 consecutive eggs where one is overcooked and the
other is undercooked. In this case, the ideal time is approximately the averge
of the two eggs.

Happy cooking to those who accidentally stumpled upon this post! I might end up trying to solve some differential equations if I
have the time to figure out a more accurate approximation of egg cooking times.
