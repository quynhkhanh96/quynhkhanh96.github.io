---
layout: post
title: "Probability Puzzles - Easy Peasy level"
categories: fun math problems
---
This post contains my solutions to problems, Easy Peasy level from an app called [Probability Math Puzzles](https://play.google.com/store/apps/details?id=atorch.statspuzzles&pli=1).


![dice](/assets/images/probability_puzzles.png){:style="display:block; margin-left:auto; margin-right:auto"}

### **Puzzle 10 (incomplete)**
> You\'ve stolen from the king and been thrown in jail. The king is magnanimous, however, and rather than having you drawn and quartered on the spot, he allows you to play a little game. \
You\'re given 100 marbles; 50 black and 50 white - and you must place them in two urns, in any way you like, as long as you obey the king\'s rules. \
You must place all the marbles, and neither urn can be left empty. Each urn will be shaken so that the marbles are all jumbled up - the order in which you place them doesn\'t matter. \
The king will then follow a simple procedure: he will pick an urn uniformly at random (i.e., either one is equally likely to be chosen); and from that urn, he will draw a marble uniformly at random. If it\'s white, you live; but if it\'s black, you\'ll be fed to the lions, or perhaps drawn and quartered - the king hasn\'t yet made up his mind. \
You could place all the white marbles in one urn, and all the black in the other, in which case your chances are fifty-fifty - but you can do better than that! If you place the marbles in the best way possible, what is your probability of survival?

Note that we don't have partition the marbles equally into two urns and the best chance of survival is when we place 1 white marble into one urn and the rest (99 marbles, including 49 white marbles and 50 black ones) into the other urn. (I\'ll add proof for this later I guess :sweat:)

We\'ll survive if one of the two scenarios below happens:
- The king picks the urn with one white marble ($$50\%$$ chance), the probability he\'ll retrieve a white marble is $$100\%$$.
- The king picks the urn with 99 marbles (also $$50\%$$ chance), the probability he\'ll retrieve a white marble is $$\frac{49}{99}$$

The probability of survival with that setting is then $$\frac{1}{2} + \frac{1}{2}\cdot\frac{49}{99} \approx 0.7475$$

### **Puzzle 11**
> Two friends, Alice and Bob, have found an unfair coin: it has a $$72\%$$ chance of coming up heads. I have no idea what such a coin would look like, but let\'s just pretend it exists. \
Alice proposes a game: she\'ll toss the coin twice; if it comes up heads then tails, she wins; if it\'s the reverse (tails then heads), Bob wins; and if neither of those two things happens, the game restarts, and continues until there is a winner. \
What\'s Bob\'s probability of winning?

Let $$P(H) = p$$ be the probability that we have a head and $$P_B$$ be Bob's probability of winning, the probability that the coin comes out tail $$P(T)$$ is then $$(1-p)$$. Bob wins at $$n$$-th time if **all the previous $$(n-1)$$ tosses** come out either two heads or two tails. $$P_B$$ is the sum of probability that Bob wins at $$n$$-th time, for $$n$$ runs from $$1$$ to $$\infty$$.

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