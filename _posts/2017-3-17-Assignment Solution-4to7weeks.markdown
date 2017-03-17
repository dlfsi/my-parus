---
layout: post
title: First 4 Weeks Assignment Solutions
date: 2017-03-17
comments: true
external-url:
categories: Assignment-Solution
---

> Week 5 to 7 Assignment Solutions
## Week 5: Neural Network Learning
**Feedforward and cost function**
```matlab
X=[ones(size(X,1),1) X];

% turn vector y into matrices
yVec=[zeros(size(y,1),num_labels)];
for i=1:m
  yVec(i,y(i))=1;
end

a1=X;
z2=X*Theta1';
a2=sigmoid(z2);
a2=[ones(size(a1,1),1) a2]; %add first one node for layer2
z3=a2*Theta2';
hy=a3=sigmoid(z3);

% unregularizaed cost function
J=sum(sum((-yVec).*log(hy)-(1-yVec).*log(1-hy)))/m;

% regularization cost function
J=J+(lambda/(2*m))*(sum(sum(Theta1(:,2:end).^2))+sum(sum(Theta2(:,2:end).^2)));


% back propagation
delta3=hy-yVec;
Theta2_grad=(Theta2_grad+delta3'*a2)/m;
  
delta2=(delta3*Theta2)(:,2:end).*sigmoidGradient(z2);  
Theta1_grad=(Theta1_grad+delta2'*X)/m; %a1 400 columns, X 401 columns

% back propagation with regularization
Theta1_grad=Theta1_grad+(lambda/m)*[zeros(size(Theta1,1),1) Theta1(:,2:end)];
Theta2_grad=Theta2_grad+(lambda*[zeros(size(Theta2,1),1) Theta2(:,2:end)])/m;
```

**Sigmoid Gradient**
```matlab
g=ones(size(z))./(1+exp(-z));
g=g.*(1-g);
```

**Regularized Gradient**
```matlab
numgrad = zeros(size(theta));
perturb = zeros(size(theta));
e = 1e-4;
for p = 1:numel(theta)
    % Set perturbation vector
    perturb(p) = e;
    loss1 = J(theta - perturb);
    loss2 = J(theta + perturb);
    % Compute Numerical Gradient
    numgrad(p) = (loss2 - loss1) / (2*e);
    perturb(p) = 0;
end
```

## Week 6: Regularized Linear Regression and Bias-Variance
**regularized linear regression**
```matlab
J=sum((X*theta-y).^2)/(2*m);
J=J+lambda*sum(theta(2:end).^2)/(2*m);

grad(1)=(X'(1,:)*(X*theta-y))/m;
grad(2:end)=(X'(2:end,:)*(X*theta-y))/m+(lambda/m)*theta(2:end);
```

**Learning Curve**
```matlab
for i=1:m
  theta = ones(size(X,2),1);
  %[J_train, grad]=linearRegCostFunction(X(1:i,:), y(1:i,:), theta, lambda);
  [theta] = trainLinearReg(X(1:i,:), y(1:i,:), lambda);
  [J_train,grad]=linearRegCostFunction(X(1:i,:), y(1:i,:), theta, 0);
  error_train(i)=J_train;
  [J_val, grad]=linearRegCostFunction(Xval, yval, theta, 0);
  error_val(i)=J_val;
end
```

**Polynomial Feature Mapping**
```matlab
for i=2:p
  X=[X X(:,1).^i];
end

X_poly=X;
```

**Validation Curve**
```matlab
for i=1:length(lambda_vec)
      lambda=lambda_vec(i)
      [theta] = trainLinearReg(X, y, lambda);
      [J_train,grad]=linearRegCostFunction(X, y, theta, 0);
      error_train(i)=J_train;
      [J_val, grad]=linearRegCostFunction(Xval, yval, theta, 0);
      error_val(i)=J_val;
end
```

## Week 7: Support Vector Machines
**Guassian Kernel**
```matlab
x=sum((x1-x2).^2);
sim=exp(-x/(2*sigma*sigma));
```

**Parameters (C, Sigma) for dataset3**
```matlab
idx=1;
result=zeros(64,3);
for C = [0.01 0.03 0.1 0.3 1 3 10 30]
  for sigma = [0.01 0.03 0.1 0.3 1 3 10 30]
    model=svmTrain(X,y,C,@(x1,x2) gaussianKernel(x1,x2,sigma));
    predictions=svmPredict(model,Xval);
    result(idx,:)=[C sigma mean(double(predictions~=yval))];
    idx+=1;
end
pos=find(result(:,3)==min(result(:,3)));
C=result(pos,1);
sigma=result(pos,2);
```

**Email Preprocessing**
```matlab
    for i=1:length(vocabList)
      if (strcmp(str,vocabList{i})==1)
        word_indices=[word_indices;i];
      end
    end
```

**Email Feature Extraction**
```matlab
for i=1:length(word_indices)
  idx=word_indices(i);
  x(idx)=1;
end
```
