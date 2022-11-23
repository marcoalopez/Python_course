# How to install Python for Data Science using anaconda

[TOC]

To install Python and the necessary scientific libraries we are going to use an open-source package and environment management system called **conda**. Conda serves to install, run, and update Python packages while making sure there are no incompatibilities between the versions of the packages you install. Also to manage (create, delete, and change), between environments on your local computer. Simply put, environments are Python installations that work independently so that you can have different versions of Python or other packages installed on your computer at the same time to test your scripts.

## Install Python and conda using miniconda

1. Go to https://docs.conda.io/en/latest/miniconda.html and download the latest version of miniconda for your operating system.

2. Install miniconda

3. Open the **Anaconda Prompt (miniconda)** and a console will pop up. You will see something similar to the following

   ```
   (base) C:\Users\Marco>
   ```

   this may change slightly depending on the file system of your operating system.

4. First make sure you have the latest version of **conda** installed, which is the python package manager. To do this, enter the following command:

   ```
   conda update conda
   ```
   and update if necessary. 

5. If you have been paying attention, you will see that the current line of the console says "base" in parentheses. This means that you are in the base Python environment. A wise strategy is to install nothing in this environment apart from the default Python libraries that were already added during the miniconda installation process. You can see which libraries using  ``conda list`` if you are curious. Our strategy will be to create a new Python environment, which we will call "main" and install all the libraries we are going to use in the course. For this we use the following command:

   ```
   >>> conda create --name main python
   ```

6. Once finished, use the command ``conda env list`` and you will see listed two environments, base and main, and an asterisk indicating that "base" is the current active environment. To install the Python libraries needed for the course we first have to activate the "main" environment, so we enter ``activate main``. Now you will see in parentheses the word "main" instead of "base" indicating that we are in the environment "main".

7. Then we proceed to install the libraries that we will use during the course. Instead of doing it one by one, we will do it in a single line as follows (you can paste and copy in your console)

   ```
   >>> conda install numpy scipy pandas matplotlib jupyterlab
   ```

   and say yes to all. Conda will install the chosen libraries and all the necessary dependencies. Once finished you're done.

8. Now you can launch Jupyter lab by simply typing ``jupyter lab`` in the console and it will open the application in your default browser. We will see later how to work with Jupyter lab. The important thing is that the application has been launched.

9. Once the above installation process is done, we will proceed in the same way to launch Jupyter lab from scratch:
	- Open the Anaconda Prompt (miniconda)
	- activate the environment "main" using ``activate main``
	- launch Jupyter lab using ``jupyter lab``

## Manage Python packages (install, remove, update, clean)

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




## More on conda environments managements

TODO

```
# list all environments
conda env list
```



### Create an environment

to create a new environment using conda the general procedure is as follows (in the anaconda prompt)

``conda create --name nameofmyenv <list of packages>``

some examples below

```
# create an environment with the last version of Python supported by conda
>>> conda create --name myenv python
# or 
>>> conda create -n myenv python

# create an environment with a specific version of Python
conda create --name new_env python=3.10

# create an environment with the libraries numpy, scipy, matplolib and jupyterlab (conda # # will include all the necessary dependencies)
>>> conda create --name myscienv numpy scipy matplolib jupyterlab

# create an environment with the library scikit-image and all the neccesary dependencies
>>> conda create --name image scikit-image
```

### Using a environment.ylm file

``conda env create -f environment.yml``



