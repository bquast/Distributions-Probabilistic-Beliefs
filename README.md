Single-Agent Belief Distributions
========================================================
Modelling probabilistic beliefs for single agents as distributions, incorporating changes and apparent incommensurability.
--------------------------------------------------------


Abstract
--------------------------------------------------------
By constructing a distribution of the belief structure of a single agent, we can mitigate seemingly incommensurable beliefs. We propose to generalise the concept of a single agents beliefs, from a point estimate, to a distributional approximation. This will allow us to deal with differing estimates of the probability of an event *p(e)*, as well as with estimates of *p(e)* and *p(¬e)* which violate unitarity, in meaningful way. Additionally with a distributional approximation, we can guess at agents' beliefs, depending on which state they are in.


Introduction
--------------------------------------------------------
It generally held to be so that people sometimes hold beliefs which are incommensurable with each other. In technical terms we could say, the knowledge base is interally inconsistent. This incommensurability becomes especially apparent when these beliefs are quantified. 

As an example consider the following. If we have the probability of some event *e* occuring with probability *p(e)*, and an agents belief on this probability *b[p(e)]*. By definition, all probabilities are exhausted at *1*. Therefore the probability of that event not occuring, i.e. *p(¬e)* or *p of not e*, is *1-p(e)*.

> p(¬e) = 1 - p(e)

It is often observed, that people hold beliefs that do not fullfil this condition, these beliefs can thus be described as:

> b[p(¬e)] ≠ 1 - b[p(e)]

In addition to this, we often see that people have different beliefs about the same probability, often just moments apart (e.g. beginning and end of a survey). This could be the case for many (unrelated) reasons, such as, fatigue, hunger, anchoring, etc. We can express this as:

> b_1[p(e)] ≠ b_2[p(e)] 

In this paper we describe how we can generalise the idea of perception of probability *for a single agent* from a point estimate, to a distributional approximation.

Doing this will allow us to deal with non-unitary, or otherwise seemingly inconsistent beliefs, in a single framework in a *meaningful* way.


An example
--------------------------------------------------------
On a fair die, the chance of throwing 3 eyes is 1/6, call this *p(e)*. The chance that you do not throw 3 eyes (i.e. *p(¬e)*) is therefore *1-p(e)*, or


```r
1 - (1/6)
```

```
## [1] 0.8333
```


This is a very simple statistical exercise, and most people will be able to give you the answer that we derive. The following thus holds:

> b[p(¬e)] = 1 - b[p(e)]

The reason for this is that people learn to use dice and how they operate, in e.g. board games. Idem dito for coin flipping and other basic statistical exercises. In this context, you would rarely find people accepting a bet that has a negative expected value, such as non-equal payout for a fair coin flip.

However, as soon as odds become less transparent, statistical methods are often applied with less rigour. Especially when dealing with observed implicit payout structures. As bets with negative expected value, such as lotteries, are often accepted (though there could be many other reasons for this too). 

Let us continue with the idea of a lottery. For a lottery at the local sports club, 100 tickets were printed, yet only 3 out of every 4 tickets was sold, therefore tickets will be drawn until a winner is found. The price of a ticket is 1 apple, and the prize for the winner is 50 apples.

Our subject is called Janus. Janus know exactly how many tickets were available, and also how many were sold. After Janus buys a ticket for the lottery, we ask him the following questions.

  1. What do you think is the chance (as a percentage) that you will win the lottery?
  2. What do you think is the chance (as a ratio) that someone else will win the lottery?
  3. What is the chance that nobody wins the lottery?
  4. If you win, how many apples will you have won?
  5. What is the chance (as a ratio) that you will win the lottery?

The first question is not very hard:


```r
1/(100 * (5/8))
```

```
## [1] 0.016
```


But perhaps it is something you wouldn't always do without a calculator or at least pen and paper. 

As can be seen, question (1) and (5) are identical. If you go through the questions without having done the calculations beforehand, you will likely be inclined to give a lower answer to (5) than you were to (1). Presumably you would be quite neutral when answering question (1). Yet the question preceding question (5) is meant to lift you up by making you think of how much you could win.

Janus acts very much in accordance with our expectations, and gives us the following responses.

  1. 1%
  2. 19/20
  3. 0
  4. 50 - 1 = 49
  5. 1/60

We now observe two different estimates of the same *p(e)*.


```r
p_1 = 1/100
p_1
```

```
## [1] 0.01
```

```r
p_2 = 1/60
p_2
```

```
## [1] 0.01667
```


Normally we would take either one of the responses, or such some other way to come to a point estimate, such as averaging. 

An example of how to model this as a distribution could be the following. Let us assume that question (1) was answered in a neutral state, and that question (5) was answered in a slightly optimistic state. Furthermore, let us assume that beliefs are normally distributed.


```r
mu = p_1
mu
```

```
## [1] 0.01
```

```r
sigma = p_2 - mu
sigma
```

```
## [1] 0.006667
```


We can now define our subjects beliefs on winning the lottery as:

> B ~ N( mu, sigma )

In this example we assume the shape of the distribution, as well as the location of our observations on this distribution.

In this case we assumed the normal distribution. Generally, in a situation where our distribution is positively skewed we would assume a different type of distribution, such as the log-normal, the exponential, or the Gumbel distribution. Additionaly, if our mean does lie more to the center of the distribution we would probably expect to find high levels of kurtosis, in which case a t-distribution with a low number of degrees of freedom would be more fitting.


An application
--------------------------------------------------------
Let us now suppose that our subject loses his wallet before the winner is drawn. If we want to guess at how his beliefs have changed, we can for example assume that he is currently one standard deviation below his mean belief.


```r
mu - sigma
```

```
## [1] 0.003333
```


If however, Janus there after is in a euphoric state because he find his wallet again, and on top of this a nice shiny green apple, than his new belief might change to two standard deviations above above his mean level.


```r
mu + 2 * sigma
```

```
## [1] 0.02333
```


Equivalently, we can combine non-unitary responses using:

> b_2[p(e)] = 1 - b_2[p(¬e)]


In conclusion
--------------------------------------------------------
We propose to generalise the modeling a single agents' beliefs from a point-estimate to a distribution. This allows us to deal with seemingly incommensurable beliefs, such as non-unitarity) in a meaningful manner.

By means of illustration, we provide an example in which we assume both the distribution, as well as the location of our observations on this distribution. However, other ways of constructing distributions, such as distribution fitting, can also be used.


Now...for something much more important
--------------------------------------------------------
[A video of a penguin being tickled](http://www.youtube.com/watch?v=FVwtTrlPSSk)
