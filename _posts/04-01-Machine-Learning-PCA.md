---
layout: post
title: Machine learning&#58; PCA  
--- 
PCA stands for Principal Component Analysis.  It's what's called an _unsupervised learning_ algorithm and it's a (clever!) way of reducing the number of dimensions in a data set.  As a bonus, it reveals correlations between features.  In this post I want to explain the idea, the math behind it (why it's clever and why it reveals correlations between features), and how I used it in my project.  This is a new topic for me, but I want to try to explain it to the best of my abilities.  This post is going to take some research and citations, mostly from Matt's data science boot camp lecture on the topic.  I'm assuming the reader has a very basic background in statistics (mainly voabulary words), linear algebra (matrices, vectors, and maybe eigenvectors/eigenvalues), and maybe calculus (using derivatives to optimize).  

## The idea

Most data sets in practice have a very large number of features, and it's impossible to graph them when there are more than 3.  PCA resets the coordinate system so that only a few of the new coordinate vectors are needed to capture most of the variance in the data, while the rest of the new coordinate vectors are small enough that they can be "flattened" (eliminated).  This is useful when running _supervised learning_ algorithms on the data, since fewer dimensions make the algorithms run faster.

More abstractly, say you have a matrix of data, where the columns are indexed by the features of a data set and the rows give the observations for each feature.  PCA turns that matrix into an ordered list of vectors.  The first vector points in the direction of the highest amount of variance in the data, the second vector points in the direction of the highest amount of variance, out of all of the vectors that are perpendicular to the first.  The third vector points in the direction of the highest amount of variance out of all the vectors perpendicular to both the first and the second, and so on.  The vectors are the **PCA components**.  Each component has an "explained variance ratio", ordered from greatest to least in the component vectors, and so we can safely drop most of the components when the first few explained variance ratios add up to close to 100%. 

The following visualizations are from Matt's data science bootcamp lecture on PCA from fall 2022.  The first visualization is a data set with two features, $x_1$ and $x_2$.  The arrows on the graph are the PCA components.  The longer one is the first one and the shorter one is the second one.  The PCA components are always ordered from longest to shortest.  The second visualization is the data replotted with the new coordinate system given by the PCA components.  The point is that the variance in the data from the first graph is preserved in the second graph, the data points have just been rotated and scaled to make a more homogeneous picture.

<img src="https://wh33les.github.io/images/data_with_components.png" alt="Original data with PCA component vectors" title="Original data with PCA component vectors" width=49%> </img>
<img src="https://wh33les.github.io/images/transformed_data.png" alt="Data with the PCA components as coordinate vectors" title="Data with the PCA components as coordinate vectors" width=49%></img>

<!--
![Original data with PCA component vectors](https://wh33les.github.io/images/data_with_components.png)
![Data with the PCA components as coordinate vectors](https://wh33les.github.io/images/transformed_data.png)
-->
Since the first component is so much longer than the second component, with the highest amount of variance in the first graph stretched out horizontally in the second graph, the data points in the second graph can be flattened to the $x$-axis without losing information about the variance.  Flattening reduces this data set with 2 dimensions to one with 1 dimension.

## The math

The problem PCA solves is an optimization problem.  Let $X$ be the $m\times n$ matrix whose columns are vectors $X_1,\dots,X_n$ corresponding to the features.  Each vector $X_i$ is $m\times 1$, and the entries are the observations of that feature.  We wish to find a projection of the feature vectors to a vector $\vec w$, that has maximum variance, in other words, we want to maximize Var$(X\vec w)$.  

To make this problem simpler, it is typical to scale $X_1,\dots,X_n$ so that they have expectation $0$.  We also impose the convention that $||\vec w||=1$.  Then the problem reduces to maximizing 
$$
\text{Var}(X\vec w) = \text{E}(\vec w^TX^TX\vec w) = \vec w^T\tect{E}(X^TX)\vec w,
$$
but since we've standardized the features to have expectation $0$, E$(X^TX)$ is just the covariance matrix!  

Furthermore, the problem of maximizing a quadratic form $\vec x^TA\vec x$, where $A$ is a symmetric matrix and $||\vec x||=1$, is a standard problem in linear algebra called the **constrained optimization problem**.  The solution is the eigenvectors of $A$, and the maximum values are the eigenvalues of $A$.
