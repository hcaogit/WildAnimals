# WildAnimals

## Domain Background

Camera Traps (or Wild Cams) enable the automatic collection of large quantities of image data. Biologists all over the world use camera traps to monitor biodiversity and population density of animal species. Scientists have recently been making strides towards automating the species classification challenge in camera traps, but as they try to expand the scope of these models from specific regions where they have collected training data to nearby areas they are faced with an interesting probem: how do you classify a species in a new region that you may not have seen in previous training data?

In order to tackle this problem, they have prepared a challenge where the training data and test data are from different regions, namely The American Southwest and the American Northwest. The species seen in each region overlap, but are not identical, and the challenge is to classify the test species correctly. To this end, we will allow training on our American Southwest data (from CaltechCameraTraps), on iNaturalist 2017/2018 data, and on simulated data generated from Microsoft AirSim. We have provided a taxonomy file mapping our classes into the iNat taxonomy.

More Details of the project can be found at: https://www.kaggle.com/c/iwildcam-2019-fgvc6/overview

## Problem Statement

Classify a species in a new region that you may not have seen in previous training data.

## Datasets and Inputs

The training set contains 196,157 images from 138 different locations in Southern California. You may also choose to use supplemental training data from iNaturalist 2017, iNaturalist 2018, iNaturalist 2019, and images simulated with Microsoft AirSim. As a courtesy, we have curated all the images from iNaturalist 2017/2018 containing classes that might be in the test set and mapped them into the iWildCam categories. This data (which we call "iNat Idaho") can be downloaded from our git page here.

The test set contains 153,730 images from 100 locations in Idaho.

The competition task is to label each image with one of the following label ids:

name, id
empty, 0
deer, 1
moose, 2
squirrel, 3
rodent, 4
small_mammal, 5
elk, 6
pronghorn_antelope, 7
rabbit, 8
bighorn_sheep, 9
fox, 10
coyote, 11
black_bear, 12
raccoon, 13
skunk, 14
wolf, 15
bobcat, 16
cat, 17
dog, 18
opossum, 19
bison, 20
mountain_goat, 21
mountain_lion, 22


## Solution Statement


The minimum requirement of the model output is to have a better than random recognition rate. A better than 50% rate would be more desirable.

## Benchmark Model

We are also providing a general animal detection model, using Faster-RCNN with Inception-Resnet-v2 backbone and atrous convolution, which competitors are free to use as they see fit.

Sample code for running the detector over a folder of images can be found here.

We have run the detector over the three datasets and provide the top 100 detected boxes for each image with their associated confidence here.

## Evaluation Metrics

Submissions will be evaluated based on their macro F1 score - i.e. F1 will be calculated for each class of animal (including "empty" if no animal is present), and the submission's final score will be the unweighted mean of all class F1 scores.

The submission format for the competition is a csv file with the following format:

Id,Category
58857ccf-23d2-11e8-a6a3-ec086b02610b,1
591e4006-23d2-11e8-a6a3-ec086b02610b,5

The Id column corresponds to the test image id. The Category is an integer value that indicates the class of the animal, or 0 to represent the absence of an animal.

## Project Design

Student is suggested to design a convolutional network, train the model on the training data set, then use the model to label the testing set. 

