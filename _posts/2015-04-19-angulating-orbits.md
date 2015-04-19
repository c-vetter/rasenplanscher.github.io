---
title: Angulating Orbits
---

Finally! I get to start on my anticipated reference project: "Project Pluto" <small>I chose that name because this is about showing elements that look like planets but are none ;)</small>

## What is it about?
I want to implement a display widget that turns a data list into something that resembles a [planetary system](https://en.wikipedia.org/wiki/Planetary_System). Technology-wise, I think SASS should be fine, but since I'm learning [AngularJS](https://angularjs.org/), I'll start with that and go for SASS afterward. If I'm in the mood, I may investigate porting to jQuery as well. Additional options include [canvas](http://html5doctor.com/element-index/#canvas) and [three.js](http://threejs.org/)(I know, it uses canvas :P).

So, starting off, I read up on ellipses because I want my `planetoid`s to move on elliptical paths with a `sunoid` at one of the foci. The main thing here is that circles are child's play and I like using proper physics or at least approximate that in order to achieve high credibility in regard to my visuals.

## So, ellipses

First off, what is an ellipse? It's not [a punctuation mark](https://en.wikipedia.org/wiki/Ellipsis), but [a geometrical figure](https://en.wikipedia.org/wiki/Ellipse). In the simplest, most intuitive description, it is a compressed or stretched circle. More precisely:

> An ellipse is a curve on a plane surrounding two focal points
> such that the sum of the distances to the two focal points is
> constant for every point on the curve.

> The orbit of a planet is an ellipse with the Sun at one of the two foci.

Now, what can we do with that knowledge? Actually not a whole lot yet, but as it turns out, mathematicians love ellipses and have investigated those lovable things in-depth. Being the [lazy bastard](http://threevirtues.com/) that I am, I'm taking their research and using it for my own ends. And they did find out a lot, including all the formulae I need.

## Research
Initially I searched [the web](https://duckduckgo.com/) for complete or partial solutions, but it seems like no one has publicly done that -- great, first one :D. People do use and/or struggle with ellipses, but my particular project is not in what people talk about. There are similar things, but they are usually focused differently.

In the end, [Wikipedia](https://en.wikipedia.org/wiki/Ellipse) was all I needed for this... Including the [proper speed calculation](https://en.wikipedia.org/wiki/Kepler%27s_laws_of_planetary_motion#Second_law)!

Extracting the formulae in usable form took some doing, especially in the beginning when I was just skipping about kind of haphazardly. But here they are in all their splendor and glory:

### Basics

I'll be using the following symbols here and in code for the respective items (mostly identical to [standard parlance](https://en.wikipedia.org/wiki/Ellipse), but I'm not using [Greek sigils](https://en.wikipedia.org/wiki/Greek_alphabet))

System-wide state, a.k.a. application-constant data:

+ `a`: [length of the semi-major axis](https://en.wikipedia.org/wiki/Semi-major_axis)
+ `b`: [length of the semi-minor axis](https://en.wikipedia.org/wiki/Semi-minor_axis)
+ `sol`(`xs`, `ys`): [focus point 1, a.k.a. the sun](https://en.wikipedia.org/wiki/Kepler's_laws_of_planetary_motion#First_law)
+ `ext`(`xe`, `ye`): focus point 2
+ `C`: the geometrical center of the ellipse
+ `f`: [distance between `C` and `sol`]()
+ `e`: [eccentricity](https://en.wikipedia.org/wiki/Eccentricity_(mathematics))
+ `dt`: delta time -- how much time has passed since the last calculation

Item-local state, a.k.a. calculation data:

+ `p`(`xp`, `yp`): the point or planetoid under focus, i.e. what we're calculating data about
+ `A`: area in the ellipse
+ `P`: period, the time for a single round-trip
+ `V`: areal velocity
+ `theta`: the angle in `sol` from the major axis (`sol`---`ext`)
+ `dtheta`: delta theta -- the difference between the current angle and the next
+ `r`: current "radius", the distance between `sol` and `p`

### Calculations

In order to progress the planetoids along their paths, we need a few calculations for each step along the way:

+ `r(theta)`: `a * (1 - e*e) / (1 - e * cos(theta))`
+ `dtheta`: `2 * dt * V / r / r`
+ `theta`: `theta + dtheta`
+ `xp`: `xs + acos(theta) * r(theta)`
+ `yp`: `ys + asin(theta) * r(theta)`

That's local to each ellipse, so that needs to be converted into 3D coordinates. That means rotation and translation from a possibly tilted plane. But I'll tackle that on another day.
