# How to install Python for Data Science using anaconda

To install Python and the necessary scientific libraries, we will use a free environment management system called **conda**. The conda management system allows you to install, run, and update Python packages while ensuring compatibility between different package versions on your machine. It also allows you to efficiently manage Python environments, which are essentially independent Python installations. This capability enables you to have multiple versions of Python or scientific packages installed on your computer at the same time. This is useful, for example, to test a script on different versions of Python and any other Python library, or to keep separate different scientific libraries that may work with different Python versions, etc.

- [Install Python and conda using miniconda](#install-python-and-conda-using-miniconda)
- [Managing Python packages (install, remove, update, clean)](#managing-python-packages--install--remove--update--clean-)
- [More on conda environments](#more-on-conda-environments)
  * [Create an environment](#create-an-environment)
  * [Using an environment.ylm file](#using-an-environmentylm-file)

## Install Python and conda using miniconda

For this course, we will install miniconda which allows us to manage Python packages through the console with a minimal installation (don't be scared, it's simpler than it sounds).

1. Go to https://docs.conda.io/en/latest/miniconda.html and download the latest version of miniconda for your operating system.

2. Install miniconda following the instructions.

3. Open the **Anaconda Prompt** and a console will pop up. You will see something like this (the path may vary depending on the file system of your operating system)

   ```
   (base) C:\Users\Marco>
   ```

4. First, make sure you have the latest version of **conda** installed. To do this, type the following command:

   ```
   >conda update conda
   ```
   and update if necessary (👉 tip: do this often). 

5. If you have been paying attention, you will see that the current line in the console says "base" in parentheses. This means that you are in a Python environment called "base". A wise strategy is to not install anything in this environment other than the standard Python libraries that have already been added during the Miniconda installation process. If you are curious, you can see which libraries these are by entering the command ``conda list``. Our strategy will be to create a new Python environment, which we will call "course", and install there all the libraries that we will use during the course. To do this, we will enter the following command:

   ```
   >conda create --name course python
   ```

6. Once finished, use the command ``conda env list`` and you will see two environments listed, "base" and "course", and an asterisk indicating that "base" is the currently active environment. To install the Python libraries needed in the "course" environment, we need to activate it first, so we type ``activate course``. Now you will see the word "course" in parentheses, indicating that "course" is now the active environment.

7. Next, we proceed to install the libraries needed for the course. Instead of doing it one by one, we will do it in a single line as follows (you can paste and copy the command directly into your console)

   ```
   >conda install numpy scipy pandas matplotlib jupyterlab
   ```

   and say yes to all. Conda will install the chosen libraries/packages and all the necessary dependencies. Once finished, you're done.

8. Now you can start Jupyter lab by typing ``jupyter lab`` in the console and it will open the application in your default browser. We will see later how to work with Jupyter lab. The most important thing is that the application is running.

9. Once the above installation process is complete, we will follow the same procedure to start Jupyter Lab from scratch:
	- Open the Anaconda Prompt (miniconda)
	- activate the environment "course" using ``activate course``
	- launch Jupyter lab using ``jupyter lab``
	

We will learn how to use Jupyter Lab in the course.

> [!TIP]
> **Using a dedicated Jupyter notebook application**
> 
> If you prefer to use a dedicated application instead of opening jupyter notebooks in your default browser, there are several alternatives. Here we will mention two:
>
> - Visual Studio Code (a.k.a. vscode)  https://code.visualstudio.com/
>
> This is a free code editor that can be used with a variety of programming languages including Python and supports Jupyter notebooks via extensions. As an advantage over Jupyter Lab, it has a variable browser by default. More detailed instructions on how to use jupyter notebooks in vscode can be found at the following link https://code.visualstudio.com/docs/datascience/jupyter-notebooks
>
> - JupyterLab desktop https://github.com/jupyterlab/jupyterlab-desktop/releases
>
> This is a cross-platform desktop application for JupyterLab. You can find the user guide at the following link https://github.com/jupyterlab/jupyterlab-desktop/blob/master/user-guide.md

> [!NOTE]
> An alternative is to download and install the [Anaconda Python distribution](https://docs.anaconda.com/free/anaconda/install/) instead of miniconda, as it contains all the scientific packages needed for the course and many more (> 5 GB of disk space). Please note that during the course we won't be using most of the libraries that come with the Anaconda distribution (e.g. machine learning libraries, etc.), so we recommend using Miniconda.

## Managing Python packages (install, remove, update, clean)

The following are the basic commands for installing, removing and and keep your Python libraries up to date.

```
list all Python packages and the versions installed in a specific environment:
>conda list

install a new package in a specific environment:
>conda install <name(s) of the package(s)>

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
list all existing environments
>conda env list
```

### Create  and remove an environment

to create a new environment using conda the general procedure is as follows (in the anaconda prompt)

``>conda create --name <name of my env> <list of packages>``

> you can use ``-n`` instead of ``--name`` if preferred 

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

> [!TIP]
> Sharing Conda environments with other researchers facilitates reproducibility in research. So we encourage you to create and share environment.yml files in which you have conducted the data analysis every time you make a scientific publication.
