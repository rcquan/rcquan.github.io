---
layout: post
categories: blog
tags: [python, sklearn, pca, principal component analysis, eigenfaces, dimensionality reduction]
preview_pic: /assets/images/2014-09-23-principal-component-analysis-eigenfaces.png
comments: true
title: Principal Component Analysis and Eigenfaces
---

After an afternoon of playing around with Python's [sklearn](http://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html) library, I present to you a short little experiment in dimensionality reduction using the [Extended Yale Faces Database B](http://vision.ucsd.edu/content/extended-yale-face-database-b-b). The extended Yale Face Database B contains 16128 images of 28 human subjects under 9 poses and 64 illumination conditions. Here are some example images from this paper:

#### Eigenfaces
<img src = "/assets/images/2014-09-23-principal-component-analysis-eigenfaces.png" class = "halfw">

#### Reconstruction using PCA
<img src = "/assets/images/2014-09-23-principal-component-analysis-eigenfaces-2.png" class = "halfw">

Although facial recognition now employs far more [sophisticated algorithms](http://arxiv.org/abs/1404.3840) to classify faces, principal component analysis ([PCA](http://en.wikipedia.org/wiki/Principal_component_analysis)) is still used in many modern approaches for pre-processing, either as a means of dimension reduction or to form basis images for different modes of variation. So even though the [proposed use of PCA](http://www.opticsinfobase.org/josaa/abstract.cfm?uri=josaa-4-3-519) for facial characterization dates all the way back to 1987, we are still seeing the so-called "[eigenface](http://en.wikipedia.org/wiki/Eigenface)" approach being used today - now that's something!

Access the iPython notebook [here](http://nbviewer.ipython.org/github/rcquan/sklearn-practice/blob/master/pca_eigenfaces.ipynb).
