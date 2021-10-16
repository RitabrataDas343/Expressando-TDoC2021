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
> It is advisable to download **Python version 3.6** as it is the latest **stable** version of Python used widely nowadays.

Now let us start by making a **virtual environment**, which is one of the basic necessities for any Python projects.

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

_**For Windows**_: 

**Step 1**: Create a directory called "**Ten Days of Code**", where you will create your 

_**For Linux/UNIX**_:

**Step 1**: Create a directory called "**Ten Days of Code**", where you will create and save your Python files. We will also create our virtual environment inside this created directory. 

Open your terminal at the desired directory and type:

**For Python version less than 3.0:**
```bash
pip install virtualenv
```

**For Python version 3.0:**
```bash
pip3 install virtualenv
```

```
├── Ten Days of Code
|    ├── env       
```

In order to create a virtual environment we can use built-in module named **virtualenv**.
let's look at how we can create virtual environments i'll first create a directory or open directory if already and i'll open the terminal/cmd in this workspace. By default we are using the global python environment.
if you wnat to check which environment you use than. 


now let's create an isolated python environment. To create an isolated pyhton environment use this command.

```bash
python -m virtualenv <name_of_venv>
```

then my new virtual enivronmnet has beeb created. Now you can see that there's a folder called (name_of_venv) in this folder. This directroy contains minimal python setup and executables for our python project.

No that we have created a virtual environment let's activate it we'll go to our terminal/cmd and use.

**FOR LINUX** <br>
```bash
source <name_of_venv>/bin/activate
```

**FOR WINDOWS** <br>
```bash
./env/Scripts/activate
```

now you can check which virtual environment use or list of packages in that virtual environment.
None of the global packages and modulea are available in this virtual environment now we kan install a specific library.
That version of library is available only for this virtual environment. it will not have any effect on our global python setup.

In order to deactivate a virtual environment we can simply use the deactivate command on our terminal/cmd. You can see that currently the (name_of_venv) virtual environment is activated let me deactivate this virtual environment.

```bash
deactivate
```

and you can see that the virtual env is deactivated now if i do **which python** than show your global environment.


if we create a another virtual environment , this won't affect our previous virtual environment in any way. No that we have learned about virtual environments. I highly encourage you to use separate virtual environments for each of your python projects this will prove very useful once you start working on a number projects with different requirements. 
you can then put all these requirements in a requirements file this requirements file can then be used to set up the same type of virtual environment on any machine.
if you want to remove a virtual environment you cna just delete the folder containing the virtual environment.

# **NumPy**

**NumPy** is a Python package that stands for ‘Numerical Python’. It is the core library for scientific computing, which contains a powerful n-dimensional array object.

## Where is NumPy used?

Python NumPy arrays provide tools for integrating C, C++, etc. IT is also useful in linear algebra, random number capability etc. NumPy array can also be used as an efficient multi-dimensional container for generic data. Now, let me tell you what exactly is Python NumPy aaray.

## How do I install NumPy?

To install Python NumPy, go to your command prompt and type:

```bash
pip install numpy
```

Once the installation is completed, go to your IDE/editor and simply import it by typing:

```python
import numpy as np
```


You can also refer to the following resources to know further about [**NumPy**](https://numpy.org/)

# What is Computer Vision?

Computer vision is an interdisciplinary field that deals with how computers can be made to gain high level understanding from digital images or videos so the idea is to automate tasks that the human visual systems can do so a computer should be able to recognize that this is a face of a human being, this is what a lamppost looks like so things like that right so i hope i'm clear what is meaning of computer vision.

Computer Vision is a field of study which enables computers replicate the human visual system. As already mentioned above, it's a subset of artificial intelligence which coolects information form digital images or videos and processes them to define the attributes. The entire process involves image acquiring, screening, analysing, identifiying and extracting information. This extensive processign helps computers to usnderstand any visual content and act on it accordingly.

Computer vision projects translate digital visual content inot explicit descriptons to gather multi-dimensional data. This data is then turned into a computer-readable language to aid the decision-making process. The main objective of this branch of artificial intelligence is to teach machines to collect information from pixels.

# How does a computer read an image?

How does a human mind apprehend an image? When you see the image below whtat do you actually see and how do you say what is in the image?

you most probably look for different shapes and colours in the image and that might help you decide that this is an image of a dog. But does a computer also see it in the same way? The answer is no.

A digital image is an image composed of picture elements, alsso knows as pixels, each wiht finite, discrete quantities of numeric representation for its intensity or grey level. So the computer sees an images as numerical values of these pixels and in order to recognise a certain image, it has to recognise the patterns and regularities in this numerical data.

Here is a hypothetical example of how pixels form an image. The darker pixels are represented by a number closer to the zero and lighter pixels are represented by numbers approaching one. All other colours are represented by the numbers between 0 and 1. 

But usually, you will find that for any colour image, there are 3 primary channels – Red, green and blue and the value of each channel varies from 0-255. In more simpler terms we can say that a digital image is actually formed by the combination of three basic colour channels  Red, green, and blue whereas for a grayscale image we have only one channel whose values also vary from 0-255.

# Waht is OpenCV?

OpenCv (Open Soucre Computer Vision Library) is an open source software library for computer vision and machine learning. OpenCV was created to provide a shared infrastucture for applications for computer vision add to speed up the use of machine perception in consumer products. OpenCV, as a BSD-licensed software, makes it simple for companies to use and chagne the code. There are some predefined packages and libraries that makes our life simple and OpenCV is one of them.


# Install OpenCV

## For Windows Or Linux 

you can use pip to install OpenCV on windows. Pip is a de facto standard package-management system used to install and manage software packages written in Python and it usually comes in installed when you install Python. If you do not have Python installed, I would suggest download it from here. Use this command in the command prompt to install OpenCV:

```bash
pip install opencv-python
```

## For Mac

You can use homebrew to intall OpenCV as it makes it really easy and you just have to use this command for installing:

```bash
brew install opencv
```

You can also refer to the following resources to know further about **[OpenCV](https://opencv.org/)**

---
# **TensorFlow**

## What is tensorflow?
**TensorFlow** is a free and open-source software library for machine learning and artificial intelligence. It can be used across a range of tasks but has a particular focus on training and inference of deep neural networks. Tensorflow is a symbolic math library based on dataflow and differentiable programming.

# **Keras**

## What is keras?
**Keras** is an open-source neural-network library written in Python. It was developed by Francois Chollet while he was at Google. In simple words, Keras is a high Level API(Application Programmable Interface) that allow to build the Deep learning or Machine Learning models easily without detail understanding about internal architecture how the ML algorithm works internally.
