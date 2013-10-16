Single-Agent Belief Distributions
========================================================
Modeling probabilistic beliefs for single agents as distributions, incorporating changes and apparent inconsistencies.
--------------------------------------------------------

Abstract
--------------------------------------------------------
This paper explains a method of incorporating conflicting beliefs for a single agent into a belief distribution.

*It is generally accepted that most if a not all people have conflicting beliefs. It is the basis of Socrates' midwife method, showing that two beliefs cannot be in accordance with each other.* This incommensurability becomes especially apparent when we asks people about beliefs in probabilities, or, the odds of something occurring, and the odds of the same thing not occurring.

More strongly, we often see that people have different beliefs about the same thing, often times just moments apart (e.g. beginning and end of a survey). There are many reasons for this, such as fatigue, hunger, anchoring, etc.

Thus, beliefs change, so we cannot discard a response because it does sum to unity with its negation. In this paper I try to describe how the idea of attempting to describe peoples beliefs in a point estimate (i.e. one number) is a problematic simplification, even in cases where we have no (knightian) uncertainty.

In this paper I try to show how we can use all the information that is provided to come up with an inclusive framework to model beliefs on probabilities using a distribution, rather than the traditional point estimate.

An example
--------------------------------------------------------
On a fair die, the chance of throwing 3 eyes is 16, call this p. The chance that you do not throw 3 eyes has therefore to be *1-p*, or *1-1/6=5/6*. This is a very simple statistical exercise, and most people will be able to give you the answer I derive. The reason for this is that most people have learned to use dice and how they operate, in e.g. board games. Likewise for coin flipping and many other basic statistical situations. In this context, you would rarely find people accepting a bet that has a negative expected value. *Such as ...*

However, as soon as odds become less obvious, statistics is not applied with the same rigor, and bets with negative expected values are often accepted. I would argue that this is a major factor (though not the only) at work when people buy lottery tickets for a lottery which usually has a negative expected value.

Let us continue with the idea of a lottery. For a lottery at the local sports club, 100 tickets were printed, yet only 5 out of every 8 tickets was sold, therefore tickets will be drawn until a winner is found. The price of a ticket is 1 apple, and the prize for the winner is 50 apples.

Our victim is called Achim. After Achim buys a ticket for the lottery, we ask him the following questions.

  1. How many apples can you win in this lottery?
  2. What is the chance (in percent) that you will win the lottery?
  3. What is the chance (as a ratio) that someone else will win the lottery?
  4. What is the chance that nobody wins the lottery?
  5. You came with one apple, with how many apples do you expect to walked away?
  6. What is the chance (as a ratio) that you will win the lottery?

The answer to the first question is given. The second question is not very hard:

```r
1/(100 * (5/8))
```

```
## [1] 0.016
```

But perhaps it is something you wouldn't always do without a calculator or at least pen and paper. The third answer should be:

```r
1 - 1/(100 * (5/8))
```

```
## [1] 0.984
```

Definitely something most people would do on paper. However, since we are at the sports club, this is something we probably do not have at hand.

As can be seen, question 2 and 6 are identical. If you go through the questions without having done the math beforehand, you will likely be inclined to give a lower answer to 6 than you were to 2. The reason is probably that the question directly preceding question 2, has a very positive content, it talks of the prize. Yet the question preceding question 6 is rather negative, since you would probably expect to walk away with zero apples. Furthermore, you could have become tired of answer so many questions, which generally diminishes your (perception) of your chance of being successful.

Achim act very much in accordance with our expectations, and gives us the following responses.

  1. 50
  2. 2% (has to be more than two)
  3. 19/20
  4. 0
  5. 0
  6. 1/60

Normally we would take either one of the responses, or such some other way to come to a point estimate, such as averaging. 

As a distribution
--------------------------------------------------------
Let us assume that question 2 was answered in an slightly optimistic state, and question 6 in a slightly pessimistic state. Furthermore, let us assume that beliefs are normally distributed, and that these slightly pessimistic and slightly optimistic state are each away from the mean, below and above respectively. Lets express (6.) as a number: 0.0167. We can now construct the standard deviation.


```r
(0.02 - 0.0167)/2
```

```
## [1] 0.00165
```

Our mean is therefore *0.0167+0.00167=0.01834*. We can now define our subjects beliefs on winning the lottery as:

> B~N(0.0167,0.00167)

Let us now suppose that our subject loses his wallet before the winner is drawn. If we want to predict how is beliefs have changed, we can for example assume that they are now 2below is mean belief. This would thus give us:


```r
0.0167 - 2 * (0.00167)
```

```
## [1] 0.01336
```

If however, he there after is in a euphoric state because he find his wallet again, and on top of this a shiny green apple, than his new belief might change to 3above his mean level. Which would give us:


```r
0.0167 + 3 * (0.00167)
```

```
## [1] 0.02171
```

>p anp (1-p)

How do we match the answers to questions 2 and 3, the chance that Achim thinks he has of winning, with the chance that somebody else win (i.e. that he does not win). Let us write both odds as numbers:

> p_1 = 0.02
> 1-p_2 = 0.95 => p_2 = 0.05

Let us suppose that the estimate of pwas positive by one and that the estimate of 1-p was positive by 3then we know:


```r
twosigma = 0.05 - 0.02
twosigma/2
```

```
## [1] 0.015
```


Using this, we can then find the mean:

```r
0.02 - 0.015 = 0.005
```

```
## Error: target of assignment expands to non-language object
```

An application
--------------------------------------------------------
Estimation of a 95% confidence interval for a belief on probability, how the lottery profit from this.


Now...for something much more important
--------------------------------------------------------
[A video of a penguin being tickled](http://www.youtube.com/watch?v=FVwtTrlPSSk)
