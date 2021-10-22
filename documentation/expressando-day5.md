<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<p align="center">
<img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png" style="height:auto; width:50%"></img>
</p>

<h1 align="center">DAY 5</h1>

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

After importing them we need to create some directories to store our data/image. The directory structure will look like the following shown below:

```bash
├── TDoC-2021
|     ├── data
|          ├──train
|               ├──0
|               ├──1
|               ├──2
|               ├──3
|               ├──4
|               ├──5
|          ├──test
|               ├──0
|               ├──1
|               ├──2
|               ├──3
|               ├──4
|               ├──5
|     ├── collect-data.py
|     ├── defects.py
|     ├── env
|     ├── check.py
|     ├── requirements.txt

```

```python
if not os.path.exists("data"):
    os.makedirs("data")
    os.makedirs("data/train")
    os.makedirs("data/train/0")
    os.makedirs("data/train/1")
    os.makedirs("data/train/2")
    os.makedirs("data/train/3")
    os.makedirs("data/train/4")
    os.makedirs("data/train/5")
```
The `if not` statement check if the directory ***data*** exists or not, where as `os.path.exists` method returns Boolean value & depending on which next lines are executed. Next if `os.path.exists` returns **False** then `os.makedirs` method will create the necessary directories.

## Step 3: 
Now we will create some variables for the path of the folders where we will save our dataset of images. After that, we need to collect the required images via webcam. For that, we will use the already learned `cv2.VideoCapture()` method.

```python
mode = 'train'
directory = 'data/'+mode+'/'

cap=cv2.VideoCapture(0)
```
We already read about `cap=cv2.VideoCapture(0)`. So we are not discussing it anymore.

```python
while (cap.isOpened()):
    _, frame = cap.read()
    frame = cv2.flip(frame , 1)
```
The function cap.isOpened() checks whether the **VideoCapture** object (here 'cap') is functional or not. This is done by usually checking the response from the webcam under consideration. This code initiates an infinite loop (to be broken later by a break statement), where we have `_` and `frame` is defined as the `cap.read()`. Basically, `_` is a boolean regarding whether or not there was a return at all. On the other hand, `frame` contains each frame that is being returned in the form of an image array vector.

## Step 4:
To make the process of collecting the data more interactive and visually appealing, we will display some statistics in the live view screen of the webcam. In this project, we will be storing the data for detecting _zero_ inside `directory/0/` folder. We will do a similar thing for storing the data for detecting **_one, two, three, four_** and **_five_** as well. So to know how many images we have collected inside the folder, we can simply use these codes and record them as `count` objects and keep the counts of images as a dictionary for every number.
```python
 count = {'zero': len(os.listdir(directory+"/0")),
          'one': len(os.listdir(directory+"/1")),
          'two': len(os.listdir(directory+"/2")),
          'three': len(os.listdir(directory+"/3")),
          'four': len(os.listdir(directory+"/4")),
          'five': len(os.listdir(directory+"/5"))}
```

Now we have the required data (image count in every specific folders), we can display it in the live view of the webcam. It can be done very easily, made possible by OpenCV. This can be achived by the following lines of code:

```python
cv2.putText(frame, "MODE : "+mode, (10, 50), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,0,255), 1)
cv2.putText(frame, "IMAGE COUNT", (10, 100), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,0,255), 1)
cv2.putText(frame, "ZERO: "+str(count['zero']), (10, 120), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,0,255), 1)
cv2.putText(frame, "ONE: "+str(count['one']), (10, 140), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,0,255), 1)
cv2.putText(frame, "TWO: "+str(count['two']), (10, 160), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,0,255), 1)
cv2.putText(frame, "THREE: "+str(count['three']), (10, 180), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,0,255), 1)
cv2.putText(frame, "FOUR: "+str(count['four']), (10, 200), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,0,255), 1)
cv2.putText(frame, "FIVE: "+str(count['five']), (10, 220), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,0,255), 1)
```
As you can see that the above code may seem so big but they are all repetitive and the same. What this `cv2.putText(parameters)` mode does is that it adds texts as we desire, in the live view of the webcam. It takes several parameters. The parameter structure of `cv2.putText` looks like this: `cv2.putText(image, text, org, font, fontScale, color[, thickness[, lineType[, bottomLeftOrigin]]])`. Here:
- image: It is the image on which text is to be drawn.
- text: Text string to be drawn.
- org: It is the coordinates of the bottom-left corner of the text string in the image. The coordinates are represented as tuples of two values i.e. (X coordinate value, Y coordinate value).
- font: It denotes the font type. Some of the font types are FONT_HERSHEY_SIMPLEX, FONT_HERSHEY_PLAIN, etc.
- fontScale: Font scale factor that is multiplied by the font-specific base size.
- color: It is the color of the text string to be drawn. For BGR, we pass a tuple. eg: (255, 0, 0) for blue color.
- thickness: It is the thickness of the line in px.
- lineType: This is an optional parameter. It gives the type of line to be used.
- bottomLeftOrigin: This is an optional parameter. When it is true, the image data origin is at the bottom-left corner. Otherwise, it is at the top-left corner.

> <h2 align="center">To be continued...</h2>

