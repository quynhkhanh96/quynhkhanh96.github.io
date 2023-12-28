---
layout: post
title: "Probability Puzzles - Easy Peasy level"
categories: fun math problems
---
This post contains my solutions to problems, Easy Peasy level from an app called [Probability Math Puzzle](https://play.google.com/store/apps/details?id=atorch.statspuzzles&pli=1).


![dice](/assets/images/probability_puzzles.png){:style="display:block; margin-left:auto; margin-right:auto"}

### **Puzzle 11**
> Two friends, Alice and Bob, have found an unfair coin: it has a $$72\%$$ chance of coming up heads. I have no idea what such a coin would look like, but let\'s just pretend it exists. \
Alice proposes a game: she\'ll toss the coin twice; if it comes up heads then tails, she wins; if it\'s the reverse (tails then heads), Bob wins; and if neither of those two things happens, the game restarts, and continues until there is a winner. \
What\'s Bob\'s probability of winning?

Let $$P(H) = p$$ be the probability that we have a head and $$P_B$$ be Bob's probability of winning, the probability that the coin comes out tail $$P(T)$$ is then $$(1-p)$$. Bob wins at $n$-th time if **all the previous $$(n-1)$$ tosses** come out either two heads or two tails. $$P_B$$ is the sum of probability that Bob wins at $$n$$-th time, for $$n$$ runs from $$1$$ to $$\infty$$.

$$
\begin{align*}
    P_B & = \sum_{n=0}^{\infty} (P(H)P(H) + P(T)P(T))^n P(T)P(H) \\
    & = \sum_{n=0}^{\infty} (p^2 + (1-p)^2)^n (1-p)p \\
    & = (p-p^2) \sum_{n=0}^{\infty} (2p^2 - 2p + 1)^n \\
\end{align*}
$$

Recall that for $$t \in \mathbb{R}$$ we have:
$$1+t+t^2+...+t^n = \frac{1-t^{n+1}}{1-t}$$

Thus,
$$\sum_{n=0}^{\infty} (2p^2 - 2p + 1)^n = \lim_{n \to \infty} \frac{1 - (2p^2-2p+1)^{n+1}}{1 - (2p^2-2p+1)} = \lim_{n \to \infty} \frac{1 - (2p^2-2p+1)^{n+1}}{2p-2p^2}$$

We have $$2p^2-2p+1 = 2p(p-1)+1 < 1$$ since $$2p(p-1) < 0$$, as $$p<1$$. Hence $$(2p^2-2p+1)^{n+1} \to 0$$ as $$n \to \infty$$. Hence $$\sum_{n=0}^{\infty} (2p^2 - 2p + 1)^n = \frac{1}{2p-2p^2}$$.

Hence,
$$
\begin{align*}
    P_B & = (p-p^2)\frac{1}{2p-2p^2} = \frac{1}{2}
\end{align*}
$$

Therefore, regardless of the probability that the coin comes out head, Bob always has $$50\%$$ chance of winning.