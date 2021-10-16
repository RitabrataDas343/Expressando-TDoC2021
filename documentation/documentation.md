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
> It is advisable to download **Python version 3.6 and above** as it is the latest **stable** version of Python used widely nowadays.

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

<h1 align="center">DAY 2</h1>

After installing all the required dependencies in the virtual environment, we will now have a short look at the installed Python packages to know more about their functionalities and their usage in the project. 

<h1 align="center">NumPy</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593132-9ee471cf-c6ef-4b34-820a-3ea08bd653e8.png"></img></h1>

**NumPy** is a Python package that stands for ‘Numerical Python’. It is the core library for scientific computing, which contains a powerful n-dimensional array object. Python NumPy arrays provide tools for sophisticated (broadcasting) functions, integrating C/C++ and Fortran code, useful linear algebra, Fourier transform, and random number capabilities. NumPy array can also be used as an efficient multi-dimensional container for generic data. 

You can know more abput NumPy from here:<s(https://numpy.org/doc/stable/user/quickstart.html)
<h1 align="center">OpenCV</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593200-aa8b4e81-0d4f-4100-b1a9-e612858b4d0f.png"></img></h1>
Computer vision is an interdisciplinary field that deals with how computers can be made to gain high level understanding from digital images or videos so the idea is to automate tasks that the human visual systems can do so a computer should be able to recognize that this is a face of a human being, this is what a lamppost looks like so things like that right so i hope i'm clear what is meaning of computer vision.

Computer Vision is a field of study which enables computers replicate the human visual system. As already mentioned above, it's a subset of artificial intelligence which coolects information form digital images or videos and processes them to define the attributes. The entire process involves image acquiring, screening, analysing, identifiying and extracting information. This extensive processign helps computers to usnderstand any visual content and act on it accordingly.

Computer vision projects translate digital visual content inot explicit descriptons to gather multi-dimensional data. This data is then turned into a computer-readable language to aid the decision-making process. The main objective of this branch of artificial intelligence is to teach machines to collect information from pixels.

OpenCv (Open Soucre Computer Vision Library) is an open source software library for computer vision and machine learning. OpenCV was created to provide a shared infrastucture for applications for computer vision add to speed up the use of machine perception in consumer products. OpenCV, as a BSD-licensed software, makes it simple for companies to use and chagne the code. There are some predefined packages and libraries that makes our life simple and OpenCV is one of them.

<h1 align="center">Tensorflow</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593236-58a743bd-9df2-47ec-a478-a7f044eae41b.png"></img></h1>

**TensorFlow** is a free and open-source software library for machine learning and artificial intelligence. It can be used across a range of tasks but has a particular focus on training and inference of deep neural networks. Tensorflow is a symbolic math library based on dataflow and differentiable programming.

<h1 align="center">Keras</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593369-90a41d91-5bf8-4df5-ad31-2ba47d76d79d.png"></img></h1>

**Keras** is an open-source neural-network library written in Python. It was developed by Francois Chollet while he was at Google. In simple words, Keras is a high Level API(Application Programmable Interface) that allow to build the Deep learning or Machine Learning models easily without detail understanding about internal architecture how the ML algorithm works internally.

<h1 align="center">SciPy</h1>
<h1 align="center"><img src="https://user-images.githubusercontent.com/76585827/137593374-d1238644-350e-48bd-976f-0a30a187e23a.png"></img></h1>
