https://contest.yandex.ru/contest/69765/problems/F/


## Introduction

In many machine learning algorithms, there is often a need to classify data. In this task, you need to implement the **support vector machine (SVM)** method, which belongs to the family of linear classifiers.

For simplicity, consider \(n\) points on a two-dimensional plane. Each of these points belongs to one of two classes, denoted as \(l_i = \pm 1\). It is guaranteed that the points can be separated by a straight line such that points of one class lie on one side of it. There may be many such lines, so we will search for a line \(L\) such that the sum of the distances from it to the two nearest points lying on opposite sides is maximized. This leads to more reliable classification.

<img width="874" height="684" alt="image" src="https://github.com/user-attachments/assets/f670e35b-8e70-4687-bf25-b532eff08693" />


## Classification Algorithm

Let the line \(L\) be given by the equation \(ax + by + c = 0\). Then the lines \(L'\) and \(L''\), parallel to \(L\), can be described by the equations \(ax + by + c + \delta = 0\) and \(ax + by + c - \delta = 0\), respectively, where \(\delta > 0\). For convenience, we will refer to the lines \(L'\) and \(L''\) that pass through these two points as support vectors. The distance between the lines \(L'\) and \(L''\) is:
  
  
\begin{equation}
    H = \frac{2\delta}{\left|\vec{n}\right|}
\end{equation}

Точку $(x, y)$ будем классифицировать следующим образом:

\[
a(x, y)  =
\begin{cases}
+1  & \text{если $ax+by+c \geq 0$,} \\
-1 & \text{иначе} 
\end{cases}
\]

<img width="1288" height="1004" alt="image" src="https://github.com/user-attachments/assets/7ea8f647-6d3f-4684-8843-f0e369cff0ef" />


## Loss Function

We penalize the algorithm for incorrect classification:

\[
f(x, y, l)  =
\begin{cases}
0  & \text{if $a(x, y) = l$,} \\
\left|\vec{n}\right|\; d(L, x, y) & \text{otherwise}
\end{cases}
\]

Here, $d(L, x, y)$ denotes the distance from the point $(x, y)$ to the line $L$.

We also want the margin between the support vectors $L'$ and $L''$ to be as large as possible, so we consider the following loss function (the algorithm hyperparameter $\lambda$ should be chosen independently):

\begin{equation}
    \mathrm{Loss} = \lambda {\left|\vec{n}\right|}^2 + \frac{1}{k} \sum_{i=1}^{k} f(x_i, y_i, l_i)
\end{equation}

Your task is to find the parameters $a, b, c$ of the line $L$ using gradient descent that minimizes $\mathrm{Loss}$.
## Metric

In the contest, for each test we will measure the proportion of correct answers (accuracy), and the final metric is defined by the following formula:

\[
\text{score} =
\begin{cases}
0  & \text{if accuracy < 0.97} \\
100 \cdot \text{accuracy} & \text{otherwise}
\end{cases}
\]

The final score will be the average score across all test sets.

## Input Format

```
k

x_1 y_1 l_1


x_2 y_2 l_2

...

x_k y_k l_k
```

### Description

$k$ — number of points.

$(x_i, y_i)$ — coordinates of the $i$-th point.

$l_i$ — class (label) of the $i$-th point.

### Constraints

$1000 < k < 4000$


$-100000 <  x_i, y_i < 100000$

### Input example

```
10

2 6 -1

4 -8 1

9 -1 -1

5 2 -1

-9 7 -1

10 4 -1

2 -8 1

-6 -4 1

-10 -4 1

-2 8 -1
```

## Output format
$a$ $b$ $c$

### Output example

\vspace{5mm}
```
1 1 0
```

