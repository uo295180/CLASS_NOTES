
# Notable discrete distributions

## Binomial distribution


## Poisson distribution

Appears with the law of rare events. It can be seen as the limit of a binomial distribution B(n, p) where n $\rightarrow$ +$\infty$, p $\rightarrow$ 0 and n\*p = $\lambda$.

It also happens in queuing systems to model the number of arrivals to a service in a time interval. To have a Poisson distribution, the following conditions must be hold:
- The expected number of arrivals only depends on the length of the time interval 
- The number of arrivals in different points of the interval are independent random variables
- The probability of two simultaneous arrivals is 0
If this conditions holds, the distribution of the number of arrivals must be a Poisson distribution.
X follows a Poisson distribution with parameter $\lambda$. We denote it  X~P($\lambda$) and its probability mass function is P(P($\lambda$) = K) = $e^{-\lambda}*\frac{\lambda ^{K}}{K!}$ for K = 0, 1, 2, 3...

E(X) = $\lambda$ = Var(X)


# Exercises 

## 5

P(being defective) = 0.05
a) probability of not having to inspect the whole batch:

P(NOT having to inspect the whole batch) $\rightarrow$ P(at most 2 defective components out of 30) $\rightarrow$ P(B(30, 0.05) $\leq$ 2) $\rightarrow$ P(B(30, 0.05) = 0) + P(B(30, 0.05) = 1) + P(B(30, 0.05) = 2) $\rightarrow$ **0.8121**.

b) the probability distribution of the random variable "number of components examined"

| x    | f(x)                |
| ---- | ------------------- |
| 30   | 0.8121              |
| 1000 | 1 - 0.8121 = 0.1879 |
c) expected number of components examined per batch
E(X) = 30\*0.8121 + 1000\*0.1879 = 212.263

## 7

The number of breakdowns in an information system is a random variable X following a Poisson distribution with parameter 2 ($\lambda$ = 2)

a) Expected number of breakdowns $\rightarrow$ E(X)  = 2

b) What's the probability that the number of breakdowns is between 1.5 and 3.7

P(1.5 $\leq$ X $\leq$ 3.7) = P(X=2) + P (X=3) = $e^{-2}*\frac{2^{2}}{2!} + e^{-2}*\frac{2^{3}}{3!}$

c) P(-2.24 $\leq$ X $\leq$ 6.24) = $\sum^{6}_{k=0}$ P(X = K) = $\sum^{6}_{k=0} e^{-2}*\frac{2^{k}}{k!}$ = 0.9955

## 8
P(0.3\*t)

a) Two incoming messages in a period of 2 sec

Two messages in 10 seconds follows ~P(0.3\*10)

P(Y = 2) = $e^{-3}*\frac{3^{2}}{2!}$  = 0.224

b) Number of messages in 5 messages between 2 and 4

It follows ~P(1.5)
P(2 $\leq$ Z $\leq$ 4) $\rightarrow$ P(Z = 2) + P(Z = 3) + P(Z = 4) = $e^{-1.5}*\frac{1.5^{2}}{2!} + e^{-1.5}*\frac{1.5^{3}}{3!} + e^{-1.5}*\frac{1.5^{4}}{4!}$

c) P more than 4 seconds pass between two messages. This is the same as say that in 4 seconds there was no messages. 
It follows ~P(0.3\*4) 
P(P(1.2) = 0) = $e^{-1.2}*\frac{1.2^{0}}{0!}$ = 0.301

## 12

X = diameter ~ N(20, 0.01)
Specifications 20.015 +- 0.025 = \[19.99, 20.04]

a) P(19.99 $\leq$ X $\leq$ 20.04) = P(19.99 $\leq$ N(20, 0.01) $\leq$ 20.04) = P($\frac{19.99 - 20}{0.01} \leq \frac{N(20, 0.01) - 20}{0.01} \leq \frac{20.04 -20}{0.01}$) = P(-1 $\leq$ N(0, 1) $\leq$ 4) = P(N(0, 1) $\leq$ 4) - P(N(0, 1) $\leq$ -1)

>[!Important]
>$$\frac{N(\mu, \delta) - \mu}{\delta} ~ N(0, 1)$$


P(N(0, 1) $\leq$ 4) = 1
P(N(0, 1) $\leq$ -1) = P(N(0,1) $\geq$ 1) = 1 - P(N(0, 1) $\geq$ -1) = 1 - 0.8413 = 0.1587

 P(N(0, 1) $\leq$ 4) - P(N(0, 1) $\leq$ -1) = 1 - 0.1587 = 0.8413

b) Now X ~ N(20.015, 0.015)

 P(19.99 $\leq$ X $\leq$ 20.04) = P($\frac{19.99 - 20.015}{0.015} \leq \frac{N(20.015, 0.015) - 20.015}{0.015} \leq \frac{20.04 -20.015}{0.015}$) = P(-2.5 $\leq$ N(0, 1) $\leq$ 2.5) = P(N(0, 1) $\leq$ 2.5) - P(N(0, 1) $\leq$ -2.5)

P(N(0, 1) $\leq$ 2.5) = 0.9938
P(N(0, 1) $\leq$ -2.5) = P(N(0,1) $\geq$ 2.5) = 1 - P(N(0, 1) $\geq$ -2.5) = 1 - 0.9938 = 0.0062

 P(N(0, 1) $\leq$ 2.5) - P(N(0, 1) $\leq$ -2.5) = 0.9938 - 0.0062 = 0.9876

## 13

X = amount of liquid ~ N(500, 50)

a) P(X > 550) = P(N(500, 50) > 550) = P(N(0, 1) > $\frac{550 - 500}{50}$) = P(N(0, 1) > 1) = 1 - P(N(0, 1) $\leq$ 1) = 1-0.8413 = 0.1587 

b) We're looking for K where The probability of a bottle having > K ml is 5%

Then, P(X > K) = 0.05 = P(N(500, 50) < K) = P(N(0, 1) > $\frac{K - 500}{50}$)

$\frac{K - 500}{50} = 1.64 \rightarrow K = 1.64 * 50 + 500 = 582$ 

c) Y = liquid ~ N($\mu$, 50)

P(Y - $\mu$ > 75) = P (Y > 75 + $\mu$) = P(N($\mu$, 50) > 75 + $\mu$) = P(N(0, 1) > $\frac{75 + \mu - \mu}{50}$)  =P(N(0, 1) > 1.5) = 1 - P(N(0, 1) $\leq$ 1.5)  = 1 - 0.9332 = 0.0668

## 23 
