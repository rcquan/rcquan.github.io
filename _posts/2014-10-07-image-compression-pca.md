---
layout: post
categories: blog
tags: [image compression, dimensionality reduction, PCA, eigenfaces]
preview_pic: /assets/images/2014-10-07-image-compression-pca.png
title: Image Compression with Principal Component Analysis
---

Ever wonder how various graphics software are able to reduce the file size of your image without a significant loss in quality? Welcome to the world of [image compression](http://en.wikipedia.org/wiki/Image_compression)!

Expanding on a [previous post](/blog/2014/09/23/principal-component-analysis-eigenfaces/) in which I used principal component analysis (PCA) to generate so-called ["eigenfaces"](http://en.wikipedia.org/wiki/Eigenface), I will be using the infamous [Lenna](http://en.wikipedia.org/wiki/Lenna) image to demonstrate how the same technique can be used to compress images and reduce file size.

Before we dive into the demonstration, however, let's briefly go over PCA in the context of color images. As most of you know, the smallest representation of a digital image on a display is called a "pixel." PNG color images, like the ones we will be using, are typically comprised of pixels in RGB space. Here is a visual representation of one RGB pixel for more clarity:

<img src = "/assets/images/2014-10-07-image-compression-pca.png" class = "halfw">

So each pixel has three dimensions associated with it - red, green, and blue.

Now let's say we have an PNG file that has the dimensions 512 x 512. The representation of this square image in RGB color space is therefore 512 x 512 x 3, a 3-D array. This may be hard to imagine, so for the purposes of interpretation, let's split this image into its individual color spaces and focus only on the red dimension, a 512 x 512 matrix.

Now that we are working with a matrix, we can do some fun statistics. Grossly summarizing the algorithm, we can use PCA to find new directions in our red color space that describe the most information (maximizing the variance of our data). We can then project our red pixel values onto this new space, being sure to choose a smaller number of dimensions without resulting in too much information loss.

We could then extend PCA to both the green and blue color spaces and stitch back individual 512 x 512 matrices into the original 3-D array.

So what does this look like? How many principal components must we use to get a similar image quality to the original while still reducing the overall file size? Check out the gallery below:![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c3e4b0d289e73ef331/1412725273683/reduced_pc1_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c3e4b0d5d3278fb8c0/1412725287775/reduced_pc2_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c3e4b0d5d3278fb8c2/1412725316192/reduced_pc5_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c3e4b0d5d3278fb8c4/1412725334947/reduced_pc10_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c3e4b021140b8afa90/1412725446864/reduced_pc15_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c3e4b0d5d3278fb8c6/1412725441952/reduced_pc20_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c4e4b021140b8afa92/1412725454101/reduced_pc30_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c4e4b0d5d3278fb8c8/1412725460574/reduced_pc40_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c4e4b021140b8afa94/1412725466654/reduced_pc50_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c4e4b0d5d3278fb8ca/1412725472556/reduced_pc60_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c4e4b021140b8afa96/1412725478301/reduced_pc70_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c4e4b021140b8afa98/1412725484678/reduced_pc80_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c4e4b021140b8afa9a/1412725495751/reduced_pc90_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/543479c4e4b021140b8afa9c/1412725507164/reduced_pc100_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/54347fa5e4b03176bba43c6c/1412726710097/reduced_lenna.png)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/54347fa0e4b0d289e73f008a/1412726723981/lenna.png)

Interesting! But did we reduce the file size at all?

![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/54348f32e4b0f145b0834b4d/1412730680988/#img.png)

Awesome! We can even see how the first few principal components captures most of the information (variability) and how the reduction in file size for subsequent components decreases - just as PCA [says it should](http://little-book-of-r-for-multivariate-analysis.readthedocs.org/en/latest/_images/image6.png)!

As always, I encourage you to try it for yourself. Here's some R code so you can go wild:

<script src="https://gist.github.com/rcquan/089e47403c5290a65b31.js"></script>


