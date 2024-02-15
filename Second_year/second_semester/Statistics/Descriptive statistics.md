

# Frequency tables

# Graphical representations

- Bar charts
- Pie charts
- Histogram
- Box-plots

The appropriate graph representation will depend on the type of variable
- If the variable is qualitative or quantitative discrete $\rightarrow$ bar char
- If the variable is quantitative continuous $\rightarrow$ box-plot

## Bar chart

It's an x-y representation, where we'll put the different values that we have on the dataset at the X axis and the frequencies at the Y axis. For each value we have a bar whose height will be proportional to its frequency (we can use the absolute or relative frequencies, not the cumulative frequencies).

## Pie chart

In a pie chat we divide a circle in as many sections as different values in the dataset. The area associated to each value should be proportional to the frequency of that value. We need to know the number of degrees associated with the sector. Then, fi \* 360. The category should be exhaustive, so the data must be exclusive.

## Histograms

It's an X-Y representation. In the x axis we represent the values grouped into intervals, and on each interval we draw a rectangle whose height is related to the frequency . Three types:
- **Frequencies**: The height is the number of data
- **Percentage**: The height is the proportion of data within the interval
- **Densities**: The area is the proportion within the interval

## Box-plot

It's a graphical representation for a quantitative continuous variables, depicting a few descriptive measures. We have a box from $Q_{1}$ to $Q_{3}$, showing the value o fi the median inside
The **whiskers** go until the smallest and largest data that are NOT outliers. An observation is an outlier if it's outside the interval \[$Q_{1} - 1.5*IQR, Q_{3} + 1.5*IQR$]. Any value out of that range is considered as an outlier and it's represented with a circle 

# Descriptive measures

They're values that provides some kind of information about the data. 3 types:
- **Measures of central tendency** $\rightarrow$  they hive the central value of the dataset
- **Measures of position** $\rightarrow$ We order the data and give the ones in particular positions
- **Measures of dispersion** $\rightarrow$ Tell us the if the values in the dataset are similar or not

## Measures of central tendency

- **Arithmetic mean** or **average**: Gives the 'most important' or central value in the sample. If the dataset is x1, x2, .... , xn
$$\text{Mean(X)} = \frac{x_{1}\text{ +  ... + }x_{n}}{n}$$
	It's always $\text{min} \leq \text{\=X} \leq \text{max}$ 
	We can only compute it with quantitative variables
	If we add a constant K to all data, the new mean is the prev one plus K (same for multiplying)
	It's **very** sensitive to **outliers** (data much greater or smaller than the rest)
	
- **Median**: Value occupying the central position in the ordered sample
	If n is odd:	$X(\frac{n +1}{2})$
	If n is even: $\frac{X(\frac{n}{2}) + X(\frac{n}{2} + 1)}{2}$
	With the freq table, we look at the cumulative relative frequencies
		 $\rightarrow$ If $F_{i-1} \textless 0.5 \textless F_{i}$ 
		 $\rightarrow$ If $F_{i} = 0.5$, then $Me = \frac{x_{i} + x_{i+1}}{2}$
		 $\rightarrow$ $\text{min} \leq \text{Me} \leq \text{max}$
		 $\rightarrow$ We compute it with quantitative variables
		  $\rightarrow$ If we add a constant K to all data, the new is the prev plus K (same for multiplying)
		   $\rightarrow$ Less sensitive to **outliers** than the mean

- **Mode**: It's the value that appears more frequently in the dataset. We pick the value associated with the highest absolute or relative frequency. We can also obtain the mode with qualitative values. It's not sensitive to outliers.

## Measures of position

Gives values occupying other positions. We fix a proportion $\alpha$ in \[0,1]. The $\alpha$-quantile is the value with a proportion $\alpha$ of data below in the ordered sample (and 1-$\alpha$ above )
As particular cases:
$\rightarrow$ $\alpha$ = 0.5 => the median (Me)
$\rightarrow$ $\alpha$ = 0.25 => the first quartile ($Q_1$) 
 $\rightarrow$ $\alpha$ = 0.75 => the third quartile ($Q_3$)
 $\rightarrow$ If $\alpha$ = $\frac{j}{100}$ for  j $\in$ {0,1,...,99,100} => the percentile j ($P_j$)

To compute the $\alpha$-quantile, we look for $\alpha$ in the cumulative relative frequencies
$\rightarrow$ If $F_{i-1} < \alpha < F_{i}$, the quantile is $X_i$
$\rightarrow$ If $F_i = \alpha$, the quantile is $\frac{X_{i}+X_{i+1}}{2}$

## Measures of dispersion

They provide information about the degree of variability in the sample. They measure if the values in the dataset are similar or not.
They're five:
### The range

It's the difference between the maximum value on the dataset and the minimum one.
It's sensitive to outliers

### The inter-quartile range (IQR)

It's the difference between the third and first quartiles: **IQR = Q3 - Q1**. It's not sensitive to outliers

### Variance

Average of the square distances to the mean ($s^2$)
$$\text{Var(X) = } \sum{}{}(X - \mu)^2$$
If we multiply all data by K, the new variance is the one before times $K^{2}$ 

### The standard deviation

$$s = + \sqrt{s^2}$$

If we multiply all the data by K, the new standard deviation is the one before times |K|













# Exercises


### Ex 4

| Variable | Type | Graph |
| ---- | ---- | ---- |
| Oven brand | Qualitative (categorical) | Bar chart / Pie chart |
| Lifetime | Quantitative (continuous) | Histogram / Box plot |
| Number of breakdowns | Quantitative (discrete) | Bar chart / Pie chart  |
| Exam marks | Qualitative (ordinal) | Bar chart / Pie chart |

### Ex 5

n = 2000
1 test $\rightarrow$ 5% (0.05) $\rightarrow$ fi \* n = 100
2 test $\rightarrow$ 10% (0.1) $\rightarrow$ fi * n = 200
3 test $\rightarrow$ 80% (0.8) $\rightarrow$ fi \* n = 1600 
4 test $\rightarrow$ 5% (0.05) $\rightarrow$ fi \* n = 100

| Xi | ni | fi | Ni | Fi |
| ---- | ---- | ---- | ---- | ---- |
| 1 | 100 | 0.05 | 100 | 0.05 |
| 2 | 200 | 0.1 | 300 | 0.15 |
| 3 | 1600 | 0.8 | 1800 | 0.95 |
| 4 | 100 | 0.05 | 2000 | 1 |

```chart
	type: bar
	labels: [1,2,3,4]
	series:
	 - title: Tires
	 - 
```

### Ex 7
| xi | fi | Fi |
| ---- | ---- | ---- |
| 40 | 0.45 | 0.45 |
| 50 | 0.35 | 0.8 |
| 60 | 0.2 | 1 |

- Average  $\rightarrow \text{\=X} = 40 * 0.45 + 50 * 0.35 + 60  * 0.2 = 47.5$
- Median   $\rightarrow$ We look into the freq table for the value 0.5. As it does not appear, we take the next bigger value (Me = 50)
### Ex 9

n=50
$f_{i} = \frac{n_{i}}{n}$   $F_{i} = \frac{N_{i}}{n}$

| xi | ni | fi | Ni | Fi |
| ---- | ---- | ---- | ---- | ---- |
| 0 | 4 | 0.08 | **4** | 0.08 |
| 1 | 5 | **0.1** | 9 | 0.18 |
| 2 | 9 | 0.18 | 18 | **0.36** |
| 3 | 22 | 0.44 | **40** | 0.8 |
| 4 | **6** | 0.12 | 46 | 0.92 |
| 5 | 4 | 0.08 | 50 | 1 |

Mode = 3      Me = 3      Mean = $\frac{0 * 0.8 + 1 * 0.1 + 2 * 0.18 + 3 * 0. 44 + 4 * 0.12 + 5 * 0.08}{50}$ = 2.66

### Ex 10

Values: 2 0 0 1 3 1 0 0 0 2 3 3 3 2 1 0 0 0 1 0

Freq. table

| Xi | ni | fi | Ni | Fi |
| ---- | ---- | ---- | ---- | ---- |
| 0 | 9 | 0.45 | 9 | 0.45 |
| 1 | 4 | 0.2 | 13 | 0.65 |
| 2 | 3 | 0.15 | 16 | 0.8 |
| 3 | 4 | 0.2 | 20 | 1 |

Pie chart
To obtain the degrees corresponding to each value by multiplying 360\*fi

Percentile 60 ($P_{60}$). This percentile corresponds to $\alpha = 0.6$
We look for the value 0.6 at the Fi column and, if we can't find it, we can just take the next value over 0.6 (1 in this case)

### Ex 12

Table of frequencies:

| xi | ni | fi | Ni | Fi |
| ---- | ---- | ---- | ---- | ---- |
| -1 | 1 | 0.033 | 1 | 0.033 |
| 0 | 2 | 0.066 | 3 | 0.1 |
| 1 | 4 | 0.133 | 7 | 0.233 |
| 2 | 5 | 0.166 | 12 | 0.4 |
| 3 | 6 | 0.2 | 18 | 0.6 |
| 4 | 4 | 0.133 | 22 | 0.733 |
| 6 | 4 | 0.133 | 26 | 0.866 |
| 9 | 1 | 0.033 | 27 | 0.966 |
| 10 | 3 | 0.1 | 30 | 1 |

Mode = 3
Median = 3, since $F_{2} < 0.5 < F_{3}$
$P_{35}$ = $q_{0.35}$, $\alpha = 0.35$ = 2, since  $F_{1} < 0.35 < F_{2}$
Avg = 
$$\text{\=X = } \frac{-1*1 + ... + 10*3}{30} = 3.67 $$

### Ex 13

| mean | sd | 0% | 25% | 50% | 75% | 100% | n |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 55.9 | 56.53001 | 4.4 | 22.2 | 36.6 | 73.7 | 209.9 | 101 |

a) Mean and median
	Mean = 55.9, Median = 36.6
b) 
