# Nerual-Network-Image-Data

# Import data
The data we will be using are computer generated images of hands showing the different pose for rock paper scissors. The “rock paper scissors” dataset is available directly from the Tensorflow package. In the cells that follow, we’ll get the data, plot a few examples, and also do some pre-processing.

# Pre-process dataset
Even though the images for our analysis are cropped but we still need to scale the images and pre-process it before they can be used as suitable input for our models. As the existing models have few constraints about the size of the input image we need to reshape our data set.

# Background: fine-tuning a model
When we talk about convolutional neural network we take into considerations of a lot of layers between to input and the output and a typical convolutional neural network looks something like this:
![image](https://user-images.githubusercontent.com/55652596/116507829-b1d99e80-a8dd-11eb-8079-03418c1f38e3.png)

We have a sequence of convolutional layers followed by pooling layers. These layers are feature extractors that “learn” key features of our input images.
Then, we have one or more fully connected layers followed by a fully connected layer with a softmax activation function. This part of the network is for classification.
The key idea behind transfer learning is that the feature extractor part of the network can be re-used across different tasks and different domains.
This is especially useful when we don’t have a lot of task-specific data. We can get a pre-trained feature extractor trained on a lot of data from another task, then train the classifier on task-specific data.
The general process is:
Get a pre-trained model, without the classification layer.
Freeze the base model.
Add a classification layer.
Train the model (only the weights in your classification layer will be updated).

# Fine-tune model
We have fitted our own classification head, but there’s one more step we can attempt to customize the model for our particular application.
We are going to “un-freeze” the later parts of the model, and train it for a few more epochs on our data, so that it is better suited for our specific classification task.
Note that we are not creating a new model. We’re just going to continue training the model we already started training.

# Conclusion
In practice, for most machine learning problems, we wouldn’t design or train a convolutional neural network from scratch — we would use an existing model that suits our needs (does well on ImageNet, size is right) and fine-tune it on our own data.Application of transfer learning is endless and it has seen an upsurge in its application since the advent of powerful GPU’s and computational hardware.
