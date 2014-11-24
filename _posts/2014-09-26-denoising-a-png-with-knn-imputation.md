---
layout: post
categories: blog
tags: [knn, data science, image recovery, imputation]
preview_pic: /assets/images/2014-09-26-denoising-a-png-with-knn-imputation.png
comments: true
title: Denoising a PNG Image with kNN Imputation
---

Given a PNG image with noise, where noise is defined as having an RGB value equal to [0, 0, 0], we can use k-nearest neighbors imputation to fill in the zeros using nearest neighbor averaging. For each row with a zero value, we find the k-nearest neighbors using a Euclidean metric, confined to columns for which that row is not zero. The accuracy of this image restoration technique will vary depending on how we set our `k` parameter.

Here, we attempt to denoise [Lena.png](https://www.dropbox.com/s/hq40pvtelpawp84/Lena_noise.png?dl=0). The target image can be downloaded [here](https://www.dropbox.com/s/9xduhkpe9zguaro/lenna.png?dl=0). See what happens when we vary the `k` parameter.

<iframe class="imgur-album" width="100%" height="550" frameborder="0" src="//imgur.com/a/USfRg/embed?background=f2f2f2&amp;text=1a1a1a&amp;link=4e76c9"></iframe>

So which value of k do you think produces the best image? Try denoising the image yourself with the script provided below:

<script src="https://gist.github.com/rcquan/bb8066562c15c42678c2.js"></script>
