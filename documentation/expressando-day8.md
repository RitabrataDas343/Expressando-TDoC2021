
<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<p align="center">
<img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png" style="height:auto; width:50%"></img>
</p>

<h1 align="center">DAY 8</h1>

# Live Prediction of Customised Sign Language

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
    prediction = sorted(prediction.items(), key=operator.itemgetter(1), reverse=True) #(0.9 = FIVE, 0.7, 0.6, 0.5, 0.4)
    cv2.putText(frame, "PREDICTION:", (30, 90), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 2)
    cv2.putText(frame, prediction[0][0], (80, 130), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255), 2)    
    cv2.imshow("Frame", frame)

    interrupt = cv2.waitKey(10)
    if interrupt & 0xFF == 27:
        break


cap.release()
cv2.destroyAllWindows()
```

Run the code in your Powershell/terminal using 
```bash
python prediction.py
```

## Now you have your own version of Expressando ready. 
## Thank you for attending Ten Days of Code, 2021. May the Source be with you!!
---
