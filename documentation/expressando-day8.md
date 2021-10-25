
<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<p align="center">
<img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png" style="height:auto; width:50%"></img>
</p>

<h1 align="center">DAY 8</h1>

# Live Prediction of Customised Sign Language

Now let us go through the code: 

## Step 1:

Create a file named as **'prediction.py'** inside the directory of **'TDoC-2021'**. As the name suggests, it will be predicting the customised sign with which we have trained the model, when we give a similar gesture to what we have trained it. 
Open the file your code-editor/IDE. The folder structure would look like the following (this structure includes the files used in past sessions as well):

```
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
|     ├── prediction.py
|     ├── train_model.py
|     ├── model-bw.h5
|     ├── model-bw.json
|     ├── requirements.txt
```

## Step 2: 
**First activate your virtual environment.** Also, make sure you have the **model-bw.h5** and **model-bw.json** Prepared before running the code. Refer to the previous documentation, for preparing them. 
Then open the **prediction.py** in your preferred code editor. Next we will be importing **cv2**, **operator**(an inherent module present in the standard Python library), and **model_from_json**, which is to be imported to read the model content in the **JSON** file.

```python
from keras.models import model_from_json
import operator
import cv2
```

## Step 3: 

```python
json_file = open("model-bw.json", "r")
model_json = json_file.read()
json_file.close()
loaded_model = model_from_json(model_json)
loaded_model.load_weights("model-bw.h5")
print("Loaded model from disk")
```
Here, we will be declaring the object **json_file**, which will parse the **model-bw.json** present in the **same** directory as the **prediction.py** file. 
Next, we will parsing the contents from the **json_file**, which has the **model-bw.json** already passed in it. 

Then, we use the **read()** and **close()** function to store the contents in the file in the object **model_json**. 

Next we will load the data model and JSON model simultaneously using the **load_weights()** and **model_from_json()** function respectively. When the models are successfully loaded, it will print "**Loaded model from disk**" in the terminal/Powershell.


## Step 4:

```python
cap = cv2.VideoCapture(0) 

categories = {0: 'ZERO', 1: 'ONE', 2: 'TWO', 3: 'THREE', 4: 'FOUR', 5: 'FIVE'}
```
Next, we have initialised a Video-Capture object called **"cap"**. Then, we have declared a dictionary called **categories**, having integer numbers as their key index. This will be helpful in rendering the string value of their respective numbers, which will be shown in the prediction.

## Step 5: 

```python
while True:
    _, frame = cap.read()
    frame = cv2.flip(frame, 1)

    x1 = int(0.5*frame.shape[1])
    y1 = 10
    x2 = frame.shape[1]-10
    y2 = int(0.5*frame.shape[1])

    cv2.putText(frame, "Expressando - TDOC 2021", (175, 450), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (225,255,0), 3)
    cv2.rectangle(frame, (x1-1, y1-1), (x2+1, y2+1), (255,255,255) ,3)
    roi = frame[y1:y2, x1:x2]

    roi = cv2.resize(roi, (64, 64)) 
    roi = cv2.cvtColor(roi, cv2.COLOR_BGR2GRAY)
    cv2.putText(frame, "R.O.I", (440, 350), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,225,0), 3)

    _, test_image = cv2.threshold(roi, 120, 255, cv2.THRESH_BINARY)
    cv2.imshow("ROI", test_image)
```

Then, we will initialise a while-loop which will run infinitely, as long as the video is being captured, or a break statement has been encountered. Then we read the frames of the video using **cap.read()** function, and invert the reading frame using the **flip()** function.

Next, we will be defining the Region of Interest, where we will be showing our hand gesture. We have previously discussed how to define the region of interest in our previous documentations. Then, we will be using the **rectangle()** function to enclose the region of interest, within the rectangle for the user to know where the sign will be detected. We will extract the region separately, and apply **grayscale** using **cvtColor()** function and **threshold** to it with the module **cv2.THRESH_BINARY** and name it as **test_image**. We will be showing the **test_img** separately using the **imshow()** function under the name **ROI**. We have also used **putText()** function to label the frame as much as possible.

## Step 6: 

```python
    result = loaded_model.predict(test_image.reshape(1, 64, 64, 1))
    prediction = {'ZERO': result[0][0], 
                  'ONE': result[0][1], 
                  'TWO': result[0][2],
                  'THREE': result[0][3],
                  'FOUR': result[0][4],
                  'FIVE': result[0][5]} 
    prediction = sorted(prediction.items(), key=operator.itemgetter(1), reverse=True)
    cv2.putText(frame, "PREDICTION:", (30, 90), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 2)
    cv2.putText(frame, prediction[0][0], (80, 130), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 2)    
    cv2.imshow("Frame", frame)
```
We will use the **predict()** function, which enables us to predict the labels of the data values on the basis of the trained model. It accepts only a single argument which is usually the data to be tested. It returns the labels of the data passed as argument based upon the learned or trained data obtained from the model. Thus, the **predict()** function works on top of the trained model and makes use of the learned label to map and predict the labels for the data to be tested. We will pass the **test_image**, reshaped to the input size which we will be passing into the Convolutional Neural Network, which is **64 x 64 x 1**. 

> We are gaining a speed and accuracy advantage as, we have use thresholded (black and white) images while training, and we are also using thresholded images of **test_image** for comparison. Since it involves two colours only, the process is faster and accurate

Then, we will declare a dictionary called **prediction**, which has the integer name in string as the key, which in turn returns the **result[0][key]**. Here result[0] refers to the first element in the list, which is the **categories** dictionary. Then, we parse the results depending on the key value in **result[0][key]**.

Next, we be sorting the **prediction.items()**, which are the **individual probabilities that the input gesture you are showing in the Region of Interest (R.O.I) resembles the images/dataset with which you have trained the models.** The **operator.itemgetter(1)** helps to sort with more than one columns. Also, **reverse=True** refers to sorting in the descending order such that **prediction[0][0]** contains the string integer with the **maximum probability.** 

> For example, if you show the gesture "ZERO", the probability that the gesture shown will resemble "ZERO" will be maximum than any other gesture of any number. Thus **prediction[0][0]** will contain "ZERO" in the form of a string since it has the maximum probability.

We will then showing the string using the **putText()** function on the frame, and then showing the frame under the name **Frame** using the **imshow()** function.

## Step 7: 
```python
    interrupt = cv2.waitKey(10)
    if interrupt & 0xFF == 27:
        break

cap.release()
cv2.destroyAllWindows()
```
Next, we initialise the **interrupt** variable, which returns 10 frames per second here. 0xFF collects and recognises the keyboard response and matches it to the **Escape Key**. Then, after the detection is over, we release our webcam and deallocate all the memory rendered to the image array vectors. This has been previously explained in the past documentations. 

---

Now your **prediction.py** should look like the following. 

```python
from keras.models import model_from_json
import operator
import cv2

json_file = open("model-bw.json", "r")
model_json = json_file.read()
json_file.close()
loaded_model = model_from_json(model_json)
loaded_model.load_weights("model-bw.h5")
print("Loaded model from disk")

cap = cv2.VideoCapture(0) 

categories = {0: 'ZERO', 1: 'ONE', 2: 'TWO', 3: 'THREE', 4: 'FOUR', 5: 'FIVE'}

while True:
    _, frame = cap.read()
    frame = cv2.flip(frame, 1)

    x1 = int(0.5*frame.shape[1])
    y1 = 10
    x2 = frame.shape[1]-10
    y2 = int(0.5*frame.shape[1])

    cv2.putText(frame, "Expressando - TDOC 2021", (175, 450), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (225,255,0), 3)
    cv2.rectangle(frame, (x1-1, y1-1), (x2+1, y2+1), (255,255,255) ,3)
    roi = frame[y1:y2, x1:x2]

    roi = cv2.resize(roi, (64, 64)) 
    roi = cv2.cvtColor(roi, cv2.COLOR_BGR2GRAY)
    cv2.putText(frame, "R.O.I", (440, 350), cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (0,225,0), 3)

    _, test_image = cv2.threshold(roi, 120, 255, cv2.THRESH_BINARY)
    cv2.imshow("ROI", test_image)

    result = loaded_model.predict(test_image.reshape(1, 64, 64, 1))
    prediction = {'ZERO': result[0][0], 
                  'ONE': result[0][1], 
                  'TWO': result[0][2],
                  'THREE': result[0][3],
                  'FOUR': result[0][4],
                  'FIVE': result[0][5]} 
    prediction = sorted(prediction.items(), key=operator.itemgetter(1), reverse=True) 
    cv2.putText(frame, "PREDICTION:", (30, 90), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 2)
    cv2.putText(frame, prediction[0][0], (80, 130), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 2)    
    cv2.imshow("Frame", frame)

    interrupt = cv2.waitKey(10)
    if interrupt & 0xFF == 27:
        break


cap.release()
cv2.destroyAllWindows()
```

Run the code in your Powershell/terminal using:
```bash
python prediction.py
```
Now, see your real-time sign-language detection in action!!!

<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/138715473-1904ca37-d9d7-4afa-be2e-04e3c196ddcb.jpeg" style="height:auto; width:80%"></img></h1>

## Now you have your own version of Expressando ready. 
## Thank you for attending Ten Days of Code, 2021. May the Source be with you!!
---
