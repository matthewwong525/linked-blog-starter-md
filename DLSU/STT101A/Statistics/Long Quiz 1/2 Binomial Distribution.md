## Definition
In order to be a binomial distribution it must satisfies these four cases (BINS):

**B** - Binary Outcomes
- There are only two outcomes either success (occur) or failure (does not occur)
**I** - Independent Trials
- The success or failure of one event must not somehow affect the success or failure of any other event.
**N** - Number of Trials
- Must have defined $N$ number of trials
**S** - Same $p$ per trial.
- Each trial must have the same probability of success each time.

## Properties
where $x$ = value of a random variable, $\mu$ = mean, $n$ = no. of trials, $p$ = prob. of success, $q$ = prob. of failure.

| Properties         | Formula                                                            |                                                              |
| :----------------- | :----------------------------------------------------------------- | :----------------------------------------------------------- |
| Mean               | $\mu=n\cdot p$                                                     |                                                              |
| Standard Deviation | $\sigma=\sqrt{n\cdot p \cdot (1-p)}$                               |                                                              |
| Probability        | $P(X=x)=\left(\begin{array}{c} n \\ x\end{array}\right)p^xq^{n-x}$ | To calculate probability of getting $x$ number of successes. |

## Probability Property
$$P(X=x)=\left(\begin{array}{c} n \\ x\end{array}\right)p^xq^{n-x}$$
**Example**
1. Rolling a die 4 times. What is the probability of rolling a 1 twice?$$p^xq^{n-x}=\left(\frac{1}{6}\right)^2 \left(\frac{5}{6}\right)^2$$Expanded to$$\left(\frac{1}{6}\right)\left(\frac{1}{6}\right)\left(\frac{5}{6}\right)\left(\frac{5}{6}\right)$$In this order, we find the probability of getting success on the 1st, and 2nd roll, and failure on the 3rd, and 4th roll.
	
	The right side is used to calculate the probability of one specific situation that safitisfies our desired outcome of rolling a one twice.
	
	But what if the arragement goes like:
	$$\left(\frac{5}{6}\right)\left(\frac{5}{6}\right)\left(\frac{1}{6}\right)\left(\frac{1}{6}\right)$$
	To account for all these possibilities, we refer to the notation $$\left(\begin{array}{c} n \\ x\end{array}\right)$$which is pronounced as "$n$ choose $x$". This number gives us the **total** number of ways we can write the desired outcome. In other words, out of our $n$ trials, how many ways are there to have $x$ successes.
	
	To calculate $n$ choose $x$, we refer the notation to a factorial formula $$\frac{n!}{(n-x)! x!}$$Therefore, when evaluated, it becomes $$\left(\begin{array}{c}4 \\ 2\end{array}\right)=\frac{4!}{(4-2)!2!}=\frac{4\cdot3\cdot2\cdot1}{(2\cdot1)(2\cdot1)}=\frac{24}{4}=6$$ It means that there are $6$ different ways to roll a **one** twice.
	When combined, we have $$6\left(\frac{1}{6}\right)^2\left(\frac{5}{6}\right)^2=0.1157$$ It means that there are $0.1157$ probability chance that rolling **one** twice in **four** rolls.