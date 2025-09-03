# Linear approximation using the mean value theorem

we know that $\cos(x)$ is very close to $1$ for $x$ near $0$. But this is not a very useful statement from a computational perspective. Is $1$ small enough for this approximation to be good? First recall:

````{prf:lemma} Mean Value Theorem
Suppose that $f: (-a,a) \to \mathbb{R}$ is differentiable. For any $x > 0$ there is a number $c$ strictly between $x$ and $0$ such that 
```{math}
    f(x) = f(0) +f'(c)x  \;. 
```
Similarly, for any $x < 0$, there is a number $c$ strictly between $x$ and $0$ such that 
```{math}
    f(x) = f(0) + f'(c) x \;. 
```
````


If we apply the statement to the question of estimating $\cos(x)$, notice we would get
```{math}
    |\cos(x) - 1| = |\cos(x) - \cos(0)| = |-\sin(c)x| \leq |x| 
```
since $|\sin(c)| \leq 1$. That is, we can guarantee that $\cos(x)$ is near $1$ with an error of $|x|$. In other words, we know that $\cos(1) = 1 \pm 1$, not *super* useful, but at least we can guarantee that $\cos(1) \geq 0$. 

So a constant approximation gives us some information, but it is not enough information to give us a precise approximation of $\cos(1)$.