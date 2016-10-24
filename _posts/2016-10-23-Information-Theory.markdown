---
layout: post
title:  "Learning Notes: Information Theory"
categories: Notes of ML
---
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
### Entropy
Suppose $$p(x)$$ is the distribution of a random variable value $$x$$, the **entropy** of $$x$$ is:

$$H[x] = -\sum_x p(x)\log_2{p(x)} \tag{1}$$

Note that $$\lim_{p\to0} p\ln{p} = 0$$, so when $$p(x)$$ equals to 0, we take $$p(x)\ln{p(x)} = 0$$.

If x is a continous variable equation 1 can be written as

$$H(x) = \lim_{\Delta\to 0} \left\{\sum_i p(x_i)\Delta \ln{p(x_i)} \right\} = - \int{p(x) \ln{p(x)}\, \mathrm{d}x} \tag{2}$$

For a density defined over multiple continous variables, denoted collectively by the vector $$\mathbf{x}$$, the differential entropy is given by

$$H[\mathbf{x}] = - \int p(\mathbf{x})\ln{p(\mathbf(x))} \,\mathrm{d}\mathbf{x} \tag{3}$$

### KL divergence
**Relative entropy** or **Kullback-Leibler divergence**, or **KL divergence** for short, is a quantity that measures the addtional information needed by an approximate distribution $$q(\mathbf{x})$$ over $$\mathbf{x}$$ to model some unknown distribution $$p(\mathbf{x})$$. In other words, KL divergence measures the similarity bewteen $$q(\mathbf{x})$$ and $$p(\mathbf{x})$$.

For discrete random variable $$x$$, KL divergence can be written as

$$KL(p||q) = \sum_i p(x_i)\log \frac{p(x_i)}{q(x_i)} \tag{4}$$

For continous random variable or vector $$\mathbf{x}$$, KL divergence can be written as

$$\begin{align}
KL(p||q) & = -\int p(\mathbf{x})\ln{q(\mathbf{x})} \,\mathrm{d}\mathbf{x} - \left( -\int p(\mathbf{x})\ln{p(\mathbf{x})} \,\mathrm{d}x \right) \\
& = -\int p(\mathbf{x}) \ln \left\lbrace \frac{q(\mathbf{x})}{p(\mathbf{x})} \right\rbrace \mathrm{d}x \tag{5}
\end{align}$$

Note that KL divergence is not a symmertical quantity, which means $$KL(p\vert\vert {q}) \not\equiv KL(p \vert\vert {q})$$. At any time, KL divergence satisfies $$KL(p \vert\vert {q}) \ge 0$$, with the equality if and only if, $$p(\mathbf{x})=q(\mathbf{x})$$. The insight behind the lower bound, which equals to $$0$$ of KL divergence shows that we cannot compress data or use another distribution($$q$$) to model some unknown distribution($$p$$) without lose its original information.

On some times, we can use KL divergence to approximate the unknown distribution $$p(\mathbf{x})$$. Suppose we have a set of data points $$\mathbf{x}={x_1, x_2,..., x_n}$$, a set of parameters $$\mathbf{\theta}$$, like mutivariate Guassian. Then we can contruct a distribution $$q(\mathbf{x}\vert\mathbf{\theta})$$ to model $$p(\mathbf{x})$$. In order to make $$q(\mathbf{x}\vert\mathbf{\theta})$$ more likely to $$p(\mathbf{x})$$, we can minimize the KL divergence

$$KL(p\vert\vert{q}) \simeq \sum_i \left\lbrace -\ln{q(\mathbf{x}_n\vert\mathbf{\theta})} + \ln{p(\mathbf{x}_n)} \right\rbrace    \tag{6}$$

Noticed that the second term of equation (6) is independent of $$\mathbf{\theta}$$. Meanwhile, the first term is the negative log likelihood function for $$\mathbf{\theta}$$ under distribution $$q(\mathbf{x}\vert\mathbf{\theta})$$ evaluated using training set. Thus, minimizing KL divergence equals to maximizing the likelihood function.

#### Reference: Pattern Recognition and Machine Learning