>[!Summary]
>- [ ] Descriptive statistics
>	- [ ] Types of variables
>	- [ ] Graphs
>	- [ ] Descriptive measures
>- [ ] Probability theory
>	- [ ] Product rule
>	- [ ] Law of total probability
>	- [ ] Bayer's rule
>- [ ] Random variables 
>	- [ ] Discrete
>	- [ ] Continuous
>	- [ ] Functions
>	- [ ] Parameters
>	- [ ] Distributions
>	- [ ] Central limit theorems




# Descriptive statistics

Goal: to summarize data

## Types of variables

- **QUALITATIVE** (Values are NOT numbers)
	- **CATEGORICAL** (There's not a natural order)
	- **ORDINAL** (Naturally ordered)
- **QUANTITATIVE** (Values are numbers)
	- **DISCRETE** (Countable values) $\rightarrow$ N
	- **CONTINUOUS** (Uncountable values) $\rightarrow$ R

|             | Categorical | Ordinal | Discrete | Continuous |
| ----------- | ----------- | ------- | -------- | ---------- |
| Frequencies | ni fi=ni/n  |         |          |            |
|             |             |         |          |            |
|             |             |         |          |            |
|             |             |         |          |            |
### Histogram

Freq: height = abs freq of interval
Perc: height = rel freq of interval
Densities: area = rel freq of interval
# Probability theory

Goal: to measure the likelihood of an event
- P(A) belongs \[0, 1]
- P($\Omega$)= 1, P($\empty$) = 0
- A <= B $\rightarrow$ P(A) <= P(B)
- A $\cap$ B = /0 $\rightarrow$ P(A $\cup$ B) = P(A) + P(B)
- P($\neg$A) = 1 - P(A)
- P(A$\cup$B) = P(A) + P(B) - P(A $\cap$ B)
- P(A | B) = $\frac{P(A\cap B)}{P(B)}$ A, B independent $\rightarrow$ P(A | B) = P(A)
- Product rule: P(A $\cap$ B)  = P(A | B) \* P(B) and P(A1 $\cap$ ... $\cap$ An)=P(A1)\*P(A1 | A)\*P(A3|A1 $\cap$ A2), .... P(An | A1 $\cap$ ... $\cap$ An-1)
- {A1, .... , An} partition of $\Omega$ $\rightarrow$ $\Omega$ = A1 $\cup$ ... $\cup$ An and Ai $\cap$ Aj = Empty set $\rightarrow$ Law of total probability $\rightarrow$ Bayer's rule

# Random variables

We aassume that the outcomes of the experiments are going to be numbers

Goal: to measure the probabilities of the outcomes of one particular experiment

## Types of variables

- **DISCRETE** (Countable values)
- **COUNTINUOUS** (Uncountable values)

## Distributions

### Discrete

- Binomial(n, p): we make n independent repetitions of the same experiment and count in how many of those repetitions an event happens. p=P(event happens in a repetition)
- Poisson($\lambda$): we count how many times an event happens in a time interval. $\lambda$ = E($\lambda$)

### Continuous

- Uniform(a, b): we pick a number at random between a, b
- Normal($\mu$, $\Phi$ ): height/weight/errors. $\rightarrow$ Symmetric with respect to $\mu$. Any distribution can be transformed into the standard normal distribution by $\frac{N(\mu,\Phi) - \mu}{\Phi}$ ~ N(0,1). $\rightarrow$ Central Limit Theorem: if X1, ... , Xn independent and identically distributed with  E(Xi)=$\mu$, SD(Xi)=$\Phi$ then $\frac{X1+...+Xn}{n} ~ N(\mu,\frac{\Phi}{\sqrt{n}})$ <- we use it if n >= 30, and $X1 + ... + Xn ~ N(n\mu, \Phi\sqrt{n})$ 
- Exponential($\lambda$): time until an event happens. -> Lack of memory (future independent of past)
- Weibull(K, $\lambda$): lifetime. If K > 1, the component deteriorates with time, if K < 1 it improves and if K = 1 it neither deteriorates or improves = exp($\frac{1}{\lambda}$)