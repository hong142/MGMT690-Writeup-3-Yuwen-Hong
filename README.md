# Object Detection with Tensorflow
In previous writeups, we've discussed our team's plan to develop and implement a pipeline for security system object detection analyses, and we've covered the setup of data storage and organization. Our next focus is the analysis and machine learning process. This writeup introduces Tensorflow, the software we are going to use for the process, based on why we choose it and how we use it. 
## Intro to Neural Nets
Before we talk about the Tensorflow, we need to briefly introduce the concept of 'neural network', becuase its our choice of approch for our model building. In artificial context, it means a network of nodes connected in a way similar to the biological neural network in a brain. The picture below shows a relatively simple neural network example. Basically, the whole network represents a function used in the machine learning process, with each node represents a sub-function. The left side is input layer and each node represents an input (feature). The data pass through those functions to reach the right side, which gives us the output. More complication can be added to the network if more hidden layers is added, although a single hidden layer is powerful enough for majority of classification tasks.

<img src="https://github.com/hong142/MGMT690-Writeup-3-Yuwen-Hong/blob/master/network.png" width="350">

The assumption here is that some relationships exist between input elements and output elements. We define the inputs, outputs and a basic structure. The network is going to figure out those relationships for us, in other words, getting the proper weights of each inputs as well as bias for the ultimate function.

There might be several reasons you can't get the relationship out of the network. Typically, it's either because you don’t have the right data, which are right features to describe the relationship you want, or because your network is not complicated enough to detect that relationship.

By combining things in a lot of different ways, we get flexibility in combining inputs. The process of randomly changing weights and bias until the function totally mimic the relationship is what we called “training process’, a combination of defining the function and parameterization of inputs. The function providing a good output is a trained model. 
## Intro to Tensorflow
The analysis model we want to build is about object detection and we want to do it through a neural network. Currently, Tensorflow came out of google is a good choice, because it is free and was designed for very large scale analyses, including those using neural network.
### Why Tensorflow
1. Portable

One of the advantage of Tensorflow is its portableness. It uses graph-based computation, in which any sort of operation you do on a computer can be represented as a graph. Here is an example of graph representation of a complicated function. 

<img src="https://github.com/hong142/MGMT690-Writeup-3-Yuwen-Hong/blob/master/graph.png" width="350">

When operations are broken down into the graph form, your complied codes are portable as any function at the lowest level can be represented by this graph and is well defined. You can implement the computational stuff in almost any environment. On the other hand, Scikitlearn, another commonly used free software library for machine learning, has many restrictions on input, scale and running environment. It requires systems that can install the software and can only run certain types of data on a relatively small scale. 

2. Distributed, Flexible

Another advantage of Tensorflow due to its graphical representation is that works can be distributed and in a flexible way. You may have noticed that while some of steps in the function have to be executed consequently, some of them can run simultaneously. By setting things up in graphics, we can separate different steps, and distribute them across different machines or instances in a cloud, so that we can expect to run things much faster than we would if we run all of the steps on a single computer. Moreover, depends on the architecture or environment we assigned, we get the flexibility to distribute things in varies ways to accelerate the process and get optimization for the assigned architecture. It doesn’t matter whether the architecture is a GPU or CPU or a cluster of any of them.

However, in general, we only use Tensorflow for distributing machine learning or image-based processing. You probably don’t want to turn to Tensorflow if you can finish the implementation shortly on a single machine. Otherwise, instead of saving time, you may actually generate extra trouble for your implementation.

3. Active, Supported

In addition to the flexibility in terms of where and how you can run it, Tensorflow is also well supported. It has an active community, where probably thousands of people are working on it every day to get bugs fixed and make it better. If you search for Tensorflow on Github, there are currently more than 21K repository and more than 241K commits about it. You can expect to get answers or solutions for your problems quickly through the communities such as Slack and Github. 

<img src="https://github.com/hong142/MGMT690-Writeup-3-Yuwen-Hong/blob/master/active.png" width="600">

But at the same time, you can’t expect to contact a certain service person to get your problems solved in a short amount of time with guarantee. Here comes the tradeoff between open source and proprietary software. With open source, you do not have to pay for anything, so you also do not get any customized customer support. That’s why it’s important to make sure the open source software you intend to use has an active community around it, so that you would not stuck in a problem forever. Besides, you also need to make sure the software is compatible with your intended environment. As we mentioned, Tensorflow is compatible with most environment.


4. Nice Object Detection API

Tensorflow object detection API has a nice interface and everything for the API is well-documented. With many prebuilt models, the barrier of entry to do object detection in Tensorflow is very low, and usually you don’t have to start from scratch. Especialy, the common setup of obejct detection, such as visulization of box and lable on object is taken care of by the APT, saving us a lot time in coding. There are varies ways to interact with the API depends on your need. Our team is planning to use Python as our programming language, so we can call it just like we call a package in python. You can also set a sever to interact with it.
## Hands on with Tensorflow
Currently, there is no Pachyderm on our team’s machines, and we are connected to a remote machine in DigitalOcean’s cloud with a program called SSH. We will just guide you through the basic running process of Tensorflow object detection from python. 

As we mentioned about the API, we called Tensorflow from python similar to calling a package. Then we put our images into the image-before folder. In the same folder, we ran a prebuilt model where all the reference things are defined, including the location of the labels and the size of output images.  Tensorflow would read in the image and translate it to a series of descriptive values, such as color, brightness and RBG. Then those values become the input values for the input layer of the neural network. And the data was further processed to get an output indicating the object in the image corresponds to a certain label. And Tensorflow would go through the label map to identify the object name and visualize it on the image. Those middle processes are invisible and do not requiring extra actions from us. All we get is an output image in another folder with a little box and name of object, sometimes with a possibility, on the detected object. The following shows the input and output of one detection using a jpg image of an owl.

<img src="https://github.com/hong142/MGMT690-Writeup-3-Yuwen-Hong/blob/master/before.png" width="350" height ="300">   <img src="https://github.com/hong142/MGMT690-Writeup-3-Yuwen-Hong/blob/master/after.png" width="350" height ="300">

This time, our team used an already trained model from Tensorflow, which is already fairly robust because the model has been trained by tons of different images. In the future, we will talk about how to expand the model and where to put more training in to better fit our intruder detection purpose. If you trained a new model, fitted in parameters, and you want to save it, you could do it with protobuf file, recording where the model is defined, weights and bias, and how to run the network.

During the process, we had to do a couple of preprocessing steps, including manually copying stuff back and forth from servers. It was not only annoying but also causing many unexpected problems. Obviously, it would be even more troublesome if we are working on a large scale and want the process to run continuously. As a result, our team’s ultimate goal is to automate the process of moving and analyzing data. When we do the full deployment, there will be Pachyderm and Kubernetes.

