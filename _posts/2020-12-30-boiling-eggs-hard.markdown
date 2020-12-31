---
layout: post
title: "Estimating the Amount of Time Needed Boiling Eggs, the Hard Way"
date: 2020-12-30 12:42:00 -0800
---

Last time, we modeled the egg as a rod, then irresponsibly reduced it to a cone
by dividing by 3. Now finally getting to the realm of a
closer estimation: a sphere.
As it turns out, the differential equation for heat equation in spherical coordinates is a fraction
harder than the rod case, so I spent some time trying to figure out how it works. Only if we can naively bring out the
r squared, the formulas look the same.

$$ \frac{\partial u(r, t)}{\partial t} = \frac{\alpha}{r^2} \frac{\partial}{\partial r} \left(r^2  \frac{\partial u(r, t)}{\partial r}\right)$$

As a reminder, u(r, t) is temperature as a function of radius r and time t, $$
\alpha $$ is a constant. r = 0 means the center of the egg and r = R is
located at the shell of the egg.

The boundary conditions are:

The center of the egg is as cold as the fridge: $$ u(0, 0) = 4 $$

No heat flow at the center of the egg: $$ \frac{\partial u(0, t)}{\partial r} = 0 $$

The shell of the egg is always boiling: $$ u(R, t) = 100 $$

Eventually, the egg reaches thermal equilibrium with the water: $$ u(r, \infty) = 100 $$

Let's split $$ u(r, t) $$ into $$u(r, t) = \Gamma(r) T(t)$$

I was gonna use $$ R $$ instead of $$ \Gamma $$, then I realized I've already
used $$ R $$ to denote the radius of the egg.

Fast forwarding the computations, a similar pattern to the rod case emerges 

$$ \frac{T'(t)}{\alpha T(t)} = \frac{X''(r)}{X(r)} = -\lambda^2 $$

$$ X(r) = r\Gamma(r) $$

$$ T(t) = C \exp(-\lambda^2 \alpha t)$$

After some rigorous internet research, if we skip all the rest of the smaller
terms, a generic functional form that works most of the time is a sinc function

$$ \Gamma(r) = A sinc(\lambda r) $$

$$ \lambda_k = \frac{k \pi}{R}, k = 1, 2, 3, ...$$, picking k = 1

As always, applying this technique of rewriting the boundary conditions

$$ u(r, t) = u(r, \infty) + v(r, t) $$

New boundary conditions:

$$ v(R, t) = 0 $$

$$ \frac{\partial v(0, t)}{\partial r} = 0 $$

$$ v(0, 0) = -96 $$

So conveniently, $$ A = -96 $$

$$ u(0, t) = 100 - 96 sinc\left(\frac{\pi}{R} r\right)\exp\left(-\frac{\pi^2}{R^2} \alpha t\right) = 70 $$

Note $$ sinc(0) = 1 $$

$$ u(0, t) = 100 - 96 \exp\left(-\frac{\pi^2}{R^2} \alpha t\right) = 70 $$

$$ \frac{30}{96} =  \exp\left(-\frac{\pi^2}{R^2} \alpha t\right) $$

$$ t = \frac{R^2}{\pi^2 \alpha} \ln\frac{96}{30} $$

$$ R = \left(\frac{3M}{4000\pi}\right)^{1/3} $$

$$ t = \frac{\left(\frac{3M}{4000\pi}\right)^{2/3}}{\pi^2 \alpha} \ln\frac{96}{30} $$

Using $$ \alpha = \frac{k}{\rho c} $$, $$ c = 3120 \frac{J}{kg C} $$, $$ \rho =
1000 \frac{kg}{m^3} $$, $$ k = 0.4 \frac{J}{s\ m\ C}$$

This gives us:

$$ t = 3500 M^{2/3} $$

So another inaccurate set of computations for the hard boiled egg, note that
there is a chance I've made a mistake somewhere.

$$ t = 3500 M^{2/3} $$
- Small: 42g -> 0.042kg -> 422s = 7min
- Medium: 49g -> 0.049kg -> 469s = 7.8min
- Large: 56g -> 0.056kg -> 512s = 8.5min
- Extra Large: 63g -> 0.063kg -> 554s = 9.2min
- Jumbo: 70g -> 0.070kg -> 595s = 10min
