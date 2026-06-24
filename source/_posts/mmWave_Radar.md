---
title: FMCW mmWave Radar
date: 2026-06-06
mathjax: true
categories: [blog]
tags: [eletrical engineering]
---

Hey! I want to take you on a tour that explains FMCW (Frequency Modulated Continuous Wave) mmWave radars. It is supposed to be fun. 

We will first go back to high school physics and touch up our memory on eletcromagnetic waves.

We will then talk about how we can use a circle to represent radar signals and go over some very fundamental stuffs for the radar to help build familiarity around this topic.

The ultimate goal is to briefly answer "what is FMCW mmWave radar" in this 20-minute read.

Bear with me, annnnnnnd, let's go!

## Section 1: Electromagnetic Waves

We will begin the blog with the light bulb, something we're all familiar with. 

When we flip a switch to turn on the light, what we are doing essentially is just closing the electric circuit for the light bulb. 

The power source creates a voltage that generates an eletectric field and drives electrons towards the bulb's filament. 

This causes the filament's atoms to vibrate and release electromagnetic waves that light up the space.

  <figure>
    <img src="lightbulb.gif" alt="A light bulb emitting EM waves">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 1: A light bulb emitting electromagnetic waves to the surrounding.
    </figcaption>
  </figure>

The electromagnetic waves created this way have relatively high energy and short wave lengths $\lambda$ (380-760 nano meters), and we call them "visible lights".

The radar works very similarly. 

In the radar, we also use a voltage to move electrons (which happens in the conductor). 

Instead of letting the electrons vibrate freely like the light bulb's filament (which generates random electromagnetic waves that are good enough for brightening the room but not good enough for analysis), we oscillate them up and down in an ordered manner to produce controlled waves. 

The electromagnetic waves produced this way have much longer $\lambda$, usually around 5 millimeters ish. So they are called mmWaves.

The animation below shows how these electromagnetic waves can be generated. Note how some of them appear darker. That is because the electromagnetic waves produced this way have lower intensity along some directions due to the geometry of the oscillation. (ps. there are also some special radars that transmit the same intensity of electromagnetic waves in all direction - those are called isotropic radars.)

  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates eletromagnetic waves.
    </figcaption>
  </figure>

To get a closer look at some of these waves, let's freeze the animation and zoom right in on some of them! 

  <figure>
    <img src="em_wave_zoom.png" alt="A zoomed-in view on some of the EM rays.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 3: A zoomed-in view on some of the electromagnetic rays.
    </figcaption>
  </figure>

See the wavy nature of these rays now? Also note the amplitude difference across different directions.

At the end of the day, these mmWaves are essentially just the same matter as visible lights, only more spread out (longer $\lambda$) and carry less energy. 

So whenever I think of mmWaves or electromagnetic waves, I just picture them in my head as visible lights. Somehow, this mental model has made me feel more comfortable working around mmWave radars.

So far so good? This will wrap up everything for section 1. 

It's not too bad. Right? I will leave you with a fun fact below, then let's dive into section 2!

Fun fact: there are electromagnetic waves that have very very short $\lambda$, much shorter than visible lights, like the gamma ray (whose $\lambda$ is less than 0.01 nano meters). They carry high energy and can damage our cells in the body. That is why the doctors use them as a "gamma knife" to treat cancers sometimes.


## Section 2: The Basics of a Cricle

In this chapter, our goal is to understand more about the circle -> because it is actually what we use to describe the event of voltage oscillation in the radar, the process which produces those mmWaves. 

I will explain why the circle is used in section 3, for now, let's just focus on the fundamentals together. 

How about we start with my claim: there maybe no such thing as a circle. 

What!? This is such non-sense. You might wonder. You have understood the circle for so long (perhaps from Kindergarten or middle school) and now there's a guy telling you there is no such thing as a circle. 

I totally get it. Let me explain. 

Also, this blog should be written in a way that makes it totally up to you whether you decide if the circle exsits.

(yes, it is going to be up to you anyway regardless of what I wrote... 😂 Just wanted to emphasize it here so it can serve as some kind of a reminder).

OK enough BS. Let's get back to our blog.

Do you remember this guy? The one highlighted in the corner with a red circle, who looks just like you doing your little thing in the classroom and not paying attention to the instructor.

  <figure>
    <img src="euclid.png" alt="The School of Athens with Euclid highlighted.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 4: The School of Athens with Euclid highlighted.
    </figcaption>
  </figure>

It is Euclid. 

Using propositions 1, 9, 10 from the book he wrote around 2000 years ago, we can draw two circles to make one equilateral triangle, then split it in half to get two right-angled triangles (with proofs!). 

Here are the two right-angled triangles I draw using his method:

  <figure>
    <img src="euclid_construction.png" alt="Drawing two right-angled triangles using Euclid's propositition 1, 9, 10.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 5: Drawing two right-angled triangles using Euclid's propositition 1, 9, 10.
    </figcaption>
  </figure>

Let's look at the one on the left. The blue shaded one. What is the definition of the ratio between the slope (r) and the verticle side (y)? 

Ah, yes, you are right. We have learned this in middle school. It is defined by the sine function $\sin(\theta) = y/r$.

  <figure>
    <img src="triangle_only.png" alt="The blue shaded right-angled triangle alone.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 6: The blue shaded right-angled triangle alone.
    </figcaption>
  </figure>

If r is 1, say the cricles we draw were unit circles, then y is just equal to sin($\theta$). And x is just cos($\theta$). 

Now, let's vary the angle $\theta$ from 0° to 90°. What do we get for x and y? 

  <figure>
    <img src="q1_quadrant.png" alt="Varying $\theta$ from 0 deg to 360 to draw a group of points using (x, y) coordinates.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 7: Varying $\theta$ from 0 deg to 90 to draw a group of points using (x, y) coordinates.
    </figcaption>
  </figure>

Indeed, we will get a group of points. Each point will have a x-coordinate, and a y-coordinate. And so we can plot them onto the xy plane.

As you might have observed, these points all land on the path of the circle's arc. 

And it is not hard to see that if $\theta$ is varied from 0° all the way to 360°, we will get a bunch of x and y's that eventually make up the whole circle. 

(this is also why Euclid can get to the right-angled triangles from two circles in the first place, the math is just defined so coherently)

The fact that when $\theta$ becomes 360, we will land on the origin again, gives the sine and cosine functions a very nice property to allow them to be used for describing periodic events (such as for the oscillating voltage that you have seen in Figure 2). 

But to describe the event of voltage oscilation, there is one thing missing here. And that's time. Our event varies with time. 

Indeed, $\theta$ can be expressed as a function of time, which turns y into $\sin(\omega t)$, and x into $\cos(\omega t)$, where $\omega$ is the frequency (in rad/sec). (side note: since one circle is 2$\pi$, to relate $\omega$ with a frequency (f) in Hz (cycle/sec), we can do $\omega = 2\pi f$)

OK, so now we plot the x and y points as a function of time. What will that look like on the xy plane? 

See this visual below, with a slow frequency to allow us to follow the points more easily. 

  <figure>
    <img src="phasor_animation.gif" alt="(Right) Varying $\theta$ from 0 to 360° as a function of time, and (Left) drawing out the points on the xy plane.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 8: (Right) Varying $\theta$ from 0 to 360° as a function of time, and (Left) drawing out the points on the xy plane.
    </figcaption>
  </figure>

See how the x and y from the right-angled triangle traces out a nice circle on the left side in like 10 seconds? See how the $\theta$ is changing with time? Pretty cool eh?

Now let's do something crazier. What if we extends the circle to a 3-dimensional space? Let's visualize this thing together with one more dimension, time. 

Here's the 3D representation in (time, x, y): 

  <figure>
    <img src="helix_3d.png" alt="Adding one more dimension (time) to visualize the circle.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 9: Adding one more dimension (time) to visualize the circle.
    </figcaption>
  </figure>

The circle became a sprial. Now when $\theta$ becomes 360°, the point does not land on the origin anymore, because time has lapsed. The same circle has essentially been expanded along the time axis. 

Interestingly, when we project the spiral on the yt plane, we will get our sine function back. And if we do that to the xt plane, we will get our cosine function back. 

So hopefully by this point you see what we have done here, is actually just repreesnting the sprial using a coodintate of ($\sin(\omega t)$,$\cos(\omega t)$), just like how a point on a 2D plane can be defined by a coodinate of (x, y). 

And indeed, this is written formally in math as 
$$
Z(t) = x(t) + j \cdot y(t)
$$
where Z is the spiral, and the j is there in front of the y component to indicate that the y component is on a different plane. 

The components x(t) and y(t), are actually tracked separately in the radar and fused together later to reconstruct the signal. 

This will wrap up our section 2. Feeling cool?

And oh yeah, we didn't even find time to talk more about whether the circle exists. Maybe you can think about that on your own as well. 

Do you believe that there is such thing as a circle, or is it just a bunch of points that follow the sine and cosine function and repeat in locations? 


## Section 3: Why Use a Circle to Represent Oscillating Voltage

Welcome to section 3. In this section, we will go over why the circle (or the spiral, if extended along time axis) is used to describe our event - voltage oscillation. 

One property of the circle, which we kinda mentioned above, is that it repeats itself every 360°, so you can see already that there is some kind of a sign there for periodicity. This however is not the only way to represent peridic events. 

Let's have a look at Figure 2 again from above which shows how electromagnetic waves can be generated in the radar by oscillating the voltage up and down.

  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates eletromagnetic waves.
    </figcaption>
  </figure>

For simplicity, let's assume the voltage in the animation oscillates from +10V to -10V, and completes every cycle in about 10 seconds.

We can then represent the event clearly using a straight vertical line that looks like this (see,not only the circle will get the job done):

  <figure>
    <img src="voltage_oscillation.gif" alt="Oscillating voltage represented on a straight line. ">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 10: Oscillating voltage represented on a straight line. 
    </figcaption>
  </figure>

Notice how the +10V and -10V can be normalized into a range that goes from +Max to -Max? We can even describe these boundaries with +1 and -1.

In fact, if we do that, it will become quite obvious that the verticle line is just the y-component in the unit circle, which is governed by this relationship: Y(t) = $\sin(\omega t)$, or more specifically Voltage(t) = $\sin(\omega t)$.

With this formula, we can make some observations. 

Since the voltage V can be measured at any given time t, both V and t are considered known. And $\omega$ is known from how fast we oscillate the voltage, so basically everything in this formula is known and well-considered. 

Great. 

That means this equation alone already perfectly describes the event of an oscilating voltage. (it surely does)

But what if the signal has a phase shift that makes it look something like this?

Voltage(t) = $\sin(\omega(t-\tau))$, where $\tau$ stands for a time delay. (and $\\omega \tau$ is called the phase shift)

In fact, this equation shows exactly what we will get, when the transmitted electromagnetic waves are later on received back at the radar. 

But now there is a problem.

Given V, $\omega$, and t, can you solve for $\tau$? 

Indeed, if you attempt to solve for $\tau$, you will notice the sine function produces two results that are both mathmatically correct. 

This can also be visualized graphically as follows:

  <figure>
    <img src="sine_ambiguity.png" alt="Two times are associated with one given voltage.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 11: Two times are associated with one given voltage.
    </figcaption>
  </figure>

That's why we need the second coordinate x(t) which gives:

x(t) = $\cos(\omega(t-\tau))$

Now if we solve both Voltage(t) and x(t) together for $\tau$, we shall get four answers (2 results per equation), out of which, exactly two of them you will find matching, which indicates the true $\tau$ value. 

And in this case, since we will need both Voltage(t) and x(t), technically, we'll need a circle. And this is why the circle is used to represent the event.

Now let's see that same circle again from Figure 8 but this time we will actually use it to represent our event. 

Do you now feel more comfortable reading this animation?

  <figure>
    <img src="circle_voltage.gif" alt="Circle relabeled.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 12: The same circle from Figure 8 but with y-axis relabeled as voltage.
    </figcaption>
  </figure>

I also want to guide your attention to the labels of the y and x-axis above. Notice how only the y-axis has meanings (voltage) and the x-axis is actually meaningless?

This is completely normal. In fact, in the radar, x(t) is actually manipulated from the sine function by shifting it into a cosine one. Its primary role is to rule out the ambiguity from using just the sine function alone.

OK! This is it for section 3. How does it feel? 

Hopefully by now you understand why the circle is used to represent an oscillating voltage. (but does it even exist in the first place? - oh boy.)

## Section 4: Connecting the Circle with Electromagnetic Waves

Welcome to chapter 4. So far we have understood that mmWaves are electromagnetic waves generated by an oscillating voltage which can be described using a circle. 

We will now discuss more about the electromagnetic waves and their relation with the oscillating voltage. Our goal for this section is to understand the system in greater details. 

Let's have another look at our friend, Figure 2:

  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates eletromagnetic waves.
    </figcaption>
  </figure>

In section 1, we briefly talked about how these electromagnetic waves have different intensities along multiple directions.

This property is governed by the geometry of the oscillating voltage. Say if the oscillation takes place along the z-axis, then the electromagnetic waves released towards the x and y-axis would have maximum amplitude, and along the z-axis their amplitude will be zero. 

Everything else in between "parallel to oscillation" and "perpendicular to oscillation" will have some amplitude, not maxed nor nothing.

The viusal below might help you see this in 3D:

  <figure>
    <img src="em_radiation_3d.gif" alt="Oscillating voltage generates electromagnetic waves (3D).">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 13: Oscillating voltage generates eletromagnetic waves (3D).
    </figcaption>
  </figure>

There are 2 ways to understand this animation. 

First, since the intensity is max in directions perpendicular to oscillation, and is zero in the direction of oscillation, if we plot the points out with the coordinates (I, $\theta$, $\phi$), where I is the intensity value, and $\theta$ and $\phi$ are the two angles that the z-axis makes with x and y, we will get some kind of intensity mapping that looks like the donut formed in the end. This is called a radiation pattern.

Second, because electromagnetic waves can be absorbed and reflected by small particles in air when they travel through space, their amplitude decreases as function of distance travelled. So with that, you can also picture this animation as a way of showing the directions in which the electromagnetic waves can travel longer distances before their amplitude falls off.

Moving on, since we are pretty faimilar witht the circle by now, we might as well just use one to replace the oscillation above. This will get us something that looks like this:

  <figure>
    <img src="em_radiation_circle.gif" alt="Eletromagnetic waves generated by the circle.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 14: Eletromagnetic waves generated by the circle.
    </figcaption>
  </figure>

And... let us zoom in on some of these waves generated by the circle (region highlighted above), like we did for Figure 3. The waves along this direction shall have max intensity because they are perpendicular to oscillation.

  <figure>
    <img src="wave_from_circle.gif" alt="A zoomed-in view of eletromagnetic waves generated by the circle.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 15: A zoomed-in view of eletromagnetic waves generated by the circle.
    </figcaption>
  </figure>

Note what is shown here (on the right) is the actual electromagnetic wave within one unit of wavelength. It is not the sine function that we've been talking about in section 3, which is y-axis of the circle.

Now, what is going to happen if we speed up the voltage oscillation, like for 2x the speed?

  <figure>
    <img src="wave_from_circle_2x.gif" alt="A zoomed-in view of eletromagnetic waves generated by the circle (2x speed).">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 16: A zoomed-in view of eletromagnetic waves generated by the circle (2x speed).
    </figcaption>
  </figure>

Mmmm... It seems like the wavelength of the electromagnetic waves is cut in half. Interesting eh?

How about we supply less voltage during oscillation? 

  <figure>
    <img src="wave_from_circle_2x_halfA.gif" alt="A zoomed-in view of eletromagnetic waves generated by the circle (2x speed / half voltage)">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 17: A zoomed-in view of eletromagnetic waves generated by the circle (2x speed / half voltage).
    </figcaption>
  </figure>

Oh... the cirlce has become smaller, and the amplitude of the wave is decreased. 

The lower voltage has caused the strongest wave (along the perpendicular direction) to have an equivalent amplitude to those along the weaker directions.

With the poor starting momentum, this wave will not likely make it too far before its amplitude vanishes. In fact, they will offer no use to us well before they get to absolute zero amplitude.

This is because there exists a lot of signal noises in the environment. So whenever the waves' amplitude is lower than that of the noise, we will lose the ability to distinguish between them from the noise.

Hence, it is quite critical that we supply a strong electromagnetic wave to begin with.

## Section 5: Beam Forming

And... Amplitude enhancement can be done via beam forming.

Let us kick off this section with a 2D version of Figure 14 - under the context of beam forming, it will be easier if we visualize the radiation pattern this way.

  <figure>
    <img src="em_radiation_circle_2d.gif" alt="A 2D version of the oscillating voltage producing electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 18: A 2D version of the oscillating voltage producing electromagnetic waves.
    </figcaption>
  </figure>

Here we are looking into the donut from Figure 14 from the front direction (where the y-axis was) and are projecting the pattern on to the xz-plane. 

To make the electromagnetic waves stronger, one convenient way is to ultilize a reflective material to re-direct those in one direction towards the other. This way although in one direction we get no signals at all, the other direction gets more of it.

This can be illustrated as follows:

  <figure>
    <img src="reflector_2d.gif" alt="A reflector producing stronger electromagnetic waves in one direction.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 18: A reflector producing stronger electromagnetic waves in one direction.
    </figcaption>
  </figure>

Another way to increase the signal power further is to add more sources that emit electromagnetic waves, such as, another circle. 











