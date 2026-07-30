---
title: L1 & L2 Regularizors - A Way Better Way To Understand Them
date: 2026-06-30
mathjax: true
categories: [blog]
tags: [machine learning]
---

I learned the L1 and L2 regularizors on *SEP740: Deep Learning* (a course at McMaster) couple years back. The prof first introduced overfitting, and then taught these regularizors as a way to combat overfitting in neural networks. 

We were shown the effects of these regularizors on the network's weights and were told to remember them. What a terrible way to learn. 

I passed the test but soon forgot most of it.

Here I present a better way to learn them. A way that sticks.

We will start with the Bayesian Theorem. 

  <figure>
    <img src="bayesian_theorem.png" alt="bayesian_theorem">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 1: Bayesian Theorem.
    </figcaption>
  </figure>

The Bayesian Theorem states that, given the event B has happened, the probability of our hypothesis A being true (Posterior Probability), is equal to, the probability of how likely B is to happen if A is true (Likelihood), times, the probability of A being true (Prior Probability), over the probability of B happening regardless of A being true or not (Evidence).

For neural networks, we rewrite the Bayesian Theorem into this form:

  <figure>
    <img src="bayesian_theorem_for_nn.png" alt="bayesian_theorem_for_nn">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 2: Bayesian Theorem for Neural Networks.
    </figcaption>
  </figure>

where we assume there are some underlying weights $\theta_{\text{underlying}}$ in some generative model $g_{\theta}(\cdot)$ that has produced some data D, and we are trying to find a set of weights $\theta$ in our neural network that best matches $\theta_{\text{underlying}}$.

Here we ask, given the obserevd data D, what is the posterior probability of the hypothesis that "*the weights of my network $\theta$ indeed correspond to the underlying mechanism that led to the data D*" holds true.

The likelihood term $P(D \mid \theta)$ states that, given the weights of the network $\theta$, how likely are we to observe the data D again. Here, the more likely we are to observe D, the higher our chance for getting the weights $\theta$ right (increass the probability of our hypothesis being true). 

And the evidence term $P(D)$ here states that rarer events would provide more evidence for supporting the hypothesis. 

For generative models, we directly substitute D with $x$ because the neural net, once parameterized with $\theta$, outputs $x$. We can rewrite the Bayesian description as:

$$P(\theta \mid x) = \frac{P(x \mid \theta) \cdot P(\theta)}{P(x)}$$

For supervised learning mdoels (say an image classifier), we substitute D with a pair of ($x$, $y$), where $x$ stands for the input data, and $y$ stands for the label. 

We will rewrite the Bayesian expression as:

$$P(\theta \mid x,y) = \frac{P(x,y \mid \theta) \cdot P(\theta)}{P(x,y)}$$

There is a problem with that though, because that expression implies that our model takes $\theta$ and outputs $x$ and $y$, which is not true. An classification model should take $x$ and $\theta$, to output $y$. 

To fix that, we'll expand the Likelihood term and the Evidence term using the chain rule. This will get us

$$P(\theta \mid x, y) = \frac{P(y \mid x, \theta) \cdot P(x \mid \theta) \cdot P(\theta)}{P(y \mid x) \cdot P(x)}$$

which can be simplified into

$$P(\theta \mid x, y) = \frac{P(y \mid x, \theta) \cdot P(\theta)}{P(y \mid x)}$$

if we assume $P(x \mid \theta) = P(x)$. 

(The two $P(x)$ terms cancel out each other; this is a valid assumption because the probability of observing $x$, $P(x)$, shouldn't depend on the weights of our network.)

Anyway, this final form of Bayesian expression for the supervised model is stating that

"*The posterior probability that my hypothesis of the network's weights $\theta$ is indeed $\theta_{\text{underlying}}$, is equal to, the likelihood of getting the label $y$ from the neural network given the input $x$ and weights $\theta$, times, the prior probability of observing $\theta$, over the probability of observing the label $y$ given the data $x$ across all scenarios, which serves as the evidence.*"

Now let us take Maximum A Posterior to obtain this expression below:

$$\hat{\theta} = \arg\max_{\theta} \frac{P(y \mid x, \theta) \cdot P(\theta)}{P(y \mid x)}$$

The evidence term $P(y \mid x)$ does not depend on $\theta$. If we drop it, it won't affect our ability to find $\hat{\theta}$ through Maximum A Posterior. So let's drop it. 

We will be left with:

$$\hat{\theta} = \arg\max_{\theta} \left[ P(y \mid x, \theta) \cdot P(\theta) \right]$$

Now if we expand the data pair ($x$, $y$) to a set of data pairs (X, Y), the posterior probability of our hypothesis holding will be reduced, because now we will need to predict every pair of data correctly. 

That will be equivalent to multipling the likelihood terms across all sample pairs, which will give us:

$$\hat{\theta} = \arg\max_{\theta} \left[ \left( \prod_{i=1}^{N} P(y_i \mid x_i, \theta) \right) \cdot P(\theta) \right]$$

This Maximum A Posterior equation is essentially looking for a set of $\theta$, call it $\hat{\theta}$ (estimated), that will output the highest posterior probability for our hypothesis to hold true across all N data pairs. 

From here, we will do two things. First, we will add a log term into the expression. This is benefitial for two reasons. No.1 reason is that the product of a bunch of probabilities (that are less than 1) will shrink to a very small value, but if we take logarithm, we can add them together linearly. No.2 reason is that later on when we expand the probability term, we will see that they carry an exponential term with them. So taking the log will cancel that exponential term out and make the math cleaner. (So yes, here when I say log, I refer to log with a base of e, so Ln, technically.)

Anyway, after taking logarithms, what we will get is this expression:

$$\hat{\theta} = \arg\max_{\theta} \left( \sum_{i=1}^{N} \log P(y_i \mid x_i, \theta) + \log P(\theta) \right)$$

We will then flip it from an maximinzing objective to a minimizing one, by multiplying -1, which will give us 

$$\hat{\theta} = \arg\min_{\theta} \left( -\sum_{i=1}^{N} \log P(y_i \mid x_i, \theta) - \log P(\theta) \right)$$

As a reminder, the first term above is our likelihood; second term is our prior.

Here, we will assume each $y$ in the data pairs collected, (X, Y), deviates from the underlying y because there exists some noise in the real world during the data colleciton process. 

If we assume the noise is Gaussian, it will allow us to replace the likelihood term with a Probability Density Function (PDF) of a Gaussian distribution. 

In other words, we will get this expression for our likelihood term:

$$P(y_i \mid x_i, \theta) = \frac{1}{\sqrt{2\pi\sigma^2}} \exp\left( -\frac{(y_i - f_{\theta}(x_i))^2}{2\sigma^2} \right)$$

The stuff on the right side of the equation above is the Gaussian probability density function.

Here is a demonstration from Wiki to help you understand that. The y-axis is the probability density, and the x-axis is the value of the variable.

  <figure>
    <img src="gaussian.png" alt="gaussian.png">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 3: Gaussion distribution probability density functions from Wikipedia.
    </figcaption>
  </figure>

Now if we substitute this into the argmin equation above, what we will get is this: 

$$\hat{\theta} = \arg\min_{\theta} \left( -\sum_{i=1}^{N} \log \left( \frac{1}{\sqrt{2\pi\sigma^2}} \exp\left( -\frac{(y_i - f_{\theta}(x_i))^2}{2\sigma^2} \right) \right) - \log P(\theta) \right)$$

Expanding the terms inside the logarithm will get us

$$\hat{\theta} = \arg\min_{\theta} \left( \sum_{i=1}^{N} \left( \frac{(y_i - f_{\theta}(x_i))^2}{2\sigma^2} + \frac{1}{2}\log(2\pi\sigma^2) \right) - \log P(\theta) \right)$$

and we can drop the constant term $\frac{1}{2}\log(2\pi\sigma^2)$ here to get a final form of

$$\hat{\theta} = \arg\min_{\theta} \left( \frac{1}{2\sigma^2} \sum_{i=1}^{N} (y_i - f_{\theta}(x_i))^2 - \log P(\theta) \right)$$

Here you can start to see, the likelihood term becomes the main loss function used in neural network trainings; it is calculating the error between the predicted label $\hat{y}$ and $y$. And the prior term becomes the space for the regularizors.

(ps. A common variant of this loss function is the Mean Squared Error (MSE), expressed as)

$$\text{MSE} = \frac{1}{N} \sum_{i=1}^{N} \left( y_i - f_{\theta}(x_i) \right)^2$$

Now let us focus on the prior term, $-\log P(\theta)$.

For L2 regularization, what we actually do, is to assume that each element $\theta_j$ within the weights of the network, is independently drawn from a Gaussian distribution (see the distribution again from above). 

Well, this is an assumption. But what this assumption does is that it allows us to replace the prior probability $P(\theta)$ with the probability density function of a Gaussian distribution. In another word, we get this:

$$P(\theta) = \prod_{j=1}^{d} \frac{1}{\sqrt{2\pi\sigma_{\theta}^2}} \exp\left( -\frac{\theta_j^2}{2\sigma_{\theta}^2} \right)$$

When we substitute this back to the Negative Log Prior term, we will get

$$-\log P(\theta) = \frac{1}{2\sigma_{\theta}^2} \sum_{j=1}^{d} \theta_j^2 + \frac{d}{2}\log(2\pi\sigma_{\theta}^2)$$

The second term is a constant that we can drop. 

If we simply it a bit, we will get the final form of

$$-\log P(\theta) = \frac{1}{2\sigma_{\theta}^2} \sum_{j=1}^{d} \theta_j^2$$

where $\frac{1}{2\sigma_{\theta}^2}$ is grouped into one $\lambda$, which controls the strength of the regularization. When variance ${\sigma}^2$ is small, $\lambda$ increases, the Gaussion distribution becomes more narrow, so the weights $\theta$ tend to locate closer to the mean of the distribution, thus getting smaller.

One more note to add here is that, the whole Negative Log Prior term is a quadratic function of $\theta$, whose derivative goes to zero when $\theta$ approaches zero. So it does not encourage sparsity.

When we train neural networks, we compute the gradient (a vector that contains all the partial derivatives for each element j in $\theta$) for a backward pass. This is what we get:

$$\nabla_j = \frac{\partial}{\partial \theta_j} \left( -\log P(\theta) \right) = \frac{1}{\sigma_{\theta}^2} \theta_j$$

If we put together all the elements of $\nabla$, we will see the gradient vector as:

$$\nabla = \frac{1}{\sigma_{\theta}^2} [\theta_1, \theta_2, \dots, \theta_D] \end{bmatrix}^T$$

During training, once we have the $\nabla$, we can update the existing weights with a step size, for each element j, towards the direction of the gradients.

For L1, this is similar. 

We assume the weights are drawn independently, not from a Gaussian distribution, but from a Laplace distribution, which looks like this. 

  <figure>
    <img src="laplace.png" alt="laplace.png">
    <figcaption style="text-align:center; font-size:0.85em; color:#888;">
      Figure 4: Laplace distribution probability density functions from Wikipedia.
    </figcaption>
  </figure>

Just like L2, this will allow us to replace the prior term with the probability density function of Laplace distribution. 

$$P(\theta) = \prod_{j=1}^{d} \frac{1}{2b} \exp\left( -\frac{|\theta_j|}{b} \right)$$

And if we put it back into the Negative Log Prior expression, we will get:

$$-\log P(\theta) = \frac{1}{b} \sum_{j=1}^{d} \vert{}\theta_j\vert{} + d \log(2b)$$

where the second term on the right side is a constant that we can drop.

So we are left with

$$-\log P(\theta) = \frac{1}{b} \sum_{j=1}^{d} \vert{}\theta_j\vert{}$$

Now since there is an absolute operation on $\theta$, when we take the partial derivative, we will get:

$$\nabla_j = \frac{\partial}{\partial \theta_j} \left( -\log P(\theta) \right) = \frac{1}{b} \operatorname{sign}(\theta_j)$$

where the sign function stands for 

$$\operatorname{sign}(x) = +1 \text{if } x > 0 $$
$$\operatorname{sign}(x) = -1 \text{if } x < 0 $$

(ps. the derivative is not defined at x=0.)

Since the gradient is always either +1 or -1 regardless of the value of $\theta$, the L1 regularizor will always try to pull the weights towards zero, thus creating sparsity.

And there you have it. L1 & L2 regularizations.

I hope the explaination was clear and that it sticks with you from now on. (just in case you get asked about these regularizors on an interview 😆)