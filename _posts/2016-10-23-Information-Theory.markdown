---
layout: post
title:  "Learning Notes:Linear Regression"
categories: Notes of ML
---
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
### Entropy
Suppose $$p(x)$$ is the distribution of a random variable value $$x$$, the **entropy** of $$x$$ is:

$$H[x] = -\sum_x p(x)log_2p(x)$$

Note that $$\lim_{p\to0} plnp = 0$$, so when $$p(x)$$ equals to 0, we take $$p(x)lnp(x) = 0$$.
