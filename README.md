Single-Agent Belief Distributions
========================================================
Modelling probabilistic beliefs for single agents as distributions, incorporating changes and apparent incommensurability.
--------------------------------------------------------

TODO
--------------------------------------------------------
 [] implicit beliefs


Abstract
--------------------------------------------------------
By constructing a distribution of the belief structure of a single agent, we can mitigate seemingly incommensurable beliefs. This paper proposes to generalise the concept of a single agents belief, from a point estimate to a distributional approximation. This will allow us to deal with differing estimates of the probability *p*, as well as with estimates of *p* and *¬p* not summing to unity, in meaningful way. Additionally with a distributional approximation, we can estimate agents' beliefs, using the state they are in.

Introduction
--------------------------------------------------------
It generally held to be so that people sometimes hold beliefs which are incommensurable with each other. In technical terms we could say, the knowledge base is interally inconsistent. This incommensurability becomes especially apparent when these beliefs are quantified. 

As an example consider the following. If we have the probability of some event *e* occuring with probability *p*. By definition, all probabilities are exhausted at *1*. Therefore the probability of that event not occuring (i.e. *¬p* or *not p*) is *1-p*.

> ¬p = 1 - p

It is often observed, that people hold beliefs that do not meet this condition, these beliefs can thus be described as:

> ¬p ≠ 1 - p

In addition to this, we often see that people have different beliefs about the same thing, often just moments apart (e.g. beginning and end of a survey). This could be the case for many (unrelated) reasons, such as, fatigue, hunger, anchoring, etc. We can express this as:

> p_1(e) ≠ p_2(e) 

We are thus faced with the fact that we get responses from agents 

In this paper I describe how we can generalise the idea of perception of probability -for a single agent- from a point estimate, to a distributional approximation.

Doing this will allow us to deal with seemingly inconsistent beliefs in a single framework in a *meaningful* way.

An example
--------------------------------------------------------
On a fair die, the chance of throwing 3 eyes is 16, call this *p*. The chance that you do not throw 3 eyes (i.e. *¬p*) is therefore *1-p*, or


```r
1 - (1/6)
```

```
## [1] 0.8333
```


This is a very simple statistical exercise, and most people will be able to give you the answer that I derived. The reason for this is that people learn to use dice and how they operate, in e.g. board games. Likewise for coin flipping and many other basic statistical trials. In this context, you would rarely find people accepting a bet that has a negative expected value. Such as non-equal payout for a fair coin flip.

However, as soon as odds become less transparent, statistical methods are often applied with less rigour. Especially when dealing with observed implicit payout structures. As a results bets with negative expected payouts, such as lotteries, are often accepted. 

Let us continue with the idea of a lottery. For a lottery at the local sports club, 100 tickets were printed, yet only 5 out of every 8 tickets was sold, therefore tickets will be drawn until a winner is found. The price of a ticket is 1 apple, and the prize for the winner is 50 apples.

Our victim is called Janus. After Janus buys a ticket for the lottery, we ask him the following questions.

  1. What is the chance (in percent) that you will win the lottery?
  2. What is the chance (as a ratio) that someone else will win the lottery?
  3. What is the chance that nobody wins the lottery?
  4. You came with one apple, with how many apples do you expect to walked away?
  5. What is the chance (as a ratio) that you will win the lottery?

The first question is not very hard:


```r
1/(100 * (5/8))
```

```
## [1] 0.016
```


But perhaps it is something you wouldn't always do without a calculator or at least pen and paper. The second probability is:


```r
1 - 1/(100 * (5/8))
```

```
## [1] 0.984
```


Definitely something most people would do on paper. However, since we are at the sports club, this is something we might not have at hand.

As can be seen, question (1) and (5) are identical. If you go through the questions without having done the calculations beforehand, you will likely be inclined to give a lower answer to (5) than you were to (1). *The reason is probably that the question directly preceding question (1), has a very positive content, it talks of the prize.* Yet the question preceding question (5) is rather negative, since you would probably expect to walk away with zero apples. Furthermore, you could have become tired of answer so many questions, which generally diminishes your (perception) of your chance of being successful.

Janus act very much in accordance with our expectations, and gives us the following responses.

  1. 2% (has to be more than two)
  2. 19/20
  3. 0
  4. 0
  5. 1/60

Normally we would take either one of the responses, or such some other way to come to a point estimate, such as averaging. 

As a distribution
--------------------------------------------------------
Let us assume that question (2) was answered in an slightly optimistic state, and question 6 in a slightly pessimistic state. Furthermore, let us assume that beliefs are normally distributed, and that these slightly pessimistic and slightly optimistic state are each away from the mean, below and above respectively. Lets express (5) as a number: 0.0167. We can now construct the standard deviation.


```r
two_mu = (0.02 - 0.0167)/2
mu = two_mu/2
mu
```

```
## [1] 0.000825
```

We can now define our subjects beliefs on winning the lottery as:

> B~N(0.0167,0.00167)

Let us now suppose that our subject loses his wallet before the winner is drawn. If we want to predict how is beliefs have changed, we can for example assume that they are now 2below is mean belief. This would thus give us:


```r
0.0167 - 2 * (0.00167)
```

```
## [1] 0.01336
```


If however, Janus there after is in a euphoric state because he find his wallet again, and on top of this a nice shiny green apple, than his new belief might change to *3s* above his mean level. Which would give us:


```r
0.0167 + 3 * (0.00167)
```

```
## [1] 0.02171
```


>p anp (1-p)

How do we match the answers to questions (2) and (3), the chance that Janus thinks he has of winning, with the chance that somebody else win (i.e. that he does not win). Let us write both odds as numbers:

> p_1 = 0.02
> 1 - p_2 = 0.95 => p_2 = 0.05

Let us suppose that the estimate of *p* was positive by one and that the estimate of *1-p* was positive by *3s* then we know:


```r
twosigma = 0.05 - 0.02
twosigma/2
```

```
## [1] 0.015
```


Using this, we can then find the mean:


```r
0.02 - 0.015
```

```
## [1] 0.005
```


An application
--------------------------------------------------------
Estimation of a 95% confidence interval for a belief on probability, how the lottery profit from this.

Now...for something much more important
--------------------------------------------------------
[A video of a penguin being tickled](http://www.youtube.com/watch?v=FVwtTrlPSSk)
