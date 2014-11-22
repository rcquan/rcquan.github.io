---
layout: post
categories: blog
tags: [image compression, dimensionality reduction, PCA, eigenfaces]
preview_pic: /assets/images/2014-10-07-image-compression-pca.png
comments: true
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

So what does this look like? How many principal components must we use to get a similar image quality to the original while still reducing the overall file size? Check out the gallery below:

<iframe class="imgur-album" width="100%" height="550" frameborder="0" src="//imgur.com/a/08sUP/embed?background=f2f2f2&amp;text=1a1a1a&amp;link=4e76c9"></iframe>

Interesting! But did we reduce the file size at all?

<img src = "/assets/images/2014-10-07-image-compression-pca-2.png" class = "halfw">

Awesome! We can even see how the first few principal components captures most of the information (variability) and how the reduction in file size for subsequent components decreases - just as PCA [says it should](http://little-book-of-r-for-multivariate-analysis.readthedocs.org/en/latest/_images/image6.png)!

As always, I encourage you to try it for yourself. Here's some R code so you can go wild:

<script src="https://gist.github.com/rcquan/089e47403c5290a65b31.js"></script>


