+++
title = "Classify Images with Tensorflow"
description = ""
weight = 10
+++

In our [2018 paper, 'Fleshing out the Bones'](/papers), we used Duhaime's modified `classify_images.py` script using Tensorflow and Inception 3 to extract the image vectors from the second-to-last layer of the cnn (before labelling). These image vectors can then be fed through `cluster_vectors.py` to find nearest neighbors. This data can be visualized with t-sne; then we use affinity propagation to see the clusters in R.

You may obtain and run the code for yourself in our online [jupyter notebook binder](https://mybinder.org/v2/gh/shawngraham/bindr-test-Identifying-Similar-Images-with-TensorFlow/master).

The repository for this data is at [https://osf.io/9cfja/](https://osf.io/9cfja/).