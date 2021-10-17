<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png"></img>

## Brief Preview

**Expressando** is a real-time sign language detection system made using **OpenCV, Keras, Tensorflow and SciPy.** It is a beginner-friendly project, suitable for the enthusiasts in the field of Machine-Learning and Deep-Learning. The projects primarily aim to highlight the basic use of OpenCV in image processing manipulation, training of models with Keras using Tensorflow as backend, and finally, the detection of our customised sign-language after constructing a Convolutional Neural Network on it. So, without any further ado, let us begin with the tutorial: 

<h1 align="center">DAY 1</h1>

Expressando has been written in **Python**. So, before we start, you can have a quick recapitulation of the basics from the following resources, which will be beneficial for a better understanding of the concepts:

* <strong>[Python Beginner's Guide](https://wiki.python.org/moin/BeginnersGuide/Programmers)</strong>
* <strong>[W3Schools](https://www.w3schools.com/python/)</strong>
* <strong>[Tutorials Point](https://www.tutorialspoint.com/python/index.htm)</strong>

Also, make sure that you have Python installed on your system. 

In case, you do not have Python pre-installed, download the latest version of Python from <strong>[here](https://www.python.org/downloads/)</strong>.
> It is advisable to download **Python version 3.6 and above** as ithese are the latest **stable** versions of Python used widely nowadays.

After installation, check for the installed version of Python by typing the following command in **Powershell/Terminal**:
```bash
python3 --version
```
In case, you have Python version lower than 3.0, use the following command:  

```bash
python --version
```
If your installation has been successful, then the Python version gets displayed on your command line interface.

For example:
```bash
Python 3.8.5
```
Now, we will now have a short look at the Python packages that are need to be installed, to know more about their functionalities and their usage in the project. 

<h1 align="center">NumPy</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593132-9ee471cf-c6ef-4b34-820a-3ea08bd653e8.png"></img></h1>

**NumPy** is a Python package that stands for ‘Numerical Python’. It is the core library for scientific computing, which contains a powerful n-dimensional array object. Python NumPy arrays provide tools for sophisticated (broadcasting) functions, integrating C/C++ and Fortran code, useful linear algebra, Fourier transform, and random number capabilities. NumPy array can also be used as an efficient multi-dimensional container for generic data. 

You can know more about **NumPy** from: <strong>[here](https://numpy.org/doc/stable/user/quickstart.html)</strong>

<h1 align="center">OpenCV</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593200-aa8b4e81-0d4f-4100-b1a9-e612858b4d0f.png"></img></h1>

**OpenCV (Open Soucre Computer Vision Library)** is an open source software library for computer vision and machine learning, created to provide a shared infrastucture for applications for computer vision add to speed up the use of machine perception in consumer products. OpenCV, as a BSD-licensed software, makes it simple for companies to use and change the code.

Computer vision is an interdisciplinary field that deals with how computers can be made to gain high level understanding from digital images or videos. It helps to automate tasks that the human visual systems would be able to perform. It is a field of study which enables computers replicate the human visual system. As already mentioned above, it's a subset of artificial intelligence which collects information form digital images or videos and processes them to define the attributes. The entire process involves image acquiring, screening, analysing, identifiying and extracting information. This extensive processign helps computers to usnderstand any visual content and act on it accordingly.

You can know more abput **OpenCV** from: <strong>[here](https://opencv.org/)</strong>

<h1 align="center">Tensorflow</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593236-58a743bd-9df2-47ec-a478-a7f044eae41b.png"></img></h1>

**TensorFlow** is a free and open-source software library for machine learning and artificial intelligence. It can be used across a range of tasks but has a particular focus on training and inference of deep neural networks. It has a comprehensive, flexible ecosystem of tools, libraries and community resources that lets researchers push the state-of-the-art in ML and developers easily build and deploy ML powered applications. Tensorflow is a symbolic math library based on dataflow and differentiable programming. 

You can know more abput **TensorFlow** from: <strong>[here](https://www.tensorflow.org/tutorials)</strong>

<h1 align="center">Keras</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593369-90a41d91-5bf8-4df5-ad31-2ba47d76d79d.png"></img></h1>

**Keras** is an open-source neural-network deep-learning library written in Python. It reduces developer cognitive load to free you to focus on the parts of the problem that really matter. It further adopts the principle of progressive disclosure of complexity: simple workflows should be quick and easy, while arbitrarily advanced workflows should be possible via a clear path that builds upon what you've already learned. In simple words, Keras is a high Level API(Application Programmable Interface) that allow to build the Deep learning or Machine Learning models easily without detail understanding about internal architecture how the ML algorithm works internally.

You can know more abput **Keras** from: <strong>[here](https://keras.io/api/)</strong>

<h1 align="center">SciPy</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593374-d1238644-350e-48bd-976f-0a30a187e23a.png"></img></h1>

**The SciPy ecosystem** is a collection of open source software for scientific computing in Python. It includes modules for statistics, optimization, integration, linear algebra, Fourier transforms, signal and image processing, ODE solvers, and more. SciPy is built to work with NumPy arrays, and provides many user-friendly and efficient numerical routines, such as routines for numerical integration and optimization. Together, they run on all popular operating systems, are quick to install, and are free of charge. NumPy and SciPy are easy to use, but powerful enough to be depended upon by some of the world's leading scientists and engineers.

You can know more abput **SciPy** from: <strong>[here](https://docs.scipy.org/doc/)</strong>

Since, you are well aware of the Python packages that we are going to use in the projects, let us now get into some coding action!!

<h1 align="center">DAY 2</h1>
Now let us start by making a **virtual environment**, which is one of the basic necessities for any Python project.

## What is a 'Virtual Environment'?

A virtual environment is an **isolated Python-stimulated environment where a project's dependencies and packages are installed in a different directory from the other packages installed in the system's default Python path (known as the base environment) and other virtual environments.** It is synonymous to a 'container', where you have all your required dependencies installed and ready to be used in your project. 

Let us assume that you are specifically working on a project/task, which might not need all the Python packages installed in your system. So, you basically create a different 'container' or 'directory', which serves as a virtual environment regardless of the packages installed in the system environment. You can always create additional environments in your system, like one environment for each one project. This helps to keep track of your installed dependencies as well.

Virtual environments allow us to create **isolated environments** for each of our Python projects. **Each virtual environment will be independent of one another**, without any interference from any other virtual environment or the base system environment. It is considered as a good practice to setup virtual environments before proceeding directly with the projects as it ensures the installed dependencies and packages. 

## Why do we use 'Virtual Environment'?

When we start developing on any detailed or sufficiently large Python projects involving numerous Python packages and libraries, we tend to use other different packages and modules that are not pre-installed in our system (**packages which are not included in the standard Python library**). These packages and modules are **open-source repositories**, which are constantly being updated with every new release. Now, there exists a probability that the projects might use different versions of the same packages. **Virtual environments allow us to install both the versions simultaneously in our systems**, isolated from each other, each project having a virtual environment of it's own.

> For example: Project A uses **opencv-python version: 4.5.3.36**, whereas Project B uses **opencv-python version: 3.2.1.25**. Now if both the projects use the same base environment having the same version of the project installed on them, then either of the projects will be incompatible and will throw an error on rendering the functions of the packages. 

> In that case, you will either need to change the entire code base of either project to make it compatible with the new version, or you will have to uninstall the latest version and reinstall the old version more often, which is hectic and not feasible. Virtual environments allow us to solve this problem by installing both the versions: **opencv-python version: 4.5.3.36** and **opencv-python version: 3.2.1.25** in the respective environments of **Project A and Project B.** 

So, instead of using a single and global Python installation for all of our projects, we will create a virtual environment for each of our independent projects. Now let us begin by creating our own virtual environment, which will be required to proceed with our objective.

## Creating Virtual Environment

_**For Linux/UNIX**_:

**Step 1:** For creating virtual environments, you need a Python package called **virtualenv**. To install virtualenv on your system, type the following command in your terminal.

**For Python version less than 3.0:**
```bash
pip install virtualenv
```

**For Python version 3.0 and above:**
```bash
pip3 install virtualenv
```

Now, check whether 'virtualenv' has been installed successfully on your system. Type the following command:
```bash
virtualenv --version
```

The following output will be displayed on successful installation. For example: 
```bash
16.0.2
```


**Step 2:** Create a directory called "**TDoC-2021**", where you will create and save your Python files. This is the main directory for the project. We will also create our virtual environment inside this created directory. 

Open your terminal at the desired directory and type:

```bash
mkdir TDoC-2021
```
A folder called "**TDoC-2021**" will be created at your desired directory. Now, let us create our virtual environment inside this directory.


**For Python version less than 3.0:**
```bash
cd TDoC-2021
python -m venv <NAME_OF_THE_ENVIRONMENT>
```

**For Python version 3.0 and above:**
```bash
cd TDoC-2021
python3 -m venv <NAME_OF_THE_ENVIRONMENT>
```

Here, substitute the **<NAME_OF_THE_ENVIRONMENT>** with a proper string, which you want to name the environment. For example:
```bash
python3 -m venv env
```
> It is preferable to name your environment as "**env**" or "**venv**", as these directories has already been included under "**.gitignore**". Hence, you do not need to make any further changes in the gitignore file, while commiting your files in Github/Gitlab.

Here we will be using "**env**" as the name of our environment.


**Step 3:** After creating the virtual environment named "**env**", you will notice that a directory called "**env**" is created. This directory basically serves as your virtual environment. Now, let us activate our virtual environment by the following command.
```bash
source <NAME_OF_THE_ENVIRONMENT>/bin/activate
```

In our case, we will be using the following command:

```bash
source env/bin/activate
```
You will be able to see the name of the environment in closed parantheses in your terminal, which will indicate that your virtual environmant has been activated.
For example:

```bash
(env) ┌─[ritabrata@ritabrata-VivoBook-ASUSLaptop-X409JB-X409JB]─[~/Desktop/TDoC-2021]
      └──╼ $
```


**Step 4:** Download the "**requirements.txt**" from the given link: <strong>[requirements.txt](https://drive.google.com/file/d/1l1xqC7-Bbv3KosGItOUyzgmnjSSQKeIZ/view?usp=sharing)</strong>.

Copy the "**requirements.txt**" file and store it under the directory "**TDoC-2021**". You will have the following folder structure: 

```
├── TDoC-2021
|    ├── env       
|    ├── requirements.txt
```

Now type the following command in your Terminal window: 

```bash
pip3 install -r requirements.txt
```
You will now have all the required dependencies and Python packages with their appropriate versions installed in your virtual environment named "**env**". You can check whether the dependencies are installed according to the "requirements.txt" file by the following command: 
```bash
pip3 list 
```
This command enlists all the installed dependencies installed in your encironment.

You can also deactivate the environment, when it is not in use, by typing the following command:
```bash
deactivate
```
The virtual environment will be deactivated, and the name of the environment in closed paranthesis will cease to appear.

_**For Windows**_: 

**Step 1:** For creating virtual environments, you need a Python package called **virtualenv**. To install virtualenv on your system, type the following command in your **Windows Powershell**.

In case, you do not have Windows Powershell, you can download it from: <strong>[here](https://www.microsoft.com/en-in/download/details.aspx?id=42554&ranMID=46131&ranEAID=a1LgFw09t88&ranSiteID=a1LgFw09t88-.l4oqm.FvUCUi6UzmMU8qQ&epi=a1LgFw09t88-.l4oqm.FvUCUi6UzmMU8qQ&irgwc=1&OCID=AID2200057_aff_7806_1243925&tduid=%28ir__w0vmuhh3v0kf6hs2kgvlvbrdnu2xr9yt62nusoij00%29%287806%29%281243925%29%28a1LgFw09t88-.l4oqm.FvUCUi6UzmMU8qQ%29%28%29&irclickid=_w0vmuhh3v0kf6hs2kgvlvbrdnu2xr9yt62nusoij00)</strong>

```bash
pip install virtualenv
```

Now, check whether 'virtualenv' has been installed successfully on your system. Type the following command:
```bash
virtualenv --version
```

The following output will be displayed on successful installation. For example: 
```bash
virtualenv 16.0.2 from c:\users\administrator\appdata\local\programs\python\python39\lib\site-packages\virtualenv\__init__.py 
```


**Step 2:** Create a directory called "**TDoC-2021**", where you will create and save your Python files. This is the main directory for the project. We will also create our virtual environment inside this created directory. 

Open your Powershell at the desired directory and type:

```bash
mkdir TDoC-2021
```
A folder called "**TDoC-2021**" will be created at your desired directory. Now, let us create our virtual environment inside this directory.

```bash
cd TDoC-2021
python -m venv <NAME_OF_THE_ENVIRONMENT>
```

Here, substitute the **<NAME_OF_THE_ENVIRONMENT>** with a proper string, which you want to name the environment. For example:
```bash
python3 -m venv env
```
> It is preferable to name your environment as "**env**" or "**venv**", as these directories has already been included under "**.gitignore**". Hence, you do not need to make any further changes in the gitignore file, while commiting your files in Github/Gitlab.

Here we will be using "**env**" as the name of our environment.


**Step 3:** After creating the virtual environment named "**env**", you will notice that a directory called "**env**" is created. This directory basically serves as your virtual environment. Now, let us activate our virtual environment by the following command.
```bash
. <NAME_OF_THE_ENVIRONMENT>/Scripts/activate
```

In our case, we will be using the following command:

```bash
. env/Scripts/activate
```

You will be able to see the name of the environment in closed paranthesis in your terminal, which will indicate that your virtual environment has been activated.
For example:

```bash
(env) PS C:\Users\Administrator\Desktop\Expressando-TDoC2021>
```


**Step 4:** Download the "**requirements.txt**" from the given link: <strong>[requirements.txt](https://drive.google.com/file/d/1l1xqC7-Bbv3KosGItOUyzgmnjSSQKeIZ/view?usp=sharing)</strong>.

Copy the "**requirements.txt**" file and store it under the directory "**TDoC-2021**". You will have the following folder structure: 

```
├── TDoC-2021
|    ├── env       
|    ├── requirements.txt
```

Now type the following command in your Terminal window: 

```bash
pip install -r requirements.txt
```
You will now have all the required dependencies and Python packages with their appropriate versions installed in your virtual environment named "**env**". You can check whether the dependencies are installed according to the "requirements.txt" file by the following command: 
```bash
pip list 
```
This command enlists all the installed dependencies installed in your environment.

You can also deactivate the environment, when it is not in use, by typing the following command:
```bash
deactivate
```
The virtual environment will be deactivated, and the name of the environment in closed paranthesis will cease to appear.

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






