---
layout: post
title: First 4 Weeks Assignment Solutions
date: 2017-03-06
comments: true
external-url:
categories: Assignment-Solution
---

> Week 1 to 4 Assignment Solutions
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

## Week 4: Multi-class Classification and Neural Networks
**Regularized Logistic Regression**
```matlab
idx=length(theta);
J=sum((-y)'*log(sigmoid(X*theta))-(1-y)'*log(1-sigmoid(X*theta)))/m+...
    sum(theta(2:idx).^2)*lambda/(2*m);
theta(1)=(X'(1,:)*(sigmoid(X*theta)-y))/m;
theta(2:idx)=(X'(2:idx,:)*(sigmoid(X*theta)-y))/m+(lambda/m)*theta(2:idx);
```

**One-vs-All Classifier Training**
```matlab
for c=1:num_labels
  initial_theta = zeros(n + 1, 1);
  options = optimset('GradObj', 'on', 'MaxIter', 50);
  [theta, J, exit_flag]=fmincg(@(t)(lrCostFunction(t,X,(y==c),lambda)),...
                        initial_theta, options);
  all_theta(c,:)=theta(:);
end
```

**One-vs-All Classifier Prediction**
```matlab
result=sigmoid(X*all_theta');
[value,p]=max(result,[],2);
```

**Neural Network Prediction Function**
```matlab
X=[ones(size(X,1),1) X];
layer2=sigmoid(X*Theta1');
layer2=[ones(size(X,1),1) layer2];
output=sigmoid(layer2*Theta2');
[value,p]=max(output,[],2);
```

