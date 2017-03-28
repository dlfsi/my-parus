---
layout: post
title: Assignment Solutions for Week 8 to 9
date: 2017-03-25
comments: true
external-url:
categories: Assignment-Solution
---

> Week 8 to 9 Assignment Solutions

Completed all 11 weeks ML course on Coursera last week. It's a fundermental class which focus on essential concepts of traditional ML, mostly like data mining technologies. Only touch a little bit of deep learning. Very good for ML introductory.

## Week 8: K-Means Clustering and PCA
**Find Closest Centroids**

```matlab
for i=1:size(X,1)
  tmp=(X(i,:)-centroids).^2;
  dist=zeros(size(X,1),1);
  for j=1:K
    value=sum(tmp(j,:));
    if j==1
      idx(i)=1;
      dist=value;
    elseif dist>value
      idx(i)=j;
      dist=value;
    end
  end  
end
```

**Compute Centroid Means**
```matlab
for i=1:K
  v=find(idx==i);
  centroids(i,:)=sum(X(v,:))/size(v,1);
end
```

**PCA**
```matlab
sigma=(X'*X)/m;
[U, S, V]=svd(sigma);
```

**Project Data**
```matlab
for i=1:length(X)
  x=X(i,:)';
  Z(i,:)=x'*U(:,1:K);
end
```

**Recover Data**
```matlab
for i=1:length(Z)
  for j=1:length(U)
    X_rec(i,j)=Z(i,:)*U(j,1:K)';
  end
end
```

## Week 9: Anomaly Detection and Recommender Systems
**Estimate Gaussian Parameters**
```matlab
mu=sum(X(:,1:end))/m;
sigma2=sum((X-mu).^2)/m
```

**Select Threshhold**
```matlab
pred=(pval<epsilon);
tp=sum((pred==1)&(yval==1));
fp=sum((pred==1)&(yval==0));
fn=sum((pred==1)&(yval==0));
precision=tp/(tp+fp);
recall=tp/(tp+fn);
F1=2*precision*recall/(precision+recall)
```

**Collaborative Filtering Cost/Gradient with Regularization**
```matlab
cost=(X*Theta'-Y);
J=sum(sum((cost.^2).*R))/2;
J=J+(lambda/2)*sum(sum(Theta.^2))+(lambda/2)*sum(sum(X.^2));

X_grad=(cost.*R)*Theta;
X_grad+=lambda*X;

Theta_grad=(cost.*R)'*X;
Theta_grad+=lambda*Theta;
```
