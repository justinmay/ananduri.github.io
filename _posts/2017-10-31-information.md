---
layout: post
title: "Information"
category: posts
---

### Information

What does it mean to get information about one variable by observing another variable? (I'm going to assume that you know what joint, conditional, and marginal probability distributions are.) Let's consider the simplest possible case: there are two variables, $$x$$ and $$y$$, and their joint probability distribution is $$P(x,y)$$. 

Let's say that you have a device that only measures the variable $$x$$. Over some span of time you record a bunch of measurements for $$x$$, and come up with a putative probability distribution for $$x$$, $$P(x)$$. If you knew $$P(x,y)$$, this would correspond to the marginal distribution for $$x$$ you could get by integrating out $$y$$.

Now let's say that you have another device, that only measures $$y$$. Pick a certain value of $$y$$, and call that value $$a$$. Now, _only_ when your second device tells you that the variable $$y$$ is close to $$a$$, you measure $$x$$. Again, after some time you can come up with another probability distribution for $$x$$. This distribution is denoted by $$P(x\vert y=a)$$, which means the probability distribution of $$x$$ given that $$y$$ is $$a$$. This is also known as a conditional probability distribution (it's the distribution of $$x$$ conditioning on the fact that $$y$$ is $$a$$).

<!-- diagram for this -->
What if $$P(x\vert y=a)$$ and $$P(x)$$ are different? Let's consider a concrete case: say $$P(x)$$ is a flat, uniform distribution, but $$P(x\vert y=a)$$ sharply spikes around one value. This means that normally, we don't have a good idea what value $$x$$ takes. But, when we happen to know that $$y$$ is taking on the value $$a$$, we have a pretty good idea of what value $$x$$ will take. Observing the value of $$y$$ _changes_ our idea of what value $$x$$ will be, in a way that would let us better predict $$x$$ (it literally changes our state of knowledge and therefore the probability distribution we would use for $$x$$, as a Bayesian would say). Another way of saying this is that we have gained information about one variable, $$x$$, by observing another variable, $$y$$.

To get really concrete, let $$x$$ be a variable measuring hair length, and $$y$$ be a categorical variable representing gender. If we used our first measuring device, our eyes, to indiscriminately look at the hair lengths of everyone around us, we'd observe a distribution that would be quite broad, with a sizable right tail. But, if we first pick a value for $$y$$ (male), and only observe someone's hair length after we ascertain that the variable $$y$$ is male, we'd come up with a very different distribution of hair lengths, one that is concentrated at small values, and falls off much more quickly from 0. Knowing someone's gender lets us make better predictions (on average) of what their hair length would be; observing the gender variable gives us information about the hair length variable (by Bayes' theorem, the converse is also true, although the information gain could be much less substantial).

What about the opposite case, when $$P(x\vert y=a)$$ and $$P(x)$$ are the same? Does that mean we won't get information about $$x$$ by observing $$y$$? Not quite--what if you pick a different value for $$y$$, other than $$a$$? It's possible that $$P(x\vert y=a) = P(x)$$, but when $$y$$ takes another value, $$b$$, you find that $$P(x\vert y=b) \neq P(x)$$. In this case, you can still gain information about $$x$$ if you observe that $$y$$ is $$b$$. So the true requirement that two variables $$x$$ and $$y$$ have to satisfy if they can't give you information about each other--in other words, if they're _statistically independent_-- is

\begin{equation}
P(x\vert y = c) = P(x)\quad \forall c \in \mathrm{range}(y).
\end{equation}

In other words, you have to make sure that $$P(x\vert y = c) = P(x)$$ for every value $$c$$ that $$y$$ can take.

To summarize, gaining information means that we're better able to predict one variable if we first observe another variable, compared to if we didn't know what value the second variable was. 
