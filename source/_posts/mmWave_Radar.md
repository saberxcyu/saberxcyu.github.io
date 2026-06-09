---
title: FMCW mmWave Radar
date: 2026-06-06
mathjax: true
categories: [blog]
tags: [eletrical engineering]
---

Hey! I want to take you on a taur that explains FMCW (Frequency Modulated Continuous Wave) mmWave radars. It is supposed to be fun, and I plan on first taking you back to high school physics and then elementary school math. 

Trust me - they are essential. Bear with me, annnnnnnd, let's go!

## Section 1: Electromagnetic Waves

We will begin with the light bulb, something we are all familiar with. 

When we flip a switch to turn on the light, we essentially close the electric circuit for the light bulb. The power source creates a voltage that generates an eletectric field that drives electrons towards the bulb's filament. 

This causes the filament's metal atoms to vibrate (which means, they accelerate randomly in different directions) and release electromagnetic waves that travel through space and light up the night.

  <figure>
    <img src="lightbulb.gif" alt="A light bulb emitting EM waves">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 1: A light bulb emitting electromagnetic waves to the surrounding.
    </figcaption>
  </figure>

The electromagnetic waves that are created this way have relatively high energy and short wave lengths $\lambda$ (380-760 nano meters). We call them "visible lights".

The radar works very similarly. 

In the radar, we also use a voltage to move electrons in the conductor, but instead of letting the electrons vibrate freely like the atoms in the light bulb (which produces random electromagnetic waves that are good enough for brightening the room but not good enough for analysis), we oscillate them up and down to produce controlled waves. 

The electromagnetic waves we produce this way have much longer $\lambda$, usually around 5 millimeters ish (this depends on the frequency of the voltage oscillation). So we call them mmWaves.

The animation below shows how these electromagnetic waves are generated. Note how some of the waves appear darker. That is because the electromagnetic waves produced this way have lower intensity along some directions due to the geometry of the oscillation.

  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates eletromagnetic waves.
    </figcaption>
  </figure>

To get a closer look at some of these waves, let's zoom right in on some of them! 

See how they are wavy as their name suggests. And note the amplitude difference as well.

  <figure>
    <img src="em_wave_zoom.png" alt="A zoomed-in view on one of the EM rays.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 3: A zoomed-in view on one of the electromagnetic rays.
    </figcaption>
  </figure>

Well, at the end of the day, the mmWave we generate this way is essentially the same matter as visible lights. They are just more spread out (longer $\lambda$) and carries lower energy. 

So whenever I think of mmWaves or electromagnetic waves, I just picture them in my head just as visible light rays. I feel more comfortable this way since I am more faimiliar with visible lights. 

So far so good? This will wrap up section 1. 

I think it is not too bad. Right? I will leave you with a fun fact below, then let's dive into section 2~

Fun fact: there are electromagnetic waves that have very very short $\lambda$, much shorter than visible lights. One example is the gamma ray. These rays carry high energy and can kill cells in our body. The doctors sometimes use them as gammar knifes to treat cancer. Their $\lambda$ is less than 0.01 nano meters. 


## Section 2: The Cricle

In this chapter, our goal is to understand more about the circle -> because the circle is actually what we use to describe radar signals. I will explain why the circle is used to represent radar signals in section 3, but for now, let's just look at the circle together. 

What the hell is a circle, if you ask. Then I must answer you, very seriously, that there maybe no such thing as a circle. 

What??? What are you talking about? And how the hack did we go from talking about light bulbs to talking about circles? I know I know. Bear with me 😊.

Do you remember this guy? The one highlighted with a red circle at the bottom. Looks like you doing your little thing and not paying attention in the classroom.

  <figure>
    <img src="euclid.png" alt="The School of Athens with Euclid highlighted.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 4: The School of Athens with Euclid highlighted.
    </figcaption>
  </figure>

It is Euclid. 

Using propositions 1, 9, 10 from the book he wrote, we can draw two circles to make one equilateral triangle, then split it in half to get two right-angled triangles (with proofs!). 

Here are the two right-angled triangles I draw using his method:

  <figure>
    <img src="euclid_construction.png" alt="Drawing two right-angled triangles using Euclid's propositition 1, 9, 10.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 5: Drawing two right-angled triangles using Euclid's propositition 1, 9, 10.
    </figcaption>
  </figure>

Let's look at the one on the left. The blue shaded one. What is the definition of the ratio between the slope (r) and the verticle side (y)? 

Ah, yes, you are right, maybe we should take it out from that diagram so we can examine more closely. 

  <figure>
    <img src="triangle_only.png" alt="The blue shaded right-angled triangle alone.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 6: The blue shaded right-angled triangle alone.
    </figcaption>
  </figure>

Now you see the ratio is defined by the sine function $\sin(\theta) = y/r$. (hopefully not from my labels?)

If r is 1, say the cricles we draw were unit circles, then y is just equal to sin($\theta$). And x is just cos($\theta$). 

Now, let's vary the angle $\theta$ from 0 degree to 90 degrees. What do we get for x and y? 

  <figure>
    <img src="q1_quadrant.png" alt="Varying $\theta$ from 0 deg to 360 to draw a group of points using (x, y) coordinates.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 7: Varying $\theta$ from 0 deg to 90 to draw a group of points using (x, y) coordinates.
    </figcaption>
  </figure>

Indeed, we will get a group of points. Each point will have a x coordinate, and a y coordinate. So we can plot them onto the xy plane.

As you might have observed, these points all land on the path of the circle's arc. And it is not hard to see that if $\theta$ is varied from 0 degree all the way to 360 degrees, we will get a bunch of x and y's that eventually make up the whole circle. (this is also why Euclid can get to the right-angled triangles from two circles in the first place, the math is just defined so coherently)

On top of that, the fact that we can go back to the first point when $\theta$ becomes 360 degrees, also gives the sine and cosine functions a very nice property to allow them to be used for describing periodic events (such as the event for oscillating voltage, which you have seen in Figure 2 above). 

But there is one thing missing here. Time. Our events vary with time. 

And actually, the sine and cosine functions have already thought of this and made room for it! Indeed, $\theta$ can be expressed as a function of time, which turns the sine function into $\sin(\omega t)$, and the cosine function into $\cos(\omega t)$, where $\omega$ is the frequency (in rad/sec). (side note: since one circle is 2$\pi$, to relate $\omega$ with a frequency (f) in Hz (cycles/sec), we can do $\omega = 2\pi f$)

OK, so now we can use the sine and cosine functions (and the circle it makes) as a function of time. What will that look like? 

I made a visual below, using a slow frequency so you can follow the points more easily. 

  <figure>
    <img src="phasor_animation.gif" alt="Varying $\theta$ as a function of time and drawing out the points on the circle using (x, y) coordinates.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 8: Varying $\theta$ as a function of time and drawing out the points on the circle using (x, y) coordinates.
    </figcaption>
  </figure>

See how the sine and cosine functions provide a list of (x, y) coordinates, which you can use to trace the circle on the left side in like 10 seconds? See how the $\theta$ is changing with time? Pretty cool eh?

Now let's do something crazy. So far, the circle is drawn on a 2-dimensional plane. What if we extends it to a 3-dimensional space? Let's visualize this thing together. 

I will show you a 3D (time, x, y) representation here: 

  <figure>
    <img src="helix_3d.png" alt="Adding one more dimension (time) to visualize the circle.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 9: Adding one more dimension (time) to visualize the circle.
    </figcaption>
  </figure>

The circle became a sprial. Now when $\theta$ becomes 360 degrees, the point does not land on the origin anymore, because time has lapsed. The same circle has essentially been expanded along the time axis. 

Interestingly, when we project the spiral on the yt plane, we will get our sine function back. And if we do that to the xt plane, we will get our cosine function back. 

So technically, what we have done here, is that we have represented the sprial using $\sin(\omega t)$ and $\cos(\omega t)$, just like how a point on a 2D plane can be defined by (x, y). 

And indeed, this is written formally in math as 
$$
Z(t) = x(t) + j \cdot y(t)
$$
where Z is the spiral, and the j is there in front of the y component to indicate that the y component is on a different plane. 

The components x(t) and y(t), are actually tracked separately in the radar and fused together later to reconstruct the spiral. 

This will wrap up our section 2. Feeling cool?

And oh yeah, we didn't even find time to talk more about whether the circle exists. Maybe you can think about that on your own time. 

Do you believe the circle exists, or is it pretty much just a bunch of points that follow the sine and cosine function and repeat in locations? 


## Section 3: Why Use a Circle to Represent Radar Signals

Welcome to section 3. We will go over why the circle (or the spiral, if extended along time axis) is used to describe our radar signals. 

One property of the circle, which we kinda mentioned above, is that it repeats itself every 360 degrees, so you can see that there is a sense of periodicity already in there. But this is not the only way to represent peridic events. 

Let's have a look at Figure 2 again from above which shows how electromagnetic waves can be generated in the radar by oscillating the voltage up and down.

  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates eletromagnetic waves.
    </figcaption>
  </figure>

For simplicity, let's assume the voltage in the animation oscillates from +10V to -10V, and completes every cycle in about 10 seconds.

We can then represent the event clearly using a straight vertical line that looks like this (see, it is not only the circle):

  <figure>
    <img src="voltage_oscillation.gif" alt="Oscillating voltage represented on a straight line. ">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 10: Oscillating voltage represented on a straight line. 
    </figcaption>
  </figure>

Notice 2 things. 

First, see how I have normalized the +10V and -10V into a range that goes from +Max to -Max? We can even describe these boundaries with +1 and -1.

Indeed, if we do that, it will be not so hard to see, that the verticle line is just identical to the y-component in the unit circle, which is governed by this relationship: Y(t) = $\sin(\omega t)$, or Voltage(t) = $\sin(\omega t)$.

Hopefully by this point (following the way I explain things), you realize the signal in the radar almost has nothing to do with the electromagnetic waves? In my perspective, the radar signals are completely made up by the voltage oscillation. Although the waves carry the same signal too, I tend to think of them as some kind of transformation that gets the voltage signal into a medium that can be sent into space and interact with things. 

Anyway! So now we have Voltage(t) = $\sin(\omega t)$. In this equation, the voltage can be measured, and $\omega$ and t are known. So it is a perfect equation to describe the oscillating voltage. For sure. 

But what if the signal has a phase shift, that makes it look something like this: Voltage(t) = $\sin(\omega(t-\tau))$ ? Given V, $\omega$, and t, can you solve for $\tau$? 

This is exactly what we get, when the signals are transmitted out to space, travel for a while, and then bounced back to the radar's receiver. The returned signal in this case are shifted by a time difference $\tau$.

But there is a problem, if you attempt to solve that equation for $\tau$, you will notice the sine function will give you two results for $\tau$. But how do you know which answer for $\tau$ is right?

That's when you need the second coordinate, x(t), which gives you x(t) = $\cos(\omega(t-\tau))$. 

If you solve this together with your Voltage(t) equation above, you will get four answers, out of which, two of them you will find matching, meaning that this number is the true $\tau$ that you are looking for, which satisfy both equations. 

The uncertainty about the phase shift, is exactly why you need two coordinates, thus a circle. 

One tricky thing to note is that, on the circle, only the y axis has actual meanings, because it represents the voltage readings during our oscillation, the x axis is actually meaningless. 

To get a reading for x, so that we can solve x(t) and y(t) together for $\tau$, we actually need to make it up in the radar by manipulating the sine singal from the y axis in the beginning and shift that into a cosine one. 

Now let's see that same circle again from Figure 8. Does it make it a little bit easier to read?

  <figure>
    <img src="circle_voltage.gif" alt="Circle relabeled.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 11: The same circle from Figure 8 but with y-axis relabeled as voltage.
    </figcaption>
  </figure>

OK! This is it for section 3. How does it feel? Hopefully by now you understand why a circle is used to represent the radar signal. (but does the circle even exist in the first place? - oh well.)

## Section 4: I have not decided what to write yet

