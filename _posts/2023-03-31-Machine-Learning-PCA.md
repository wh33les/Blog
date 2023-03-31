---
layout: post
title: Machine learning&#58; PCA  
--- 
PCA stands for Principal Component Analysis.  It's what's called an _unsupervised learning_ algorithm and it's a (clever!) way of reducing the number of dimensions in a data set.  As a bonus, it reveals correlations between features.  In this post I want to explain the idea, the math behind it (why it's clever and why it reveals correlations between features), and how I used it in my project.  This is a new topic for me, but I want to try to explain it to the best of my abilities.  This post is going to take some research and citations, mainly from Matt's data science boot camp lecture on the topic.  I'm assuming the reader has a very basic background in statistics (mainly voabulary words), linear algebra (matrices, vectors, and maybe eigenvectors/eigenvalues), and maybe calculus (using derivatives to optimize).  

## The idea

Most data sets in practice have a large number of features, and it's impossible to graph them when there are more than 3.  PCA resets the coordinate system so that only a few of the new coordinate vectors are needed to capture most of the variance in the data, while the rest of the coordinate vectors are small enough that they can be "flattened" (eliminated).  This is useful when running _supervised learning_ algorithms on the data, since fewer dimensions make the algorithms run faster.

More abstractly, say you have a matrix of data, where the columns are indexed by the features of a data set and the rows give the observations for each feature.  PCA turns that matrix into an ordered list of vectors.  The first vector points in the direction of the highest amount of variance in the data, the second vector points in the direction of the highest amount of variance, out of all of the vectors that are perpendicular to the first.  The third vector points in the direction of the highest amount of variance out of all the vectors perpendicular to both the first and the second, and so on.  The vectors are the **PCA components**.  Each component has an "explained variance ratio", ordered from greatest to least in the component vectors, and so we can safely drop most of the components when the first few explained variance ratios add up to close to 100%. 

The following visualization is a data set with two features, $x1$ and $x2$.  The second visualization is the data replotted with the new coordinate system.  The variance in the data from the first graph is preserved in the second graph.

<!-- <img src="images/data_with_components.png" alt="Original data with PCA component vectors" width=49%> </img>
<img src="images/transformed_data.png" alt="Data with the PCA components as coordinate vectors" width=49%></img>
-->

[Original data with PCA component vectors](images/data_with_components.png)
[Data with the PCA components as coordinate vectors](images/transformed_data.png)


## The math

