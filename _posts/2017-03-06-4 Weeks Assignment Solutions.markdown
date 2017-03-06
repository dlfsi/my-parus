---
layout: post
title: First 4 Weeks Assignment Solutions
date: 2017-03-06
comments: true
external-url:
categories: Assignment-Solution
---

> ## Week 1: Introduction
**No Assignment**

## Week 2: Linear Regression
**Warm Up Exercise**
```matlab
A = eye(5);
```

**Compute Cost For One Variable**
```matlab
J=sum((X*theta-y).^2)/(2*m);
```

**Gradient Descent For One Variable**
```matlab
for iter = 1:num_iters
	theta = theta - alpha / m * ((X * theta - y)'* X)';
	J_history(iter) = computeCost(X, y, theta);
end
```

**Feature Normalization**
```matlab
mu=mean(X);
sigma=std(X);
X_norm=(X-mu)./sigma;
```

**Compute Cost For Multiple Variable**
```matlab
J=((X*theta-y)'*(X*theta-y))/(2*m);
```

**Gradient Descent For Multiple Variable**
```matlab
for iter = 1:num_iters
	theta=theta-(alpha/m)*(X'*((X*theta)-y));
	J_history(iter) = computeCostMulti(X, y, theta);
end
```

**Normal Equations**
```matlab
theta=pinv(X'*X)*X'*y;
```
## Week 3: Logistic Regression
