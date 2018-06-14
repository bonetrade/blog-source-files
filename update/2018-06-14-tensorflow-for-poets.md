+++
title= "Tensorflow for Poets"
date= 2018-06-14T08:35:47-04:00
description = "building a classifier with tensorflow"
draft= false
+++

2018-06-14

In our recent paper, ['Fleshing Out the Bones'](https://journal.caa-international.org/articles/10.5334/jcaa.8/) we used the trained 'Inception 3' model as a way of determining clusters of images that we then studied for clues and hints: _why_ did the machine cluster them this way? What are the common features? 

Unsupervised learning: It's not unlike reading entrails.

![Diagram of the sheep's liver found near Piacenza with Etruscan inscriptions on the bronze sheep's Liver of Piacenza, Wikipedia](/update/2018-06-14-tensorflow-for-poets_files/219px-Piacenza_Bronzeleber.jpg)


An alternate approach is to take an existing model, and add new training data to it. Pete Warden put together a tutorial a few years ago called [Tensorflow for Poets](https://petewarden.com/2016/02/28/tensorflow-for-poets/) that has since been formalized as a [Google CodeLabs tutorial](https://codelabs.developers.google.com/codelabs/tensorflow-for-poets/#0). Last night I tried the tutorial out using a corpus of Roman fabrics and wares. The nuts-and-bolts of doing this are over in the [tutorials](/tutorials/tensorflow-for-poets).

The hardest part was getting the training data organized. It needs to be in a folder where each image is in a subfolder where the name of the subfolder is the category, eg:

```
|
|-training-images
  |
  |-terrasig
  |-african_red_slip
  |-veranice_nera
```  
...etc. Once that was done, it went quite smoothly. What will take some _time_ is figuring out what the different `architecture` and other flags do. For instance, in the default command suggested by the tutorial, I had to determine that I needed to add the flag on validation size and set it to use the entire training set (as my training set is probably way too small). 

```
python -m scripts.retrain \
  --bottleneck_dir=tf_files/bottlenecks \
  --how_many_training_steps=500 \
  --model_dir=tf_files/models/ \
  --summaries_dir=tf_files/training_summaries/mobilenet_0.50_224 \
  --output_graph=tf_files/retrained_graph.pb \
  --output_labels=tf_files/retrained_labels.txt \
  --architecture mobilenet_0.50_224 \
  --validation_batch_size=-1 \
  --image_dir=tf_files/gallery
```

> "The architecture flag is where we tell the retraining script which version of MobileNet we want to use. The 1.0 corresponds to the width multiplier, and can be 1.0, 0.75, 0.50 or 0.25. The 224 corresponds to image resolution, and can be 224, 192, 160 or 128. For example, to train the smallest version, you’d use --architecture mobilenet_0.25_128." [Harvey, 2017](https://hackernoon.com/creating-insanely-fast-image-classifiers-with-mobilenet-in-tensorflow-f030ce0a2991)

I'm not sure I understand exactly what this all means yet, practically speaking. Anyway, I now know what I'll need our MA research assistants to do this fall.

1. study our first corpus' clustering results to come up with some training categories
2. divide that corpus into a training dataset
3. train a new image classifier
4. run that classifier on our new corpus (which I'm still collecting)
5. compare that with the clustering approach without our new classifier.
6. compare the results of both with the posts' text

The ambition? To be able to sort at scale the images we find automatically into sensible structure. 
