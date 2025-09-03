# Proof of Taylor's Theorem

We now present a proof of Taylor's Theorem. 
````{prf:proof} 

We only prove the case $x >0$, since the case $x < 0$ is similar. Fix $n \geq 0$ and define the function
```{math}
        F(t) = f(x) - \sum_{k=0}^n \frac{f^{(k)}(t)}{k!}(x-t)^k \; (t \in [0,x]). 
```
For each $t \in (0,x)$, $F(t)$ gives us a polynomial estimate for $f(x)$. Our goal is to show that there is a constant $c \in (0,x)$ such that $F(0) = \frac{f^{(n+1}(c)}{(n+1)!}x^{n+1}$. Firstly note that since $x$ is a constant, for all $t \in (0,x)$, by a telescoping sum argument:
```{math}
    F'(t) &= -\sum_{k=0}^n \frac{f^{(k+1)}(t)}{k!}(x-t)^k + \sum_{k=1}^n \frac{f^{(k)}(t)\cdot k}{k!}(x-t)^{k-1} \\
    &= -\frac{f^{(n+1)}(t)}{n!}(x-t)^n + \sum_{k=1}^{n} \left(-\frac{f^{(k)}(t)}{(k-1)!}(x-t)^{k-1} \right) + \frac{f^{(k)}(t)}{k!}(x-t)^{k-1} \\
    &= -\frac{f^{(n+1)}(t)}{n!}(x-t)^n \;.
```
Let us define the function 
```{math}
        g(t) = F(t) - \frac{(x-t)^{n+1}}{x^{n+1}}F(0)\;.
```
Note that $g(0) = 0 = g(x)$. By Rolle's Theorem, there must be some $c \in (0,x)$ such that $g'(c) = 0$. That is, 
```{math}
    0 = F'(c) + (n+1)\frac{(x-c)^n}{x^{n+1}}F(0) = -\frac{f^{(n+1)}(c)}{n!}(x-c)^{n} + (n+1)\frac{(x-c)^n}{x^{n+1}}F(0) \;.
```
Rearranging the terms give us the desired identity. 
````
We therefore have a precise error estimate for our approximations.     
````{prf:corollary} Error estimates for Taylor approximations

Let $n \geq 0$ and let $f: (-a,a) \to \mathbb{R}$ be a $n+1$-times differentiable function. For any $x > 0$, we have the bound 
```{math}
    \left|f(x) - \sum_{k=0}^n \frac{f^{(k)}(0)}{k!}x^k \right| \leq \left(\sup_{t \in (0,x)}|f^{(n+1)}(t)| \right) |x|^{n+1} \;. 
```
The same identity holds for $x < 0$ with $(0,x)$ replaced with $(x,0)$. In particular, if $f$ is an infinitely differentiable function and $x > 0$ is such that the sequence 
```{math}
    \left(\sup_{t \in (0,x)} |f^{(n+1)}(t)| \right)|x|^{n+1}
```
tends to zero as $n$ tends to infinity, then we have the identity 
```{math}
    f(x) = \sum_{k=0}^\infty \frac{f^{(k)}(0)}{k!}x^k \;. 
```
The same statement is true for $x < 0$, where $(0,x)$ is replaced with $(x,0)$.
````
````{prf:proof}
    The first statement is an immediate consequence of Taylor's Theorem. The second follows from the squeeze theorem. 
````
In the next page are a few exercises to test your knowledge. 