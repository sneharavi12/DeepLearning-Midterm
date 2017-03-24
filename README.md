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

Model 1 - Neural net implemented with MLPs.
Input - Flattened 1-D image, input to Dense Layer
1 hidden layer
Output - Flattened 1-D image, Dense Layer
The mean dice coefficient over all the images started at -0.41 and improved to  only 0.0315 after 200 epochs

Model 2 - Neural Net with CNNs. This was a simplified U-net with just one Downsampling and Upsampling Layers
The input images are pre processed - Standardized, broght to a smaller resolution and 
After a dropout layer of 25%, in the contacting path of the U-net, the model consiss of 4 convolution Layers and two maxpooling layers.
In the expanding path, the upsampling layer is followd by two convolutions, 32 filters each.
The final layer is a single channel 1x1 convolution 3D, giving the same number of ouput pixels.
The model is compiled with Adam Optimizer, 0.00001 Learning Rate.

Model 3 - The complete UNET.
The input images are pre processed - Standardized, broght to a smaller resolution.
The Unet model is trained.
It is run for 100 epochs. Each training epoch took about 1500 Seconds on an Amazon EC2 instance enabled with CUDA.

Hyperparamets tweaks and results:
1. Reducing the number of layers only decreased the dice coefficient
2. Increased the number of layers, adding another level of depth. This slowed down the training process. Each epoch took about 4500 seconds. This experiment was stopped after one epoch with the interest of time




