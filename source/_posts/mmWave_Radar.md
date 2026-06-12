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

We will begin with the light bulb, something we all familiar with. 

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

The electromagnetic waves we produce this way have much longer $\lambda$, usually around 5 millimeters (the wavelength we get depends on the frequency of the voltage oscillation). So they are called mmWaves.

The animation below shows how these electromagnetic waves are generated. Note how some of the waves appear darker. That is because the electromagnetic waves produced this way have lower intensity along some directions due to the geometry of the oscillation. (ps. there are also some special radars that transmit the same intensity of electromagnetic waves in all direction - those are called isotropic radars.)

  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates eletromagnetic waves.
    </figcaption>
  </figure>

To get a closer look at some of these waves, let's zoom right in on some of them! 

  <figure>
    <img src="em_wave_zoom.png" alt="A zoomed-in view on some of the EM rays.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 3: A zoomed-in view on some of the electromagnetic rays.
    </figcaption>
  </figure>

See how wavy these rays are in their nature? Also note the amplitude difference across directions.

At the end of the day, these mmWaves are essentially the same matter as visible lights. They are just more spread out (longer $\lambda$) and carry lower energy. 

So whenever I think of mmWaves or electromagnetic waves, I just picture them in my head as visible light rays. This is a nicer model for me since I am more faimiliar with visible lights. 

So far so good? 

This will wrap up section 1. 

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


## Section 3: Why Use a Circle to Represent Oscillating Voltage

Welcome to section 3. We will go over why the circle (or the spiral, if extended along time axis) is used to describe our event: voltage oscillation. 

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

In fact, if we do that, it will become very obvious that the verticle line is just identical to the y-component in the unit circle, which is governed by this relationship: Y(t) = $\sin(\omega t)$, or Voltage(t) = $\sin(\omega t)$.

With this formula, we can make some observations. Since the voltage can be measured at any given time t, they are both considered known, and $\omega$ is known from how fast we oscillate the voltage, so basically everything is known and well-considered here. Great. That means this equation alone already perfectly describes the event of an oscilating voltage. Sure. 

But what if the signal has a phase shift that makes it look something like this?

Voltage(t) = $\sin(\omega(t-\tau))$, where $\tau$ stands for a time delay.

In fact, this is exactly we will get with the radar when the transmitted electromagnetic waves are later on received. 

Now given V, $\omega$, and t, can you solve for $\tau$? 

And yeah, that is the problem, if you attempt to solve for $\tau$, you will notice the sine function will give you two results that are both mathmatically correct. This can also be visualized on the sine curve.

  <figure>
    <img src="sine_ambiguity.png" alt="Two times are associated with one given voltage.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 11: Two times are associated with one given voltage.
    </figcaption>
  </figure>

That's when you need the second coordinate x(t) which gives you:

x(t) = $\cos(\omega(t-\tau))$

Now if we solve both Voltage(t) and x(t) together for $\tau$, we shall get four answers (2 results for each equation), out of which, exactly two of them you will find matching, indicating the true $\tau$ that satisfies both equations. 

And given both Voltage(t) and x(t), technically, we will get a circle. And this is why the circle is used to represent the oscillating voltage.

Now let's see that same circle again from Figure 8 but actually use it to represent our event. Do you feel more comfortable reading this graph now?

  <figure>
    <img src="circle_voltage.gif" alt="Circle relabeled.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 12: The same circle from Figure 8 but with y-axis relabeled as voltage.
    </figcaption>
  </figure>

I also want to guide your attention to the labels of the y and x-axis above. Notice how only the y-axis has meanings (voltage) and the x-axis is actually meaningless?

This is completely normal. In fact, in the radar, x(t) is actually manipulated from the sine function by shifting it into a cosine one. Its primary role is to rule out the ambiguity from using just the sine function alone.

OK! This is it for section 3. How does it feel? 

Hopefully by now you understand why the circle is used to represent the radar signal. (but does it even exist in the first place? - oh boy.)

## Section 4: 

Welcome to chapter 4. So far we have understood that mmWaves are electromagnetic waves generated by an oscillating voltage which can be described using a circle. In this section, we will discuss the oscillating voltage together with the electromagnetic waves, to understand more in depth how this system works. 

Let's have a look at our old friend again, Figure 2:

  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates eletromagnetic waves.
    </figcaption>
  </figure>

In section 1, we briefly talked about how these electromagnetic waves have varied intensities in different directions.

This intensity difference is governed by the geometry of the oscillating voltage. If the oscillation takes place along the z-axis, then the electromagnetic waves released towards the x and y-axis would have maximum amplitude, and along the z-axis their amplitude will be zero. Everything else going from "parallel to oscillation" to "perpendicular to oscillation" will be in between zero and max amplitude. 

In 3D, this will look something like:

  <figure>
    <img src="em_radiation_3d.gif" alt="Oscillating voltage generates electromagnetic waves (3D).">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 13: Oscillating voltage generates eletromagnetic waves (3D).
    </figcaption>
  </figure>

This animation can be understood in two ways. 

First, since the intensity is max in directions perpendicular to oscillation, and is zero in the direction of oscillation, if we draw the points out (every intensity value per x, y, z), we will get some kind of intensity mapping. This is called the radiation pattern in the literature. (see the donut shape formed in the end)

Second, because the electromagnetic waves can be absorbed and reflected in air (due to small partcicles inside), their amplitude decreases as they travel more distance. So in a sense, you can also picture this animation as if the waves that have the strongest initial amplitude can travel the furthest distance before their amplitude falls to zero. (this is indicated by the rays shooting outwards center)

We will come back to discuss the amplitude of the electromagnetic waves later. 

Right now, let's focus on the wavelength of the electromagnetic waves first. Since we got ourselves familiarized with the circle, let's just use the circle to represent the oscillation from the figure above.

  <figure>
    <img src="em_radiation_circle.gif" alt="Eletromagnetic waves generated by the circle.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 14: Eletromagnetic waves generated by the circle.
    </figcaption>
  </figure>

Now, let us zoom in to some of these electromagnetic waves generated by the circle, like we did for Figure 3.

More specifically, let's look at the one along the x-axis with maximum intensity. 

  <figure>
    <img src="wave_from_circle.gif" alt="A zoomed-in view of eletromagnetic waves generated by the circle.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 15: A zoomed-in view of eletromagnetic waves generated by the circle.
    </figcaption>
  </figure>

Note what is shown here on the right is the actual electromagnetic wave. Not a sine function, which is one axis of the circle.

Now what is going to happen if we speed up the voltage oscillation to 2x the speed?

Let's visualize it!

  <figure>
    <img src="wave_from_circle_2x.gif" alt="A zoomed-in view of eletromagnetic waves generated by the circle (2x speed).">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 16: A zoomed-in view of eletromagnetic waves generated by the circle (2x speed).
    </figcaption>
  </figure>

Mmmm... It seems like the wavelength of the electromagnetic waves is dependent on the speed of the cirlce that represents the oscillation frequency.

Intersting!

What if we use with a smaller circle (less voltage during oscillation)? 

  <figure>
    <img src="wave_from_circle_2x_halfA.gif" alt="A zoomed-in view of eletromagnetic waves generated by the circle (2x speed).">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 17: A zoomed-in view of eletromagnetic waves generated by the circle (2x speed).
    </figcaption>
  </figure>

Oh... Now even amplitude of the strongest wave along the perpendicular direction is only half of that from before, just like the waves in some of these other weaker directions.  

With this poor starting momentum, the electromagnetic wave will travel less distance before they turn into zero amplitude.

In fact, these waves will be no use to us well before they get to absolutely zero amplitude -> as long as their amplitude is lower than most of the noisy signals that exist around them in the enviornment, they will offer no use to us because the low Singal-to-Noise ratio will make it impossible to distinguish the waves from noise.







