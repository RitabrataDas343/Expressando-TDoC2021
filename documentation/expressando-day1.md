<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png" style="height:600px; width:900px"></img></hi>

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
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593132-9ee471cf-c6ef-4b34-820a-3ea08bd653e8.png" style="height:200px; width:400px"></img></h1>

**NumPy** is a Python package that stands for ‘Numerical Python’. It is the core library for scientific computing, which contains a powerful n-dimensional array object. Python NumPy arrays provide tools for sophisticated (broadcasting) functions, integrating C/C++ and Fortran code, useful linear algebra, Fourier transform, and random number capabilities. NumPy array can also be used as an efficient multi-dimensional container for generic data. 

You can know more about **NumPy** from: <strong>[here](https://numpy.org/doc/stable/user/quickstart.html)</strong>

<h1 align="center">OpenCV</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593200-aa8b4e81-0d4f-4100-b1a9-e612858b4d0f.png" style="height:200px; width:400px"></img></h1>

**OpenCV (Open Soucre Computer Vision Library)** is an open source software library for computer vision and machine learning, created to provide a shared infrastucture for applications for computer vision add to speed up the use of machine perception in consumer products. OpenCV, as a BSD-licensed software, makes it simple for companies to use and change the code.

Computer vision is an interdisciplinary field that deals with how computers can be made to gain high level understanding from digital images or videos. It helps to automate tasks that the human visual systems would be able to perform. It is a field of study which enables computers replicate the human visual system. As already mentioned above, it's a subset of artificial intelligence which collects information form digital images or videos and processes them to define the attributes. The entire process involves image acquiring, screening, analysing, identifiying and extracting information. This extensive processign helps computers to usnderstand any visual content and act on it accordingly.

You can know more abput **OpenCV** from: <strong>[here](https://opencv.org/)</strong>

<h1 align="center">Tensorflow</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593236-58a743bd-9df2-47ec-a478-a7f044eae41b.png"></img></h1>

**TensorFlow** is a free and open-source software library for machine learning and artificial intelligence. It can be used across a range of tasks but has a particular focus on training and inference of deep neural networks. It has a comprehensive, flexible ecosystem of tools, libraries and community resources that lets researchers push the state-of-the-art in ML and developers easily build and deploy ML powered applications. Tensorflow is a symbolic math library based on dataflow and differentiable programming. 

You can know more abput **TensorFlow** from: <strong>[here](https://www.tensorflow.org/tutorials)</strong>

<h1 align="center">Keras</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593369-90a41d91-5bf8-4df5-ad31-2ba47d76d79d.png" style="height:150px; width:500px"></img></h1>

**Keras** is an open-source neural-network deep-learning library written in Python. It reduces developer cognitive load to free you to focus on the parts of the problem that really matter. It further adopts the principle of progressive disclosure of complexity: simple workflows should be quick and easy, while arbitrarily advanced workflows should be possible via a clear path that builds upon what you've already learned. In simple words, Keras is a high Level API(Application Programmable Interface) that allow to build the Deep learning or Machine Learning models easily without detail understanding about internal architecture how the ML algorithm works internally.

You can know more abput **Keras** from: <strong>[here](https://keras.io/api/)</strong>

<h1 align="center">SciPy</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593374-d1238644-350e-48bd-976f-0a30a187e23a.png" style="height:170px; width:400px"></img></h1>

**The SciPy ecosystem** is a collection of open source software for scientific computing in Python. It includes modules for statistics, optimization, integration, linear algebra, Fourier transforms, signal and image processing, ODE solvers, and more. SciPy is built to work with NumPy arrays, and provides many user-friendly and efficient numerical routines, such as routines for numerical integration and optimization. Together, they run on all popular operating systems, are quick to install, and are free of charge. NumPy and SciPy are easy to use, but powerful enough to be depended upon by some of the world's leading scientists and engineers.

You can know more abput **SciPy** from: <strong>[here](https://docs.scipy.org/doc/)</strong>

Since, you are well aware of the Python packages that we are going to use in the projects, let us now get into some coding action!!
