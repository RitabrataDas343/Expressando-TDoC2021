<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<p align="center">
<img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png" style="height:auto; width:50%"></img>
</p>

<h1 align="center">DAY 7</h1>

# Convolutional Neural Networks (CNN)

Artificial Intelligence has been witnessing a monumental growth in bridging the gap between the capabilities of humans and machines. Researchers and enthusiasts alike, work on numerous aspects of the field to make amazing things happen. One of many such areas is the domain of Computer Vision.

The agenda for this field is to enable machines to view the world as humans do, perceive it in a similar manner and even use the knowledge for a multitude of tasks such as Image & Video recognition, Image Analysis & Classification, Media Recreation, Recommendation Systems, Natural Language Processing, etc. The advancements in Computer Vision with Deep Learning has been constructed and perfected with time, primarily over one particular algorithm — Convolutional Neural Network.

<h1 align="center"><img src = "https://miro.medium.com/max/500/1*GcI7G-JLAQiEoCON7xFbhg.gif"></img></h1>

## What is a CNN?

In deep learning, a convolutional neural network (CNN/ConvNet) is a **class of deep neural networks, most commonly applied to analyze visual imagery**. It uses a special technique called Convolution. In Mathematics, **Convolution** is a mathematical operation on two functions that produces a third function that expresses how the shape of one is modified by the other.

**Neural networks** are a subset of machine learning, and they are at the heart of deep learning algorithms. They are comprised of **node layers**, containing an input layer, one or more hidden layers, and an output layer. Each node connects to another and has an associated **weight** and **threshold**. If the output of any individual node is above the specified threshold value, that node is activated, sending data to the next layer of the network. Otherwise, no data is passed along to the next layer of the network.

There are various types of neural nets, which are used for different use cases and data types. For example, recurrent neural networks are commonly used for natural language processing and speech recognition whereas convolutional neural networks (ConvNets or CNNs) are more often utilized for classification and computer vision tasks. Prior to CNNs, manual, time-consuming feature extraction methods were used to identify objects in images. However, convolutional neural networks now provide a more scalable approach to image classification and object recognition tasks, leveraging principles from linear algebra, specifically matrix multiplication, to identify patterns within an image. That said, they can be computationally demanding, requiring graphical processing units (GPUs) to train models. 

<h1 align="center"><img src = "https://editor.analyticsvidhya.com/uploads/183560_qcMBDPuKpDvICcdd.png"></img></h1>

## How does CNN work?

Before we go to the working of CNN’s let’s cover the basics such as what is an image and how is it represented. An RGB image is nothing but a matrix of pixel values having three planes whereas a grayscale image is the same but it has a single plane. Take a look at this image to understand more.

<h1 align="center"><img src = "https://editor.analyticsvidhya.com/uploads/306461_15yDvGKV47a0nkf5qLKOOQ.png" style="height:auto; width:80%"></img></h1>

For simplicity, let’s resume with grayscale images as we try to understand how CNNs work. CNNs with grayscale images requires less number of Convoluted Layers.

<h1 align="center"><img src = "https://editor.analyticsvidhya.com/uploads/750710_QS1ArBEUJjjySXhE.png" style="height:auto; width:80%"></img></h1>

The above image shows what a convolution is. We take a **filter/kernel**(3×3 matrix) and apply it to the input image to get the convolved feature. This convolved feature is passed on to the next layer. The filter is used for manipulating the image size and characteristics, which are required for the image analysis.

In the case of RGB color, channel take a look at this animation to understand its working

<h1 align="center"><img src = "https://editor.analyticsvidhya.com/uploads/556091_ciDgQEjViWLnCbmX-EeSrA.gif" style="height:auto; width:80%"></img></h1>

Convolutional neural networks are composed of multiple layers of artificial **neurons/layers**. Artificial neurons, a rough imitation of their biological counterparts, are mathematical functions that calculate the weighted sum of multiple inputs and outputs an activation value. When you input an image in a ConvNet, each layer generates several activation functions that are passed on to the next layer.

The first layer usually extracts basic features such as horizontal or diagonal edges. This output is passed on to the next layer which detects more complex features such as corners or combinational edges. As we move deeper into the network it can identify even more complex features such as objects, faces, etc.

Convolutional neural networks are distinguished from other neural networks by their superior performance with image, speech, or audio signal inputs. They have three main types of layers, which are:

* **Convolutional layer**
* **Pooling layer**
* **Fully-connected (FC) layer**

## What is a Convolutional Layer?

The **Convolutional layer** is the **first layer of a convolutional network**. While convolutional layers can be followed by additional convolutional layers or pooling layers, the **fully-connected layer is the final layer**. With each layer, the CNN increases in its complexity, identifying greater portions of the image. Earlier layers focus on simple features, such as colors and edges. As the image data progresses through the layers of the CNN, it starts to recognize larger elements or shapes of the object until it finally identifies the intended object.

The convolutional layer is the **core building block of a CNN**, and it is where the majority of computation occurs. It requires a few components, which are input data, a filter, and a feature map. Let’s assume that the input will be a color image, which is made up of a matrix of pixels in 3D. This means that the input will have three dimensions—a height, width, and depth—which correspond to RGB in an image. We also have a feature detector, also known as a **kernel or filter**, which will move across the receptive fields of the image, checking if the feature is present. This process is known as a **Convolution**.

The feature detector is a **two-dimensional (2-D) array of weights**, which represents part of the image. While they can vary in size, the filter size is typically a 3x3 matrix; this also determines the size of the receptive field. The filter is then applied to an area of the image, and a **dot product** is calculated between the input pixels and the filter. This dot product is then fed into an output array. Afterwards, the filter shifts by a stride, repeating the process until the kernel has swept across the entire image. The final output from the series of dot products from the input and the filter is known as a **feature map, activation map, or a convolved feature.** The number of filters affects the depth of the output. For example, three distinct filters would yield three different feature maps, creating a depth of three. 

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138590455-f2a26064-c6dc-415d-9450-c1e09298a442.png" style="height:auto; width:80%"></img></h1>

## What is a Pooling Layer?

Similar to the Convolutional Layer, the Pooling layer is responsible for reducing the spatial size of the Convolved Feature. This is to decrease the computational power required to process the data by reducing the dimensions. There are two types of pooling average pooling and max pooling. 

**Pooling layers**, also known as **downsampling**, conducts dimensionality reduction, reducing the number of parameters in the input. Similar to the convolutional layer, the pooling operation sweeps a filter across the entire input, but the difference is that this filter does not have any weights. Instead, the kernel applies an aggregation function to the values within the receptive field, populating the output array. There are two main types of pooling:

* **Max pooling**: As the filter moves across the input, it selects the pixel with the **maximum** value to send to the output array. As an aside, this approach tends to be used more often compared to average pooling.
* **Average pooling**: As the filter moves across the input, it calculates the **average** value within the receptive field to send to the output array.

While a lot of information is lost in the pooling layer, it also has a number of benefits to the CNN. They help to reduce complexity, improve efficiency, and limit risk of overfitting. 

<h1 align="center"><img src = "https://editor.analyticsvidhya.com/uploads/597371_KQIEqhxzICU7thjaQBfPBQ.png" style="height:auto; width:80%"></img></h1>

## What is a Fully-Connected Layer ?

The name of the full-connected layer aptly describes itself. As mentioned earlier, the pixel values of the input image are not directly connected to the output layer in partially connected layers. However, in the fully-connected layer, each node in the output layer connects directly to a node in the previous layer.

This layer performs the task of classification based on the features extracted through the previous layers and their different filters. While convolutional and pooling layers tend to use ReLu functions, FC layers usually leverage a softmax activation function to classify inputs appropriately, producing a probability from 0 to 1.

Thus, CNN works in the following manner: 

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138591124-e5d9c6af-b234-4773-aa88-4d6c7ef6105d.png" style="height:auto; width:80%"></img></h1>

To know more about CNN go through the following link: <strong>[https://deepai.org/machine-learning-glossary-and-terms/convolutional-neural-network](https://deepai.org/machine-learning-glossary-and-terms/convolutional-neural-network)</strong>

---

Now let us go through the code: 

## Step 1:

Create a file named as **'train_model.py'** inside the directory of **'TDoC-2021'**. As the name suggests, it will be training the models using **TensorFlow** and **Keras** with the Convolutional Neural Network been trained on it.
Open the file your code-editor/IDE. The folder structure would look like the following (this structure includes the files used in past sessions as well):

```bash
├── TDoC-2021
|     ├── data
|         ├── train
|             ├── 0
|             ├── 1
|             ├── 2
|             ├── 3
|             ├── 4
|             ├── 5
|         ├── test
|             ├── 0
|             ├── 1
|             ├── 2
|             ├── 3
|             ├── 4
|             ├── 5
|     ├── env
|     ├── check.py
|     ├── collect-data.py
|     ├── defects.py
|     ├── train_model.py
|     ├── requirements.txt
```

## Step 2: 
**First activate your virtual environment.** Also, make sure you have the **test** dataset and **train** dataset ready for the operation.

You can get the **test** dataset from here: <strong>[https://drive.google.com/drive/folders/1q0hettAk_e1kQNn8EX_no4zXQ2geIJyF?usp=sharing](https://drive.google.com/drive/folders/1q0hettAk_e1kQNn8EX_no4zXQ2geIJyF?usp=sharing)</strong>

Then open the **train_model.py** in your preferred code editor.

## Step 3:

At first, we will import the **model** and **layers**, which we will be using from **Keras**. Here, **Keras** uses **TensorFlow** as it's backend, i.e, the functions in **Keras** also makes uses of the functions in **TensorFlow** for all of the results. This forms the basic of all **Deep Learning Algorithms.**

```python
from keras.models import Sequential
from keras.layers import Convolution2D, MaxPooling2D, Flatten, Dense
```
Here, we will be making use of the **Sequential** model. This model is used when you have one input, and one output at a time. Morever, it applies to simple models, which does not involve any kind of branching and sharing. This is the most primitive and beginner kind of models. This model basically stacks the layers and serves as a container for the layers in connection. 

To know more about the **Sequential** model, go here: 
* <strong>[https://www.tensorflow.org/guide/keras/sequential_model](https://www.tensorflow.org/guide/keras/sequential_model)</strong>
* <strong>[https://keras.io/guides/sequential_model/](https://keras.io/guides/sequential_model/)</strong>

The process of building a Convolutional Neural Network always involves four major steps.

* **Convolution**
* **Pooling**
* **Flattening**
* **Full Connection**

Now we will be using the following functions to enhance the functionalitites:

* **Convolution2D** -  This performs the convolution operation i.e the first step of a CNN, on the training images. Since we are working on images here, which a basically 2 Dimensional arrays, we’re using Convolution 2-D, you may have to use Convolution 3-D while dealing with videos, where the third dimension will be time.
* **MaxPooling2D** - This is used for the pooling operation.  this is to perform the convolution operation i.e the first step of a CNN, on the training images. Since we are working on images here, which a basically 2 Dimensional arrays, we’re using Convolution 2-D, you may have to use Convolution 3-D while dealing with videos, where the third dimension will be time.
* **Flatten** - This is used for Flattening. Flattening is the process of converting all the resultant 2 dimensional arrays into a single long continuous linear vector.
* **Dense** - It is used for the coonection of the layers of the CNN.

Now, we will create an object of the sequential class below:

```python
classifier = Sequential()
```

## Step 4:

Next we will define the first convolutional layer. This will modulate the image input tensor and result in convoluted matrices. The matrices produced will be merged and amalgamated into a single matrix. This basically consists of mathematical operands, each of which serves as a node. The operands are decided on the basis of image size, colour and characteristics. After the convolution, we will be Max-Pooling the matrix, so that the size of the matrix is reduced, and it will help in efficient determination. It will be achieved by the following code:


```python
classifier.add(Convolution2D(32, (3, 3), input_shape=(64, 64, 1), activation='relu'))
classifier.add(MaxPooling2D(pool_size=(2, 2)))
```

Here, the **add()** function helps to add successive layers in the Convolution Neural Network object. 

The parameters of the **Convolution2D()** function are:
* **32**: It is the number of filters/kernels, which are used for successive mapping or multiplication.
* **(3, 3)**: It is the size of the filter/kernel. It is defined as a **3 x 3** two dimensional matrix.
* **input_shape=(64, 64, 1)**: It basically passes the shape of the input image, which will be stored in the form of an array.
* **activation='relu'**: It is the activation function, which helps to stimulate the type of response to be given on the input.

We will be using two types of **activation** function:

* **relu**: It stands for **Rectified Linear Unit**. It helps in indpendent activation of neurons/nodes in the layers.
* **softmax**: It helps to activate the neurons, if there are multiple branching present, and it requires to detect simultaneous figures.

To know more about activation functions, go here: <strong>[https://www.v7labs.com/blog/neural-networks-activation-functions](https://www.v7labs.com/blog/neural-networks-activation-functions)</strong>


The parameters of the **MaxPooling2D()** function are:
* **pool_size=(2, 2)**: This takes a 2x2 matrix to have minimum pixel loss and get a precise region where the feature are located.

Similarly, we will be adding a second Convolutinal Layer to it, in order to increase the efficiency of detection. However, we cannot add infinite number of layers, as it would decrease the speed and also, can result in wrong detections. Please note that we are not passing the input shape again, as the image array has been already been manipulated.

```python
classifier.add(Convolution2D(32, (3, 3), activation='relu'))
classifier.add(MaxPooling2D(pool_size=(2, 2)))
```
## Step 5:

Next, we will be flattening the layers, and connecting them to produce our entire **Neural Network**. Flattening is a very important step to understand. What we are basically doing here is taking the 2-D array, i.e pooled image pixels and converting them to a one dimensional single vector. We’ve used flatten function to perform flattening, we no need to add any special parameters, keras will understand that the “classifier” object is already holding pooled image pixels and they need to be flattened.

```python
classifier.add(Flatten())
```
Now, we need to create a fully connected layer, and to this layer we are going to connect the set of nodes we got after the flattening step, these nodes will act as an input layer to these fully-connected layers. As this layer will be present between the input layer and output layer, we can refer to it a hidden layer.

**Dense()** is the function to add a fully connected layer. **Units** is where we define the number of nodes that should be present in this hidden layer, these units value will be always between the number of input nodes and the output nodes but the art of choosing the most optimal number of nodes can be achieved only through experimental tries. Though it’s a common practice to use a power of 2 and the activation function will be a rectifier function.

```python
classifier.add(Dense(units=128, activation='relu'))
classifier.add(Dense(units=6, activation='softmax'))
```
## Step 6:

As, the model has been prepared

---

Now your **train_model.py** should look like the following. 

```python
from keras.models import Sequential
from keras.layers import Convolution2D, MaxPooling2D, Flatten, Dense

classifier = Sequential()

classifier.add(Convolution2D(32, (3, 3), input_shape=(64, 64, 1), activation='relu'))
classifier.add(MaxPooling2D(pool_size=(2, 2)))

classifier.add(Convolution2D(32, (3, 3), activation='relu'))
classifier.add(MaxPooling2D(pool_size=(2, 2)))

classifier.add(Flatten())

classifier.add(Dense(units=128, activation='relu'))
classifier.add(Dense(units=6, activation='softmax'))

classifier.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])


from keras.preprocessing.image import ImageDataGenerator

train_datagen = ImageDataGenerator(
        rescale=1./255,
        shear_range=0.2,
        zoom_range=0.2,
        horizontal_flip=True)

test_datagen = ImageDataGenerator(rescale=1./255)

training_set = train_datagen.flow_from_directory('data/train',
                                                 target_size=(64, 64),
                                                 batch_size=5,
                                                 color_mode='grayscale',
                                                 class_mode='categorical')

test_set = test_datagen.flow_from_directory('data/test',
                                            target_size=(64, 64),
                                            batch_size=5,
                                            color_mode='grayscale',
                                            class_mode='categorical') 

classifier.fit_generator(
        training_set,
        epochs=10,
        validation_data=test_set)
        
model_json = classifier.to_json()
with open("model-bw.json", "w") as json_file:
    json_file.write(model_json)
classifier.save_weights('model-bw.h5')
```

Run the code in your Powershell/terminal using 
```bash
python train_model.py
```
---
