---
layout: post
title: "Estimating the Amount of Time Needed Boiling Eggs, the Medium Way"
date: 2019-08-10 12:02:00 -0800
---

As soon as I finished my post about the easier way of estimating the amount of
time it takes to cook eggs, I remeber that a long long time ago, I took a math course dealing with
heat equations in 1D.

$$ \frac{\partial u(x, t)}{\partial t} = \alpha \frac{\partial^2 u(x, t)}{\partial x^2} $$

Where u(x, t) is a temperature as a function of position x and time t, $$
\alpha $$ is a constant. Here x = 0 means the temperature at egg shell and x =
L means we are right at the center of the egg.

Looking through the past lecture slides, if I were to also flatten the egg to a
disk for this post, but use some differential equations, I think I can get a better approximation. So my assumptions are still:

- The egg is a cylindrical disk/rod consists of egg yolk. For analytical
    purposes, we stand up the egg disk vertically so that the round faces are
    facing side ways, and we are staring at the body of the disk/rod.
- The height/width/length of the disk is the egg's equivalent radius if we
    morph the egg into a sphere.
- left side is 100C, and the right side is a perfect insulator with an initial
    temperature of 4C.

The boundary conditions are:

On the left side we have water at 100:

$$ u(0, t) = 100 $$

On the right side, the derivative is 0, because heat is trapped in the center (before flatten) and the flow rate is almost zero,
note I used L instead of R from last post, this is to emphasize we are talking about the
thickness of the disk.

$$ \frac{\partial u(L, t)}{\partial x} = 0 $$

$$ u(L, 0) = 4 $$

As time goes to infinity, all of the egg will reach thermal equilibrium with
the boiling water:

$$ u(x, \infty) = 100 $$

Also, a trick to mixed boundary condition is to rewrite the equation into two
pieces:

$$ u(x, t) = u(x, \infty) + v(x, t) $$

New boundary conditions for $$ v(x, t) $$:

$$ v(0, t) = 0 $$

$$ \frac{\partial v(L, t)}{\partial x} = 0 $$

$$ v(L, 0) = -96 $$

Now the standard technique of separation of variables letting $$ v(x, t) = X(x)T(t) $$

$$ X(x)T'(t) = \alpha X''(x)T(t) $$

$$ \frac{T'(t)}{\alpha T(t)} = \frac{X''(x)}{X(x)} = -\lambda^2 $$

$$ T(t) = C \exp(-\lambda^2 \alpha t)$$

$$ X(x) = A \cos(\lambda x) + B \sin(\lambda x)$$

$$ X'(x) = -A\lambda \sin(\lambda x) + B\lambda \cos(\lambda x)$$

$$ v(0, t) = 0 \Rightarrow A = 0$$

$$ \frac{\partial v(L, t)}{\partial x} = 0 \Rightarrow  B\lambda \cos(\lambda L) = 0$$

$$ \lambda_k = \frac{(2k - 1) \pi}{2L}, k = 1, 2, 3, ...$$

A general solution takes into account of sum of all possible sine terms with
different ks and different coefficients, to simplify the answer, we pick k = 1 :)

$$ v(L, 0) = -96 \Rightarrow C = -96, B = 1$$

$$ u(L, t) = 100 - 96 \exp\left(-\frac{\pi^2}{4L^2} \alpha t\right) \sin\left(\frac{\pi}{2}\right) = 70 $$

$$ \frac{30}{96} =  \exp\left(-\frac{\pi^2}{4L^2} \alpha t\right) $$

$$ t = \frac{4L^2}{\pi^2 \alpha} \ln\frac{96}{30} $$

$$ L = R = \left(\frac{3M}{4000\pi}\right)^{1/3} $$

$$ t = \frac{4\left(\frac{3M}{4000\pi}\right)^{2/3}}{\pi^2 \alpha} \ln\frac{96}{30} $$

Using $$ \alpha = \frac{k}{\rho c} $$, $$ c = 3120 \frac{J}{kg C} $$, $$ \rho =
1000 \frac{kg}{m^3} $$, $$ k = 0.4 \frac{J}{s\ m\ C}$$

$$ t = 14150 M^{2/3} $$

Doing some computations, a 50g egg gets us a whopping 32min!!!

So how do we fix this mistake? If we think carefully, the geometry should instead look like a triangle pointed to the right, so a cone is more accurate, not a cylinder/disk!

2D wise, this means we only need to realistically heat up half the material. 3D wise, we only
need to heat up a third of the material so that it is more like a cone. So roughly and inaccurately:

$$ \frac{14150}{3} M^{2/3} \lt t \lt \frac{14150}{2} M^{2/3} $$

$$ 4716 M^{2/3} \lt t \lt 7075 M^{2/3} $$

Note that $$ 7075 M^{2/3} $$ is pretty close to the result from last post for a
hard boiled egg. Also note that $$ t = O(M^{2/3}) $$? This means all we need to
do is to do a couple of experiments, plot t vs M, then figure out the constant by
fitting a line of $$ t = cM^{2/3} $$ through it.

So we are not done yet, time to compute the value for a soft boiled egg.
Here it makes more sense to unwrap the egg white part and transform it into a disk, so
we can reuse our solution to the differential equation, note we are using little $$ l $$ here, $$ l = 0.31L $$ as we have computed in last post.
I got scared of my large unexpected result cooking the hard boiled egg, I
started using variables related with egg white. Another difference is that egg white completely
coagulates at 65 degrees, not 70. Although the original solution is off, it should be
more accurate as the distance we are evaluating is close to left.

$$ u(l, t) = 100 - 96 \exp\left(-\frac{\pi^2}{4L^2} \alpha t\right) \sin\left(\frac{\pi l}{2L}\right) = 65 $$

$$ t = \frac{4L^2}{\pi^2 \alpha} \ln\frac{96\sin\left(\frac{0.31\pi}{2}\right)}{35} $$

$$ t = \frac{4L^2}{\pi^2 \alpha} \ln\frac{96\sin\left(\frac{0.31\pi}{2}\right)}{35} $$

$$ t = \frac{4\left(\frac{3M}{4 \times 1043\pi}\right)^{2/3}}{\pi^2 \alpha} \ln\frac{96\sin(\frac{0.31\pi}{2})}{35} $$

Here I realized the importance of using the right numbers, here we are using variables related to
egg white, so using $$ \alpha = \frac{k}{\rho c} $$, $$ c = 3800 \frac{J}{kg C} $$, $$ \rho = 
1043 \frac{kg}{m^3} $$, $$ k = 0.5 \frac{J}{s\ m\ C}$$

This gives us:

$$ t = 3000 M^{2/3} $$

So that is a good formula of a soft boiled egg?
$$ t = 3000 M^{2/3} $$
- Small: 42g -> 0.042kg -> 362s = 6min 
- Medium: 49g -> 0.049kg -> 402s = 6.7min 
- Large: 56g -> 0.056kg -> 439s = 7.3min 
- Extra Large: 63g -> 0.063kg -> 475s = 7.9min 
- Jumbo: 70g -> 0.070kg -> 510s = 8.4min 

So that is a good formula of a hard boiled egg?
$$ t = 7000 M^{2/3} $$
- Small: 42g -> 0.042kg -> 846s  = 14.1min
- Medium: 49g -> 0.049kg -> 937s = 15.6min
- Large: 56g -> 0.056kg -> 1024s = 17.1min
- Extra Large: 63g -> 0.063kg -> 1108s = 18.5min
- Jumbo: 70g -> 0.070kg -> 1189s = 19.8min 

You may ask, all these approximations are so inaccurate, what's the point?
In all of those approximations, we have arrived at a simple formula, where
t is proportional to $$ M^{2/3} $$.
A practical use of this $$ t = c M^{2/3} $$ is, supposed you found the
perfect time for a medium sized egg, but now you wanted to cook a jumbo egg. What
would be the expected time to cook it?
Suppose $$ t = 10min = 600s, M = 0.049 \Rightarrow c = 4481 $$,
then your new time would be $$ 4481 (0.070)^{2/3} = 761s = 12.5min$$

I will probably figure out a more accurate approximation in a follow up post.
But I think 3000 and 7000 are easy numbers to remember, now it's time to test
my numbers.
