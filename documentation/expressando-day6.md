<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<p align="center">
<img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png" style="height:auto; width:50%"></img>
</p>

<h1 align="center">DAY 6</h1>

# Demonstration of Data-Collection and Introduction to TensorFlow 

In this session, we are going to have a demonstartion on how to collect data with increased precision. This is a vital step, as it governs the future processes which are required in making the model. So let us begin.

## What is a 'Dataset'? 

A Dataset as **a collection of data that is treated as a single unit by a computer**. This means that a dataset contains a lot of separate pieces of data/images but can be used to train an algorithm with the goal of finding predictable patterns inside the whole dataset. The datasets contains individual classes, which are representation of the single unit. Here. we will be having two **customised** datasets - **test** and **train**. Each dataset here contains: 0, 1, 2, 3, 4 and 5, which are the classes, or the single units.

Datasets are of three types: 
* **Training Dataset** - This dataset which contains the necessary data with which the model is to be trained. This dataset contains the maximum amount of data, and it is primarily used by the machine for comparison. 
* **Validation Dataset** - This dataset checks for the validation of the input in accordance with the training dataset. It is a subset of the training dataset. It eliminates unnecessary inputs, and increase the speed of operation.
* **Test Dataset** - This dataset is used for testing the models, and determine the accuracy and losses which are incurred while training the machine. This is very much important, as it serves as a test set for the training data, and the user can verify the results.

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138554679-310f64e8-a1d0-4711-8552-5b4bc246d18d.png" style="height:auto; width:80%"></img></h1>


Now let us go thorugh a quick example on how to collect data:

## Step 1: 

Run the **collect-data.py** file using the command:

```bash
python collect-data.py
```
The window will open, taking a reference input from the webcam. It will also display a thresholded image of the area under the rectangle (**Region of Interest**) in another window. This image will be recorded under the respective directories of the dataset.

## Step 2:

Let us first begin with the "**zero**" gesture, which basically involves a closed fist. Bring the gesture close inside the Region of Interest, as much that it is completely enclosed within the rectangle, and covers most of the area of the region. 

Make sure, you have a clear background and do not let unexpected disturbances to appear inside the rectangle/ROI. Try to collect clear data as much as possible. Make sure all your fingers are visible. 

Then, start collecting the data by pressing '**0**' of the numpad. This will capture the images, which will be the images stored in the dataset under the **train** directory in the **0** folder. 

Collect approximately **100-120** images to train the model. Make sure to collect data, while changing your orientation over the rectangle, so that the machine can recognise the gesture whenever you show the gesture as input inside the rectangle.  

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138554772-5aaee721-fc1c-47d3-be1b-1c72c3e56d45.jpeg" style="height:auto; width:80%"></img></h1>

## Step 3:

Let us first begin with the "**one**" gesture, which basically involves only the index finger. Please note that you should train by only using one finger. Do not collect numerous data having the same gesture being shown by different fingers. It results in inaccuracy and losses. Bring the gesture close inside the Region of Interest, as much that it is completely enclosed within the rectangle, and covers most of the area of the region. 

Make sure, you have a clear background and do not let unexpected disturbances to appear inside the rectangle/ROI. Try to collect clear data as much as possible. Make sure all your fingers are visible. 

Then, start collecting the data by pressing '**1**' of the numpad. This will capture the images, which will be the images stored in the dataset under the **train** directory in the **1** folder. 

Collect approximately **100-120** images to train the model. Make sure to collect data, while changing your orientation over the rectangle, so that the machine can recognise the gesture whenever you show the gesture as input inside the rectangle.  

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138554837-24f74153-afab-4412-9f06-f9d1b27ceec0.jpeg" style="height:auto; width:80%"></img></h1>

## Step 4:

Let us first begin with the "**two**" gesture, which basically involves the two fingers, separated by some uniform space (The Victory Sign). It is one of the difficult gestures as the space between the two fingers, needs to be a lot more constant. Also, train with the same two fingers, as you have did while collecting the data. Do not use different fingers as differnet inputs. The machine might not give accurate results as the shape is not being maintained if you use different fingers. Bring the gesture close inside the Region of Interest, as much that it is completely enclosed within the rectangle, and covers most of the area of the region. 

Make sure, you have a clear background and do not let unexpected disturbances to appear inside the rectangle/ROI. Try to collect clear data as much as possible. Make sure all your fingers are visible. 

Then, start collecting the data by pressing '**2**' of the numpad. This will capture the images, which will be the images stored in the dataset under the **train** directory in the **2** folder. 

Collect approximately **100-120** images to train the model. Make sure to collect data, while changing your orientation over the rectangle, so that the machine can recognise the gesture whenever you show the gesture as input inside the rectangle.  

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138554910-6f1b263e-eee5-4d5c-a43c-e0c60a87bd7c.jpeg" style="height:auto; width:80%"></img></h1>

## Step 5:

Let us first begin with the "**three**" gesture, which basically involves only the three middle fingers, except the thumb and the ring finger. Follow the rules as above. Bring the gesture close inside the Region of Interest, as much that it is completely enclosed within the rectangle, and covers most of the area of the region. 

Make sure, you have a clear background and do not let unexpected disturbances to appear inside the rectangle/ROI. Try to collect clear data as much as possible. Make sure all your fingers are visible. 

Then, start collecting the data by pressing '**3**' of the numpad. This will capture the images, which will be the images stored in the dataset under the **train** directory in the **3** folder. 

Collect approximately **100-120** images to train the model. Make sure to collect data, while changing your orientation over the rectangle, so that the machine can recognise the gesture whenever you show the gesture as input inside the rectangle.  

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138554920-a9fe139d-537b-4240-baa5-a953176d05d8.jpeg" style="height:auto; width:80%"></img></h1>

## Step 6:

Let us first begin with the "**four**" gesture, which basically involves the four fingers, except the thumb. Follow the rules as above. Bring the gesture close inside the Region of Interest, as much that it is completely enclosed within the rectangle, and covers most of the area of the region. 

Make sure, you have a clear background and do not let unexpected disturbances to appear inside the rectangle/ROI. Try to collect clear data as much as possible. Make sure all your fingers are visible. 

Then, start collecting the data by pressing '**4**' of the numpad. This will capture the images, which will be the images stored in the dataset under the **train** directory in the **4** folder. 

Collect approximately **100-120** images to train the model. Make sure to collect data, while changing your orientation over the rectangle, so that the machine can recognise the gesture whenever you show the gesture as input inside the rectangle.   

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138554938-c037c869-a723-45e3-8781-ff3bcfc4ba64.jpeg" style="height:auto; width:80%"></img></h1>

## Step 7:

Let us first begin with the "**five**" gesture, which basically involves all the fingers as in an open palm. Follow the rules as above. Bring the gesture close inside the Region of Interest, as much that it is completely enclosed within the rectangle, and covers most of the area of the region. 

Make sure, you have a clear background and do not let unexpected disturbances to appear inside the rectangle/ROI. Try to collect clear data as much as possible. Make sure all your fingers are visible. 

Then, start collecting the data by pressing '**5**' of the numpad. This will capture the images, which will be the images stored in the dataset under the **train** directory in the **5** folder. 

Collect approximately **100-120** images to train the model. Make sure to collect data, while changing your orientation over the rectangle, so that the machine can recognise the gesture whenever you show the gesture as input inside the rectangle.   

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138554954-320e70ab-e6ec-4598-8149-a334ae8aa452.jpeg" style="height:auto; width:80%"></img></h1>

Now, as you have collected the data, now let us see what TensorFlow has in store for us.

# TensorFlow

Implementing machine learning is a complex stream mainly the concerns related to the creation of real-time models. Hence the end-to-end open source framework -  **TensorFlow** is used for **collecting datasets, training systems through models and providing the results based on it**.

TensorFlow is an open-source framework created by Google Creative Labs. It executes machine learning and heps to build neural networks easily (along with Keras) in Python as well as in Javascript. It builds an environment of networks to experiment with the algorithms of machine learning and visualizes it using flow graphs. The graphs represent the progression of all nodes where nodes are the operations in the model.

## Why TensorFlow

TensorFlow provides pre-built functions and advanced operations API to ease the task of building different neural network models. It provides the required infrastructure and hardware which makes them one of the leading libraries used extensively by researchers and students in the deep learning domain.

## Features of TensorFlow

Let us learn some exciting Tensorflow features:

### 1. Open-source Library

It is an open-source library that allows rapid and easier calculations in machine learning. It eases the switching of algorithms from one tool to another TensorFlow tool. With the help of Python, it provides the front-end API for the development of various machines and deep learning algorithms.

### 2. Easy to run
We can execute TensorFlow applications on various platforms such as Android, Cloud, IOS and various architectures such as CPUs and GPUs. This allows it to be executed on various embedded platforms.

TensorFlow has its own designed hardware to train the neural models known as Cloud TPUs (TensorFlow Processing unit).

### 3. Fast Debugging
It allows you to reflect each node, i.e., operation individually concerning its evaluation. Tensor Board works with the graph to visualize its working using its dashboard. It provides computational graphing methods that support an easy to execute paradigm.

### 4. Effective
It works with multi-dimensional arrays with the help of data structure tensor which represents the edges in the flow graph. Tensor identifies each structure using three criteria: rank, type, shape.

### 5. Scalable
It provides room for prediction of stocks, products, etc with the help of training using the same models and different data sets. It also allows for synchronous and asynchronous learning techniques and data ingestion. The graphical approach secures the distributed execution parallelism.

### 6. Easy Experimentation
TensorFlow transforms the raw data to the estimators-a form of data neural networks understand. TensorFlow feature columns allow the bridge between raw data and estimators to train the model. This adds the agility to the model for fast developmental insights.

### 7. Abstraction
TensorFlow provides a defined level of abstraction by reducing the code length and cutting the development time. The user needs to focus on logic disregarding the proper way of providing input to functions. A user can choose the model apt according to the system’s requirement.

### 8. Flexibility

TensorFlow provides the process of resolving complex topologies with the support of Keras API and data input pipelines. Keras provides easy prototyping and suits best for object-oriented neural networks.

TensorFlow eases the mechanism of machine learning with the assistance of such characteristics. It allows the user to create and manipulate the system to create different types of real-time models.

To begin with Tensorflow, you can go through the following tutorials: 

* <strong>https://www.tensorflow.org/tutorials</strong>
* <strong>https://www.tensorflow.org/tutorials/load_data/images</strong>
* <strong>https://www.tensorflow.org/tutorials/keras/classification</strong>

In the next session, we will be training and preparing our models using TensorFlow and Keras. 

---





