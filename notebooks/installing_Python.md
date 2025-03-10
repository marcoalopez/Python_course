# How to install Python for Data Science using Miniconda

We will use a free environment management system called **conda** to install Python and the necessary scientific libraries for the course. The conda management system allows to install, run, and update Python packages while ensuring compatibility between different package versions on your machine. It also allows to efficiently manage Python environments, which are essentially independent Python installations. More details on this later.

## Install Python, Python scientific libraries, and Jupyter Lab using Miniconda

For this course, we will use Miniconda which allows us to manage Python packages through a console with a minimal installation (don't be scared, it's simpler than it sounds).

1. Go to https://docs.conda.io/projects/miniconda/en/latest/ and download the latest version of miniconda for your operating system.

2. Install Miniconda following the instructions.

> [!NOTE]
> An alternative is to download and install the [Anaconda Python distribution](https://docs.anaconda.com/free/anaconda/install/) that contains more than 250 scientific packages (> 5 Gb of disk space) including those needed for the course. Since during the course we won't be using most of the scientific libraries that come with the default Anaconda distribution (e.g. machine learning libraries, etc.), we recommend using Miniconda instead.

3. Open the **Anaconda Prompt** and a console will pop up. You will see something like the line below (the path may vary depending on the file system of your operating system)

   ```
   (base) C:\Users\Marco>
   ```

4. First, make sure you have the latest version of **conda** installed. To do this, type the following command:

   ```
   > conda update conda
   ```
   and update if necessary (👉 tip: do this often). 

5. If you have been paying attention, you will see that the current line in the console says "base" in parentheses. This means that you are in a Python environment called "base". A wise strategy is to not install anything in this environment other than the standard Python libraries that have already been added during the Miniconda installation process. If you are curious, you can see which libraries these are by entering the command ``conda list``. Our strategy here will be to create a new Python environment  called "course" and install there all the scientific libraries that we will use during the course. To do this, we will enter the following command:

   ```
   > conda create --name course python
   ```

6. Once finished, use the command ``conda env list`` and you will see two environments listed, "base" and "course", and an asterisk indicating that "base" is the currently active environment. To install the Python libraries needed in the "course" environment, we need to activate it first, so we type ``activate course``. Now you will see the word "course" in parentheses, indicating that "course" is now the active environment.

7. Next, we proceed to install the libraries needed for the course. Instead of doing it one by one, we will do it in a single line as follows (you can paste and copy the command directly into your console)

   ```
   >conda install numpy scipy pandas matplotlib jupyterlab
   ```

   and say yes to all. Conda will install the chosen libraries/packages and all the necessary dependencies. Once finished, you're done.

8. Now you can start Jupyter Lab by typing ``jupyter lab`` in the console and it will open the application in your default browser. We will see later how to work with Jupyter Notebooks in Jupyter Lab. The most important thing is that the application runs.

9. Once the above installation process is complete, we will follow the same procedure to work with Jupyter notebooks during the course:
	- Open the Anaconda Prompt (miniconda)
	- activate the environment "course" using ``activate course``
	- launch Jupyter lab using ``jupyter lab``
	

We will learn how to use Jupyter Lab properly during the course.

> [!TIP]
> **Using a dedicated application to work with Jupyter notebooks**
>
> If you prefer to use a dedicated application instead of opening Jupyter notebooks in your default browser, there are several alternatives. Here we will mention two free alternatives:
>
> - **Visual Studio Code** (a.k.a. vscode):  https://code.visualstudio.com/
>
> This is a free code editor that can be used with a variety of programming languages including Python and supports Jupyter notebooks via extensions. As an advantage over vanilla Jupyter Lab, it has a handy variable browser. More detailed instructions on how to use Jupyter notebooks in vscode at the following link https://code.visualstudio.com/docs/datascience/jupyter-notebooks
>
> - **JupyterLab desktop**: https://github.com/jupyterlab/jupyterlab-desktop/releases
>
> This is a cross-platform desktop application for Jupyter Lab. It is exactly the same application that opens in the browser, but in an encapsulated application. You can find the user guide at the following link https://github.com/jupyterlab/jupyterlab-desktop/blob/master/user-guide.md


## Managing Python packages (install, remove, update, clean)

The following are the basic commands for installing, removing and and keep your Python libraries up to date.

```
list all Python packages and the versions installed in a specific environment:
> conda list

install a new package in a specific environment:
> conda install <name(s) of the package(s)>

uninstall a package
> conda remove <name of the package>

update a specific package
> conda update <name of the package>

update all packages in the environment ensuring compatibility
> conda update --all

clean all outdated packages (by default conda does not delete
previous versions of packages/libraries when upgrading).
> conda clean --all
```




## More on conda/Python environments

TODO

Environments enables you to have multiple versions of Python or scientific packages installed on your computer at the same time. This is useful, for example, to test a script on different versions of Python and any other Python library, or to keep separate different scientific libraries that may work with different Python versions, etc.

```
list all existing environments
>conda env list
```

### Create  and remove an environment

to create a new environment using conda the general procedure is as follows (in the anaconda prompt)

``>conda create --name <name of my env> <list of packages>``

> you can use ``-n`` instead of ``--name`` if preferred 

some examples below

```markdown
create an environment named "main" with the last version of Python supported by conda
>conda create --name main python

create an environment with a specific version of Python
>conda create --name new_env python=3.8.1

create an environment named "SCIENV" with the libraries numpy, scipy, matplolib and jupyterlab (conda will take care of including all the necessary dependencies)
>conda create --name SCIENV numpy scipy matplolib jupyterlab

create an environment named "image" with the library scikit-image and all the neccesary dependencies
>conda create --name image scikit-image

remove an existing environment
>conda env remove --name <ENV NAME>
or
>conda remove --name <ENV NAME> --all
```



More info here: https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html

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
