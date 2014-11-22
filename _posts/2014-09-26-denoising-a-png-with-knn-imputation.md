---
layout: post
categories: blog
tags: [knn, image recovery, data science]
preview-pic: /assets/images/2014-09-26-denoising-a-png-with-knn-imputation.png
title: Denoising a PNG with kNN Imputation
---

Given a PNG image with noise, where noise is defined as having an RGB value equal to [0, 0, 0], we can use k-nearest neighbors imputation to fill in the zeros using nearest neighbor averaging.

For each row with a zero value, we find the k-nearest neighbors using a Euclidean metric, confined to columns for which that row is not zero. The accuracy of this image restoration technique will vary depending on how we set our `k` parameter.

Here, we attempt to denoise [Lena.png](https://www.dropbox.com/s/hq40pvtelpawp84/Lena_noise.png?dl=0). The target image can be downloaded [here](https://www.dropbox.com/s/9xduhkpe9zguaro/lenna.png?dl=0). See what happens when we vary the `k` parameter.

![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088de4b084cab60b5f24/1411778772887/png_processing1x1.jpg)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088de4b017861366b7ca/1411778925242/png_processing2x1.jpg)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088ee4b084cab60b5f26/1411778931242/png_processing3x1.jpg)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088ee4b084cab60b5f28/1411778936970/png_processing4x1.jpg)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088ee4b084cab60b5f2a/1411778942179/png_processing5x1.jpg)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088ee4b084cab60b5f2c/1411778947089/png_processing6x1.jpg)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088ee4b084cab60b5f2e/1411778955097/png_processing7x1.jpg)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088ee4b084cab60b5f30/1411778962702/png_processing8x1.jpg)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088ee4b084cab60b5f32/1411778970139/png_processing9x1.jpg)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088ee4b084cab60b5f3f/1411778977852/png_processing10x1.jpg)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088ee4b084cab60b5f45/1411778985327/png_processing11x1.jpg)![](http://static.squarespace.com/static/535d5283e4b0b9aa73979311/539493cce4b0879e3181f243/5426088ee4b084cab60b5f48/1411778992852/png_processing12x1.jpg)

So which value of k do you think produces the best image? Try denoising the image yourself with the script provided below:

<script src="https://gist.github.com/rcquan/bb8066562c15c42678c2.js"></script>
