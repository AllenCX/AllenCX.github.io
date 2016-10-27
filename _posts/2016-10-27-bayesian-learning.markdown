---
layout: post
title:  "Learning Notes: Bayesian Learning"
categories: Notes of ML
---
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
### Bayes' Rule:
Suppose we have a hypothesis $$h$$ and a set of data $$D$$, the Bayes' rule of the two is

$$P(h|D) = \frac{P(D|h)P(h)}{P(D)} \tag{1}$$

where $$P(h\vert D)$$ is **posterior probability**, $$P(D\vert h)$$ is **likelihood**, $$P(h)$$ is **prior probability**.

Note that, at some times, $$P(D)$$ can be obtained by **the law of total probability**.

$$P(D) = \sum_i{P(D|h_i)P(h_i)} \tag{2}$$

At some other times, we need not to caculate $$P(D)$$ because it is constant and will not influence the ultimate result.

#### An example(from [Udacity's Machine Learning course])
Suppose a kind of machine can diagnose a patient whether have cancer or not. In most of the time, the machine will work without mistake. However, sometimes, the machine may goes wrong. Statistically, on 98% of the time, that the machine will correctly diagnose a person without cancer, which is also called correct positive; on 97% of the time, the machine will conclude a cancer patient has cancer, which is also called correct negative. In addition, we also know that there are only 0.8% of the total population who have cancer. Now the question is when the machine diagnose one man is healthy, what's the probablity that the man who take the diagnose is healthy?

Using Beyes' Rule, we can present 

$$
\begin{align}
\require{cancel} P(c\vert +) &= \frac{P(+|c)P(c)}{\cancel{P(+)}} \\
&= 0.98 \times 0.008 = 0.00784 \tag{3} \label{3}
\end{align}
$$

$$
\begin{align}
P(\bar{c}|+) &= \frac{P(+|\bar{c})P(\bar{c})}{\cancel{P(+)}} \\
&= 0.03 \times 0.992 = 0.02976 \tag{4} \label{4}
\end{align}
$$

Because $$P(+)$$ is constant and we only need a normalized probability, thus we can omit $$P(+)$$.

Then we normalize $$\ref{3}$$ and $$\ref{4}$$ we get

$$P(\text{The man is healthy}) = \frac{0.02976}{0.02976+0.00784} \approx 79\%$$

$$P(\text{The man has cancer}) = \frac{0.00784}{0.0296+0.00784} \approx 21\%$$

So theoretically, if we trust the machine all the time, we will tell everyone who take the diagnose that he or she is healthy. 

The conclusion looks weird, isn't it? The reason is that in daily life, only a small percent of the population who has cancer, which caused the imbalance of the dataset.

[Udacity's Machine Learning course]:https://classroom.udacity.com/courses/ud262/lessons/454308909/concepts/4733385500923#