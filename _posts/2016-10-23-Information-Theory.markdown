---
layout: post
title:  "Learning Notes:Linear Regression"
categories: Notes of ML
---
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
### Entropy
Suppose $$p(x)$$ is the distribution of a random variable value $$x$$, the **entropy** of $$x$$ is:

$$H[x] = -\sum_x p(x)\log_2{p(x)} \tag{1}$$

Note that $$\lim_{p\to0} p\ln{p} = 0$$, so when $$p(x)$$ equals to 0, we take $$p(x)\ln{p(x)} = 0$$.

If x is a continous variable equation 1 can be written as

$$H(x) = \lim_{\Delta\to 0} \left\{\sum_i p(x_i)\Delta \ln{p(x_i)} \right\} = - \int{p(x) \ln{p(x)}\, \mathrm{d}x} \tag{2}$$

###### To be continued 