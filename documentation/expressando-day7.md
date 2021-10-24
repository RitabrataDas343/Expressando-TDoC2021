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

To know more about CNN go through the following link: [https://deepai.org/machine-learning-glossary-and-terms/convolutional-neural-network](https://deepai.org/machine-learning-glossary-and-terms/convolutional-neural-network)

---

Now let us go through the code: 

## Step 1

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
**First activate your virtual environment (This is very important as OpenCV is installed inside the virtual environment and not globally).** Then open the file in your preferred code editor.

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

test_datagen = ImageDataGenerator(rescale=1./255) #epoch

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

#Saving
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