<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png" style="height:600px; width:900px"></img></h1>

<h1 align="center">DAY 4</h1>

## Checking for Convexity Defects in the Camera Input

Since the initial input has been configured through the webcam input, it becomes important to understand the concepts of "defect" as a basic and fundamental method in the domain of detection. In this session, we are going to learn about defects and detect them in our digital video input.

**Step 1:** Create a file named as **'defects.py'** inside the directory of **'TDoC-2021'**. As the name suggests, we are checking for the defects in images taken by webcam using the OpenCV library. Open the file your code-editor/IDE. The folder Structure would look like the following:

```bash
├── TDoC-2021
|     ├── env
|     ├── check.py
|     ├── defects.py
|     ├── requirements.txt
```

**Step 2:** First import **OpenCV**, **NumPy (as np)**, and **math** into the **'defects.py'** file. Here, **math** is present in the standard Python library, and it need not to be installed separately. It can be accomplished by the following line of code:

```python
import cv2
import numpy as np
import math
```

After importing the packages, we need to create a VideoCapture object, which will initiate the process to retrieve the input through the webcam.

```python
cap = cv2.VideoCapture(0)
```

**Step 3:** The next step involves rendering a while loop to stimulate asynchronous input through the webcam with the help of a suitable condition. In this step, we will be discussing the most common and important methods that are present in the OpenCV library, which are required for making basic projects and develop sound understanding about the various methods present in OpenCV and their uses. 
Continue in the code-editor as follows: 

```python
while (cap.isOpened()):
    ret, img = cap.read()
    img=cv2.flip(img, 1)
    cv2.rectangle(img, (20, 20), (250, 250), (255, 0, 0), 3)
    cv2.imshow("RGB Output", img)
    img1 = img[20:250,20:250]       
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

Then we are introduced to the method "**cvtColor()**". This method is used to convert the image into different color-spaces. There are more then hundreds of color-space filters available in OpenCV, but we will be using **COLOR_BGR2GRAY** for now. This converts the image taken into consideration, in the form of BGR, and converts the entire image into grayscale. We name the grayscale image as **gray**. 

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/137963065-a2560499-6bc6-405f-ac94-ca0bc9ae418b.PNG"> </img></h1>

The left image is the original image, while the right image represents it's grayscale form.

We will also use the **GaussianBlur()** method here. It is an image-smoothening technique (also known as blurring) to reduce the amount of luminant noise in the image. We will stored the reduced image as **blur**.  

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/137963285-f38f40d4-01ef-4e6e-a87c-4e5b938fb1c2.png"> </img></h1>

The left image is the original image, while the right image represents it's blurred form.

It has the following parameters:
* **gray**: It is the frame taken into consideration on which the method is to be applied.
* **(5, 5)**: It is the gaussian Kernel size defined along the X and Y axes, passed in the form of a tuple.
* **0**: It denotes the thickness of the rectangle border line in **px**. 

**Step 5:**

```python
    ret, thresh1 = cv2.threshold(blur, 10, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)
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

<<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/137963402-4bfb58e2-f05d-442e-b3c3-fe3dbf3293d7.jpg"> </img></h1>

The above are the examples of the thresholding modules.

**Step 6:**
```python
    contours, hierarchy = cv2.findContours(thresh1, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
    cv2.drawContours(imCopy, contours, -1, (0, 255, 0))
    cv2.imshow('Draw Contours', imCopy)
```
**Contours are defined as the line joining all the points along the boundary of an image that are having the same intensity. Contours come handy in shape analysis, finding the size of the object of interest, and object detection.** It is defined by the minimum number of edges required to define the shape taken into consideration. This is done well with **thresholded and grayscale images**. It is done by the function **findContours().** 

Normally we use the **cv.findContours()** function to detect objects in an image. Sometimes, the objects are in different locations and in some cases, some shapes are inside other shapes just like nested figures or concentric figures. In this case, we call outer one as **parent** and inner one as **child**. This way, contours in an image has some relationship to each other. And we can specify how one contour is connected to each other, like, is it child of some other contour, or is it a parent etc. Representation of this relationship is called the **Hierarchy**. 

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/137963548-95870f41-5893-491a-b0f4-1a46a014f6c6.png"></img></h1>

The above picture represents the hierarchy of the contours. Contours that have the same integer have the same hierarchy.

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

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/137963685-dac31eb6-9167-487f-abda-2cfc71f33a52.png"></img></h1>

The examples of the approximation methods are shown as above.


The function **drawContours()** is used to draw the contours that have been traced, superimposed on the top of an image. In case, we do not want to display it over any image, the default is set to black.


The function has the following parameters:
* **imCopy**: The input image array on which the contours are to be displayed.
* **contours**: These refers to the 'contours' array that have been declared and initialised in the **findContours()** function. 
* **-1**: It is the parameter to show all the contours in the 'contours' array. However, if you want to display a specific contour according to the hierarchy, pass the desired number as the parameter. For example, to get the 3rd contour, you have to pass **2** as a parameter.   
* **(0, 255, 0)**: It is the color of contour which is to be drawn, passed in the form of BGR index. Here, (0, 255, 0) denotes the green colour.

Then we display the contours, superimposed on **"imCopy"** image using the **imshow()** function.

**Step 7:** 
```python
    cnt = max(contours, key = lambda x: cv2.contourArea(x))
    x,y,w,h = cv2.boundingRect(cnt)
    cv2.rectangle(crop_img,(x,y),(x+w,y+h),(0,0,255),2)
    cv2.imShow("Image", crop_img)
```
> **cv2.boundingRect()** is a function used to create an approximate rectangle along with the image. This function’s primary use is to highlight the area of interest after obtaining the image’s outer shape. With proper markings, the users can easily highlight the desired aspect in an image.
Every function in the OpenCV is bound to return some numeric data or lists of data. In some cases where you have operations on the images, you might get ‘None’ as a return.

CV2 Boundingrect returns 4 numeric values when the contour is passed as an argument. These 4 values correspond to x, y, w, h respectively. These values are more described as –

- X coordinate
- Y coordinate
- Width
- Height

These values can be used to either draw a rectangle or crop out the image part using pixel coordinates.

It has the following parameters:

img: It is the frame taken into consideration on which the rectangle is to be drawn.
- (20, 20): It is the starting coordinates of rectangle. The coordinates are represented as tuples of two values, the X and Y coordinates respectively.
- (250, 250): It is the ending coordinates of rectangle. The coordinates are represented as tuples of two values similarly as the starting point. Both the tuples indicate the right diagonal of the rectangle drawn. If the x and y coordinates of the tuples are same, it will result in a square.
- (0,0,255): It is the color of border line of rectangle which is to be drawn, passed in the form of BGR index. BGR index comprises of Blue, Green and Red colour values, which are used to define other colours as well. Each of the values ranges from 0 to 255. Here, (255, 0, 0) denotes the blue colour.
- 2: It denotes the thickness of the rectangle border line in px.

**Step 8:**

We saw what is convex hull. Any deviation of the object from this hull can be considered as convexity defect.

OpenCV comes with a ready-made function to find this, cv2.convexityDefects(). A basic function call would look like below:

```python
    hull = cv2.convexHull(cnt)
    drawing = np.zeros(crop_img.shape,np.uint8)
    
    cv2.drawContours(drawing,[cnt],0,(0,255,0),0)
    cv2.drawContours(drawing,[hull],0,(0,0,255),0)

    hull = cv2.convexHull(cnt,returnPoints = False)
    defects = cv2.convexityDefects(cnt,hull)
```

>Remember we have to pass returnPoints = False while finding convex hull, in order to find convexity defects.

It returns an array where each row contains these values - [ start point, end point, farthest point, approximate distance to farthest point ]. We can visualize it using an image. We draw a line joining start point and end point, then draw a circle at the farthest point. Remember first three values returned are indices of cnt. So we have to bring those values from cnt.

Once we draw a convex hull around this hand, OpenCV produces the following output.


**np.zeros** is use for black background

![alt text](https://miro.medium.com/max/318/1*Ve9ft6pSCTF1K3zmfGTbLg.jpeg)

To draw the contours, cv.drawContours function is used. It can also be used to draw any shape provided you have its boundary points. Its first argument is source image, second argument is the contours which should be passed as a Python list, third argument is index of contours (useful when drawing individual contour. To draw all contours, pass -1) and remaining arguments are color, thickness etc.

To draw all the contours in an image:

>cv.drawContours(img, contours, -1, (0,255,0), 3)

To draw an individual contour, say 4th contour:
>cv.drawContours(img, contours, 3, (0,255,0), 3)

But most of the time, below method will be useful:

>cnt = contours[4]<br>
>cv.drawContours(img, [cnt], 0, (0,255,0), 3)

Draws contours outlines or filled contours.

The function draws contour outlines in the image if thickness≥0 or fills the area bounded by the contours if thickness<0 . The example below shows how to retrieve connected components from the binary image and label them.

![alt text](https://miro.medium.com/max/318/1*OoiBHM_JtjtLyjwRQGT05g.jpeg)

![alt text](https://miro.medium.com/max/445/1*HJm9AOtFNdUQtRgoR5pWcw.png)


Convexity Defects returns an array where each row contains these values :
- start point
- end point
- farthest point
- approximate distance to farthest point

By, this point we can easily derive Sides: a,b,c (see CODE) and from cosine theorem we can also derive gamma or angle between two finger. As you read earlier, if gamma is less than 90 degree we treated it as a finger. After knowing gamma we just draw circle with radius 4 in approximate distance to farthest point. And after we just simple put text in images we represent finger counts (cnt).

**Step 9:**

```python
 for i in range(defects.shape[0]):
        s,e,f,d = defects[i,0]
        start = tuple(cnt[s][0])
        end = tuple(cnt[e][0])
        far = tuple(cnt[f][0])
        a = math.sqrt((end[0] - start[0])**2 + (end[1] - start[1])**2)
        b = math.sqrt((far[0] - start[0])**2 + (far[1] - start[1])**2)
        c = math.sqrt((end[0] - far[0])**2 + (end[1] - far[1])**2)
        angle = math.acos((b**2 + c**2 - a**2)/(2*b*c)) * 57

        if angle <= 90:
            count_defects += 1
            cv2.circle(crop_img,far,1,[0,0,255],-1)

        cv2.line(crop_img,start,end,[0,255,0],2)
```
defects returns an array where each row contains these values [ start point, end point, farthest point, approximate distance to farthest point ] (s,e,f,d)

Now, this is Math time! Let’s understand cosine theorem.
In trigonometry, the law of cosines relates the lengths of the sides of a triangle to the cosine of one of its angles. Using notation as in Fig. , the law of cosines states where γ denotes the angle contained between sides of lengths a and b and opposite the side of length c.

![alt text](https://miro.medium.com/max/258/1*zWCg03itsV2E_EiNiXPDEQ.png)

**Formula** 

![alt text](https://miro.medium.com/max/331/1*65KdbkLNmdNrZmtwsQ05pQ.png)

By seeing this formula now we understand that if we have; a,b and gama then we also find c as well as if we have; a,b,c then we also find gamma (vice-versa)
For finding gamma this formula is used:

![alt text](https://miro.medium.com/max/310/1*er17-GcEg3K9dUmsODTi8w.png)

Using Cosine theorem to recognize fingers

![alt text](https://miro.medium.com/max/318/1*MKShVvV1S-XUOqRJ5AbN-w.jpeg)

In Fig. I am draw a Side: a,b,c and angle: gamma. Now this gamma is always less than 90 degree, So we can say: If gamma is less than 90 degree or pi/2 we consider it as a finger.

```python
if count_defects == 1:
        cv2.putText(img,"Number : 2", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, 1)
    elif count_defects == 2:
        cv2.putText(img, "Number : 3", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, 1)
    elif count_defects == 3:
        cv2.putText(img,"Number : 4", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, 1)
    elif count_defects == 4:
        cv2.putText(img,"Number : 5", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, 1)
    else:
        cv2.putText(img,"Number : 1", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, 1)
```


Let’s see our final result

![alt text](https://miro.medium.com/max/318/1*XH_RIgJ0UglxkWxbeR7nXQ.jpeg)  


**Step 8:** Now, after checking for the input, it is time to proceed for the termination of the while loop and close all the windows and close our Video Capture object.

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


