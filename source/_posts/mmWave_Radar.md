---
title: FMCW mmWave Radar
date: 2026-06-06
mathjax: true
categories: [blog]
tags: [eletrical engineering]
---

Hey! I want to take you on a tour that explains FMCW (Frequency Modulated Continuous Wave) mmWave radars. It is supposed to be fun, and I plan on first taking you back to high school physics and then elementary school math. 

Trust me - they are essential. Bear with me, annnnnnnd, let's go!

## Section 1: Electromagnetic Waves

We will begin with the light bulb, something we are all familiar with. 

When we flip a switch to turn on the light, we essentially close the electric circuit for the light bulb. The power source creates a voltage that generates an eletectric field that drives electrons towards the bulb's filament. 

This causes the filament's metal atoms to vibrate (accelerate randomly in different directions), which releases electromagnetic waves that travel through space. 

![Alt text](lightbulb.gif)
  <figure>
    <img src="lightbulb.gif" alt="A light bulb emitting EM waves">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 1: A light bulb emitting electromagnetic waves to the surrounding.
    </figcaption>
  </figure>

The electromagnetic waves that are created this way have relatively high energy and short wave lengths $\lambda$ (380-760 nano meters ($10^{-9}\ \text{m}$)). We call them "visible lights".

The radar works very similarly. 

In the radar, we use a voltage to generate an electric field that accelerate electrons in a conductor, but instead of letting the electrons vibrate freely like the atoms in a light bulb, which produces electricmagnetic waves with randomly varying $\lambda$, we move them up and down in a controlled manner, to produce electricmagnetic waves with a fixed $\lambda$ . 

These electromagnetic waves we produce for the radar have much longer $\lambda$, usually around 5 millimeters ish ($10^{-3}\ \text{m}$). Electromagnetic waves at this level carry less energy and we cannot see them with our eyes. They are called mmWaves.

The animation below shows how these electromagnetic waves are generated. 

![Alt text](em_radiation.gif)
  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates eletromagnetic waves.
    </figcaption>
  </figure>

And... Let's zoom in on one of them to see their wavy nature.

![Alt text](em_wave_zoom.png)
  <figure>
    <img src="em_wave_zoom.png" alt="A zoomed-in view on one of the EM rays.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 3: A zoomed-in view on one of the electromagnetic rays.
    </figcaption>
  </figure>

The mmWave we generate this way is essentially the same matter as visible lights, just more spread out (longer $\lambda$) and carries lower energy. 

Whenever I think of electromagnetic waves, I picture them in my head just as visible light rays. This mind model makes me feel more comfortable since I am more faimiliar with visible lights. 

So far so good? This wraps up section 1. I think it is not too bad. I will leave you with a fun fact below, then let's dive into section 2~

Fun fact: there are electromagnetic waves that have very very short $\lambda$, much shorter than visible lights. One example is the Gamma ray. These rays carry high energy and can damage or kill our cells in the body, so they are sometimes used as a gamma knife to treat cancers. Gamma rays' $\lambda$ is less than 0.01 nano meters. It is going to need a very brutal (but controlled) acceleration of particles to achieve that kind of electromagnetic waves.


## Section 2: The Cricle

In this chapter the goal is to understand more about the circle -> because the circle is actually what we use to describe radar signals. I will explain why we use the circle to represent radar signals in section 3, but for now, let's just look at the circle together. 

What the hell is a circle, if you ask. Then I must answer, seriously, that there is no such thing as a circle. 

What??? What are you talking about? And how the hack did we go from talking about light bulbs to talking about circles? I know I know. Bear with me 😊.

Do you remember this guy? The one highlighted with a red circle at the bottom. Looks like you not paying attention in the classroom.

![Alt text](euclid.png)
  <figure>
    <img src="euclid.png" alt="The School of Athens with Euclid highlighted.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 4: The School of Athens with Euclid highlighted.
    </figcaption>
  </figure>

It is Euclid. 

Using propositions 1, 9, 10 from the book he wrote, we can draw two circles to make one equilateral triangle, then split it in half to get two right-angled triangles (with proofs!). 

Here are the two right-angled triangles I draw using his method:

![Alt text](euclid_construction.png)
  <figure>
    <img src="euclid_construction.png" alt="Drawing two right-angled triangles using Euclid's propositition 1, 9, 10.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 5: Drawing two right-angled triangles using Euclid's propositition 1, 9, 10.
    </figcaption>
  </figure>

Let's look at the one on the left. The blue shaded one. What is the ratio between the slope (r) and the verticle side (y)? 

Ah, yes, you are right, maybe we should take it out from that diagram so we can examine more closely. 

![Alt text](triangle_only.png)
  <figure>
    <img src="triangle_only.png" alt="The blue shaded right-angled triangle alone.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 6: The blue shaded right-angled triangle alone.
    </figcaption>
  </figure>

Ah ha, now you see the ratio is defined by the sine function $\sin(\theta) = y/r$. (hopefully not from my labels?)

If r is 1, say the cricles we draw were unit circles, then y is just equal to sin($\theta$). And x is just cos($\theta$). 

Now, let's vary the angle $\theta$ from 0 degree to 90 degrees. What do we get for x and y? 

![Alt text](q1_quadrant.png)
  <figure>
    <img src="q1_quadrant.png" alt="Varying $\theta$ from 0 deg to 360 to draw a group of points using (x, y) coordinates.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 7: Varying $\theta$ from 0 deg to 360 to draw a group of points using (x, y) coordinates.
    </figcaption>
  </figure>

Indeed, we will get a group of points, with each one expressed in a coordinate system of (x, y). 

As you might have observed, these points all land on the path of the circle's arc. And it is not hard to see that if $\theta$ is varied from 0 degree all the way to 360 degrees, we will get a bunch of x and y's, which will make up the whole circle. (this is also why Euclid can get to the right-angled triangles from two circles in the first place, the math is just defined so coherently)

On top of that, the fact that we can go back to the first point when $\theta$ becomes 360 degress, also gives the sine and cosine functions a very nice property to allow them to be used for describing periodic events (such as the oscillating voltage, which you have seen in Figure 2 above). 

But there is one thing missing. Time. Our events vary with time. 

Actually, the sine and cosine functions have already thought of this and made room for it! Indeed, $\theta$ can be expressed as a function of time, which turns the sine function into $\sin(\omega t)$, and the cosine function into $\cos(\omega t)$, where $\omega$ is the frequency (in rad/sec). (side note: since one circle is 2$\pi$, to relate $\omega$ with a frequency (f) in Hz (cycles/sec), we can do $\omega = 2\pi f$)

OK, so now we can use the sine and cosine functions (and the circle it makes) as a function of time. What will that look like? 

I made a visual below, using a slow frequency so you can follow the points more easily. 

![Alt text](phasor_animation.gif)
  <figure>
    <img src="phasor_animation.gif" alt="Varying $\theta$ as a function of time and drawing out the points on the circle using (x, y) coordinates.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 8: Varying $\theta$ as a function of time and drawing out the points on the circle using (x, y) coordinates.
    </figcaption>
  </figure>

See how the sine and cosine functions provide a list of (x, y) coordinates, which you can use to trace the circle on the left side in like 10 seconds? See how the $\theta$ is changing with time? Pretty cool eh?

Now let's do something crazy. So far, the circle is drawn on a 2-dimensional plane. What if we extends it to a 3-dimensional space? Let's view this thing together with time. 

I will show you a 3D (time, x, y) visual here: 

![Alt text](helix_3d.png)
  <figure>
    <img src="helix_3d.png" alt="Adding one more dimension (time) to visualize the circle.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 9: Adding one more dimension (time) to visualize the circle.
    </figcaption>
  </figure>

The circle became something like a sprial. Now when $\theta$ becomes 360 degrees, the point does not land on the origin anymore, because time has lapsed. The circle has been expanded along the time axis. 

Interestingly, when we project the spiral on the yt plane, we will get our sine function back. And if we do that to the xt plane, we will get our cosine function back. 

So essentially, what we have done here, is that we have represented the sprial using the coordinate (x, y) with $\sin(\omega t)$ and $\cos(\omega t)$, just like how a point on a 2D plane is expressed by (x, y). 

And indeed, this is written formally in math as 
$$
Z(t) = x(t) + j \cdot y(t)
$$
where Z is the spiral, and the j is there in front of the y component to indicate that the y component is on a different plane. 

These coordinates, x(t), and y(t), are actually tracked separately in the radar and fused together later to reconstruct the spiral. 

This will wrap up our section 2. Feeling cool?

And oh yeah, we didn't even find time to talk more about whether the circle exists. Maybe you can think about that on your own time. 

Do you believe the circle exists, or there is no such thing as the circle - pretty much just a bunch of points that follow the sine and cosine function and repeat in locations? 


## Section 3: Why Use a Circle to Represent Radar Signals

Welcome to section 3. We will go over why the circle (or the spiral, if extended along time axis) is used to describe our signals. 

One property of the circle, which we kinda mentioned above, is that it repeats itself when $\theta$ is 360 degrees, so you can see that there is a sense of periodicity already in there. But this is not the only way to represent peridic events. 

Let's have a look at Figure 2 again from above. This shows how electromagnetic waves are generated in the radar by oscillating the voltage up and down.

![Alt text](em_radiation.gif)
  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates eletromagnetic waves.
    </figcaption>
  </figure>

For simplicity, let's assume the voltage in the animation oscillates from +10V to -10V, and completes every cycle in about 10 seconds.

We can then represent the event clearly using a straight vertical line that looks like this (see, it is not only the circle):

![Alt text](voltage_oscillation.gif)
  <figure>
    <img src="voltage_oscillation.gif" alt="Oscillating voltage represented on a straight line. ">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 10: Oscillating voltage represented on a straight line. 
    </figcaption>
  </figure>

Notice 2 things. 

First, see how I have normalized the +10V and -10V into a range that goes from +Max to -Max? We can actually describe these boundaries with +1 and -1.

If we do that, it will be not so hard to see, that the verticle line is just the y-component in the unit circle, which is governed by this relationship: Y(t) = Voltage(t) = $\sin(\omega t)$.

Hopefully by this point you realize the signal in the radar has nothing to do with the electromagnetic waves. The siganls are pretty much coming from voltage oscillations. The electromagnetic waves are only used so the voltage singals can interact with the surrounding world.

Anyway! So now we get Voltage(t) = $\sin(\omega t)$. This is perfectly fine for describing the oscillating voltage. But what if voltage signal starts to shift? 

What do you mean by starting to shift? You might ask. 

In the case of a radar, the signals are generated by the voltage, the voltage oscillation also genereates electromagnetic waves that are sent to space, interact with things, and then bounce back to the radar, and again turned into voltage oscillation signals. 

The returned signals are shifted by a time difference $\tou$. 

And the thing is, the sine and cosine functions have again thought about this, and made room for it! This can be expressed as Voltage(t) = $\sin(\omega(t-\tou))$.

t is known (like, the 5th second in a cycle that repeats every 10s), w is known, and voltage can be measured. So you can solve for $\tou$. But there is a problem, because this equation actually yields two results for $\tou$. 

How do you know which $\tou$ is right? You will need the second coordinate, x(t), which gives you x(t) = $\cos(\omega(t-\tou))$. If you solve this together with your Voltage(t) equation above, you will get four answers (two results from each equation), out of which, two answers are matching, meaning this $\tou$ satisfy both your y equation and your x equation, which is why, you need two coordinates (x, y). And two coordinates make up a circle. 

One tricky thing to know is that, on the circle, only the y axis has actual meaning, because it represents the voltage reading during oscillation, the x axis is actually meaningless. To get a reading for x, so that we can solve both x and y at the same time for $\tou$, we actually need to make it up in the radar by manipulating the sine singal from the y axis in the beginning and make that into a cosine wave. 

OK~ This is it for section 3. How does it feel? Hopefully by now you understand how and why a circle is used to represent the radar signal? And perhaps how to read the circle (if it even exists)?

Next, we will talk about radars!

## Section 4: I have not decided what to write yet

