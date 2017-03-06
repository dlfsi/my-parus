---
layout: post
title: First 4 Weeks Assignment Solutions
date: 2017-03-06
comments: true
external-url:
categories: Assignment-Solution
---

## Week 1: Introduction
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
**Sigmoid Function**
```matlab
g=1.0./(1.0+exp(-z));
```

**Compute Cost for Logistic Regression**
```matlab
J=1/m*sum((-y)'*log(sigmoid(X*theta))-(1-y)'*log(1-sigmoid(X*theta)));
```

**Gradient Descent for Logistic Regression**
```matlab
theta=((sigmoid(X*theta)-y)'*X)/m;
```

**Predict Function**
```matlab
p(find(sigmoid(X*theta)>=0.5))=1;
```

**Compute Cost for Regularized LR**
```matlab
idx=length(theta);
J=sum((-y)'*log(sigmoid(X*theta))-(1-y)'*log(1-sigmoid(X*theta)))/m+...
    sum(theta(2:idx).^2)*lambda/(2*m);
```

**Gradient Descent for Regularized LR**
```matlab
idx=length(theta);
theta(1)=(X'(1,:)*(sigmoid(X*theta)-y))/m;
theta(2:idx)=(X'(2:idx,:)*(sigmoid(X*theta)-y))/m+(lambda/m)*theta(2:idx);
```

## Week 4: Neural Network
**Sigmoid Function**
```matlab
g=1.0./(1.0+exp(-z));
```

