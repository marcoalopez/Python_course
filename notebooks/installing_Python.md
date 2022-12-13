# How to install Python for Data Science using anaconda

To install Python and the necessary scientific libraries we will use an open-source package and environment management system called **conda**. Conda serves to install, run, and update Python packages while making sure there are no incompatibilities between the versions of the packages in your environment. Also, to manage (create, delete, and modify) environments on your local computer. In a nutshell, environments are Python installations that work independently so you can have installed on your computer different Python versions or scientific packages at the same time. This is useful, for example, to test a script on different versions or to keep isolated different scientific libraries that may work with different Python versions, etc.

- [Install Python and conda using miniconda](#install-python-and-conda-using-miniconda)
- [Managing Python packages (install, remove, update, clean)](#managing-python-packages--install--remove--update--clean-)
- [More on conda environments](#more-on-conda-environments)
  * [Create an environment](#create-an-environment)
  * [Using an environment.ylm file](#using-an-environmentylm-file)



## Install Python and conda using miniconda

For this course, we will install miniconda which allows conda to be used via the console (don't be afraid, it's simpler than it sounds).

1. Go to https://docs.conda.io/en/latest/miniconda.html and download the latest version of miniconda for your operating system.

2. Install miniconda following the instructions.

3. Open the **Anaconda Prompt (miniconda)** and a console will pop up. You will see something similar to this

   ```
   (base) C:\Users\Marco>
   ```

   this may change slightly depending on the file system of your operating system.

4. First, make sure you have the latest version of **conda** installed. To do this, enter the following command:

   ```
   conda update conda
   ```
   and update if necessary (tip 👉 do this often). 

5. If you have been paying attention, you will see that the current line of the console says "base" in parentheses. This means that you are in the base Python environment. A wise strategy is to install nothing in this environment apart from the default Python libraries that were already added during the miniconda installation process. You can see which libraries using  ``conda list`` if you are curious. Our strategy will be to create a new Python environment, which we will call "course" and install all the libraries we are going to use during the course. For this we use the following command:

   ```
   >>> conda create --name course python
   ```

6. Once finished, use the command ``conda env list`` and you will see listed two environments, _base_ and _course_, and an asterisk indicating that "base" is the currently active environment. To install the Python libraries needed for the course we first have to activate the "course" environment, so we enter ``activate course``. Now you will see in parentheses the word "course" indicating that we are in this environment.

7. Then we proceed to install the libraries needed for the course. Instead of doing it one by one, we will do it in a single line as follows (you can paste and copy it to your console)

   ```
   >>> conda install numpy scipy pandas matplotlib jupyterlab
   ```

   and say yes to all. Conda will install the chosen libraries/packages and all the necessary dependencies. Once finished, you're done.

8. Now you can launch Jupyter lab by simply typing ``jupyter lab`` in the console and it will open the application in your default browser. We will see later how to work with Jupyter lab. The important thing is that the application has been launched.

9. Once the above installation process is done, we will proceed in the same way to launch Jupyter lab from scratch:
	- Open the Anaconda Prompt (miniconda)
	- activate the environment "main" using ``activate course``
	- launch Jupyter lab using ``jupyter lab``



## Managing Python packages (install, remove, update, clean)

The following are the basic commands for installing, removing and and keep your Python libraries up to date.

```
# list all packages and the versions installed in a specific environment:
conda list

# install a new package in a specific environment:
conda install <name of the package>

# uninstall a package
conda remove <name of the package>

# update a specific package/librarie
conda update <name of the package>

# update all packages in the environment ensuring compatibility
conda update --all

# clean all outdated packages (by default conda does not delete
# previous versions of packages/libraries when upgrading).
conda clean --all

```




## More on conda environments

TODO

```
# list all environments
conda env list
```



### Create an environment

to create a new environment using conda the general procedure is as follows (in the anaconda prompt)

``conda create --name <name of my env> <list of packages>``

> note: you can use ``-n`` instead of ``--name`` if preferred 

some examples below

```
# create an environment named "main" with the last version of Python supported by conda
>>> conda create -n main python

# create an environment with a specific version of Python
conda create --name new_env python=3.8.1

# create an environment named "SCIENV" with the libraries numpy, scipy, matplolib and jupyterlab (conda will include all the necessary dependencies)
>>> conda create --name SCIENV numpy scipy matplolib jupyterlab

# create an environment with the library scikit-image and all the neccesary dependencies
>>> conda create --name image scikit-image
```



### Using YALM and environment.ylm files

TODO



Creating an environment using an *environment.yml* file

``conda env create -f environment.yml``



Exporting an environment to an *environment.yml* file

```
conda activate my_env
conda env export > environment.yml
```





