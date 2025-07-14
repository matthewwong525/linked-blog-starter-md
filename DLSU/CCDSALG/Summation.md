

$$\sum_{j=5}^{2n}=?$$

$$k=\frac{n(n+1)}{2}$$


IF IM USING $$k=\frac{n(n+1)}{2}$$im just gonna replace $n$ with upper bound $2n$ now how am i going to apply $j=5$?

should be  $$\sum_{j=1}^{5}=\frac{5(5+1)}{2}=15$$



# Updated Loop Cheatsheet Comparison

| Loop Name  | Comparison | Types              | Formula                                                |
| ---------- | ---------- | ------------------ | ------------------------------------------------------ |
| `for`      | $>=$ $<=$  | Loop<br>Statements | $\text{ub}-\text{lb}+2$<br>$\text{ub}-\text{lb}+1$     |
| `for`      | $>$ $<$    | Loop<br>Statements | $\text{ub}-1-\text{lb}+2$<br>$\text{ub}-1-\text{lb}+1$ |
| `while`    | $>=$ $<=$  | Loop<br>Statements | $\text{ub}-\text{lb}+2$<br>$\text{ub}-\text{lb}+1$     |
| `while`    | $>$ $<$    | Loop<br>Statements | $\text{ub}-\text{lb}+1$<br>$\text{ub}-\text{lb}$       |
| `do-while` | $>=$ $<=$  | Loop<br>Statements | $\text{ub}-\text{lb}+1$<br>$\text{ub}-\text{lb}+1$     |
| `do-while` | $>$ $<$    | Loop<br>Statements | $\text{ub}-\text{lb}$<br>$\text{ub}-\text{lb}$         |
