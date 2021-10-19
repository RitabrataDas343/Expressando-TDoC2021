<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png" style="height:600px; width:900px"></img>

<h1 align="center">DAY 3</h1>

## Configuring Input through Webcam using OpenCV

The first step of any image manipulation project starts with the configuration of digital image input using OpenCV. So let us first configure the basic webcam input. 

**Step 1:** Create a file named as "**check.py**" inside the directory of "**TDoC-2021**". As the name suggests, we are checking for the input through the webcam using the OpenCV library. Open the file in your code-editor/IDE. The folder structure would look like the following: 

```
├── TDoC-2021
|    ├── env    
|    ├── check.py
|    ├── requirements.txt
```

**Step 2:** First, import OpenCV into the "**check.py**" file. It can be accomplished by the following line of code:

```python
import cv2 
```
After importing cv2, we need to create a VideoCapture object, which will initiate the process to retrieve the input through the webcam. 

```python
cap = cv2.VideoCapture(0)
```
Here, "cap" refers to the object that is created using OpenCV to capture the video. It basically returns the video from the first webcam on your computer.
If you are using more than one webcam then the value "**0**" indicates that the input will be configured through the first webcam of your computer. 

> For example, if you want to configure the input through your 2nd webcam, then you have to pass "1" instead of "0" as the parameter. In simple words, it means if you want to configure the input through the "**n-th**" webcam, then you must pass "**n-1**" as parameter to the VideoCapture method. 

**Step 3:** This step involves rendering a while loop to stimulate asynchronous input through the webcam with the help of a suitable condition. In this step, we will be discussing the most common and important methods that are present in the OpenCV library, which are required for making basic projects and develop sound understanding about the various methods present in OpenCV and their uses. OpenCV is a house to a huge number of methods and functions, so we will be discussing only the important methods, which are necessary for beginners to understand. 

Continue in the code-editor as follows: 

```python
while (cap.isOpened()):
    ret, img = cap.read()
    img=cv2.flip(img, 1)
```

This code initiates an infinite loop (to be broken later by a break statement), where we have "**ret**" and "**frame**" being defined as the cap.read().  Basically, **ret** is a boolean regarding whether or not there was a return at all. On the other hand, **frame** contains each frame that is being returned in the form of an image array vector.
> This is practised in order to avoid unnecessary IO errors. In case, no frame was returned, **ret** will obtain **False** as it's return value. Hence, instead of throwing an IO error, it will pass **None** to the **frame**.

The next line of code introduces us to the method **flip()**. This method inverts the frame taken into consideration, laterally. Using flip, the input will be similar to a mirror. It is beneficial as it eases the orientation of the webcam input.

```python
    cv2.rectangle(img, (20, 20), (250, 250), (255, 0, 0), 3)
    cv2.imshow("RGB Output", img)
    img1 = img[20:250,20:250]       
    imCopy = img1.copy()
    gray = cv2.cvtColor(img1, cv2.COLOR_BGR2GRAY)
    blur = cv2.GaussianBlur(gray, (5, 5), 0)
```
In the next lines of code, we are introduced to few other methods in the OpenCV library. The method **rectangle()** enables us to draw a rectangle of our desired shape on the frame taken into consideration.

It has the following parameters:
* **img**: It is the frame taken into consideration on which the rectangle is to be drawn.
* **(20, 20)**: It is the starting coordinates of rectangle. The coordinates are represented as tuples of two values, the X and Y coordinates respectively.
* **(250, 250)**: It is the ending coordinates of rectangle. The coordinates are represented as tuples of two values similarly as the starting point.
* **(255, 0, 0)**: It is the color of border line of rectangle which is to be drawn, passed in the form of BGR index. BGR index comprises of **Blue, Green and Red** colour values, which are used to define other colours as well. Each of the values ranges from **0** to **255**. Here, (255, 0, 0) denotes the blue colour. 
* **3**: It denotes the thickness of the rectangle border line in **px**. 

The method **imshow()** shows the image in the form of an independent window. It has two parameters: The name of the window and the image to be displayed.
Next, we extract the region covered by the rectangle in the form of a list of pixels named "img1". We also make a copy of the extracted image and name the copy as "imCopy". 

Then we are introduced to the method "**cvtColor()**". This method is used to convert the image into different color-spaces. There are more then hundreds of color-space filters available in OpenCV, but we will be using **COLOR_BGR2GRAY** for now. This converts the image taken into consideration, in the form of BGR, and converts the entire image into grayscale. We name the grayscale image as **gray**. 

We will also use the **GaussianBlur()** method here. It is an image-smoothening technique (also known as blurring) to reduce the amount of luminant noise in the image. We will stored the reduced image as **blur**.  

It has the following parameters:
* **gray**: It is the frame taken into consideration on which the method is to be applied.
* **(5, 5)**: It is the gaussian Kernel size defined along the X and Y axes, passed in the form of a tuple.
* **0**: It denotes the thickness of the rectangle border line in **px**. 

```python
    ret, thresh1 = cv2.threshold(blur, 10, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)
    hand_resize = cv2.resize(thresh1, (width, height))
    cv2.imshow("Threshold", thresh1)
    contours, hierarchy = cv2.findContours(thresh1, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
    cv2.drawContours(imCopy, contours, -1, (0, 255, 0))
    cv2.imshow('Draw Contours', imCopy)
```






