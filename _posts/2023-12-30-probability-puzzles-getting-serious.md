---
layout: post
title: "Probability Puzzles - Getting Serious level"
categories: fun math problems
---
This post contains my solutions to problems, Getting Serious level from an app called [Probability Math Puzzles](https://play.google.com/store/apps/details?id=atorch.statspuzzles&pli=1).


![dice](/assets/images/probability_puzzles.png){:style="display:block; margin-left:auto; margin-right:auto"}

### **Puzzle 1**
> You\'re stuck on a desert island - and to pass the time, you\'ve decided to repeatedly toss a fair six-sided die. Let\'s make the reasonable assumption that tosses are independent. \
On average, how many tosses does it take until you see a number larger than four?

Let $$p$$ be the probability that we see a number smaller than 4. Denote $$X$$ the number of tosses it takes until we see number larger than 4, $$P(X=i)$$ the probability that a number larger than 4 is observed for the first time at $$i$$-th toss, $$i \geq 1$$.

We have $$P(X=i) = p^{i-1}(1-p)$$

The answer is the expected values of $$X$$, which is

$$
\begin{align*}
    E[X] & = \sum_{i=1}^{\infty}i \cdot P(X=i)  \\
    & = \sum_{i=1}^{\infty}i \cdot p^{i-1}(1-p) = (1-p)\sum_{i=1}^{\infty}i \cdot p^{i-1} \\
    & = (1-p)\sum_{i=1}^{\infty} \dfrac{\mathrm{d}p^i}{\mathrm{d}p} = (1-p)\dfrac{\mathrm{d}(\sum_{i=0}^{\infty}p^i -1)}{\mathrm{d}p} \\
    & = (1-p)\dfrac{\mathrm{d}(\frac{1}{1-p} - 1)}{\mathrm{d}p} = (1-p)\dfrac{\mathrm{d}(\frac{p}{1-p})}{\mathrm{d}p} \\
    & = (1-p)\frac{p'(1-p)-p(1-p)'}{(1-p)^2} = \frac{1}{1-p}\\
\end{align*}
$$

Now plug $$p = \frac{4}{6}$$ in the derived formula and we have $$E[X] = \frac{1}{1-\frac{4}{6}} = 3$$.

### **Puzzle 2**
> Three friends are hanging out. To keep things simple, assume their birthdays are uniformly and independently distributed across the 365-day year. \
What\'s the probability that some (i.e. either two or three) of the people in this group have a birthday in common?

Denote $$D$$ as the number of days in a year, we find the probability that three friends have different birthdays instead then take the complement. There are $$D\cdot D\cdot D$$ combinations of birthday triples, $$D\cdot (D-1)\cdot (D-2)$$ of them are pairwise distinct.

The final answer is:

$$
\begin{align*}
    & 1 - \frac{D\cdot (D-1)\cdot (D-2)}{D\cdot D\cdot D} = 1 - \frac{(D-1)\cdot (D-2)}{D^2} \\
    & = \frac{D^2-(D^2-3D+2)}{D^2} = \frac{3D-2}{D^2} \\
    & = \frac{3\cdot 365 - 2}{365^2} \approx 0.008204
\end{align*}
$$

