# Rock Paper Scissors Image Classification
## Introduction
I set out to construct a neural network that could accurately predict whether a rock, paper or scissors hand gesture was being made in an image from the game of rock paper scissors. I obtained the modeled dataset containing 2,188 images from Kaggle. The neural network that I built had a validation accuracy of .945, which outperformed that baseline dummy classifier accuracy of .332.

## Obtain Data
I went onto Kaggle and found a rock-paper-scissors dataset consisting of images of hands in the three positions associated with the game rock-paper-scissors: 1) rock, a closed fist 2) paper, an open hand and 3) scissors, a closed fist with the exception of the pointer and middle fingers being extended out. The dataset included 2,188 images. My modeling goals was to build a convolutional neural network model that could classify an image of a rock-paper-scissors hand gesture into the proper positional class.

## Scrub Data

I downloaded the kaggle dataset in 3 folders, with each folder containing all of the png format images associated with one of the 3 rock, paper and scissors classes. I used the split_folders python package to perform an 80–20 train test split on each of the 3 folders followed by a second 80–20 train test split on the training set from the first split. This created a training dataset for training my neural network, a testing set for selecting the top performing neural network and a validation set for evaluating the the top performer and overall result of the modeling process.

The split_folders package created train, test and validation folders, with each containing 3 subfolders for images of each class. This conveniently represented the format needed for Keras to convert the images into a usable form for modeling. I used the Keras ImageDataGenerator function in order to generate rgb pixel value-based image data from the files as well as image class labels that could be used as the x and y variables respectively to build a convolutional neural network in Keras.

## Explore Data

<a href="url"><img src="https://github.com/blantj/rps_image_classification/blob/main/Images/image_shape.png" align="middle" height="200" width="500" ></a>

In order to explore my dataset, I first printed the shape of the image data for the train, test and validation sets. This revealed that the train set contained 1,399 images, the test set included 352 images and the validation set included 437 images. The data for each image consisted of a 300x200x3 tensor representing a 300 pixel by 200 pixel image size across red, green and blue values for each pixel.

<a href="url"><img src="https://github.com/blantj/rps_image_classification/blob/main/Images/class_distribution.png" align="middle" height="200" width="250" ></a>

I next used a count plot to graph the class distribution of the entire rock-paper-scissors dataset. The dataset was nearly class balanced with 32.5% paper images, 33.2% rock images and 34.3% scissors images. I decided not to perform any resampling, as I thought that this class balance was sufficient to prevent the neural network from overpredicting the dominant class.

## Model Data

<a href="url"><img src="https://github.com/blantj/rps_image_classification/blob/main/Images/neural_network.png" align="middle" height="250" width="500" ></a>

I first built a baseline dummy classifier to evaluate neural network performance against. This model had an accuracy score of .332. I next trained a convolutional neural network in Keras. This model had a testing accuracy of .940 and a validation accuracy of .945. While this model significantly outperformed the baseline model and was therefore of significant value, I think that I could improve performance more with more computing power and time as each neural network took about 30 minutes to train, limiting the number of models I could build.

## Analyze Results

<a href="url"><img src="https://github.com/blantj/rps_image_classification/blob/main/Images/confusion_matrix.png" align="middle" height="250" width="250" ></a>

Looking at the cnn conusion matrix, 3.9 points worth of the 5.5% of data that was misclassified consisted of the model confusing paper images with scissors images. This would suggest that while the model was able to better distinguish the lack of fingers in a rock hand gesture, it at times failed to distinguish between the two outstretched fingers in scissors and the five outstretched fingers in paper. With more time, I would like to gridsearch new neural network structures in hopes of correcting this issue and improving model performance.

# Github Files
[Modeling.ipynb](https://github.com/blantj/rps_image_classification/blob/main/Modeling.ipynb) :  Rock Paper Scissors Image Classification Modeling

# Sources
Kaggle: https://www.kaggle.com/c/rock-paper-scissors/overview/description
