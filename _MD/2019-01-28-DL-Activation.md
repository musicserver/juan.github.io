---
layout: post
title:  "DL functions"
author: "Seudonimo"
---

[Numpy-Basic](#https://seudonimo.github.io/2019-01-31/numpy-basic)
[Numpy - Broadcasting] - 작성 중
[Numpy - DL functions]

# Basic functions in DL with numpy
-----

#### Broadcasting
Broadcasting은 shape가 다른 array간에도 산술연산이 가능하케하는 feature이다. 

다음은 numpy로 구현한 DL 관련 basic function들이다.

TBD

#### step function

``` python
import numpy as np
import matplotlib.pyplot as plt

def step_function(x):
    if x > 0:
        return 1
    else :
        return 0
 
def np_step_function(x):
    y = x > 0
    return y.astype(np.int)
#api usage
x = np.arange(-3, 3, 0.1)
y = np_step_function(x)
plt.plot(x, y)
plt.show()
```

- step_function의 경우, numpy array를 입력 받을 수 없다. 
- np_step_function은 y = x > 0에서 boolean 형식의 numpy array가 반환되는 것을 응용헤서 구현한 것이다.

![](img/190131_step.png)

#### sigmoid function

$$
\begin{aligned} sigmoid(w^Tx + b) = \frac{1}{1 + e^{-{W^Tx+b}}}\end{aligned}
$$
$$
\begin{aligned} sigmoid(x) = \frac{e^{-x}}{1+ e^{x}}=\frac{1}{1 + e^{-x}}\end{aligned}
$$

```python
def sigmoid(x):
    return 1 / (1 + np.exp(-x))
#api usage
x = np.arange(-5, 5, 0.1)
plt.plot(x, sigmoid(x))
plt.ylim(-0.1, 1.1)
plt.show()
```

![](img/190131_sigmoid.png)

#### ReLu function

```python
import numpy as np
def Relu(x):
    return np.maximum(0, x)

a = np.arange(-3, 3, 0.1)
plt.plot(a, Relu(a))
plt.ylim(-0.5, 4)
plt.show()
```

![](img/190131_relu.png)

#### Softmax function

- softmax 함수는 출력 층에서 3-class 이상의 classification을 목적으로 쓰이는 활성화 함수다.

$$
y_k = \frac{exp(a_k)}{\sum^n_{i=1}(exp(a_i))}
$$

```python
import numpy as np

def softmax(a):# a is numpy array
    exp_a = np.exp(a)
    sum_exp_a = np.sum(exp_a)
    y = exp_a / sum_exp_a
    return y

#api useage
a = np.array([1, 2, 3])
print(a)
print(softmax(a))
print(sum(softmax(a)))
```

#### etc functions
##### reshape to be flattened image
- [] Reshape에서 -1 옵션이 뭔지 알아야 할듯
(num_px, num_py, 3) ==> (num_px*num_py *3 , 1)
```python
#A trick when u want to flatten a matrix X of shape (a, b, c, d) to a matrix X_flatten of shape (b*c*d, a)
X_flattten = X.reshape(X.share[0], -1).T
```
##### np.zeros() for initialize
```python
def init_params(dim):
     #dim : size of the w vector
     #w : initialized vector of shape (dim, 1)
     w = np.zeros((dim, 1)
     b = 0
     
     return w, b
     
dim = 2
w, b = init_with_params(dim)
```
##### np.squeeze(cost)
#### matplotlib
TBD
