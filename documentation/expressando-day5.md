<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<p align="center">
<img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png" style="height:auto; width:50%"></img>
</p>

<h1 align="center">DAY 5</h1>

# Collecting data through OpenCV and labelling them 

## Step 1:
Create a file named as **'collect-data.py'** inside the directory of **'TDoC-2021'**. As the name suggests, collect data collects the images taken by webcam using the OpenCV library. creating one or more dataset(s) depending on the input, store them in the directories and pursoung them according to classes.
Open the file your code-editor/IDE. The folder structure would look like the following (this structure includes the files used in past sessions as well):

```bash
├── TDoC-2021
|     ├── env
|     ├── check.py
|     ├── collect-data.py
|     ├── defects.py
|     ├── requirements.txt
```

## Step 2: 
**First activate your virtual environment (This is very important as OpenCV is installed inside the virtual environment and not globally).** Then open the file in your preferred code editor. Then import OpenCV and OS (included in python library) as `cv2` and `os`. It can be accomplished by the following line of code:

```python
import cv2
import os
```
First, we will be checking for the presence of the `data` directory, which will be used to store the `train` and `test` data. If the `data` folder is already created then, it will not create the folders, and proceed to store the data in the form of datasets, each representing a class. This is checked by using a conditional statement. The **os.path.exists()** function checks whether the path of the directories exist or not. The **os.makedirs()** function is used to create new directories, which needs a string as a parameter. The string is basically the folder structure which needs to be created.

```python
if not os.path.exists("data"): #True
    os.makedirs("data")
    os.makedirs("data/train") 
    os.makedirs("data/test")
    os.makedirs("data/train/0") 
    os.makedirs("data/train/1")
    os.makedirs("data/train/2")
    os.makedirs("data/train/3")
    os.makedirs("data/train/4")
    os.makedirs("data/train/5")
    os.makedirs("data/test/0")
    os.makedirs("data/test/1")
    os.makedirs("data/test/2")
    os.makedirs("data/test/3")
    os.makedirs("data/test/4")
    os.makedirs("data/test/5")
```

The `if not` statement check if the directory `data` exists or not, where as `os.path.exists` method returns Boolean value & depending on which next lines are executed. Next if `os.path.exists` returns **False** then `os.makedirs` method will create the necessary directories. On running the program, the following directories will be automatically created: 

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
|     ├── requirements.txt
```
> **Note**: You do not need to create the directories by yourselves, it will be created by the program itself.

## Step 3: 
Now we will create some variables for the path of the folders where we will save our dataset of images. After that, we need to collect the required images via webcam. For that, we will use the already learnt how to use the `cv2.VideoCapture()` method to initialise the camera and store the data. 

```python
mode = 'train'
directory = 'data/'+mode+'/'

cap=cv2.VideoCapture(0)
```

Here, we are declaring two string variables **mode** and **directory**, for the ease of operations. The **mode** variable contains the type of operation we are performing, i.e either `train` or `test`. The **directory** variable stores the path, where we are operating. In this case, it will store the value `data/train/` 
We will then initialise the camera input and check for the webcam input.

```python
while True:
    _, frame = cap.read()
    frame = cv2.flip(frame , 1)
```
This code initiates an infinite loop (to be broken later by a break statement), where we have `_` and `frame` is defined as the `cap.read()`. Basically, `_` is a boolean regarding whether or not there was a return at all. On the other hand, `frame` contains each frame that is being returned in the form of an image array vector. The function **flip()** inverts the orientation of the webcam.

## Step 4:
To make the process of collecting the data more interactive and visually appealing, we will display some statistics in the live view screen of the webcam. In this project, we will be storing the data for detecting _zero_ inside `directory/0/` folder. We will do a similar thing for storing the data for detecting **_one, two, three, four_** and **_five_** as well. So to know how many images we have collected inside the folder, we can simply use these key bindings and record them as `count` objects and keep the counts of images as a dictionary for every number.
```python
 cv2.putText(frame, "Expressando - TDOC 2021", (175, 450), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (225,255,255), 3)

 count = {'zero': len(os.listdir(directory+"/0")),
          'one': len(os.listdir(directory+"/1")),
          'two': len(os.listdir(directory+"/2")),
          'three': len(os.listdir(directory+"/3")),
          'four': len(os.listdir(directory+"/4")),
          'five': len(os.listdir(directory+"/5"))}
```
Here, **count** is a **dictionary**, where we store the values according to an unique **key**, which is passed as string here (zero, one, two, three, four, five). 
Each key relates to specific data, stored in them. Whenever, we need to parse the data, we will pass the code **count['key']**. Here, each key stores **the number of files(images) stored in the folder**, passed as an integer variable. The function **os.listdir()** lists the files present in the directory under consideration. The **len()** function returns the length/count of the list produced by the **os.listdir()** function.

Now we have the required data (image count in every specific folders), we can display it in the live view of the webcam. It can be done very easily, made possible by OpenCV. This can be achived by the following lines of code:

```python
    cv2.putText(frame, "MODE : "+mode, (30, 50), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (225,255,255), 1)
    cv2.putText(frame, "IMAGE COUNT", (10, 100), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (225,255,255), 1)
    cv2.putText(frame, "ZERO : "+str(count['zero']), (10, 120), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1)
    cv2.putText(frame, "ONE : "+str(count['one']), (10, 140), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1)
    cv2.putText(frame, "TWO : "+str(count['two']), (10, 160), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1)
    cv2.putText(frame, "THREE : "+str(count['three']), (10, 180), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1)
    cv2.putText(frame, "FOUR : "+str(count['four']), (10, 200), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1)
    cv2.putText(frame, "FIVE : "+str(count['five']), (10, 220), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1
```

The parameters of **cv2.putText()** are:

* **frame**: It is the image on which text is to be drawn.
* **""ZERO: " + str(count['zero'])"**: It is the text string to be drawn on the image. Here, we are concatenating the count to the text. Here, **count['zero']** returns the number of images stored in the folder `data/train/0`. Then, we are type-casting it into a string using **str()** function.
* **(10,450)**: It is the coordinates of the bottom-left corner of the text string in the image. The coordinates are represented as tuples of two values i.e. (X coordinate value, Y coordinate value).
* **cv2.FONT_HERSHEY_SIMPLEX**: It denotes the font type, used in OpenCV.
* **1**: It is the fontScale factor that is multiplied by the font-specific base size.
* **(255, 255, 255)**: It is the color of text string to be drawn in BGR. Here, the colour is white. 
* **1**: It is the thickness of the line in px.

This helps in keeping a note of how many images we are collecting by means of the program.

## Step 5:

Next, we will learning about the **Region of Interest (R.O.I)**.A region of interest (ROI) is an **area of an image defined for further analysis or processing**.
Here, the region of interest will basically contain the region of the hand, used for portraying the gesture. We will be defining the region of interest using the following code: 

```python
    x1 = int(0.5*frame.shape[1])
    y1 = 10
    x2 = frame.shape[1]-10
    y2 = int(0.5*frame.shape[1])
    cv2.rectangle(frame, (x1-1, y1-1), (x2+1, y2+1), (255,0,0) ,3)
    roi = frame[y1:y2, x1:x2] 
    roi = cv2.resize(roi, (200, 200)) 
    cv2.putText(frame, "R.O.I", (440, 350), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,225,0), 3)
    cv2.imshow("Frame", frame)
    
    roi = cv2.cvtColor(roi, cv2.COLOR_BGR2GRAY)
    _, roi = cv2.threshold(roi, 120, 255, cv2.THRESH_BINARY)
    cv2.imshow("ROI", roi)
```

Here, **frame.shape[1]** returns the shape of the frame or the camera input. Next, we will be defining the variables **x1, y1, x2 and y2**, which will serve as the diagonals of the rectangle (x1,y1) and (x2,y2). In case, you are facing issues with the variable allocation, you can use constants in place of them. However, it is always beneficial to consider the frame shape, as the frame size may not be the same for all the users. Next, we draw a rectangle surrounding the ROI using the **rectangle()** function, so that we can record our gesture inside the rectangle. Next, we extract the region of interest separately, naming it as the variable **"roi"**. After extraction, we resixe and enlarge the region of interest using the **resize()** function. The parameters of the **rectangle()** and **resize()** function has been previously described in the previous documentations.

Next, we convert the **roi** into it's grayscale form, using the module **cv2.COLOR_BGR2GRAY**. After converting the ROI into grayscale, we will apply simple threshold using the function **cv2.threshold()**. We will be using the **cv2.THRESH_BINARY** module to apply the threshold. However, you can also use **cv2.THRESH_BINARY_INV** module, but make sure, whatever you use, do not change the threshold module in the future. The parameters of the **threshold()**  function has also been previously described in the previous documentations.

## Step 6:

```python
 interrupt = cv2.waitKey(10) 
    if interrupt & 0xFF == 27:
        break
    if interrupt & 0xFF == ord('0'):
        cv2.imwrite(directory+'0/'+str(count['zero'])+'.jpg', roi)
    if interrupt & 0xFF == ord('1'):
        cv2.imwrite(directory+'1/'+str(count['one'])+'.jpg', roi)
    if interrupt & 0xFF == ord('2'):
        cv2.imwrite(directory+'2/'+str(count['two'])+'.jpg', roi)
    if interrupt & 0xFF == ord('3'):
        cv2.imwrite(directory+'3/'+str(count['three'])+'.jpg', roi)
    if interrupt & 0xFF == ord('4'):
        cv2.imwrite(directory+'4/'+str(count['four'])+'.jpg', roi)
    if interrupt & 0xFF == ord('5'):
        cv2.imwrite(directory+'5/'+str(count['five'])+'.jpg', roi)
    
cap.release()
cv2.destroyAllWindows()
```

Next, we will recording the images in the dataset according to the key-bindings. We first initialise the **interrupt** variable, which returns 10 frames per second here. Then we define all the key-bindings. Whenever, we press `0`, data for the 'zero' key will get recorded. Similarly, it applies for the other datasets as well. 0xFF collects and recognises the keyboard response, which in turns capture the image using the function **imwrite()** in the respective directories under the `data/train/` folder. Please note that the images will be recorded in the order `0.jpg`, `1.jpg` and so on. HEre, **str(count['key'])** returns the count in the increasing order starting from 0. We are capturing the region of interest (thresholded), in order to create our respective datasets under the mentioned directories. Then, after collecting the data, we release our webcam and deallocate all the memory rendered to the image array vectors. This has been previously explained in the past documentations. 

---


Now your **collect-data.py** should look like the following. 

```python
import cv2
import os

if not os.path.exists("data"): #True
    os.makedirs("data")
    os.makedirs("data/train") 
    os.makedirs("data/test")
    os.makedirs("data/train/0") 
    os.makedirs("data/train/1")
    os.makedirs("data/train/2")
    os.makedirs("data/train/3")
    os.makedirs("data/train/4")
    os.makedirs("data/train/5")
    os.makedirs("data/test/0")
    os.makedirs("data/test/1")
    os.makedirs("data/test/2")
    os.makedirs("data/test/3")
    os.makedirs("data/test/4")
    os.makedirs("data/test/5")
    
 
mode = 'train' 
directory = 'data/'+mode+'/' #data/train/

cap=cv2.VideoCapture(0)

while True:
    _, frame = cap.read()
    frame = cv2.flip(frame, 1)
    
    cv2.putText(frame, "Expressando - TDOC 2021", (175, 450), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (225,255,255), 3)

    count = {'zero': len(os.listdir(directory+"/0")), 
             'one': len(os.listdir(directory+"/1")),
             'two': len(os.listdir(directory+"/2")),
             'three': len(os.listdir(directory+"/3")),
             'four': len(os.listdir(directory+"/4")),
             'five': len(os.listdir(directory+"/5"))} 
    
    cv2.putText(frame, "MODE : "+mode, (30, 50), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (225,255,255), 1)
    cv2.putText(frame, "IMAGE COUNT", (10, 100), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (225,255,255), 1)
    cv2.putText(frame, "ZERO : "+str(count['zero']), (10, 120), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1)
    cv2.putText(frame, "ONE : "+str(count['one']), (10, 140), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1)
    cv2.putText(frame, "TWO : "+str(count['two']), (10, 160), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1)
    cv2.putText(frame, "THREE : "+str(count['three']), (10, 180), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1)
    cv2.putText(frame, "FOUR : "+str(count['four']), (10, 200), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1)
    cv2.putText(frame, "FIVE : "+str(count['five']), (10, 220), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (255,255,255), 1)
    
    
    x1 = int(0.5*frame.shape[1])
    y1 = 10
    x2 = frame.shape[1]-10
    y2 = int(0.5*frame.shape[1])
    cv2.rectangle(frame, (x1-1, y1-1), (x2+1, y2+1), (255,0,0) ,3)
    roi = frame[y1:y2, x1:x2] 
    roi = cv2.resize(roi, (200, 200)) 
    cv2.putText(frame, "R.O.I", (440, 350), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,225,0), 3)
    cv2.imshow("Frame", frame)
    
    roi = cv2.cvtColor(roi, cv2.COLOR_BGR2GRAY)
    _, roi = cv2.threshold(roi, 120, 255, cv2.THRESH_BINARY)
    cv2.imshow("ROI", roi)
    
    interrupt = cv2.waitKey(10) 
    if interrupt & 0xFF == 27:
        break
    if interrupt & 0xFF == ord('0'):
        cv2.imwrite(directory+'0/'+str(count['zero'])+'.jpg', roi)
    if interrupt & 0xFF == ord('1'):
        cv2.imwrite(directory+'1/'+str(count['one'])+'.jpg', roi)
    if interrupt & 0xFF == ord('2'):
        cv2.imwrite(directory+'2/'+str(count['two'])+'.jpg', roi)
    if interrupt & 0xFF == ord('3'):
        cv2.imwrite(directory+'3/'+str(count['three'])+'.jpg', roi)
    if interrupt & 0xFF == ord('4'):
        cv2.imwrite(directory+'4/'+str(count['four'])+'.jpg', roi)
    if interrupt & 0xFF == ord('5'):
        cv2.imwrite(directory+'5/'+str(count['five'])+'.jpg', roi)
    
cap.release()
cv2.destroyAllWindows()
```

Run the code in your Powershell/terminal using 
```bash
python check.py
```
---

## Assignment 2: 
Submit the same code, by substituting your Github username in place of "Expressando". Also, try to add some new features or additions to the code. Submit the PRs as well.

