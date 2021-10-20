<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png" style="height:600px; width:900px"></img></h1>

<h1 align="center">DAY 4</h1>

## Checking for Convexity Defects in the Camera Input

Since the initial input has been configured through the webcam input, it becomes important to understand the concepts of "defect" as a basic and fundamental method in the domain of detection. In this session, we are going to learn about defects and detect them in our digital video input.

**Step 1:** Create a file named as **'defects.py'** inside the directory of **'TDoC-2021'**. As the name suggests, we are checking for the defects in images taken by webcam using the OpenCV library. Open the file your code-editor/IDE. The folder structure would look like the following:

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
    cv2.rectangle(img,(20,20),(250,250),(255,0,0),3)
    crop_img = img[20:250, 20:250]
    cv2.imshow('Gesture', img)
    
    grey = cv2.cvtColor(crop_img, cv2.COLOR_BGR2GRAY)
    value = (35, 35)
    blurred = cv2.GaussianBlur(grey, value, 0)
    _, thresh1 = cv2.threshold(blurred, 127, 255, cv2.THRESH_BINARY_INV+cv2.THRESH_OTSU)
    cv2.imshow('Binary Image', thresh1)    
```

The above lines of the code is just a recap of what we did in Day 3. (REFER TO THE DOCUMENTATION OF DAY-3). Here, we initialise a while loop, which iterates as long as the webcam input returns a frame or **cap.isOpened()** returns **True** value. The **cap.read()** takes the input of the image in the form of an image array vector. The **flip()** function basically returns the inverted image of the frame taken into consideration. We define a region by means of the **rectangle()** function, and then extract the region, naming it as **crop_img**. It is shown by the name "**Gesture**", using the function **imshow()**.

Then we apply the **cvtColor()** function and convert the image into it's equivalent grayscale using **cv2.COLOR_BGR2GRAY** method and name it as **grey**. Next we declare the tuple **value**, which contains the kernel standard deviation for x and y coordinates. This tuple is later used in the **GaussianBlur()** function, where it is used as a parameter. The blurred is image is named as **blurred.** Then we apply simple threshold using the modules **cv2.THRESH_BINARY_INV** and **cv2.THRESH_OTSU**, and naming the resultant image as **thresh1**. It is shown by the name "**Binary Image**", using the function **imshow()**.

**Step 4:** 
```python
    contours, hierarchy = cv2.findContours(thresh1.copy(),cv2.RETR_TREE, cv2.CHAIN_APPROX_NONE)
    cnt = max(contours, key = lambda x: cv2.contourArea(x))
    x,y,w,h = cv2.boundingRect(cnt)
    cv2.rectangle(crop_img,(x,y),(x+w,y+h),(0,0,255),2)
```
Next, we derive the contours from the threshold using **cv2.RETR_TREE** as the retrieval method and **cv2.CHAIN_APPROX_NONE** as the approximation method. We then, store the contours in the array named **contours**, while the hierarchy order is stored in **hierarchy**. We define a list called **"cnt"**, which stores the **external contour with the maximum area enclosed by it**. This refers to the area of the object, as it will have the maximum area under consideration. The function **contourArea()** returns the area enclosed by the contour, and the **max()** function returns the enclosed contour with the maximum area. 
>The key used here is: **lambda**, which is a constant unit vector, used to determine the direction and order of the contours. (ADVANCED)

Go through the following resources to know more about **Thresholding** and **Contours**:
* <strong>[Image Thresholding Tutorial](https://opencv24-python-tutorials.readthedocs.io/en/latest/py_tutorials/py_imgproc/py_thresholding/py_thresholding.html)</strong>
* <strong>[Contours and Hierarchy Tutorial](https://opencv24-python-tutorials.readthedocs.io/en/latest/py_tutorials/py_imgproc/py_contours/py_contours_hierarchy/py_contours_hierarchy.html)</strong>

 **cv2.boundingRect()** is a function used to create an **approximate rectangle of minimum area** which encloses the object/contour that is passed into the function as a parameter. This function’s primary use is to highlight the area of interest after obtaining the image’s outer shape, or the external contour. With proper markings, the users can easily highlight the desired aspect in an image. It ensures clear focus and better understanding of the operations. 

**cv2.boundingrect()** returns **4 numeric values** when the contour is passed as an argument. These 4 values correspond to **x, y, w, h** respectively. These values are more described as –

- **x** - X coordinate of the contour, closest to the origin (Top left of the window)
- **y** - Y coordinate of the contour, closest to the origin (Top left of the window)
- **w** - Width of the rectangle which will enclose the contour.
- **h** - Height of the rectangle which will enclose the contour.

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138156383-ea836bb9-4164-42ad-aabe-093cc9a7b28d.png"></img></h1>

The above shows the use of **boundingrect()** function to enclose all the 3 shapes in the figure.

Next we draw a rectangle using the **rectangle()** function, with the coordinates from **(x,y)** to **(x+w,y+h)** as the diagonal over the **crop_img.** This serves as an enclosure to the contours. 

**Step 5:**

```python
    hull = cv2.convexHull(cnt)
    drawing = np.zeros(crop_img.shape,np.uint8)
    
    cv2.drawContours(drawing,[cnt],0,(0,255,0),0)
    cv2.drawContours(drawing,[hull],0,(0,0,255),0)
    cv2.imshow('Contours', drawing)
```

## What is a 'Convex Hull'?

A Convex object is one with **no interior angles greater than 180 degrees**. A shape that is not convex is called **Non-Convex or Concave**. **Hull** means the exterior or the shape of the object. Therefore, the **Convex Hull of a shape** or a group of points is a tight fitting convex boundary around the points or the shape. Any deviation of the object from this hull can be considered as **convexity defect**. 

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138156744-963e35ea-5548-4a96-b829-e6c41adcf1f3.png"></img></h1>
This is an example of a convex hull.

## How to display the Convex Hull ?
OpenCV provides a function **convexHull()** which stores all the points of the hull in the form of list/array of points, on passing **cnt** as the contour array. 
The next line of the program makes use of a **NumPy** array to store the **crop_img**, and using the function **np.zeroes()**, it converts the entire image to **black**. 
Here, we have used black background to clearly visualise the contours. **np.uint8** is an 8-bit unsigned integer basically, used to define the source of image.

Then we use the **drawContours()** function to draw the **contour** and the **hull** using **green** and **red** colours respectively, over the image "**drawing**", which is the black coloured background of the same size as "**crop_img**". Then we show the output under the name "**Contours**", using the function **imshow()**.

**Step 6:** Next, we have to detect the defects by making use of the **Convex Hull**. 

## What are 'Convexity Defects'?
Any deviation of the contour from its convex hull is known as the **convexity defect**. 
OpenCV provides a function **cv2.convexityDefects()** for finding the convexity defects of a contour. This takes as input, the contour and its corresponding hull indices and returns an array containing the convexity defects as output. 

<h1 align="center"><img src = "https://user-images.githubusercontent.com/76585827/138157245-829397c3-4990-4d7e-8b84-fd77a7aa19d6.png"></img></h1>

This figure shows the depiction of the hull, contours and the defect.

```python
hull = cv2.convexHull(cnt,returnPoints = False)
defects = cv2.convexityDefects(cnt,hull)
```

We redeclare **hull** with an extra parameter _**returnpoints=False**_. This will give us the indices of the contour points that make the hull. The function **convexityDefects()** is used to find the defects directly by passing the contours array (cnt) and the hull. 

Convexity Defects returns an array where each row contains these values :
* **start point** as 's'
* **end point** as 'e'
* **farthest point** as 'f'
* **approximate distance to farthest point** as 'd'

**Step 7:** Now we use some mathematical expressions to determine the number of convexity defects in the hull, and count them accordingly.

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


Here, **defects** returns an array where each row contains these values **[start point, end point, farthest point, approximate distance to farthest point] , i.e. (s,e,f,d)**. We segment and store each of them as a separate independent 2D array, with y-coordinate as 0. These arrays are later converted into a tuple of coordinates, and they are named as **start**, **end** and **far**. Here, **start** and **end** points lie on the contour, whereas **far** points lie on the hull. We, then use the basic distance formula to calculate the lengthd of **a**, **b** and **c**. 

Now, this is Math time! Let’s understand the **cosine theorem**.
In trigonometry, the law of cosines relates the lengths of the sides of a triangle to the cosine of one of its angles. Using notation as in the given figure, the law of cosines states where **gamma** denotes the angle contained between sides of lengths **a** and **b** and opposite the side of length **c**.

<h1 align="center"><img src = "https://miro.medium.com/max/258/1*zWCg03itsV2E_EiNiXPDEQ.png"></img></h1>

The formula for the same is given below:

<h1 align="center"><img src = "https://miro.medium.com/max/331/1*65KdbkLNmdNrZmtwsQ05pQ.png"></img></h1>

By seeing this formula now we understand that if we have the parameters **a**, **b** and **c**, then we can find **gamma**, the angle between the sides **a** and **b**.

For finding gamma, the following formula is used:

<h1 align="center"><img src = "https://miro.medium.com/max/310/1*er17-GcEg3K9dUmsODTi8w.png"></img></h1>

The pictorial depiction of the following would look like the following:

<h1 align="center"><img src = "https://miro.medium.com/max/318/1*MKShVvV1S-XUOqRJ5AbN-w.jpeg"></img></h1>

Now, gamma is always **less than or equal to 90 degrees (maximum)**, So we can say: **If gamma is less than 90 degree or pi/2, we consider it as a finger.**

By this point, we can easily derive the three sides: **a, b, c** (see CODE) and from the cosine theorem we can derive **gamma** or **angle between two fingers.** As you read earlier, if gamma is less than 90 degree we treated it as a finger. 

> We convert gamma into **degrees** by multiplying with **57**, as **acos()** function returns the angle in **radians**.

We then check if the angle is less than or equal to 90 degrees, and if it is true, we increase the value of **count_defects** by **1**. The existence of an angle less than 90 denotes the presence of defects.

After knowing gamma we just draw circle with radius **1** in approximate distance to farthest points. The **far** points are denoted by the line drawn by **cv2.line()**. The circle drawn would not be uniform as the farthest points are not present in a straight line. Next, we display the number of defects using the function **cv2.putText()**.

The parameters of **cv2.circle()** are:
* **img**: It is the image on which circle is to be drawn. 
* **far**: It is the center coordinates of circle. The coordinates are represented as tuples of two values i.e. (X coordinate value, Y coordinate value). 
* **1**: It is the radius of circle. 
* **[0,0,255]**: It is the color of border line of circle to be drawn in BGR index.
* **-1**: It is the thickness of the circle border line in px. Thickness of -1 px will fill the circle shape by the specified color.

The parameters of **cv2.line()** are:
* **crop_img**: It is the image on which line is to be drawn. 
* **start**: It is the starting coordinates of line. The coordinates are represented as tuples of two values i.e. (X coordinate value, Y coordinate value).
* **end**: It is the ending coordinates of line. The coordinates are represented as tuples of two values i.e. (X coordinate value, Y coordinate value). 
* **[0,255,0]**: It is the color of border line of circle to be drawn in BGR index.
* **2**: It is the thickness of the circle border line in px.

The parameters of **cv2.putText()** are:
* **img**: It is the image on which text is to be drawn.
* **"Number : 2"**: It is the text string to be drawn on the image.
* **(50,450)**: It is the coordinates of the bottom-left corner of the text string in the image. The coordinates are represented as tuples of two values i.e. (X coordinate value, Y coordinate value).
* **cv2.FONT_HERSHEY_SIMPLEX**: It denotes the font type, used in OpenCV.
* **1**: It is the fontScale factor that is multiplied by the font-specific base size.
* **(255,255,255)**: It is the color of text string to be drawn in BGR. Here, the colour is white. 
* **1**: It is the thickness of the line in px.

The **fonts** available in OpenCV are:
* FONT_HERSHEY_SIMPLEX
* FONT_HERSHEY_PLAIN
* FONT_HERSHEY_DUPLEX
* FONT_HERSHEY_COMPLEX
* FONT_HERSHEY_TRIPLEX
* FONT_HERSHEY_COMPLEX_SMALL
* FONT_HERSHEY_SCRIPT_SIMPLEX
* FONT_HERSHEY_SCRIPT_COMPLEX

> If there are **n** defects, then there exists **n-1** fingers under detection. 

```python
    if count_defects == 1:
        cv2.putText(img,"Number : 2", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)
    elif count_defects == 2:
        cv2.putText(img,"Number : 3", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)
    elif count_defects == 3:
        cv2.putText(img,"Number : 4", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)
    elif count_defects == 4:
        cv2.putText(img,"Number : 5", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)
    elif count_defects == 5:
        cv2.putText(img,"Number : 6", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)
    else:
        cv2.putText(img,"Number : 1", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)
        
    cv2.imshow('Defects', crop_img)
```

The number of defects will be displayed as follows, which will be rendered by the name of **"Defects"**, using **imshow()**:
<h1 align="center"><img src = "https://miro.medium.com/max/318/1*XH_RIgJ0UglxkWxbeR7nXQ.jpeg"></img></h1>

**Step 8:** Now, after checking for the defects, it is time to proceed for the termination of the while loop and close all the windows and close our Video Capture object.

To exit the program on a specified keyboard interrupt, type the following code:
```python
    k = cv2.waitKey(10) & 0xFF
    if k == 27:
      break
 
cap.release()
cv2.destroyAllWindows()
```

Now the loop breaks when the key is entered, and exits the control out of the loop.

The function **cap.release()** closes the webcam input and prevents any resource errors. The function **cv2.destroyAllWindows()** destroys all the opened windows rendered by the **imshow()** functions and deallocates the memory used by the image vector arrays and frees them.

To know more about **Convexity Defects**, go here: [Convexity Defects](https://theailearner.com/2020/11/09/convexity-defects-opencv/)

---


Now your **defects.py** should look like the following. 

```python
import cv2
import numpy as np
import math

cap=cv2.VideoCapture(0)

while(cap.isOpened()):
    ret, img = cap.read()
    img=cv2.flip(img, 1)
    cv2.rectangle(img,(20,20),(250,250),(255,0,0),3)
    crop_img = img[20:250, 20:250]
    cv2.imshow('Gesture', img)
    
    grey = cv2.cvtColor(crop_img, cv2.COLOR_BGR2GRAY)
    value = (35, 35)
    blurred = cv2.GaussianBlur(grey, value, 0)
    _, thresh1 = cv2.threshold(blurred, 127, 255, cv2.THRESH_BINARY_INV+cv2.THRESH_OTSU)
    cv2.imshow('Binary Image', thresh1)
    
    contours, hierarchy = cv2.findContours(thresh1.copy(),cv2.RETR_TREE, cv2.CHAIN_APPROX_NONE)
    cnt = max(contours, key = lambda x: cv2.contourArea(x))
    x,y,w,h = cv2.boundingRect(cnt)
    cv2.rectangle(crop_img,(x,y),(x+w,y+h),(0,0,255),0)

    hull = cv2.convexHull(cnt)
    drawing = np.zeros(crop_img.shape,np.uint8)

    cv2.drawContours(drawing,[cnt],0,(0,255,0),0)
    cv2.drawContours(drawing,[hull],0,(0,0,255),0)
    cv2.imshow('Contours', drawing)
    
    hull = cv2.convexHull(cnt,returnPoints = False)
    defects = cv2.convexityDefects(cnt,hull)

    count_defects = 0
    cv2.drawContours(thresh1, contours, -1, (0,255,0), 3)

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

    if count_defects == 1:
        cv2.putText(img,"Number : 2", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)
    elif count_defects == 2:
        cv2.putText(img, "Number : 3", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)
    elif count_defects == 3:
        cv2.putText(img,"Number : 4", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)
    elif count_defects == 4:
        cv2.putText(img,"Number : 5", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)
    elif count_defects == 5:
        cv2.putText(img,"Number : 6", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)
    else:
        cv2.putText(img,"Number : 1", (50,450), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 1)

    cv2.imshow('Defects', crop_img)
    
    k = cv2.waitKey(10)
    if k == 27:
        break
 
cap.release()
cv2.destroyAllWindows()
```

Run the code in your Powershell/terminal using 
```bash
python check.py
```
---
