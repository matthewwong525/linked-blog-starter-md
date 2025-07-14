- Discrete or Continuous
---

Random variable is a function that associates a real number to each element of the sample space of an experiment. It is usually denoted by 

A **random variable** is just a way to assign numbers to possible outcomes of something random.
    
This helps us **measure**, **analyze**, and **make predictions** using probability and statistics.
    
It’s often written with capital letters like **X**, **Y**, or **Z**.

## Example #1
In tossing a coin twice, let $X$ be a random variable that indicates the number of heads. What are the possible values of $X$?

In tossing a coin twice, let $Y$ be the value in multiplying the number of tails with $3$ then subtract it by $1$.

In tossing a coin twice, let $Z$ be the value of the square root of the number of heads minus one.

| s   | hh           | ht           | th           | tt           |
| --- | ------------ | ------------ | ------------ | ------------ |
| z   | $\sqrt{2-1}$ | $\sqrt{1-1}$ | $\sqrt{1-1}$ | $\sqrt{0-1}$ |
|     | $            |              |              |              |


## Example #2
In tossing a coin twice, let $Y$ be a random variable that is 1 if the result is a double and 0 otherwise. What are the possible values of $Y$?

## Example #3
In a deck of cards, there are numbers, aces, and faces. If 10 cards are randomly selected, and the random variable $X$ is defined as the number of faces, what are the possible values of $X$?

## Example #4
In a deck of cards, there are numbers, aces, and faces. If 10 cards are randomly selected, and the random variable $Y$ is defined as the number of aces, what are the possible values of $Y$?

## Example #5
**Identify if it is random variable or not.**

$W$ - the number of students who are absent from the class
$X$ - the weight (in kg) of randomly selected student from the class.
$X_1$ - the name of the mayors from each city of NCR.
$X_2$ - daily temperature (in Celsius) of Japan for a week
$Z$ - the square root of daily temperature (in Celsius) of Japan for a week.


---

# Discrete Random Variable
- a random variable is said to be discrete if it could take on only a **finite** of **countably infinite** number of possible values.


# Continuous Random Variable
- a random variable is said to be continuous if it could take on any value within a given **finite** or **infinite** range of possible values.



## Example 6
**Identify if it is discrete or continuous.**

$W$ - the number of students who are absent from the class
$X$ - the number of wrong answers in am multiple-choice test
$Y$ - the amount of time (in minutes) it took a student to complete a test
$Z$ - the weight (in kilograms) of a randomly selected student from the class
$X_1$ - the number of raffle tickets sold for a fund drive
$X_2$ - the number of missed shots before a successful shot in a basketball game
$X_3$ - the age (in years of randomly selected employee) of a large supermarket chain
$X_4$ - the number of coin tosses until a tail shows up

---
# Probability Distribution Function
*Probability mass function (pmf)*
*Probability density function (pdf)*

## Probability Mass Function (pmf)
- The probability mass function (pmf) of a discrete random variable $X$ is a listing of all possible of $X$ and their corresponding probabilities.

--- start-multi-column: ID_u1nu
```column-settings
Number of Columns: 2
Largest Column: standard
```

**Formula Form**
$$p(x)=\begin{cases}
P(X=x)&\text{if } x=x_1, x_2, x_3, \dots, x_k \\
0& \text{otherwise}
\end{cases}$$

--- column-break ---

**Tabular Form**

| $x$     | $p(x)$   |
| ------- | -------- |
| $x_1$   | $p(x_1)$ |
| $x_2$   | $p(x_2)$ |
| $x_3$   | $p(x_2)$ |
| $\dots$ | $\dots$  |
| $x_k$   | $p(x_k)$ |

--- end-multi-column

## Properties of PMF
1. **Non-negative Property**
	$$p(x)\geq 0$$
2. **Norming Property**	$$\sum_{i=1}^{k}p(x_i)=1$$
## Example 7
A fair die is rolled once. Let $X$ be the number of dots on the upturned face
a. Give the pmf of $X$ in formula form
b. Give the pmf of $X$ in tabular form
c. Draw the probability histogram of $X$

## Example 8
A box contains three red marbles and four green marbles. Jayvee picks two marbles at random from this box.
a. Give the pmf of the number of red marbles picked from the box.
b. Give the corresponding probability histogram.

## Example 9
Tweet, a quality control engineer of a large computer firm, inspects a large shipment of printed circuit boards (PCB). The shipment of 1000 PCBs were inspected for defects such as misplaced components of the application of too much solder paste. Tweet found that 750 of the PCBs haven o defects, 100 with a defect each, 75 have two defects each, 50 have three defects each, and the rest have 5 defects each. Give the probability mass function of $X$, the number of defects found in a PCB, in tabular form.

## Example 10
Find the missing value for $P(X=7)$ in the probability distribution of $X=\text{no.}$ of bell pepper from one plant.

| Probability distribution of $X$ |                    |
| ------------------------------- | ------------------ |
| $x$                             | Probability $p(x)$ |
| $2$                             | $0.5$              |
| $4$                             | $0.4$              |
| $7$                             |                    |
| $8$                             | $0.07$             |

## Example 11
Let $X$ be the number of children ages $13$ and below in a household. Find the value $c$?

| $x$    | $1$ | $2$     | $3$    | $4$    | $5$    |
| ------ | --- | ------- | ------ | ------ | ------ |
| $p(x)$ | $c$ | $0.20c$ | $0.30$ | $0.05$ | $0.10$ |

---

## Probability Density Functions (pdf)
It is the probability distribution for continuous random variables.
The curve of pdf lies above the horizontal axis and bounds an area equal to $1$ above the said axis.
![[Pasted image 20250511154727.png]]

## Properties of pdf
1. **Non negativity property**
	- The graph of $f(x)$ lies above the $x\text{-axis}$.
2. Norming Property
	- The total area under the curve of $f(x)$ above the $x\text{-axis}$ is $1$.

## Example 12
$$
f(x)=
\begin{cases}
 x-1&\text{if } 1.5 \leq x \leq 2.5 \\ 0&\text{otherwise}
\end{cases}
$$
a. Verify that $f(x)$ satisfies the properties of pdf
b. Find $P(1.5 \leq X \leq 2)$
c. Find $P(X = 2)$



# Lecture 2. Mean and Variance of a Discrete Random Variable
Example 1. Let $X$ be a discrete random variable with probability mass function given by the table below.


| $x$    | $-1$          | $0$           | $2$           | $4$           |
| ------ | ------------- | ------------- | ------------- | ------------- |
| $p(x)$ | $\frac{1}{7}$ | $\frac{3}{7}$ | $\frac{2}{7}$ | $\frac{1}{7}$ |
**Give the probability that $x$ assumes a positive value**
$$P(x=)$$![[Screenshot 2025-05-19 at 1.07.04 PM.png]]

![[Screenshot 2025-05-19 at 1.39.09 PM.png]]


# Discrete Probability Distribution
