
It's the mathematical tool we use to measure the likelihood of the different results of an experiment.

We denote by $\Omega$ the set of possible outcomes. A subset of $\Omega$ is called an event, and a *probability measure* will assign a value between  0 and 1 to any event. We will make *combinations* of events:
- $A\cup B$ (union) : either A or B (or both) happen
- $A \cap B$ (intersection): Both A and B happen
- $A \backslash B$ (difference): A happens, B does not
- $A^{C}$ (complementary): A does not happen $\rightarrow$ $A\backslash B = A\cap B^{C}$

We denote by $\Omega$  the sure event (=all outcomes) and by $\phi$ the impossible event (=no outcome). A probability measure satisfies:
- P(A) belongs to \[0, 1]
- P($\Omega$) = 1 and P($\phi$) = 0
- If $A\subseteq B$ (when A happens, B happens), then P(A) $\leq$ P(B)
- If $A\cap B = \phi$, then P($A\cup B$) = P(A) + P(B)

From this we deduce that P($A\cup B$) = P(A) + P(B) - P($A\cap B$) for any pair of events
Also P($A^{C}$) = 1 - P(A) and P($A\backslash B$) = P(A) - P($A\cap B$)

# Seminar 12/02/24

How to compute the probability of an event A? 3 main interpretations

- *Classical*:
	$P(A) = \frac{\text{number of cases favorable to A}}{\text{total number of cases}}$
	$P(\text{greater than 3}) = \frac{3}{6}$
	$P(\text{even number}) = \frac{3}{6}$
	This assumes all results are equally likely. This makes sense in games of chance, but not in other contexts

- *Frequentist*:
	$P(A) = \lim_{n \to + \infty }$ (relative frequency of A in n trials)
	We can apply it if we have statistics, but some experiments cannot be repeated

- *Subjective*:
	P(A) is a measure of the evidence supporting A

## Conditional probability

The probability of B conditional to A is the probability that B happens, if we know that A has happened. We denote is $P(B|A)$, and compute it as $P(B|A) = \frac{P(B\cap A)}{P(A)}$. We apply it only if P(A) > 0
$$P(\text{even | grater than 3}) = \frac{P(\text{even and greater than 3})}{P(\text{greater than 3})} = \frac{2/6}{3/6} = \frac{2}{3}$$
## Independence

We say that A and B are independent when knowing that A has happened does  not change the probability of B:   P(B | A) = P(B). Using the formula of conditional probability, this is equivalent to $P(A\cap B) = P(A)*P(B)$. It's also equivalent to P(A | B) = P(A)
- If A, B are independent, so are $\neg A$ and $\neg B$ and so are  $\neg A | \neg B$
We say that events $A_{1}, A_{2}, ...., A_{n}$ are independent if for any $I\subset {1,..., n}$,
For example:
- $P(A_{1}\cap A_{2}) = P(A_{1}) * P(A_{2})$
- $P(A_{1}\cap A_{3}) = P(A_{1}) * P(A_{3})$
- $P(A_{2}\cap A_{3}) = P(A_{2}) * P(A_{3})$
- $P(A_{1}\cap A_{2}\cap A_{3}) = P(A_{1}) * P(A_{2}) * P(A_{3})$
Independence is NOT equivalent to pairwise independence

## Exercises

### 1
a) $F_{S} = F_{A} \cap F_{B} \cap F_{C}$
b) $F_{S} = F_{A} \cup F_{B} \cup F_{C}$
c) $F_{S} = F_{A} \cap F_{B} \cap F_{C} \cap (F_{D} \cup F_{E})$
d) $F_{S} = (F_{A} \cap F_{B} \cap F_{C} \cap F_{D})\cup F_{E}$
e) $F_{S} = (F_{A} \cup F_{B} \cup F_{C}) \cap ((F_{D} \cap F_{E}) \cup (F_{F} \cap F_{G}))$
f) $F_{S} = F_{A} \cup F_{B} \cup (F_{C} \cap F_{D} \cap (F_{E} \cup (F_{F} \cap F_{G})))$
### 2
P(A) = 0.25   $P(B^{C}) = \frac{3}{8}$    $P(A \cup B) = \frac{3}{4}$
$P(A \cap B) = P(A) + P(B) - P(A \cup B) = 0.25 + \frac{5}{8} - \frac{3}{4}  =\frac{1}{8}$

$P(\neg A \cap \neg B) = P(\neg(A\cup B)) = 1 - P(A\cup B) = \frac{1}{4} = A^{C} \cap B^{C}$

>[!De Morgan laws]
>$\neg (A \cup B) = \neg A \cap \neg B$
>$\neg (A \cap B) = \neg A \cup \neg B$

### 3 
P(A) = 0.5  P(B) = 0.3  P(A $\cap$ B) = 0.1

P(A | B) = $\frac{P(A\cap B)}{P(B)} = \frac{1}{3}$
P(B | A) = $\frac{P(B\cap A)}{P(A)} = 0.2$
$P(A | A\cup B) = \frac{P(A \cap (A \cup B))}{P(A\cup B)} = \frac{P(A)}{P (A\cup B)} = \frac{5}{7}$
$P(A | A\cap B) = \frac{P(A \cap (A \cap B))}{P(A\cap B)} = \frac{P(A\cap B)}{P (A\cap B)} = 1$
$$P(A\cap B | A\cup B) = \frac{P((A\cap B) \cap (A \cup B))}{P(A\cup B)} = \frac{P(A\cap B)}{P (A\cup B)} = \frac{1}{7}$$
### 5
P(A) = 0.8  P(B | A) = 0.625  P(B |$\neg$A) = 0.5
$$P(B | A) = \frac{P(B \cap A)}{P(A)} = \frac{P(B\cap A)}{0.8} = 0.625 \rightarrow P(B\cap A) = 0.5$$
$$P(B | \neg A) = \frac{P(B \cap \neg A)}{P(\neg A)} = \frac{P(B\cap \neg A)}{0.2} = 0.5 \rightarrow P(B\cap \neg A) = 0.1$$
$$P(A) = P(A\cap B) + P(A\cap \neg B) \rightarrow P(A\cap \neg B) = P(A) - P(A \cap B) = 0.3$$
$$P(\neg A \cap \neg B) = P(\neg A) + P(\neg A\cap B) = 0.2 - 0.1 = 0.1$$
$$P(A|B) = \frac{P(A\cap B)}{P(B)} = \frac{0.5}{P(B\cap A) + P(B\cap\neg A)} = \frac{5}{6}$$
