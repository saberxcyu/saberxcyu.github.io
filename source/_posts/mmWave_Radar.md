---
title: FMCW mmWave Radar
date: 2026-06-06
mathjax: true
categories: [blog]
tags: [engineering]
---

Hey! I want to take you on a tour that explains FMCW (Frequency Modulated Continuous Wave) mmWave radars. We will first go back to high school physics and touch up our memory on electromagnetic waves, then talk about how we can use a circle to represent radar signals and go over some very fundamental stuffs for the radar.

It is supposed to be fun. 

The ultimate goal is to answer "what is FMCW mmWave radar" and to build familiarity around this topic for anyone who works with radar data.

Bear with me, annnnnnnd, let's go!



## Section 1: Electromagnetic Waves

We will begin the blog with the light bulb, something we're all familiar with. 

When we flip a switch to turn on the light, what we are doing essentially is just closing the electric circuit for the light bulb. 

The power source creates a voltage that generates an electric field and drives electrons towards the bulb's filament. 

This causes the filament's atoms to vibrate and release electromagnetic waves that light up the space.

  <figure>
    <img src="lightbulb.gif" alt="A light bulb emitting EM waves">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 1: A light bulb emitting electromagnetic waves to the surroundings.
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

At the end of the day, these mmWaves are essentially just the same matter as visible lights, only more spread out (longer $\lambda$) and carry less energy. 

So whenever I think of mmWaves or electromagnetic waves, I just picture them in my head as visible lights. Somehow, this mental model has made me feel more comfortable working around mmWave radars.

So far so good? This will wrap up everything for section 1. 

It's not too bad. Right? I will leave you with a fun fact below, then let's dive into section 2!

Fun fact: there are electromagnetic waves that have very very short $\lambda$, much shorter than visible lights, like the gamma ray (whose $\lambda$ is less than 0.01 nano meters). They carry high energy and can damage our cells in the body. That is why the doctors use them as a "gamma knife" to treat cancers sometimes.



## Section 2: The Basics of a Circle

In this chapter, our goal is to understand more about the circle -> because it is actually what we use to describe the event of voltage oscillation in the radar, the process which produces those mmWaves. 

I will explain why the circle is used in section 3, for now, let's just focus on the fundamentals together. 

How about we start with my claim: there maybe no such thing as a circle. 

What!? This is such non-sense. You might wonder. You have understood the circle for so long (perhaps from Kindergarten or middle school) and now there's a guy telling you there is no such thing as a circle. 

I totally get it. Let me explain. 

Also, this blog should be written in a way that makes it totally up to you whether you decide if the circle exists.

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

If r is 1, say the circles we draw were unit circles, then y is just equal to sin($\theta$). And x is just cos($\theta$). 

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

Now let's do something crazier. What if we extend the circle to a 3-dimensional space? Let's visualize this thing together with one more dimension, time. 

Here's the 3D representation in (time, x, y): 

  <figure>
    <img src="helix_3d.png" alt="Adding one more dimension (time) to visualize the circle.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 9: Adding one more dimension (time) to visualize the circle.
    </figcaption>
  </figure>

The circle became a spiral. Now when $\theta$ becomes 360°, the point does not land on the origin anymore, because time has lapsed. The same circle has essentially been expanded along the time axis. 

Interestingly, when we project the spiral on the yt plane, we will get our sine function back. And if we do that to the xt plane, we will get our cosine function back. 

So hopefully by this point you see what we have done here, is actually just representing the spiral using a coordinate of ($\sin(\omega t)$,$\cos(\omega t)$), just like how a point on a 2D plane can be defined by a coordinate of (x, y). 

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

One property of the circle, which we kinda mentioned above, is that it repeats itself every 360°, so you can see already that there is some kind of a sign there for periodicity. This however is not the only way to represent periodic events. 

Let's have a look at Figure 2 again from above which shows how electromagnetic waves can be generated in the radar by oscillating the voltage up and down.

  <figure>
    <img src="em_radiation.gif" alt="Oscillating voltage generates electromagnetic waves.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Oscillating voltage generates electromagnetic waves.
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

That means this equation alone already perfectly describes the event of an oscillating voltage. (it surely does)

But what if the signal has a phase shift that makes it look something like this?

Voltage(t) = $\sin(\omega(t-\tau))$, where $\tau$ stands for a time delay. (and $\\omega \tau$ is called the phase shift)

In fact, this equation shows exactly what we will get, when the transmitted electromagnetic waves are later on received back at the radar. 

But now there is a problem.

Given V, $\omega$, and t, can you solve for $\tau$? 

Indeed, if you attempt to solve for $\tau$, you will notice the sine function produces two results that are both mathematically correct. 

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
      Figure 2: Oscillating voltage generates electromagnetic waves.
    </figcaption>
  </figure>

In section 1, we briefly talked about how these electromagnetic waves have different intensities along multiple directions.

This property is governed by the geometry of the oscillating voltage. Say if the oscillation takes place along the z-axis, then the electromagnetic waves released towards the x and y-axis would have maximum amplitude, and along the z-axis their amplitude will be zero. 

Everything else in between "parallel to oscillation" and "perpendicular to oscillation" will have some amplitude, not maxed nor nothing.

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

Note what is shown here (on the right) is the actual electromagnetic wave within one unit of wavelength. It is not the sine function that we've been talking about in section 3, which is y-axis of the circle.

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



## Section 5: Beam Forming

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

A reflector is made up of a reflective material, such as metals, to re-direct the waves in one direction into the other, hence adding up the amplitudes.

This way although in one direction we get no signals, we get more of it in the other.

  <figure>
    <img src="reflector_2d.gif" alt="Producing stronger electromagnetic waves with the help of a reflector.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 19: Producing stronger electromagnetic waves with the help of a reflector.
    </figcaption>
  </figure>

With this setup, the reflector has to be placed at a specific distance from the circle, so that the reflected waves are re-directed in a way that they travel in-phase with the original waves in that direction. 

This means the re-directed waves should have no phase shift (no time delay $\tau$) when compared to the other direction.

Mathematically the add-up of amplitude can be expressed as: 

$$A_{\text{total}} = \sum_{i=1}^{N} A_i$$

, where N is the number of waves in-phase.

And if a reflector can be used to add up the waves' amplitudes, it's likely not too hard to imagine that another signal source can probably do a similar trick.

In fact, if we add another voltage oscillation beside the one we already have, in a way that the emitted electromagnetic waves become in-phase with the original ones, the signal can be further enhanced. See here for a demonstration.

  <figure>
    <img src="two_circles_waves.gif" alt="Electromagnetic waves added up from two voltage oscillations">
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

Let's start using this long beam to sense our surroundings. We'll see this in the xy plane. (as we're looking down from the top of the z-axis)

  <figure>
    <img src="two_sources_pattern_rotating.gif" alt="A rotating radar shooting out a long beam to sense the surroundings.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 22: A rotating radar shooting out a long beam to sense the surroundings.
    </figcaption>
  </figure>

And at this point, I think we are ready to replace our mental model for the radar with one that resembles the lighthouse, where a beam of visible lights gets emitted all around to see things in the dark. 

  <figure>
    <img src="lighthouse.gif" alt="A lighthouse shooting a beam of light to the surroundings.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 23: A lighthouse shooting a beam of light to the surroundings.
    </figcaption>
  </figure>

This is the end of section 5. I hope the lighthouse model will make you feel even more comfortable working with the radar!



## Section 6: Radar Sensing

Welcome to section 6. In this chapter, we are going to talk more about actually using the radar to detect things.

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

This is the case only when the object is stationary.

What's gonna happen if the object starts moving?

Let's see that in action!

  <figure>
    <img src="wave_doppler.gif" alt="Electromagnetic waves reflected by moving object.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 26: Electromagnetic waves reflected by moving object.
    </figcaption>
  </figure>

Here we have one object moving towards the radar at a velocity v (top), and another moving away from the radar at the same speed (bottom). 

Notice how the reflected waves come back to the radar with a different frequency?

This is called the Doppler effect.

Indeed, the frequency shift due to Doppler is governed by the relationship $$f_d = \frac{2v}{\lambda}$$

Here an animation is provided to help you visualize the Doppler shifts. Note the two objects are moving at different speeds.

  <figure>
    <img src="wave_doppler_2v.gif" alt="Electromagnetic waves reflected by objects moving at different speeds.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 27: Electromagnetic waves reflected by objects moving at different speeds.
    </figcaption>
  </figure>

OK! So far we have shown that both the direction and speed of the object can be determined via the rotating beam (lighthouse model).

Can we figure out the distance of the object as well? Like, that seems pretty important too, right? (this distance in radar terminology is called the "range" of an object and is denoted by the letter R)

Let's reveal that by putting our situation into math.

Recall in section 3, we said the oscillation signal can be described as $$\text{Voltage}(t) = \sin(\omega(t-\tau))$$ and how when there is a time delay $\tau$, the signal becomes $$\sin(\omega(t-\tau))$$

  <figure>
    <img src="wave_reflection.gif" alt="Electromagnetic waves reflected at the object.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 25: Electromagnetic waves reflected at the object.
    </figcaption>
  </figure>

If we look at the orange transmitted wave again from Figure 25 above, it is produced by the circle and can be represented by the signal $\sin(\omega t)$.

When it arrives at the object, it becomes $$\sin(\omega(t-\frac{1}{2}\tau))$$ where half $\tau$ is the time it takes to get to the object (and full $\tau$ defines the round trip). 

At the point of reflection, the electromagnetic waves hit the object and flip 180° (or one $\pi$) in phase due to the flipping electric field, changing the representation to $$\sin(\omega(t-\frac{1}{2}\tau) - \pi)$$

And when those waves finally make it back to the radar, they become $$\sin(\omega(t-\tau) - \pi)$$

You might also recall from section 3, that there should be a cosine component as well to rule out the ambiguity from using just the sine function. 

Let's visualize all of these in 3D. 

  <figure>
    <img src="wave_reflection_3d.gif" alt="An 3D demonstration of the electromagnetic wave reflection.">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 28: An 3D demonstration of the electromagnetic wave reflection.
    </figcaption>
  </figure>

Now, the question becomes, given the final signal $$V(t) = \sin(\omega(t-\tau) - \pi)$$ can we find the range R between the object and the radar? ps. the formula to convert $\tau$ to R is $R=2c\tau$, where c is the speed of light. Remember light is just one kind of electromagnetic wave?

This can be tricky. Let me explain.

In that equation above, we know the angular frequency $\omega$ from the voltage oscillation (plus any Doppler effect if exists), and t is the time when we measure that signal so it is also known.

When we receive the returning electromagnetic waves, we will flip it into a voltage signal V(t) using its electric field. Assuming we can measure that as well, V will also be known.

It really seems like everything is known here.

But there's a problem.

We still can't really find $\tau$ because the phase term inside the sine function wraps every $2\pi$, meaning the value of the function repeats mathematically every $2\pi$ (or physically with the electromagnetic waves, this is every one half $\lambda$).

This is true even with the help of the cosine coordinate because the cosine function only helps to rule out the ambiguity within one $2\pi$.

Given this property, when we solve for R, we will actually get multiple possible locations for the object. These solutions are spaced out by $\frac{1}{2}\lambda$ and there is an infinite amount of them. So there is no way for us to determine which location is the correct one.

But don't worry, we can apply an engineering trick to help address this issue. And that is frequency modulation (hence the name "frequency modulated continuous wave (FMCW) mmWave radar").



## Section 7: Frequency Modulated Continuous Wave

In a frequency modulated radar, we linearly increase the frequency of the transmitted electromagnetic waves in a window called chirp. (for example, from 77GHz to 81GHz)

When one chirp ends, we stop for a bit, and then we start another chirp, and we repeat this process over and over again. 

We will see a visualization of it here. ps. the reason why this window is called a chirp is because the linear increase of frequency (if heard as audio) would make the window sound like a sharp and rapid pitch that is similar to a bird or cricket chirp.

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

And with that, we can reprsent our transmitted signal using
$$V(t) = \sin\left(\omega_0 t + \frac{1}{2}\alpha t^2\right)$$

Similar to the last section, when the waves get to the object, we consider a time delay $\tau$, changing the representation to
$$\sin\left(\omega_0 \left(t - \frac{\tau}{2}\right) + \frac{1}{2}\alpha \left(t - \frac{\tau}{2}\right)^2\right)$$

at the point of reflection, we add a 180° shift
$$\sin\left(\omega_0 \left(t - \frac{\tau}{2}\right) + \frac{1}{2}\alpha \left(t - \frac{\tau}{2}\right)^2 - \pi\right)$$

finally when the waves make it back to the radar
$$\sin\left(\omega_0 (t - \tau) + \frac{1}{2}\alpha (t - \tau)^2 - \pi\right)$$

and if we expand the terms from the equation above, we'll get this pretty fancy expression that looks like this
$$V(t) = \sin\left(\omega_0 t - \omega_0 \tau + \frac{1}{2}\alpha t^2 - \alpha \tau t + \frac{1}{2}\alpha \tau^2 - \pi\right)$$

I am going to skip all that math here 😉, but hopefully this big chunk of expression is complicated enough to convince you, that if you solve for $\tau$ here, you will get a precise solution (one solution) for $\tau$, which then will allow you to find an unique R. 

BUT!

There is one more problem!

(I know, we keep having problems, but trust me, this is the last one, at least for what I know it is the last one 😂)

Annnnnnd... our last issue is that the solution we've explained above, is all based on the assumption we made in section 6, that the returned signal, Voltage(t), of the received electromagnetic waves, can be measured. 

In fact, when we work with these radars, the returned signal is often within the range of some GHz, which means, the oscillation completes a cycle every 0.01 to 0.1 nano seconds (calculated by 1/f). 

This is like $10^{10}$ cycles per second.

It is actually happening so fast that even our sampling device can't keep up with it. ps.According to the Nyquist-Shannon Sampling Theorem, the sampler will need to fire at least 2x quicker than this frequency to ensure the received signal is reliably measured.

So, in fact, V(t) actually stays unknown in this case because we can't measure the returned signal directly. What can we do about it?

Turns out if we multiply the transmitted signal above $\sin\left(\omega_0 t + \frac{1}{2}\alpha t^2\right)$ 
with the received signal $\sin\left(\omega_0 t - \omega_0 \tau + \frac{1}{2}\alpha t^2 - \alpha \tau t + \frac{1}{2}\alpha \tau^2 - \pi\right)$

and according to the relationship $$\sin(A)\sin(B) = \frac{1}{2}\cos(A - B) - \frac{1}{2}\cos(A + B)$$

we shall obtain a delta term $\frac{1}{2}\cos(Tx - Rx)$ and a sum component $\frac{1}{2}\cos(Tx + Rx)$, where Tx and Rx here are short for transmitted and received.

In reality, this multiplication is handled physically by a component in the radar called the "mixer". Once the two signals are multiplied (a.k.a. mixed), we apply a low-pass filter to acquire the delta term and we throw away the sum. 

This delta term is what we called the beat frequency, which is a lot slower than the original signals because the reflected waves aren't too different than the transmitted waves (even with Doppler), so the delta they produce is not significant.

In other words, the beat frequency is much more sampler-friendly and can be measured.

And from there, finally, we will say that $\tau$ and R can be reliably determined.

So this is it, as I promised. We will kill the post from here.



## Section 8: The End

Oh don't worry, this is not extra information. I am just here to conclude.

Radar is actually a hugeeeeee topic. The more I learn about it, the more I know that there are more that I don't know about it. 

I started to dig into this field when I begun working with radar data for preception and detections. And to date, my conclusion is that, you will probably really need a PhD to master using the radar.

Although for computer scientists, potentially, we could just treat the data as given and not pay too much attention into understanding the radar basics, I do feel that this is essential especially for responsible and high-quality data collection, which, in the other post (AI Hierarchy - What is really important), I argued, is paradigm for deep learning.

Anyway, I hope you enjoyed the post. This one is very long and much longer than usual. During the beginning of this post, I thought I would be done in a few days. Boy, I was wrong. Radar, Radar, Radarrrrrrrr.

