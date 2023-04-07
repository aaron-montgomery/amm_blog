# Question

When we compute a product of many numbers that are each uniformly distributed
on $[0, C]$, the product becomes very small when $C$ is 1 and becomes very 
large when $C$ is 10. Where is the "cutoff" $C$ where the product exhibits a
transition?

# Answer

It's Euler's number, $e \approx 2.71828...$ -- yes, *that* $e$. It has a habit of
[doing this sort of thing](https://aaron-montgomery.github.io/amm_blog/posts/2022-07-27-ordered-objects/).

## Proof

Let's formulate this mathematically: we want to know how the product
$$U = \prod_{k=1}^{n} X_k$$
behaves, where $\{X_i\}$ is a collection of independent, identically-distributed
numbers that are all uniformly distributed on $[0, C]$. Products of random 
variables are somewhat obnoxious to work with; luckily, logarithms[^1] will let 
us trade products for sums.
$$\log(U) = \log \left( \prod_{k=1}^{n} X_k \right) = 
\sum_{k=1}^{n} \log \left( X_k \right)$$

One advantage of a sum is that it more closely resembles an *average*:

$$\frac{\log(U)}{n} = \frac 1 n \sum_{k=1}^n \log \left( X_k \right)$$

Now, the right-hand side is nothing more than an average of $n$ independent 
copies of $\log(X_i)$. The 
[Law of Large Numbers](https://en.wikipedia.org/wiki/Law_of_large_numbers) says 
that as $n$ increases, the right-hand side will converge to the expected value 
$\mathbb E[\log(X_i)]$, so we just need to calculate that. By the 
[Law of the Unconscious Statistician](https://en.wikipedia.org/wiki/Law_of_the_unconscious_statistician),
this is
$$\int_0^C \frac 1 C \cdot \log(x) \, \textrm d x = \frac 1 C \left[x \log(x) - x \right] \bigg|_0^C = \log(C) - 1.$$

Putting it all together, we can now investigate the behavior of the original
product $U$. As $n$ increases, $\frac{\log(U)}{n}$ converges to $\log(C) - 1$.

* When $C > e$, $\frac{\log(U)}{n}$ converges to a positive constant; hence,
$\log(U)$ diverges to $\infty$, so $U$ does so as well.
* When $C < e$, $\frac{\log(U)}{n}$ converges to a negative constant; in this
case, $\log(U)$ diverges to $-\infty$, implying $U$ converges to $0$.

Hence, the "transition point" for $C$ is indeed $e$.

## But wait!

We left out one case! What happens when $C = e$?

FILL IN




PROVIDE LINK BACK TO POST

[^1]: We'll use $\log(x)$ to denote the natural logarithm, i.e. the inverse of 
$e^{x}$.
