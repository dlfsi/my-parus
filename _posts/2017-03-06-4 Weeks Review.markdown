---
layout: post
title: review after 4 weeks learning
date: 2017-03-06
comments: true
external-url:
categories: Deep-Learning
---

> Completed 4 weeks learning of Andrew Ng's Machine Learing course on Coursera within 1 week. Here're some lesson learnt.

At the first beginning, all things went to Caculus, Linear Algebra, Probality, which learnt many years ago. And so many terms there like CNN, RNN, MLP, RBM, back propagation. After going through Machine **Learning Recipes** from google and **Deep Learning Simplified** from TODSI, there're so many questions in my mind. I think Andrew Ng's course is a very handy tool that connect my previous experience with new concept, which introduces some hands-on assignments to make it more understandable.

Before the course, it would be better if you know something like Matrix operations (e.g. transpose and inverse), basic Caculus (e.g. derivative and polynormial). If not, it's fine because all these would be mentioned in the course. It's very important to practice the various operations using Matlab or Octave. **Size** is a very handy function or command to verify if everything will be OK.

I'm a little bit confused between vectorized implementation and for loop implementation. And then I found vectorized implementation is easier than loop, as long as finished relevant parts of Linear Algebra.
```matlab
m = length(y);

J = ((X*theta-y)'*(X*theta-y))/(2 * m);

J = sum((X*theta-y).^2)/(2 * m);
```

both formulas lead to the same result, but vectorized one is better on performance side, and more concise.

```
cost function: J(theta)
gradient descent: theta
```

## Features Normalization

*Features Normalization* is essential for Linear Regression and Logistic Regression. It always can be done by introducing *Mean* and *Standard Deviation* functions.

> **Normalized Value** equals (X-mean(X))./std(X)

**Sigmoid** function is a vital activation function using in afterwards neural network implementation.

> g=ones(size(z))./(1+exp(-z))

[find](https://au.mathworks.com/help/matlab/ref/find.html) and [max](https://au.mathworks.com/help/matlab/ref/max.html) function are very useful for determing the result of a multi-class classifier.
