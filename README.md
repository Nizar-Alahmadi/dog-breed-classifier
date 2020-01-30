# Data Scientist Nanodegree

# Project: Dog Breed Classifier

# Project Overview

if you are looking for a guided deep learning and convolutional neural networks, you are in the right place. The goal is to classify images of dogs according to their breed, developing an algorithm that could be used as part of a mobile or web app. If a dog is detected in the image, it will provide an estimate of the dog's breed. If a human is detected, it will provide an estimate of the dog breed that is most resembling.

# project motivation

i've completed several guided projects, and now's my chance to show off your skills and creativityIn this capstone project, i will leverage what i’ve learned throughout the program to build a data science project.
 
# The Road Ahead

We break the notebook into separate steps :

* Step 0 : Import Datasets
* Step 1 : Detect Humans
* Step 2 : Detect Dogs
* Step 3 : Create a CNN to Classify Dog Breeds (from Scratch)
* Step 4 : Use a CNN to Classify Dog Breeds (using Transfer Learning)
* Step 5 : Create a CNN to Classify Dog Breeds (using Transfer Learning)
* Step 6 : Write your Algorithm
* Step 7 : Test Your Algorithm

# Instructions

If you want to run this code on your local computer, you'll also need to download the following;

[Dog dataset](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/dogImages.zip). Unzip the folder and place it in the repo, at location path/to/dog-project/dogImages.

[Human dataset](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/lfw.zip). Unzip the folder and place it in the repo, at location path/to/dog-project/lfw. If you are using a Windows machine, you are encouraged to use 7zip to extract the folder.

[VGG-16 bottleneck](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/DogVGG16Data.npz) features for the dog dataset. Place it in the repo, at location path/to/dog-project/bottleneck_features.

[VGG-19 bottleneck features](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/DogVGG19Data.npz) for the dog dataset. Place it in the repo, at location path/to/dog-project/bottleneck_features.

[ResNet-50 bottleneck features](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/DogResnet50Data.npz) for the dog dataset. Place it in the repo, at location path/to/dog-project/bottleneck_features.

[Inception bottleneck features](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/DogInceptionV3Data.npz) for the dog dataset. Place it in the repo, at location path/to/dog-project/bottleneck_features.

[Xception bottleneck](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/DogXceptionData.npz) features for the dog dataset. Place it in the repo, at location path/to/dog-project/bottleneck_features




I recommend setting up an environment for this project to ensure you have the proper versions of the required libraries.

# Install

For Mac/OSX:

	conda env create -f requirements/aind-dog-mac.yml
	source activate aind-dog
	KERAS_BACKEND=tensorflow python -c "from keras import backend"
For Linux:

	conda env create -f requirements/aind-dog-linux.yml
	source activate aind-dog
	KERAS_BACKEND=tensorflow python -c "from keras import backend"
For Windows:

	conda env create -f requirements/aind-dog-windows.yml
	activate aind-dog
	set KERAS_BACKEND=tensorflow
	python -c "from keras import backend"
 
This project requires Python 3 and the following Python libraries installed:

NumPy


Pandas


matplotlib


scikit-learn


keras


OpenCV


Matplotlib

Scipy


Tqdm


Pillow


Tensorflow


Skimage


IPython Kernel


You will also need to have software installed to run and execute an iPython Notebook

I recommend you install Anaconda, a pre-packaged Python distribution that contains all of the necessary libraries and software for this project


# file descriptions

there is dog_app.ipynb where the possible solution will found.

there is bottleneck_features when you Pick one of the above architectures, download the corresponding bottleneck features, and store the downloaded file in the bottleneck_features/ folder in the repository.

there is images where you will find the images to test your algorithm . Feel free to use any images you like. Use at least two human and two dog images.

there is saved_models where you will find the models those i worked on

# improvements section 

Create a CNN to Classify Dog Breeds (from Scratch)

i create CNN from scratch and i use using transfer learning to train a CNN , **with test accuracy of 7.8947%.**

Our three first layers is Conv2D layers. convolution layers that will deal with our input images, which are seen as 2-dimensional matrices. their number of filters  16,32,64 is the number of nodes, Kernel size is the size of the filter matrix for our convolution.So a kernel size of 2 means we will have a 2x2 filter matrix or feature detector.Padding is used on the convolutional layers to ensure the height and width of the output feature maps matches the inputs. The activation function we will be using for our layers is the ReLU Rectifier Linear Unit which helps with non linearity in the neural network. Our first layer also takes in an input shape.This is the shape of each input image, 224, 224, 3 

And between these layers I added a Max Pooling Layer. we apply max pooling for translational invariance. Translational invariance is when we change the input by a small amount the outputs do not change. Max pooling reduces the number of cells. Pooling helps detect features like colors, edges etc. For max pooling, we use the pool_size of 2 by 2 matrix for all 32 feature maps.

After that, there is a "Flatten" layer. Flatten serves as a connection between the convolution and dense layers.step is to flatten all the inputs. The flattened data will be the input to the fully connected neural network.

'Dense’ is the layer type we will use in for our output layer. Dense is a standard layer type that is used in many cases for neural networks.

we use Dropout rate of 20% to prevent overfitting.

The activation is ‘softmax’. Softmax makes the output sum up to 1 so the output can be interpreted as probabilities. The model will then make its prediction based on which option has the highest probability.


use a CNN to Classify Dog Breeds (using Transfer Learning)

i Use a CNN to Classify Dog Breeds from pre-trained VGG-16 model **with test accuracy: 36.9617%.**

The model uses the the pre-trained VGG-16 model as a fixed feature extractor, where the last convolutional output of VGG-16 is fed as input to our model.i only add a global average pooling layer and a fully connected layer, where the latter contains one node for each dog category and is equipped with a softmax.

Create a CNN to Classify Dog Breeds (using Transfer Learning)

then i use transfer learning to create a CNN that can identify dog breed from images. **with 78.9474% accuracy on the test set.**

I used the CNN architecture with the Resnet50 bottleneck and adding the GlobalAveragePooling2D to flatten the features into a vector that could be fed into a fully-connected layer to the end of the ResNet50 model.where the fully -connected layer contains one node for each dog category and is equipped with a softmax.

The output is meeted expectation but it could be improved much better if :

1- Increase the Training Data

to benifit from our training data, we will increase it throug a random transformations, so that model would not use the same picture. This helps prevent overfitting and helps the model generalize better. This can be done throug keras.preprocessing.image.ImageDataGenerator. 

2- Add more epochs in the training process

Every Epoch will pass dataset forward and backward through the neural network.
The number of epochs is related to how diverse your data is until some point.

3- Use more layers of the neural network

Increasing the number of layers will increase the capacity of the model with fewer resources, and modern techniques allow learning algorithms to successfully train deep models.

# result section 

I used the 'transfer learning - Resnet50 model' to implement an algorithm for a Dog Breed Classification application. The user provides an image, and the algorithm first detects whether the image is human or dog. If it is a dog, it predicts the breed. If it is a human, it returns the resembling dog breed.


# A blog [post](https://medium.com/@awesome_india_bear_819/dog-breed-classifier-87896810bb52)

