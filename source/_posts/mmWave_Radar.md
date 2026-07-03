---
title: FMCW mmWave Radar
date: 2026-06-06
mathjax: true
categories: [blog]
tags: [engineering]
---

Hey! I want to take you on a tour that explains FMCW (Frequency Modulated Continuous Wave) mmWave radars. We will first go back to high school physics and touch up our memory on electromagnetic waves, then talk about how we can use a circle to represent radar signals, and finish with the fundamentals of how to use the FMCW radar for object detection.

It is supposed to be fun. 

The ultimate goal is to answer, "What is FMCW mmWave radar?", and to build familiarity with this topic for anyone who wants to work with radar.

Bear with me, annnnnnnd, let's go!



## Section 1: Electromagnetic Waves

We will begin the blog with the light bulb, something we're all familiar with. 

When we flip a switch to turn on the light, what we are doing essentially is just closing the electric circuit for the light bulb. 

The power source creates a voltage that generates an electric field and drives electrons towards the bulb's filament. 

This causes the filament's atoms to vibrate and emit electromagnetic waves that light up the space.

  <figure>
    <img src="lightbulb.gif" alt="A light bulb emitting EM waves">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 1: A light bulb emitting electromagnetic waves to the surroundings.
    </figcaption>
  </figure>

The electromagnetic waves created this way have relatively high energy and short wave lengths $\lambda$ (380-760 nanometers), and we call them "visible lights".

Radar works very similarly. 

In radar, we also use a voltage to move electrons (which happens in the conductor). 

Instead of letting the electrons vibrate freely like the light bulb's filament (which generates random electromagnetic waves that are good enough for brightening the room but not good enough for analysis), we oscillate them back and forth in a specially shaped conductor called an antenna in an ordered manner to produce controlled waves. 

The electromagnetic waves produced this way have much longer $\lambda$, usually around 5 millimeters, so they are called mmWaves.

The animation below shows how these electromagnetic waves can be generated. Note how some of them appear darker. That is because the electromagnetic waves produced this way have lower intensity along some directions due to the geometry of the oscillation.

  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates electromagnetic waves.
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

At the end of the day, these mmWaves are essentially just the same matter as visible light, only more spread out (longer $\lambda$) and carry less energy (per photon). 

So whenever I think of mmWaves or electromagnetic waves, I just picture them in my head as visible light. Somehow, this mental model has made me feel more comfortable working around mmWave radars.

So far so good? This will wrap up everything for section 1. 

It's not too bad. Right? I will leave you with a fun fact below, then let's dive into section 2!

There are electromagnetic waves that have very very short $\lambda$, much shorter than visible lights, like the gamma ray (whose $\lambda$ is less than 0.01 nanometers). They carry high energy and can damage cells in the body. That is why the doctors use them as a "gamma knife" to treat cancers sometimes.



## Section 2: The Circle

In this chapter, our goal is to understand more about the circle -> because it is actually what we use to describe the event of voltage oscillation in radar, the process that produces those mmWaves. 

I will explain why the circle is used in the very end (section 7), but for now, let's focus on the fundamentals together. 

How about we start with my claim: there may be no such thing as a circle?

What!? This is such nonsense, you might wonder. You have understood the circle for so long (perhaps from kindergarten or middle school) and now there's a guy telling you there is no such thing as a circle. 

I totally get it. Let me explain. 

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

Let's look at the one on the left. The blue shaded one. What is the definition of the ratio between the slope (r) and the vertical side (y)? 

Ah, yes, you are right. We have learned this in middle school. It is defined by the sine function $\sin(\theta) = y/r$.

  <figure>
    <img src="triangle_only.png" alt="The blue shaded right-angled triangle alone.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 6: The blue shaded right-angled triangle alone.
    </figcaption>
  </figure>

If r is 1, say the circles we drew were unit circles, then y is just equal to sin($\theta$). And x is just cos($\theta$). 

Now, let's vary the angle $\theta$ from 0° to 90°. What do we get for x and y? 

  <figure>
    <img src="q1_quadrant.png" alt="Varying $\theta$ from 0 deg to 360 to draw a group of points using (x, y) coordinates.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 7: Varying $\theta$ from 0 deg to 90 to draw a group of points using (x, y) coordinates.
    </figcaption>
  </figure>

Indeed, we will get a group of points. Each point will have an x coordinate, and an y coordinate. With that, we can trace out these points on the xy plane.

As you might have observed, the points all land on the path of the circle's arc. 

And it is not hard to see that if $\theta$ is varied from 0° all the way to 360°, we will get a bunch of x and y's that eventually make up the whole circle. 

The fact that when $\theta$ becomes 360°, we will land on the origin again, gives the sine and cosine functions a very nice property to allow them to be used for describing periodic events (such as for the oscillating voltage that you have seen in Figure 2). 

But to use the circle for describing the event of voltage oscilation, there is one more thing missing. Time, because our event varies with time. 

Indeed, $\theta$ can be expressed as a function of time, which turns y into $\sin(\omega t)$, and x into $\cos(\omega t)$, where $\omega$ is the angular frequency (in rad/sec). (side note: since one circle is 2$\pi$, to relate $\omega$ with a frequency (f) in Hz (cycle/sec), we can do $\omega = 2\pi f$)

OK, so now we plot the x and y points as a function of time. What will that look like on the xy-plane? See this visual below. It's made with a slower frequency to help us follow the points more easily. 

  <figure>
    <img src="phasor_animation.gif" alt="(Right) Varying $\theta$ from 0 to 360° as a function of time, and (Left) drawing out the points on the xy plane.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 8: (Right) Varying $\theta$ from 0 to 360° as a function of time, and (Left) drawing out the points on the xy plane.
    </figcaption>
  </figure>

See how the x and y from the right-angled triangle trace out a nice circle on the left side in like 10 seconds? Also, note how $\theta$ is changing with time? Pretty cool, eh?

Now let's do something crazier. What if we extend the circle to a 3-dimensional space? Let's visualize this thing together with the third dimension, time. 

Here's the 3D representation in (time, x, y): 

  <figure>
    <img src="helix_3d.png" alt="Adding one more dimension (time) to visualize the circle.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 9: Adding one more dimension (time) to visualize the circle.
    </figcaption>
  </figure>

The circle became a helix. Now when $\theta$ becomes 360°, the point no longer lands on the origin, because time has elapsed. The same circle has essentially been expanded along the time axis. 

Interestingly, when we project the helix on the yt-plane, we will get our sine function back. And if we do that to the xt plane, we will get our cosine function back. 

So hopefully by this point you see what we have done here, is actually representing the helix using a coordinate of ($\sin(\omega t)$, $\cos(\omega t)$), just like how a point on a 2D plane can be defined by the coordinate (x, y). 

Indeed, this is written formally in math as 
$$
Z(t) = x(t) + j \cdot y(t)
$$
where Z is the helix, and the j is there in front of the y component to indicate that the y component is on a different plane. 

OK! Now that we've understood more about the circle, let's actually use it for our event! We will start all over from Figure 2 again, which shows how electromagnetic waves can be generated in the radar by oscillating voltage.

  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates electromagnetic waves.
    </figcaption>
  </figure>

For simplicity, let's assume the voltage in the animation oscillates from +10V to -10V, and completes every cycle in about 10 seconds. And instead of seeing all the electrical components from that figure, we will represent the oscillation using just a straight line.

  <figure>
    <img src="voltage_oscillation.gif" alt="Oscillating voltage represented on a straight line. ">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 10: Oscillating voltage represented on a straight line. 
    </figcaption>
  </figure>

Notice how the +10V and -10V can be normalized into a range from +Max to -Max? We can even describe these boundaries with +1 and -1.

In fact, if we do that, it will become quite obvious that the vertical line is just the y-axis of the unit circle, which is governed by $y(t) = \sin(\omega t)$, or more specifically in this case, $$\text{Voltage}(t) = \sin(\omega t)$$

Now to get to the full circle, we just need to add the second axis $x(t) = \cos(\omega t)$.

Let's visualize that same circle again from Figure 8 (left), but this time we will actually use it to represent our event of voltage oscillation. 

  <figure>
    <img src="circle_voltage.gif" alt="Circle relabeled.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 11: The same circle from Figure 8 but with y-axis relabeled as voltage. 
    </figcaption>
  </figure>

Ah, and there's one more thing, the convention in phasor analysis is that voltage is represented by the cosine term. 

So let's flip the axis on the circle and rotate it 90° to align with the convention. Now in the animation below, the vertical axis is governed by 

$$x(t) = \text{Voltage}(t) = \cos(\omega t)$$

and the horizontal axis then becomes

$$y(t) = \sin(\omega t)$$

  <figure>
    <img src="circle_voltage_flipped.gif" alt="The same circle from Figure 8 and 10 but voltage is represented by the cosine term instead.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 12: The same circle from Figure 8 and 11 but voltage is represented by the cosine term instead.
    </figcaption>
  </figure>

Do you feel more comfortable reading this animation now?

Here, I think you might ask, "Why bother using a circle if the event can be described simply with a straight line like Figure 10?".

There is actually a reason why we need that second coordinate that the circle brings, but as we mentioned earilier, let's save that till the very end where we'll be learning a lot more about radar.

This will wrap it up for section 2. Everything good?

Oh yeah, we didn't even find time to talk more about whether the circle exists. Maybe you can think more about that on your own. 

Do you believe that there is such thing as a circle, or is it just a bunch of points that follow the sine and cosine function and repeat in locations? (ps. this is actually the locus definition of a circle.)



## Section 3: Connecting the Circle with Electromagnetic Waves

Welcome to chapter 3. So far we have understood that mmWaves are electromagnetic waves generated by an oscillating voltage which can be described using a circle. 

We will now discuss more about the electromagnetic waves and their relation with the oscillating voltage. Our goal for this section is to understand the system in greater depth. 

Let's have another look at our friend, Figure 2:

  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates electromagnetic waves.
    </figcaption>
  </figure>

In section 1, we briefly talked about how these electromagnetic waves have different intensities along multiple directions.

This property is governed by the geometry of the oscillating voltage. Say if the oscillation takes place along the z-axis, then the waves released towards the x and y-axis would have maximum amplitude, and along the z-axis their amplitude will be zero. 

The visual below might help you see this in 3D:

  <figure>
    <img src="em_radiation_3d.gif" alt="Oscillating voltage generates electromagnetic waves (3D).">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 13: Oscillating voltage generates electromagnetic waves (3D).
    </figcaption>
  </figure>

There are 2 ways to understand this animation. 

First, since the intensity is max in directions perpendicular to oscillation, and is zero in the direction of oscillation, if we plot the points out with the coordinates (I, $\theta$, $\phi$), where I is the intensity value, and $\theta$ and $\phi$ are the two angles that the z-axis makes with x and y, we will get some kind of intensity mapping that looks like the donut formed in the end. This is called a radiation pattern.

Second, because electromagnetic waves can be absorbed and reflected by small particles in air when they travel through space, their amplitude decreases as function of distance travelled. So with that, you can also picture this animation as a way of showing the directions in which the electromagnetic waves can travel longer distances before their amplitude falls off.

Moving on, since we are pretty familiar with the circle by now, we might as well just use one to replace the oscillation above. This will get us something that looks like this:

  <figure>
    <img src="em_radiation_circle.gif" alt="Electromagnetic waves generated by the circle.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 14: Electromagnetic waves generated by the circle.
    </figcaption>
  </figure>

And... let us zoom in on some of these waves generated by the circle (region highlighted above), like we did for Figure 3. The waves along this direction shall have max intensity because they are perpendicular to oscillation.

  <figure>
    <img src="wave_from_circle.gif" alt="A zoomed-in view of electromagnetic waves generated by the circle.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 15: A zoomed-in view of electromagnetic waves generated by the circle.
    </figcaption>
  </figure>

Note what is shown here (on the right) is the actual electromagnetic wave within one unit of wavelength. It is not the sine function that we've been talking about in section 3, which is y-axis of the circle (or the x-axis after being flipped).

Now, what is going to happen if we speed up the voltage oscillation, like for 2x the speed?

  <figure>
    <img src="wave_from_circle_2x.gif" alt="A zoomed-in view of electromagnetic waves generated by the circle (2x speed).">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 16: A zoomed-in view of electromagnetic waves generated by the circle (2x speed).
    </figcaption>
  </figure>

Mmmm... It seems like the wavelength of the electromagnetic waves is cut in half. Interesting eh?

How about we supply less voltage during oscillation? 

  <figure>
    <img src="wave_from_circle_2x_halfA.gif" alt="A zoomed-in view of electromagnetic waves generated by the circle (2x speed / half voltage)">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 17: A zoomed-in view of electromagnetic waves generated by the circle (2x speed / half voltage).
    </figcaption>
  </figure>

Oh... the circle has become smaller, and the amplitude of the wave is decreased. 

The lower voltage has caused the strongest wave (along the perpendicular direction) to have an equivalent amplitude to those along the weaker directions.

With the poor starting momentum, this wave will not likely make it too far before its amplitude vanishes. In fact, they will offer no use to us well before they get to absolute zero amplitude.

This is because there exists a lot of signal noises in the environment. So whenever the waves' amplitude is lower than that of the noise, we will lose the ability to distinguish between them from the noise.

Hence, it is quite critical that we supply a strong electromagnetic wave to begin with.



## Section 4: Beam Forming

And... Amplitude enhancement can be done via beam forming.

Let us kick off this section with a 2D version of Figure 14.

  <figure>
    <img src="em_radiation_circle_2d.gif" alt="A 2D version of the oscillating voltage producing electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 18: A 2D version of the oscillating voltage producing electromagnetic waves.
    </figcaption>
  </figure>

Here we are looking into the donut from Figure 14 from the front side (where the y-axis was) and we project the pattern on to the xz-plane. 

To make these electromagnetic waves stronger, one convenient way is to utilize a reflector. 

A reflector is made up by a reflective material, such as metals, to re-direct the waves in one direction into the other, hence adding up the amplitudes.

This way although in one direction we get no signals, we get more of it in the other.

  <figure>
    <img src="reflector_2d.gif" alt="Producing stronger electromagnetic waves with the help of a reflector.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 19: Producing stronger electromagnetic waves with the help of a reflector.
    </figcaption>
  </figure>

With this setup, the reflector has to be placed at a specific distance from the circle, so that the reflected waves are re-directed in a way that they travel in-phase with the original waves in that direction. 

This means the re-directed waves should have no phase shift when compared to the other direction.

Mathematically the add-up of amplitude can be expressed as: 

$$A_{\text{total}} = \sum_{i=1}^{N} A_i$$

where N is the number of waves in-phase.

Now, if a reflector can be used to add up the waves' amplitudes, it's likely not too hard to imagine that another signal source can probably do that too.

In fact, if we add another voltage oscillation beside the one we already have, in a way that the emitted electromagnetic waves become in-phase with the original ones, the signal can be further enhanced. See here for a demonstration.

  <figure>
    <img src="two_circles_wave.gif" alt="Electromagnetic waves added up from two voltage oscillations">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 20: Electromagnetic waves added up from two voltage oscillations.
    </figcaption>
  </figure>

If we now zoom out from the specific waves and look at the whole thing on a more macro level, we will see the radiation pattern of the electromagnetic waves changes to something like this.

  <figure>
    <img src="two_sources_pattern.gif" alt="Producing stronger electromagnetic waves with an additional oscillation.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 21: Producing stronger electromagnetic waves with an additional oscillation.
    </figcaption>
  </figure>

The "blobs" that you see in this demonstration are called "lobes". There are 3 of them in there. One main lobe, and two small ones located on the side with less intensity.

With the reflector and the additional signal source, our electromagnetic waves have gotten much stronger along some directions. 

Let's start using this long beam to sense our surroundings. We'll see this in the xy plane. (here we're looking down from the top of the z-axis)

  <figure>
    <img src="two_sources_pattern_rotating.gif" alt="A rotating radar shooting out a long beam to sense the surroundings.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 22: A rotating radar shooting out a long beam to sense the surroundings.
    </figcaption>
  </figure>

And at this point, I think we are ready to replace our mental model for the radar with one that resembles the lighthouse, where a beam of visible light gets emitted all around to see things in the dark. 

  <figure>
    <img src="lighthouse.gif" alt="A lighthouse shooting a beam of light to the surroundings.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 23: A lighthouse shooting a beam of light to the surroundings.
    </figcaption>
  </figure>

This is the end of section 4. I hope the lighthouse model will make you feel even more comfortable working with the radar!



## Section 5: Radar Sensing

Welcome to section 5. In this chapter, we are going to talk more about actually using the radar to detect things.

Let's pull up Figure 22 again, but this time, we are going to place an object in the field to be detected. The location of it is highlighted by the white rectangle.

  <figure>
    <img src="two_sources_pattern_target.gif" alt="A rotating radar detecting objects in the surroundings.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 24: A rotating radar detecting objects in the surroundings.
    </figcaption>
  </figure>

See how the object reflects electromagnetic waves back to the radar? 

This is awesome because now whenever we receive any waves back at the radar, we can look at its rotational angle $\theta$ at the moment to tell the direction of the object.

Now, let's also see how this works on a micro level. The white rectangle on the right is the object that reflects.

  <figure>
    <img src="wave_reflection.gif" alt="Electromagnetic waves reflected at the object.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 25: Electromagnetic waves reflected at the object.
    </figcaption>
  </figure>

From this animation, we can see the reflected waves have a similar frequency with the original ones, just flipped by 180° (or one $\pi$). 

This is the case when the object is stationary.

What's gonna happen if the object starts moving? Let's see that in action too!

  <figure>
    <img src="wave_doppler.gif" alt="Electromagnetic waves reflected by moving object.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 26: Electromagnetic waves reflected by moving object.
    </figcaption>
  </figure>

Here we have one object (top) moving towards the radar at a velocity v, and another one (bottom) moving away from the radar at the same speed. 

Notice how the reflected waves come back to the radar with a different $\lambda$ and frequency?

This is called the Doppler effect.

Indeed, the frequency shift due to Doppler is governed by the relationship 

$$f_d = \frac{2v}{\lambda}$$

Here an animation is provided to help you visualize the Doppler shifts. Note the bottom object moving at 2x the speed creates more Doppler shift than the top one.

  <figure>
    <img src="wave_doppler_2v.gif" alt="Electromagnetic waves reflected by objects moving at different speeds.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 27: Electromagnetic waves reflected by objects moving at different speeds.
    </figcaption>
  </figure>

OK! So far we have shown that both the direction and speed of the object can be determined via the rotating radar beam (lighthouse model).

Can we figure out the distance of the object as well? Like, that seems critical too, right? (ps. this distance in radar terminology is called the "range" of an object and is denoted by the letter R)

Recall in section 2, we said the oscillation signal can be described as 

$$\text{Voltage}(t) = \cos(\omega t)$$

Let's have a look at Figure 25 again, which shows the transmitted and reflected electromagnetic waves.

  <figure>
    <img src="wave_reflection.gif" alt="Electromagnetic waves reflected at the object.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 25: Electromagnetic waves reflected at the object.
    </figcaption>
  </figure>

Here the orange wave is generated by the voltage oscillation and can be described by the representation below

$$V_{\text{Tx}}(t) = \cos(\omega t)$$

here Tx stands for "Transmitted".

As the wave travels to the object located at the right, our signal becomes 

$$V_{\text{Intermediate}}(t) = \cos(\omega(t-\frac{1}{2}\tau))$$ 

where $\frac{1}{2}\tau$ is the time it takes to get there (full $\tau$ stands for the round trip). 

At the point of reflection, the electromagnetic waves hit the object and flip 180° (or one $\pi$) in phase due to the flipping electric field, becoming

$$V_{\text{Intermediate}}(t) = \cos(\omega(t-\frac{1}{2}\tau) - \pi)$$

And when they finally make it back to the radar, we will have

$$V_{\text{Rx}}(t) = \cos(\omega(t-\tau) - \pi)$$

where Rx stands for "Received".

We will visualize all of these in 3D. 

  <figure>
    <img src="wave_reflection_3d.gif" alt="An 3D demonstration of the electromagnetic wave reflection.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 28: An 3D demonstration of the electromagnetic wave reflection.
    </figcaption>
  </figure>

Now, the question becomes, given the final received signal 
$$V_{\text{Rx}}(t) = \cos(\omega(t-\tau) - \pi)$$ 

can we find the range R between the object and the radar? (ps. the formula to convert $\tau$ to R is $R=2c\tau$, where c is the speed of light. Remember light is just one kind of electromagnetic wave?)

This can be tricky. Let me explain.

In that equation above, we know the angular frequency $\omega$ from the voltage oscillation (plus any Doppler effect if exists), and t is the time when we measure that signal so it is also known.

When we receive the returning electromagnetic waves, we will flip it into a voltage signal V(t) using its electric field, so $V_{\text{Rx}}(t)$ should also be known.

While it seems like everything is known here, there are actually two problems. 

First, the returned signal, $V_{\text{Rx}}(t)$, has a very high frequency (in the range of GHz), which means the oscillation completes a cycle every 0.01 to 0.1 nanoseconds (calculated by 1/f). 

This is like $10^{10}$ cycles per second or more. It is so fast that even our sampling device can't keep up with it. (ps. According to the Nyquist-Shannon Sampling Theorem, the sampler will need to fire at least 2x quicker than this frequency to ensure the received signal is reliably measured.)

So, in fact, $V_{\text{Rx}}(t)$ cannot be measured.

Second, even if $V_{\text{Rx}}(t)$ can be measured, we still can't really find $\tau$ because the phase term $\theta(t) = \omega(t-\tau) - \pi$ inside the cosine function wraps around every $2\pi$, meaning the value of the function repeats mathematically every $2\pi$ (or physically with the electromagnetic waves, this is every one half $\lambda$).

Given this property, when we solve for R, we will actually an infinite number of solutions. These ranges are spaced out by $\frac{1}{2}\lambda$ and there is no way for us to determine which location is the correct one.

But don't worry, we can apply an engineering trick to address these two issues at once. And that is frequency modulation (hence the name "frequency modulated continuous wave (FMCW) mmWave radar") plus the use of a signal mixer. These will be explained in the section below.



## Section 6: Frequency Modulated Continuous Wave

In a frequency modulated radar, we linearly increase the frequency of the transmitted electromagnetic waves in a window called chirp. (for example, from 77GHz to 81GHz)

When one chirp ends, we stop for a bit, and then we start another one, and we repeat this process over and over again. (ps. the reason why this window is called a chirp is because the linear increase of frequency (if heard as audio) would make it sound like a sharp and rapid pitch that is similar to a bird or cricket chirp.)

We will see a visualization of it here. 

  <figure>
    <img src="wave_from_circle_chirp.gif" alt="Frequency modulation within one chirp.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 29: Frequency modulation within one chirp.
    </figcaption>
  </figure>

Notice how the speed of the cycle keeps increasing?

The frequency actually follows this relationship in a FMCW radar $$\omega(t) = \omega_0 + \alpha t$$ where $\omega_0$ is the starting frequency and $\alpha$ is the rate of change. 

Since the frequency is varying, the phase term inside the sine function can no longer be computed as simply as $\theta(t) = \omega t$.

We will have to use calculus here to find the phase term with $$\theta(t) = \int_{0}^{T} \omega(t) \ dt$$ (just like how we use calculus to find the distance traveled by a falling object due to its changing velocity).

Solving that integral will give us the following equation (for the phase term)
$$\theta(t) = \omega_0 t + \frac{1}{2}\alpha t^2$$

With that phase term, we can now reprsent our transmitted signal with this equation
$$V_{\text{Tx}}(t) = \cos\left(\omega_0 t + \frac{1}{2}\alpha t^2\right)$$

Similar to the last section, when the waves get to the object, we consider a time delay $\frac{1}{2}\tau$, changing the representation to
$$V_{\text{Intermediate}}(t) = \cos\left(\omega_0 \left(t - \frac{\tau}{2}\right) + \frac{1}{2}\alpha \left(t - \frac{\tau}{2}\right)^2\right)$$

at the point of reflection, we add a 180° shift
$$V_{\text{Intermediate}}(t) = \cos\left(\omega_0 \left(t - \frac{\tau}{2}\right) + \frac{1}{2}\alpha \left(t - \frac{\tau}{2}\right)^2 - \pi\right)$$

finally when the waves make it back to the radar, we will have
$$V_{\text{Rx}}(t) = cos\left(\omega_0 (t - \tau) + \frac{1}{2}\alpha (t - \tau)^2 - \pi\right)$$

and if we expand the terms from the equation above, we'll get this pretty fancy expression for the returned signal
$$V_{\text{Rx}}(t) = \cos\left(\omega_0 t - \omega_0 \tau + \frac{1}{2}\alpha t^2 - \alpha \tau t + \frac{1}{2}\alpha \tau^2 - \pi\right)$$

with some groupings, we can simplify that down to two time terms (one quadratic and one linear) plus one phase shift term like this

$$V_{\text{Rx}}(t) = \cos\left(\frac{1}{2}\alpha t^2 + (\omega_0 - \alpha \tau)t - \left(\omega_0 \tau - \frac{1}{2}\alpha \tau^2 + \pi\right)\right)$$

Great. 

From here, we will ultilize the signal mixer, which, mathematically speaking, multiplies the transmitted signal above

$$V_{\text{Tx}}(t) = \cos\left(\omega_0 t + \frac{1}{2}\alpha t^2\right)$$

with the returned signal above

$$V_{\text{Rx}}(t) = \cos\left(\frac{1}{2}\alpha t^2 + (\omega_0 - \alpha \tau)t - \left(\omega_0 \tau - \frac{1}{2}\alpha \tau^2 + \pi\right)\right)$$

and according to the product-to-sum relationship for the cosine function

$$\cos(A)\cos(B) = \frac{1}{2}\cos(A - B) + \frac{1}{2}\cos(A + B)$$

we should get a delta term 

$$\frac{1}{2}\cos(\theta_{\text{Tx}} - \theta_{\text{Rx}})$$

and a sum term 

$$\frac{1}{2}\cos(\theta_{\text{Tx}} + \theta_{\text{Rx}})$$

Once these two signals are obtained, we apply a low-pass filter to acquire the delta term and we throw away the sum. 

This delta term is what we called the beat signal, which has a much slower frequency than the original signals because the reflected waves aren't too different than the transmitted waves (even with Doppler), so the delta they produce is not significant, which makes it much more sampler-friendly.

Now, with the beat signal 

$$V_{\text{beat}}(t) = \frac{1}{2}\cos(\theta_{\text{tx}} - \theta_{\text{rx}})$$

we will put the phase terms inside for both transmitted and received to get this very long equation here

$$V_{\text{beat}}(t) = \frac{1}{2}\cos(\left(\omega_0 t + \frac{1}{2}\alpha t^2\right) - \left(\omega_0 t - \omega_0 \tau + \frac{1}{2}\alpha t^2 - \alpha \tau t + \frac{1}{2}\alpha \tau^2 - \pi\right))$$

let's then open up all the brackets and do some groupings to get this expression below for the beat signal

$$V_{\text{beat}}(t) = \frac{1}{2}\cos\left(\alpha \tau t + \omega_0 \tau - \frac{1}{2}\alpha \tau^2 + \pi\right)$$

Notice how, unlike the unmodulated radar, there is only one linear time term $\alpha \tau t$ here?

This is very nice because it allows us to simply express the equation as

$$V_{\text{beat}}(t) = \frac{1}{2}\cos\left(\omega_b t + \phi\right)$$

where $\alpha \tau$ becomes the angular frequency for the beat signal $\omega_b$ and $\omega_0 \tau - \frac{1}{2}\alpha \tau^2 + \pi$ now becomes the phase shift $\phi$. (ps. the term $\frac{1}{2}\alpha \tau^2$ is very small because of $\tau^2$ and so it is often ignored).

From here it becomes quite clear that, since we can measure the beat signal $V_{\text{beat}}(t)$, we can look for the angular beat frequency $\omega_b$ by counting how fast its cycles are completing or using FFT (Fast Fourier Transform) to transform the signal from time domain to frequency domain. And once we have $\omega_b$, we can directly solve for $\tau$ and range. 

But we have one more problem here which we'll need to address first! (I know, we keep having problems, but trust me, this is the last one we have, at least for what I know, it is the last one. 😂) 

And to incentify you a bit, this issue actually answers the question we had from section 2 - "Why use a full circle to represent radar signals instead of just a verticle line?"

Anyway, the problem is that the cosine function has a phase ambiguity because 

$$\cos(\theta) = \cos(-\theta)$$

So it is important to determine the sign of the phase term $\omega_b t + \phi$ for the signal as we record $V_{\text{beat}}(t)$.

And this is done by utilizing the second coordinate that the circle brings, which provides the sine function below

$$y(t) = \sin(\omega t)$$

which becomes something like this in a frequency modulated radar

$$y(t) = \sin\left(\omega_0 t + \frac{1}{2}\alpha t^2\right)$$

In reality, this y component is created by manipulating the transmitted signal (in cosine form) with a 90° shift via a device called a shifter. Mathematically, this can be described as:

$$\cos\left(\theta_{\text{Tx}}(t)\right) \xrightarrow{+90^\circ} \sin\left(\theta_{\text{Tx}}(t)\right)$$

In radar analysis, the manipulated component y(t), is called the Quadrature signal, denoted by the symbol $Q(t)$, while the original transmitted signal is called the In-Phase signal, denoted by I(t).

Here, let's match that convention and rewrite what we have on hands for the transmitted signal as:

$$I(t) = \cos\left(\omega_0 t + \frac{1}{2}\alpha t^2\right)$$
$$Q(t) = \sin\left(\omega_0 t + \frac{1}{2}\alpha t^2\right)$$

And this time if we take the Quadrature signal instead of the In-Phase signal, and mix it with the returned signal from above

$$V_{\text{Rx}}(t) = \cos\left(\frac{1}{2}\alpha t^2 + (\omega_0 - \alpha \tau)t - \left(\omega_0 \tau - \frac{1}{2}\alpha \tau^2 + \pi\right)\right)$$

according to the product-to-sum relationship 

$$\sin(A)\cos(B) = \frac{1}{2}\sin(A - B) + \frac{1}{2}\sin(A + B)$$

we will get the delta term in its sine form

$$\frac{1}{2}\sin(\theta_{\text{tx}} - \theta_{\text{rx}})$$

with which, if we plug in all the phase terms and simplify it a bit (just like what we did above), will become

$$V_{\text{beat}}(t) = \frac{1}{2}\sin\left(\omega_b t + \phi\right)$$

or we can call it

$$Q_{\text{beat}}(t) = \frac{1}{2}\sin\left(\omega_b t + \phi\right)$$

Now solving this together with the In-Phase beat signal from above

$$I_{\text{beat}}(t) = V_{\text{beat}}(t) = \frac{1}{2}\cos\left(\omega_b t + \phi\right)$$

we can guarantee the sign of the phase term for the beat signal $V_{\text{beat}}(t)$.

And from there, we will find the beat frequency $\omega_b$, as well as $\tau$ and R.

So this is it. As I promised, that really was the last problem I knew. Let's kill the post from here.😁



## Section 7: The End

Oh don't worry, this is not extra information. I am just here to conclude.

Radar is actually a hugeeeeee topic. The more I learn about it, the more I know that there are more that I don't know about it. 

I started to dig into this field when I begun working with radar data for my CS project. And to date, my conclusion is that, you will probably really need a PhD to master using radar.

Although for computer scientists, potentially, we could just treat the data as given and not pay too much attention into understanding the radar basics, I do feel that this is essential, especially for ensuring responsible and high-quality data collection, which I argued in the other post (AI Hierarchy - What is really important), is paradigm for deep learning.

Anyway, I hope you enjoyed the post. This one is very long and much longer than usual. During the beginning of this post, I thought I would be done in a few days. Boy, I was wrong. Radar, Radar, Radarrrrrrrr.


## Acknowledgement

I would like to thank my colleague Dr. Mihail Georgiev for validating my understanding in radar and much of what I wrote in this blog. Thank you Mihail for the advice and the discussions. Honestly, writing this post wouldn't have been possible without you.