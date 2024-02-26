
# Random variables
## Continuous random variables
## Independent random variables

We say that two variables X, Y are *independent* if knowing the value of one of them does not change the probability distribution of the other. This means that for any pair of events A, B, P($X \in A$, $Y \in B$) = P($X \in A$)\*P($Y \in B$). In particular, P(X=x, Y=y) = P(X = x)\*P(Y = y)

# Binomial distribution

We make independent repetitions of an experiment, and count in how many repetitions an event happens.
If we make **n** repetitions, and in each repetition the probability of the event **p**, we say that X follows a binomial(n, p), and denote it **$$X~B(n,p)$$**
The probability mass function is **P( B(n,p) = k )**

>[!Example]
>P(3 heads in 5 tosses) = $p^{3}*(1-p)^{2}$ (number of sequences)
>p=P(heads)
>1 - p = P(tails)
>HHHTT $\rightarrow$ p\*p\*p\*(1-p)\*(1-p) = $p^{3}*(1-p)^{2}$

Then, the probability mass function is $$P(B(n,p)=k)= ({n\choose k}*p^{k}*(1 - p)^{n-k})$$
for k= 0, 1, 2, 3......, n












# Exercises

## Chevalier de Meré's problem

**Problem:** The probability of getting a double 6 when tossing two dies is 1/6 the probability of getting a 6 when tossing a die. Does this mean that it is equivalent betting that we shall get at least one 6 in 4 tosses to betting that we get at least one double 6 in 4x6=24 tosses?

We throw a dice 4 times. Number of 6 = B(4, $\frac{1}{6}$)
P(at least one 6) = P(B(4, $\frac{1}{6}$) $\neq$ 0) = 1 - P(B(4, $\frac{1}{6}$) = 0) =1 - $({4\choose 0})*(\frac{1}{6})^{0}*(\frac{5}{6})^{4}$ 

We cast two 24 times. Number of double 6 ~ B(24, $\frac{1}{36}$)

P(at least one double 6) = P(B(24, $\frac{1}{36}) \neq 0$) = 1 - P(B(24, $\frac{1}{36}) = 0$) =  1 - $({24\choose 0})*(\frac{1}{36})^{0}*(\frac{35}{36})^{24}$ = 0.4914

If X ~B(n, p), $E(X)$ = $\sum_{k = 0}^{n}k*({n \choose k}) * p^{k}*(1 - p)^{k-n}$

## 3.2
| profit | prob  |
| ------ | ----- |
| 30     | 5/37  |
| 0      | 7/37  |
| -5     | 19/37 |
| -10    | 6/37  |
b) P(winning) = $\frac{5}{37}$
c) X = number of times we win something ~ B(2, $\frac{5}{37}$)
P(X=1) = $({2\choose 1})*\frac{5}{37}*\frac{32}{37}$ = 0.233

## 3.4

We assume 52 cards

a)

P(winning) = P(drawing a king or an ace) = $\frac{8}{52} = \frac{2}{13}$
X = number of kings or aces Bob draws ~ B(3, 2/13)
P(going to Cannibal Holocaust)  = P(B(3, 2/13) $\geq$ 1) =  1 - P(B(3, 2/13) = 0) = $1 - ({3 \choose 0})*(\frac{2}{13})^{0}*(\frac{11}{13})^{3} = 0.3942$

b) 

If he draws n cards, P(winning the game) =
P(B(n, 2/13) $\geq$ 1) =  1 - P(B(n, 2/13) = 0) = 1 - $(\frac{11}{13})^{n}$

now $1 - (\frac{11}{13})^{n} \geq 0.5$ = $n*\log{(\frac{11}{13})} \leq \log{(0.5)}$ = n $\geq \frac{\log{(0.5)}}{\log{(\frac{11}{13})}} = 4.15 \rightarrow$ he needs at least 5 cards 

