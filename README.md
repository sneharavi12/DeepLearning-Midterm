# DeepLearning-Midterm
This repo contains the solution for Kaggle's 'Utrasound Nerve Segmentation' problem
Kaggle Competition Link: https://www.kaggle.com/c/ultrasound-nerve-segmentation#description

Objective:
Segmenting the Brachial Plexus with Deep Learning.
Predict which pixels of an ultrasound image contain the brachial plexus

Data:
5635 Training Images , Size: 420 x 580
Respective Training Masks annotated by humans for each of the training images , 420 x 580
5,508 testing images

Evaluation:
This competition was evaluated with Dice Score between the test and segmented images.

The basic model, was a direct implementation of U-NET as in this paper: https://arxiv.org/pdf/1505.04597.pdf
The keras model for the same was adopted from jocicmarko's implemetation of the U-Net model.

There are three models this was run to understand the nature and working of hyperparameters.

Model 1 - This was a regular neural net implementation.
Input - Flattened 1-D image, input to Dense Layer
1 hidden layer
Output - Flattened 1-D image, Dense Layer

The mean deice coefficient over all the images started at -0.41 and improved to  only 0.0315 after 200 epochs
