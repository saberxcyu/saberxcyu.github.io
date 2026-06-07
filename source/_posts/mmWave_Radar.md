---
title: FMCW mmWave Radar
date: 2026-06-06
categories: [blog]
tags: [eletrical engineering]
---

Hey! I want to take you on a tour that explains mmWave radars. It is supposed to be fun, and I plan on first taking you back to high school physics and math. Trust me - they are essential. Bear with me, annnnnnnd, let's go!

## Section 1: Electromagnetic Waves

We will begin with the light bulb, something that we are all familiar with (hopefully?). When we flip the light switch, we essentially close the electric circuit for the light bulb, and the power source creates a voltage that enforces an eletectric field that shoots the electrons onto the bulb's filament. This causes the filament's metal atoms to vibrate (accelerate in different directions), which releases electromagnetic waves that travel through space. 

When these electromagnetic waves hit an object and get reflected into our eyes, we see the object. The electromagnetic waves that are created this way have relatively high energy and short wave lengths ($\lambda$). Their ($\lambda$) is within the range of 380-760 nano meters ($$10^{-9} \text{ m}$$). Also, since they are visible to our eyes, we call them visible lights. 

The radar works similarly. 

In the radar, we use a voltage to generate an electric field that accelerate electrons, but instead of letting the electrons vibrate freely like in a light bulb, which produces uncontrolled electricmagnetic waves, we move them up and down in an ordered manner, to produce electricmagnetic waves that are controlled. 

These electromagnetic waves we produce for the radar have much longer $\lambda$, usually around 5 millimeters ish ($$10^{-3} \text{ m}$$). Electromagnetic waves at this wave length carry less energy and we cannot see them with our eyes. They are called mmWaves or microwaves (yes the microwave in your home uses the same stuff to heat up your food).

The animation below shows how these mmWaves are generated. 

![Alt text](em_radiation.gif)

These mmWaves are essentially the same stuff as of lights, just more spread out (longer $\lambda$) and carry lower energy. Whenever I think of mmWaves, I picture them in my head just as visible light rays. This mind model makes me feel more confortable since I am more faimiliar with visible lights, but if we zoom all the way in on one of these rays, and look closely, we will see that they are indeed waves, just as their name suggests.

A visual is provided to understand the wavy nature of these electromagnetic rays here:

![Alt text](em_wave_zoom.png)

So far so good? This wraps up section 1. I think it is not too bad. I will leave you with a fun fact below, then let's dive into section 2~

Fun Fact: there are electromagnetic waves that have very very short $\lambda$, much shorter than visible lights. One example is the Gamma ray. These rays are usually bad for our health because they carry so much energy that they can kill or mutate our cells, but sometimes they are utilized to kill cancer cells as in a gamma knife operation. Its $\lambda$ is less than 0.01 nano meters. It is going to need a very brutal vibration to achieve that kind of electromagnetic waves.


## Section 2: The Circle

What the hell is a circle, if you ask. Then I must answer, seriously, that there is no such thing as a circle. 

What??? What are you talking about? And how the hack did we go from talking about electromagnetic waves to talking about circles? I know I know. Bear with me :).

Do you remember this guy? The one highlighted with a red circle at the bottom.

![Alt text](euclid.png)

It is Euclid. 

Using propositions 1, 9, 10 from the book he wrote, we can draw two circles to make one equilateral triangle, then split it in half to get two right angled triangles (with proofs!). 

Here are the two right-angled triangles I draw using his method:

![Alt text](euclid_construction.png)

Look at the one on the left. The blue shaded one. What is the ratio between the slope (r) and the verticle side (y)? 

Let's take it out so we can see it more clearly. 

![Alt text](triangle_only.png)

Ah ha, this ratio for the right-angled triangle is defined by the sine function sin($$\theta$$) = y / r. 

If r is 1, say the cricles we draw using Euclid's method were unit circles, then y is just equal to sin($$\theta$$). And x is just cos($$\theta$$). 

Now, let's vary the angle $$\theta$$ from 0 degree to 90 degrees. What do we get for x and y? 

![Alt text](q1_quadrant.png)

Indeed, we will get a group of points, with each one represented in a coordinate system of (x, y). As you might have observed, these points all land on the path of the circle's arc. And it is not hard to see that if $$\theta$$ is varied from 0 degree all the way to 360 degrees, we will get a bunch of x and y's, which we can then use to make up a thing that looks like a circle. (this is also why Euclid can get to the right-angled triangles from two circles in the first place, the math is just defined so coherently)

On top of that, the fact that we go back to the first point when $$\theta$$ becomes 360 degress, also gives the sine and cosine functions a very nice property to allow them to be used to describe any periodic events (such as the osscilation of electrons driven by the changing voltage in the radar). 

But there is one thing missing. Time. Our events vary with time. 

Actually, the sine and cosine functions have already thought of this and made room for it! Indeed, $$\theta$$ can be expressed as a function of time, which turns the sine function into sin(wt), and the cosine function into cos(wt), where w is the frequency (in rad/sec). (side note: since one circle is 2$\pi$, to relate w with a frequency in Hz (cycles/sec), we can do w = 2$\pi$f.)

OK, so now we can use the sine and cosine functions (and the circle it makes) as a function of time. What will that look like? 

I made a visual below, using a slow frequency so you can follow the points more easily. 

![Alt text](phasor_animation.gif)

See how the sine and cosine functions provide a list of (x, y) coordinates, which you can use to trace the circle on the left side in like 10 seconds? See how the theta is changing with time? Pretty cool eh?

Now let's do something crazy. So far, the circle is drawn on a 2-dimensional plane. What if we extends it to a 3-dimensional space? Let's view this thing together with time. 

I will show you a 3D (time, x, y) visual here: 

![Alt text](helix_3d.png)

The circle became something like a sprial. Now when theta becomes 360 degrees, the point does not land on the origin anymore, because time has lapsed. The circle has been expanded via the time axis. 

Interestingly, when we project the spiral on the yt plane, we will get our sine function back. And if we do that to the xt plane, we will get our cosine function back. 

So essentially, what we have done here, is that we have represented the sprial using the coordinate (x, y) using sin(wt) and cos(wt), just like how a point on a 2D plane is expressed by (x, y). 

And indeed, this is written formally in math as Z(t) = x(t) + j*y(t), where Z is the spiral (it is our event, or we can call it our signal), and the j is there in front of the y component to indicate that the y component is on a different plane. 

These coordinates, x(t), and y(t), are actually tracked separately in the radar and fused together later to reconstruct the signal. 

This will wrap up our section 2. Feeling cool?

And oh yeah, we didn't even find time to talk more about whether the circle exists. Maybe you can think about that on your own time. 

Do you believe the circle exists, or there is no such thing as the circle - pretty much just a bunch of points that follow the sine and cosine function and repeat in locations? 


