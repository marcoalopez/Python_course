# How to install Python for Data Science using anaconda

To install Python and the necessary scientific libraries we will use an open-source package and environment management system called **conda**. Conda serves to install, run, and update Python packages while making sure there are no incompatibilities between the versions of the packages on your computer. Also, to manage (create, delete, and modify) environments on your computer. In a nutshell, environments are Python installations that work independently so you can have installed different Python versions or scientific packages at the same time. This is useful, for example, to test a script on different versions of Python and any other Python library or to keep isolated different scientific libraries that may work with different Python versions, etc.

- [Install Python and conda using miniconda](#install-python-and-conda-using-miniconda)
- [Managing Python packages (install, remove, update, clean)](#managing-python-packages--install--remove--update--clean-)
- [More on conda environments](#more-on-conda-environments)
  * [Create an environment](#create-an-environment)
  * [Using an environment.ylm file](#using-an-environmentylm-file)



## Install Python and conda using miniconda

In this course, we will install miniconda which allows us to manage Python packages through the console with minimal installation (don't be scared, it's simpler than it sounds)..

1. Go to https://docs.conda.io/en/latest/miniconda.html and download the latest version of miniconda for your operating system.

2. Install miniconda following the instructions.

3. Open the **Anaconda Prompt (miniconda)** and a console will pop up. You will see something similar to this (the path may change depending on the file system of your operating system)

   ```
   (base) C:\Users\Marco>
   ```

4. First, make sure you have the latest version of **conda** installed. To do this, enter the following command:

   ```
   >conda update conda
   ```
   and update if necessary (👉 tip: do this often). 

5. If you have been paying attention, you will see that the current line in the console says "base" in parentheses. This means that you are in the base Python environment. A wise strategy is to install nothing in this environment apart from the default Python libraries that were already added during the miniconda installation process. You can see which libraries by using  ``conda list`` if you are curious. Our strategy will be to create a new Python environment, which we will call "course", and install there all the libraries that we will use during the course. For this we will use the following command:

   ```
   >conda create --name course python
   ```

6. Once finished, use the command ``conda env list`` and you will see listed two environments, _base_ and _course_, and an asterisk indicating that "base" is the currently active environment. To install the Python libraries needed in the _course_ environment we first have to activate the environment, so we enter ``activate course``. Now you will see in parentheses the word "course" indicating that we are within this environment.

7. Next, we proceed to install the libraries needed for the course. Instead of doing it one by one, we will do it in a single line as follows (you can paste and copy the command directly into your console)

   ```
   >conda install numpy scipy pandas matplotlib jupyterlab
   ```

   and say yes to all. Conda will install the chosen libraries/packages and all the necessary dependencies. Once finished, you're done.

8. Now you can launch Jupyter lab by simply typing ``jupyter lab`` in the console and it will open the application in your default browser. We will see later how to work with Jupyter lab. The important thing is that the application has been launched.

9. Once the above installation process is done, we will proceed in the same way to launch Jupyter lab from scratch:
	- Open the Anaconda Prompt (miniconda)
	- activate the environment "course" using ``activate course``
	- launch Jupyter lab using ``jupyter lab``

## Using dedicated (Jupyter notebook) applications

If you prefer to use a dedicated application instead of opening jupyter notebooks in your default browser, there are several alternatives. Here we will mention two:

- Visual Studio Code (a.k.a. vscode)  https://code.visualstudio.com/

This is a free code editor that can be used with a variety of programming languages including Python and supports Jupyter notebooks via extensions. As an advantage over JupyterLab, it has a variable browser by default. More detailed instructions on how to use jupyter notebooks in vscode can be found at the following link https://code.visualstudio.com/docs/datascience/jupyter-notebooks

- JupyterLab desktop https://github.com/jupyterlab/jupyterlab-desktop/releases

This is a cross-platform desktop application for JupyterLab. You can find the user guide at the following link https://github.com/jupyterlab/jupyterlab-desktop/blob/master/user-guide.md

## Managing Python packages (install, remove, update, clean)

The following are the basic commands for installing, removing and and keep your Python libraries up to date.

```
list all packages and the versions installed in a specific environment:
>conda list

install a new package in a specific environment:
>conda install <name of the package>

uninstall a package
>conda remove <name of the package>

update a specific package
>conda update <name of the package>

update all packages in the environment ensuring compatibility
>conda update --all

clean all outdated packages (by default conda does not delete
previous versions of packages/libraries when upgrading).
>conda clean --all
```




## More on conda environments

TODO

```
list all environments
>conda env list
```



### Create  and remove an environment

to create a new environment using conda the general procedure is as follows (in the anaconda prompt)

``>conda create --name <name of my env> <list of packages>``

> note: you can use ``-n`` instead of ``--name`` if preferred 

some examples below

```
create an environment named "main" with the last version of Python supported by conda
>conda create -n main python

create an environment with a specific version of Python
>conda create --n new_env python=3.8.1

create an environment named "SCIENV" with the libraries numpy, scipy, matplolib and jupyterlab (conda will include all the necessary dependencies)
>conda create --n SCIENV numpy scipy matplolib jupyterlab

create an environment named "image" with the library scikit-image and all the neccesary dependencies
>conda create --n image scikit-image

remove an existing environment
>conda env remove -n <ENV NAME>
```



More info here: https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html

### Using environment.ylm (YALM) files

An ``environment.ylm`` file is used to specify the dependencies for a Python project in conjunction with the ``conda`` package manager. It is a plain text file that looks like this:

![image-20221215134600921](https://github.com/marcoalopez/Python_course/blob/main/img/image-20221215134600921.png?raw=true)

These files are a useful way to share Python environments and ensure, for example, that anyone else using your code does so in the same environment as you regardless of the operating system or machine where the code runs. 

To create a conda environment using an ``environment.ylm`` file from the command lines use (if you are in the folder containing the ``environment.ylm`` otherwise you will have to specify the path)

``>conda env create -f environment.yml``

This will create a new conda environment called with the name defined within the ``environment.ylm`` file. 

To create an ``environment.ylm`` file from a specific conda environment do as follows

```
>conda activate my_env
>conda env export > environment.yml
```

This command will export the list of packages and their versions that are installed in the current active conda environment so that you can quickly share it with anyone.

> 👉 Sharing Conda environments with other researchers facilitates reproducibility in research. So we encourage you to create and share an environment.yml file that describes the Python environment in which you have conducted the data analysis every time you make a scientific publication.
