<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png" style="height:600px; width:900px"></img>

<h1 align="center">DAY 3</h1>

## Configuring Input through Webcam using OpenCV

After settinp up your virtual environment, it is time to configure your digital input. The first step of any image manipulation project starts with the configuration of digital image input using OpenCV. So let us first configure the basic webcam input. 

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

The function **cap.isOpened()** checks whether the VideoCapture object (here 'cap') is functional or not. This is done by usually checking the response from the webcam under consideration. This code initiates an infinite loop (to be broken later by a break statement), where we have "**ret**" and "**frame**" being defined as the cap.read(). Basically, **ret** is a boolean regarding whether or not there was a return at all. On the other hand, **frame** contains each frame that is being returned in the form of an image array vector.
> This is practised in order to avoid unnecessary IO errors. In case, no frame was returned, **ret** will obtain **False** as it's return value. Hence, instead of throwing an IO error, it will pass **None** to the **frame**.

The next line of code introduces us to the method **flip()**. This method inverts the frame taken into consideration, laterally. Using flip, the input will be similar to a mirror. It is beneficial as it eases the orientation of the webcam input.

**Step 4:**

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
Both the tuples indicate **the right diagonal of the rectangle drawn.** If the x and y coordinates of the tuples are same, it will result in a **square**.
* **(255, 0, 0)**: It is the color of border line of rectangle which is to be drawn, passed in the form of BGR index. BGR index comprises of **Blue, Green and Red** colour values, which are used to define other colours as well. Each of the values ranges from **0** to **255**. Here, (255, 0, 0) denotes the blue colour. 
* **3**: It denotes the thickness of the rectangle border line in **px**. 

The method **imshow()** shows the image in the form of an independent window. It has two parameters: The name of the window and the image to be displayed.
Next, we extract the region covered by the rectangle in the form of a list of pixels named "img1". The extraction  We also make a copy of the extracted image and name the copy as "imCopy" using the **copy()** function. 

Then we are introduced to the method "**cvtColor()**". This method is used to convert the image into different color-spaces. There are more then hundreds of color-space filters available in OpenCV, but we will be using **COLOR_BGR2GRAY** for now. This converts the image taken into consideration, in the form of BGR, and converts the entire image into grayscale. We name the grayscale image as **gray**. 

We will also use the **GaussianBlur()** method here. It is an image-smoothening technique (also known as blurring) to reduce the amount of luminant noise in the image. We will stored the reduced image as **blur**.  

It has the following parameters:
* **gray**: It is the frame taken into consideration on which the method is to be applied.
* **(5, 5)**: It is the gaussian Kernel size defined along the X and Y axes, passed in the form of a tuple.
* **0**: It denotes the thickness of the rectangle border line in **px**. 

**Step 5:**

```python
    ret, thresh1 = cv2.threshold(blur, 10, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)
    hand_resize = cv2.resize(thresh1, (width, height))
    cv2.imshow("Threshold", thresh1)
```

**Thresholding** is a technique in OpenCV, which is the assignment of pixel values in relation to the threshold value provided. In thresholding, each pixel value is compared with the threshold value. It is one of the most common (and basic) segmentation techniques in computer vision and it allows us to separate the **foreground (i.e., the objects that we are interested in)** from the **background** of the image. A threshold is a value which has two regions on its either side i.e. below the threshold or above the threshold. If the pixel value is smaller than the threshold, it is set to 0, otherwise, it is set to a maximum value.

Here, **ret** performs the same function as before, while **thresh1** contains our thresholded image. Then, we define a width and the height in the form of a tuple, before the initialisation of the **cap** object.

There are mainly three types of thresholding techniques:
* **Simple Threshold:** In this type of thresholding, we manually supply parameters to segment the image — this works extremely well in **controlled lighting conditions** where we can ensure **high contrast between the foreground and background** of the image. The parameters are discussed later.
* **Adaptive Threshold:** In this type of thresholding, instead of trying to threshold an image globally using a single value, it **breaks the image down into smaller pieces**, and then thresholds each of these pieces separately and individually. It is better in **limited lighting** conditions.
* **OTSU Threshold:** In Otsu Thresholding, **the value of the threshold is not defined but is determined automatically. This works well when we are not sure of the lighting conditions.** This is an **additive module**, i.e, it is applied in addition to Simple or Adaptive threshold and works well with **grayscale** images.

The function **threshold()** has the following parameters:
* **blur**: The input image array on which the blur effect is applied.
* **10**: The value of Threshold below and above which pixel values will change accordingly.
* **255**: The maximum value that can be assigned to a pixel, in general the intensity of a colour ranges from **0 to 255**.
* **cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU**: The type of thresholding that is applied to the image.

There are other thresholding techniques as well: 
* **cv2.THRESH_BINARY**: If pixel intensity is greater than the set threshold, value is set to 255 (white), else it is set to  be at 0 (black). Here the brighter pixels are converted to black and darker pixels to white.
* **cv2.THRESH_BINARY_INV**: If pixel intensity is greater than the set threshold, value is set to 0(black), else it is set to be 255 (white). Here the brighter pixels are converted to white and darker pixels to black.
* **cv2.THRESH_TRUNC**: If pixel intensity value is greater than threshold, it is truncated to the mentioned threshold. The pixel values are set to be the same as the threshold. All other values remain the same.
* **cv2.THRESH_TOZERO**: Pixel intensity is set to 0, for all the pixels intensity less than the threshold value.
* **cv2.THRESH_TOZERO_INV**: Pixel intensity is set to 0, for all the pixels intensity greater than the threshold value.

The thresholded image of the region under consideration is displayed using the **imshow()** function.

**Step 6:**
```python
    contours, hierarchy = cv2.findContours(thresh1, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
    cv2.drawContours(imCopy, contours, -1, (0, 255, 0))
    cv2.imshow('Draw Contours', imCopy)
```
**Contours are defined as the line joining all the points along the boundary of an image that are having the same intensity. Contours come handy in shape analysis, finding the size of the object of interest, and object detection.** It is defined by the minimum number of edges required to define the shape taken into consideration. This is done well with **thresholded and grayscale images**. It is done by the function **findContours().** 

Normally we use the **cv.findContours()** function to detect objects in an image. Sometimes, the objects are in different locations and in some cases, some shapes are inside other shapes just like nested figures or concentric figures. In this case, we call outer one as **parent** and inner one as **child**. This way, contours in an image has some relationship to each other. And we can specify how one contour is connected to each other, like, is it child of some other contour, or is it a parent etc. Representation of this relationship is called the **Hierarchy**. 

The function has the following parameters:
* **thresh1**: The input image array from which the contours are to be detected.
* **cv2.RETR_TREE**: This is known as the **Contour Retrieval Method**.
* **cv2.CHAIN_APPROX_SIMPLE**: This is known as the **Contour Approximation Method**.

**Contour Retrieval Method** are of the following types:

* **cv2.CV_RETR_EXTERNAL**: It retrieves only the extreme outer contours. It sets hierarchy[i][2]=hierarchy[i][3]=-1 for all the contours. This gives "outer" contours, so if you have (say) one contour enclosing another (like concentric circles), only the outermost is given. 
* **cv2.CV_RETR_LIST**: It retrieves all of the contours without establishing any hierarchical relationships. This is applied when the hierarchy and topology of the object cannot be determined from beforehand.
* **cv2.CV_RETR_CCOMP**: It retrieves all of the contours and organizes them into a two-level hierarchy. At the top level, there are external boundaries of the components. At the second level, there are boundaries of the holes. If there is another contour inside a hole of a connected component, it is still put at the top level. (ADVANCED)
* **cv2.CV_RETR_TREE**: It retrieves all of the contours and reconstructs a full hierarchy of nested contours. This full hierarchy is built and displayed. It establishes complete hierarchial relations and imagifies the contours.

**Contour Approximation Method** are of the following types:

* **cv2.CHAIN_APPROX_NONE**: It stores all the points of the boundary of the shape under consideration. It requires a huge amount of memory to store each unit. It is efficient but highly reduces the speed of execution.
* **cv2.CHAIN_APPROX_SIMPLE**: It removes all redundant points and compresses the contour, thereby saving memory. It stores the key turning points of the shape under consideration and saves a lot of memory by reducing the number of points, hence increasing the speed of execution.

The function **drawContours()** is used to draw the contours that have been traced, superimposed on the top of an image. In case, we do not want to display it over any image, the default is set to black.


The function has the following parameters:
* **imCopy**: The input image array on which the contours are to be displayed.
* **contours**: These refers to the 'contours' array that have been declared and initialised in the **findContours()** function. 
* **-1**: It is the parameter to show all the contours in the 'contours' array. However, if you want to display a specific contour according to the hierarchy, pass the desired number as the parameter. For example, to get the 3rd contour, you have to pass **2** as a parameter.   
* **(0, 255, 0)**: It is the color of contour which is to be drawn, passed in the form of BGR index. Here, (0, 255, 0) denotes the green colour.

Then we display the contours, superimposed on **"imCopy"** image using the **imshow()** function.

**Step 7:** Now, after checking for the input, it is time to proceed for the termination of the while loop and close all the windows and close our Video Capture object.

To exit the program on a specified keyboard interrupt, type the following code:
```python
    k = cv2.waitKey(10) & 0xFF
    if k == 27:
      break
 
cap.release()
cv2.destroyAllWindows()
```

>The **cv2.waitKey(10)** function returns -1 when no input is made whatsoever. As soon the event occurs (a Button is pressed, here 27 is the Unicode value for Escape Key), it returns a 32-bit integer. (ADVANCED)

>The **0xFF** in this scenario is representing binary **11111111**, a 8 bit binary, since we only require 8 bits to represent a character we AND waitKey(10) to 0xFF. As a result, an integer is obtained below 255. **ord(char)** returns the ASCII value of the character which would be again maximum 255. (we often use 'q' as the keybinding to 'quit'). Hence by comparing the integer to the ord(char) value, we can check for a key pressed event and break the loop. The **0xFF** is a hexidecimal input, known as **bit mask.**(ADVANCED)

> 32 is also the Unicode value for 'Non-breaking Space', made by the Space Bar.

Now the loop breaks when the key is entered, and exits the control out of the loop.

The function **cap.release()** closes the webcam input and prevents any resource errors. The function **cv2.destroyAllWindows()** destroys all the opened windows rendered by the **imshow()** functions and deallocates the memory used by the image vector arrays and frees them.

---

Now your **check.py** should look like the following. 
```python
import cv2

(width, height) = (130, 100)

cap=cv2.VideoCapture(0)

while (cap.isOpened()):
    ret, img = cap.read()
    img=cv2.flip(img, 1)
    cv2.rectangle(img, (20, 20), (250, 250), (255, 0, 0), 3)
    cv2.imshow("RGB Output", img)
    img1 = img[20:250,20:250]       
    imCopy = img1.copy()
    gray = cv2.cvtColor(img1, cv2.COLOR_BGR2GRAY)
    blur = cv2.GaussianBlur(gray, (5, 5), 0)
    ret, thresh1 = cv2.threshold(blur, 10, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)
    hand_resize = cv2.resize(thresh1, (width, height))
    cv2.imshow("Threshold", thresh1)
    contours, hierarchy = cv2.findContours(thresh1, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
    cv2.drawContours(imCopy, contours, -1, (0, 255, 0))
    cv2.imshow('Draw Contours', imCopy)

    k = 0xFF & cv2.waitKey(10)
    if k == 27:
        break

cap.release()
cv2.destroyAllWindows()
```

Run the code in your Powershell/terminal using 
```bash
python check.py
```






