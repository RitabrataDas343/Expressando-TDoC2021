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
    cv2.rectangle(img,(20,20),(250,250),(255,0,0),3)
    crop_img = img[20:250, 20:250]
    grey = cv2.cvtColor(crop_img, cv2.COLOR_BGR2GRAY)
    value = (35, 35)
    blurred = cv2.GaussianBlur(grey, value, 0)
    _, thresh1 = cv2.threshold(blurred, 127, 255, cv2.THRESH_BINARY_INV+cv2.THRESH_OTSU)
    contours, hierarchy = cv2.findContours(thresh1.copy(),cv2.RETR_TREE, cv2.CHAIN_APPROX_NONE)
```

The above lines of the code is just a recap of what we did in Day 3. (REFER TO THE DOCUMENTATION OF DAY-3). Here, we initialise a while loop, which iterates as long as the webcam input returns a frame or **cap.isOpened()** returns **True** value. The **cap.read()** takes the input of the image in the form of an image array vector. The **flip()** function basically returns the inverted image of the frame taken into consideration. We define a region by means of the **rectangle()** function, and then extract the region, naming it as **crop_img**. 

Then we apply the **cvtColor()** function and convert the image into it's equivalent grayscale using **cv2.COLOR_BGR2GRAY** method and name it as **grey**. Next we declare the tuple **value**, which contains the kernel standard deviation for x and y coordinates. This tuple is later used in the **GaussianBlur()** function, where it is used as a parameter. The blurred is image is named as **blurred.** Then we apply simple threshold using the modules **cv2.THRESH_BINARY_INV** and **cv2.THRESH_OTSU**, and naming the resultant image as **thresh1**. Next, we derive the contours from the threshold using **cv2.RETR_TREE** as the retrieval method and **cv2.CHAIN_APPROX_NONE** as the approximation method. We then, store the contours in the array named **contours.** 

**Step 4:** 
```python
    cnt = max(contours, key = lambda x: cv2.contourArea(x))
    x,y,w,h = cv2.boundingRect(cnt)
    cv2.rectangle(crop_img,(x,y),(x+w,y+h),(0,0,255),2)
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


