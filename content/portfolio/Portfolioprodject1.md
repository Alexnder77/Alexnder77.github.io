---
title: Hyperplane in SVM
description: Explaining how hyperplanes work in Support vector machines (part of my open genius internship)
thumbnail: "portfolio_assets/images/01.jpg"
alt: Alt text for Project 1 image
weight: 1
toc: true
tags: OpenGenius
---

## Introduction
Support Vector Machines (SVMs) are powerful machine learning models that can be used for both classification and regression tasks. In classification, the goal is to find a hyperplane that separates the data points of different classes with maximum margin. This hyperplane is known as the "optimal hyperplane" or "maximum-margin hyperplane".

To understand the concept of the hyperplane in SVMs, let's dive deeper into the working of SVMs and how the optimal hyperplane is determined.

## Support Vector Machines
The idea behind SVMs is to find a plane or a boundary that effectively separates the data points of different classes. For example in a binary classification problem where we have 2 different classes and the data is 2-dimensional. It can be separated with a line. 

Here we can see a line separating the red from the blue dots the color representing the two different classes.  
![[Attachments/Pasted image 20230619135001.png]]

If the data has 3 or more dimensions it needs to be separated by a hyperplane. which can be illustrated like this: 
![[Attachments/Pasted image 20230619133752.png]]

This principle remains even in higher dimensions, but illustrating them is harder. 

(Note: technically speaking all flat affine subspaces are hyperplanes so the 1 dimensional line from image 1 is also a hyperplane)

## Finding the best hyperplane 
The data points that lie closest to the hyperplane/the decision boundary are called support vectors. These support vectors play a crucial role in determining the optimal hyperplane. The distance between the hyperplane and the support vectors is known as the margin. The SVM tries to maximize this margin, as it provides a measure of the confidence of classification. In a sense the longer the distance between the different classes the more clearly they are separated and the better the model is.

![[Excalidraw/Drawing 2023-06-20 12.05.43.excalidraw|Drawing 2023-06-20 12.05.43.excalidraw]]
The hyperplane can be represented by the equation:
$$y = w^T  x + b$$
Where $y$ represents the label, $w$ and $b$ represents the parameters of the hyperplane. For our binary classification problem we only have the classes -1 and 1. So $y \in \begin{Bmatrix} 1, -1 \end{Bmatrix}$. 

Since the hyperplane represents the decision boundary, any point on the hyperplane will have to fit this equation $w^T  x + b = 0$. This is in the middle of the 2 classes, which can be interpreted as we don't know what class that point belongs to. 

The decision rule is based on the sign of the equation above. If $w^T \times x + b > 0$, the point $x$ is classified as class 1, and if $w^T \times x + b < 0$, the point $x$ is classified as class -1.

The optimal hyperplane is the one that maximizes the margin between the two classes. 

The margin is defined as the perpendicular distance between the hyperplane and the closest data points from each class. These closest data points are called support vectors.

Let's denote the support vectors as $x_+$for class 1 and $x_-$ for class -1. The distance between these support vectors is given by: 
$$\text{margin} = \frac{2}{\|w\|}$$ where $\|w\|$ represents the Euclidean norm of the weight vector $w$. The goal of SVM is to find the hyperplane that maximizes this margin, which in turn improves the generalization performance of the classifier.

To find the optimal hyperplane, SVM solves either the following maximization or the equivalent minimization -problem an optimization problem: 
$$\max_{w,b} = \frac{2}{\|w\|} \Leftrightarrow  \min_{w,b} \frac{1}{2} \|w\|^2$$
subject to the constraints: $$y_i(w^T x_i + b) \geq 1 \text{  for all i} = 1,2,...,N$$ 
Here, $N$ represents the number of data points, and $y_i$ represents the class labels. The constraints ensure that all data points are correctly classified and lie on the correct side of the margin.

The optimization problem can be solved using various algorithms, such as the Sequential Minimal Optimization (SMO) or the Interior Point Methods. Once the optimization problem is solved, the learned parameters $w$ and $b$ define the optimal hyperplane that separates the two classes with the maximum margin.

## Implementation
using the above equations and applying it in python (the minimization problem is solved using the function minimize from the package scipy.optimize):  

```python
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Define the dataset
X = np.array([[1, 2], [2, 0], [3, 2]])  # Features
y = np.array([1, 1, -1])  # Labels

# Step 2: Define the SVM optimization problem
def objective(w):
    return 0.5 * np.linalg.norm(w)**2

def constraint(w):
    return y * (np.dot(X, w[:-1]) + w[-1]) - 1

# Step 3: Solve the SVM optimization problem
initial_guess = np.zeros(X.shape[1] + 1)  # Initial guess for w and b
bounds = [(None, None)] * X.shape[1] + [(None, None)]  # No bounds on w and b

from scipy.optimize import minimize

solution = minimize(objective, initial_guess, bounds=bounds, constraints={'type': 'ineq', 'fun': constraint})

# Step 4: Extract the optimal parameters
w = solution.x[:-1]
b = solution.x[-1]

# Calculate the margin
margin = 2 / np.linalg.norm(w)

# Plotting the results
plt.scatter(X[:, 0], X[:, 1], c=y, cmap='bwr', label='Dataset')

# Plotting the decision boundary
x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1
xx, yy = np.meshgrid(np.arange(x_min, x_max, 0.01), np.arange(y_min, y_max, 0.01))
grid_points = np.c_[xx.ravel(), yy.ravel()]
decision_values = np.dot(grid_points, w) + b
Z = np.sign(decision_values).reshape(xx.shape)
plt.contour(xx, yy, Z, colors='k', levels=[-1, 0, 1], alpha=0.5)

# Plotting the margin
support_vectors = X[solution.success]
plt.scatter(support_vectors[:, 0], support_vectors[:, 1], s=100, facecolors='none', edgecolors='k', linewidths=2, label='Support Vectors')

# Setting plot limits and labels
plt.xlim(x_min, x_max)
plt.ylim(y_min, y_max)
plt.xlabel('X')
plt.ylabel('Y')
plt.title('SVM Classification')
plt.legend()

# Display the margin
plt.text(x_min + 0.1, y_max - 0.1, f'Margin: {margin:.2f}', fontsize=12, bbox=dict(facecolor='white', edgecolor='black', boxstyle='round'))

plt.show()
```


![[Attachments/Pasted image 20230619174013.png]]
![[Attachments/Pasted image 20230619174527.png]]
comparing to the sklearn svm function:
```python
from sklearn.svm import SVC

# Step 1: Define the dataset
X = [[1, 2], [2, 0], [3, 2]]  # Features
y = [1, 1, -1]  # Labels

# Step 2: Create and fit the SVM classifier
clf = SVC(kernel='linear')
clf.fit(X, y)

# Step 3: Calculate the weight vector, bias term, and margin
w = clf.coef_[0]
b = clf.intercept_[0]
margin = 2 / np.linalg.norm(w)

# Step 4: Print the results
print("Weight Vector:", w)
print("Bias Term:", b)
print("Margin:", margin)

```

![[Attachments/Pasted image 20230619174206.png]]

## Conclusion 
It is important to note that SVM is a linear classifier, which means it can only separate classes using linear decision boundaries. However, by applying different kernel functions, SVM can also handle non-linear decision boundaries by mapping the data into a higher-dimensional feature space.

In conclusion, the hyperplane in SVM represents the decision boundary that separates the two classes, and the optimal hyperplane is the one that maximizes the margin between the classes. SVM achieves this by solving an optimization problem and finding the best parameters that define the hyperplane.

SVM is a powerful and widely used algorithm in machine learning due to its ability to handle both linear and non-linear classification problems. It has proven to be effective in various applications, such as image classification, text categorization, and bioinformatics, among others.


## References 

[Support vector machines and machine learning on documents](https://nlp.stanford.edu/IR-book/html/htmledition/support-vector-machines-and-machine-learning-on-documents-1.html)
[Separating Hyperplanes in SVM - GeeksforGeeks](https://www.geeksforgeeks.org/separating-hyperplanes-in-svm/)
