# EXPRESSANDO (TDOC)

## What is a virtual environment?

what is an environment so environment is nothing but a it is basically a location it is like a container where you have your python and you have all other libraries installed. Now this is your base environment, base environment basically means where you have installed all your packages whenever you are working on any machine learning application or any other application but what happens let’s say you are specifically working on a project/task so in that case you might not need all these packages right you might not need everything so you may need a python but different version of python. And need some other packages. What you can do you can create a different container and this container is nothing but an environment. So when you have the base environment it is like the first environment or the like it is a default environment that is always present in your system but you can create some some additional environments also so these are know as your virtual environments.

Virtual environments allow us to create isolated environments for each of our python projects. Each virtual environment will be independent of one another due to this they can have different python versions and their own versions of packages and modules to resolve our earlier problem of conflicting versions of the module/library. We can have separate virtual environments for each project each of these virtual environments can then have their own separate packages of different versions.

## Why Virtual Environments?

When we start working on larger python projects we have to use different packages and modules that don't come pre-installed with the standard python library these packages and modules are constantly being updated with every new release let's suppose that we worked on a project that uses a library of specifically the version, after a few months you then worked on another project that uses a different version of that module, now if we have to go back to wroking on your first project you will either need to change the entire code base of the porject to make it compatible with new version or you'll have to uninstall new version and reinstall the old version more often that not your python projects will use different versions of many such packages or even an entirely different version of python that won't be compatible with one another. Virtual environments allow us to solve this problem instead of using a single and global python installation for all our projects we can create different virtual enviroments for dirfferent projects.

---

## Create Virtual Environments

In order to create a virtual environment we can use built-in module named **virtualenv**.
let's look at how we can create virtual environments i'll first create a directory or open directory if already and i'll open the terminal/cmd in this workspace. By default we are using the global python environment.
if you wnat to check which environment you use than. 

```bash
which python
```

and check how many library/modules are install that environment. 

```bash
pip list
```

now let's create an isolated python environment. To create an isolated pyhton environment use this command.

```bash
python -m virtualenv <name_of_venv>
```

then my new virtual enivronmnet has beeb created. Now you can see that there's a folder called (name_of_venv) in this folder. This directroy contains minimal python setup and executables for our python project.


## Activate Virtual Environments

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


## Deactivate Virtual Environments

In order to deactivate a virtual environment we can simply use the deactivate command on our terminal/cmd. You can see that currently the (name_of_venv) virtual environment is activated let me deactivate this virtual environment.

```bash
deactivate
```

and you can see that the virtual env is deactivated now if i do **which python** than show your global environment.


if we create a another virtual environment , this won't affect our previous virtual environment in any way. No that we have learned about virtual environments. I highly encourage you to use separate virtual environments for each of your python projects this will prove very useful once you start working on a number projects with different requirements. 
you can then put all these requirements in a requirements file this requirements file can then be used to set up the same type of virtual environment on any machine.
if you want to remove a virtual environment you cna just delete the folder containing the virtual environment.