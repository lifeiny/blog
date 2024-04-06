---
title: Why (n-1) when calculating sample variance?
date: 2023-09-28 00:08:37
mathjax: true
categories: 
  turbulence
tags:
  turbulence
---

Why (n-1) when calculating sample variance?

Suppose sample mean 
$$
\overline{X}
$$
sample variance 
$$
S^2
$$
Overall mean
$$
\mu
$$
Overall variance 
$$
\sigma^2
$$

$$
S^2=\frac{1}{n-1}\sum_{i=1}^n{\left( X_i-\overline{X} \right)}^2
$$

if 
$$
S^2=\frac{1}{n}\sum_{i=1}^n{\left( X_i-\overline{X} \right)}^2
$$
Then
$$
E\left( S^2 \right) =E\left( \frac{1}{n}\sum_{i=1}^n{\left( X_i-\overline{X} \right) ^2} \right)
$$
$$
=E\left( \frac{1}{n}\sum_{i=1}^n{\left[ \left( X_i-\mu \right) -\left( \overline{X}-\mu \right) \right] ^2} \right)
$$

$$
=E\left( \frac{1}{n}\sum_{i=1}^n{\left[ \left( X_i-\mu \right) ^2-2\left( X_i-\mu \right) \left( \overline{X}-\mu \right) +\left( \overline{X}-\mu \right) ^2 \right]} \right) 
\\
$$

$$
=E\left( \frac{1}{n}\sum_{i=1}^n{\left( X_i-\mu \right) ^2-\frac{2}{n}\sum_{i=1}^n{\left( X_i-\mu \right) \left( \overline{X}-\mu \right) +\frac{1}{n}\sum_{i=1}^n{\left( \overline{X}-\mu \right) ^2}}} \right) 
\\
$$

Note：

$$
\left( \frac{1}{n}\sum_{i=1}^n{\left( X_i-\mu \right) ^2}=\frac{1}{n}\sum_{i=1}^n{X_i-\mu =\overline{X}-\mu =\frac{1}{n}\sum_{i=1}^n{\left( \overline{X}-\mu \right)}} \right) 
$$

$$
=E\left( \frac{1}{n}\sum_{i=1}^n{\left( X_i-\mu \right) ^2}-\frac{2}{n}\sum_{i=1}^n{\left( \overline{X}-\mu \right) ^2}+\frac{1}{n}\sum_{i=1}^n{\left( \overline{X}-\mu \right) ^2} \right) 
\\
$$

$$
=E\left( \frac{1}{n}\sum_{i=1}^n{\left( X_i-\mu \right) ^2}-\frac{1}{n}\sum_{i=1}^n{\left( \overline{X}-\mu \right) ^2} \right) 
\\
$$

$$
=E\left( \frac{1}{n}\sum_{i=1}^n{\left( X_i-\mu \right) ^2} \right) -E\left( \frac{1}{n}\sum_{i=1}^n{\left( \overline{X}-\mu \right) ^2} \right) 
\\
$$

$$
=\sigma ^2-E\left( \frac{1}{n}\sum_{i=1}^n{\left( \overline{X}-\mu \right) ^2} \right) 
\\
<\sigma ^2
$$

posted 2023/09/28

modified 2023/09/28

