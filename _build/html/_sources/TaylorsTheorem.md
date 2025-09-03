# Taylor's Theorem

What if we used quadratics? Or even higher degree polynomials? Taylor's Theorem gives us an answer to this problem: 

````{prf:theorem} Taylor's Theorem for estimating near $0$

Let $n \geq 0$ and suppose that $f:(-a,a) \to \mathbb{R}$ is $n+1$-times differentiable. For any $x > 0$ there is a number $c \in (0,x)$ such that 
```{math}
        f(x) &= f(0) + \frac{1}{1!}f'(0)x + \cdots + \frac{1}{n!}f^{(n)}(0)x^n + \frac{1}{(n+1)!}f^{(n+1)}(c)x^{n+1} \\
        &= \left(\sum_{k=0}^n \frac{f^{(k)}(0)}{k!} x^k \right) + \frac{f^{(n+1)}(c)}{(n+1)!}x^{n+1} 
```
where $n! = n \cdot (n-1) \cdots 2 \cdot 1$ and $0! := 1$. The same formula holds for $x <0$ where $c$ is taken in $(x,0)$ instead. 
````
So, if we apply our example of $f(x) = \cos(x)$, then we know that $f(0) = 1, f'(0) = -\sin(0) = 0, f''(0) = -\cos(0) = -1$, and $f'''(c) = \sin(c)$, by Taylor's Theorem for $n = 2$, we get that there is some $c \in (0,x)$ such that 
```{math}
    \cos(x) &= 1 + \frac{0 \cdot x}{1!} - \frac{x^2}{2!} + \frac{\sin(c)}{3!}x^3  \\
    &= 1 - \frac{x^2}{2} + \frac{\sin(c)}{6} x^3\;.
```
**NOTE: the constant $c$ depends on your choice of $x$**. That is, for different values of $x$, we will likely get different values of $c$. For $x = 1$, we get the estimate 
```{math}
    |\cos(1) - (1 - 1/2)| \leq \frac{1}{6}\sup_{t \in (0,1)}|\sin(t)| |1^3| \leq \frac{1}{6}\;.
```
So we know that $\cos(1) = \frac{1}{2} \pm \frac{1}{6}$. A much better estimate!  

In the next section, we will see graphically some examples of Taylor approximations.