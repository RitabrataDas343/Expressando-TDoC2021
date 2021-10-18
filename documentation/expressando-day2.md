<h1 align="center">EXPRESSANDO - TDoC 2021</h1>
<img src="https://user-images.githubusercontent.com/76585827/137585523-2ff41a7e-3859-44e9-85ae-d0014a4fc661.png"></img>

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
