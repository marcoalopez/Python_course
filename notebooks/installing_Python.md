# Installing Python for Scientific Research Using Miniconda

This tutorial guides you through installing Python using Miniconda, a lightweight Python installer. It is intended for undergraduate and PhD students with little or no experience using Python. We'll focus on setting up a clean, reproducible environment suitable for data analysis and scientific computing.

[TOC]

## 1. Why Miniconda?

Python is widely used in scientific research. The Conda ecosystem, which includes Anaconda and Miniconda, is a package and environment manager that simplifies the installation and management of Python libraries. It ensures compatibility between packages and allows you to create isolated environments for different projects. This prevents conflicts and keeps your system clean.

Miniconda is a minimal installer for Conda. It includes the Conda package manager and Python but leaves out the hundreds of scientific libraries that come bundled with the Anaconda distribution. This makes Miniconda more lightweight and customizable.

## 2. Installing Miniconda

1. Go to the [Miniconda installation page](https://www.anaconda.com/docs/getting-started/miniconda/main) or the Miniconda repository at https://repo.anaconda.com/miniconda/
2. Download the installer for your operating system (Windows, macOS, or Linux).

#### On windows

3. Run the downloaded `.exe` file and follow the on-screen instructions.

#### On macOS/Linux

3. If you downloaded the `.pkg` file (Graphical installer only on macOS) run the file and follow the on-screen instructions.
3.  If you downloaded the `.sh` file, open a terminal and run the following commands:

```bash
# macOS Apple silicon
mkdir -p ~/miniconda3
curl https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh -o ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh

# macOS Intel
mkdir -p ~/miniconda3
curl https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh -o ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh

# Linux x86
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh

# Linux ARM64
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh
```

Follow the on-screen instructions.

If needed, more details on installing Miniconda here: https://www.anaconda.com/docs/getting-started/miniconda/install



> [!NOTE]
> You can also install the full Anaconda distribution, which includes over 250 scientific packages. However, it requires more than 5 GB of disk space. For this course, Miniconda is recommended because it is lightweight and sufficient for our needs.



## 3. Create a Conda Environment for the Course

After installing Miniconda, open the **Anaconda Prompt** (on Windows) or a terminal and write `conda activate`(on macOS/Linux). You should see something like (the path may vary depending on the file system of your operating system):

```
(base) C:\Users\Marco>
```

The `(base)` prefix indicates that the base environment is active. Avoid installing packages in the `base` environment. Instead, we will create a dedicated environment for the Python course.

### Step 1: Update Conda

Before proceeding, update Conda using:

```
conda update conda
```

> [!TIP]
> Run this command regularly to keep Conda up to date.

### Step 2: Create a Conda Environment

Create a new environment named `course` with the latest version of Python in the Conda repository:

```bash
conda create --name course python
```

Once created, list all environments:

```bash
conda env list
```

You should see both `base` and `course` listed. The asterisk `*` indicates the currently active environment.

### Step 3: Activate the Environment

Activate the `course` environment:

```bash
conda activate course
```

The prompt will now show `(course)` instead of `(base)`.

### Step 5: Install Scientific Libraries

Install the libraries needed for the course in one step (instead one by one):

```bash
conda install numpy scipy pandas matplotlib jupyterlab
```

Conda will resolve dependencies and install the packages.

### Step 6: Launch Jupyter Lab

Start Jupyter Lab:

```bash
jupyter lab
```

This will open Jupyter Lab in your default web browser. You’ll use this interface to write and run Python code in notebooks during the course.

### Summary

Once the above installation process is complete, we will follow the same procedure to work with Jupyter notebooks during the course:
  - Open the Anaconda Prompt (miniconda)
  - activate the environment "course" using ``activate course``
  - launch Jupyter lab using ``jupyter lab``

We will learn how to use Jupyter Lab properly during the course.



> [!TIP]
> **Using a dedicated application to work with Jupyter notebooks**
>
> If you prefer to use a dedicated application instead of opening Jupyter notebooks in your default browser, there are several alternatives. Here I mention two free alternatives:
>
> - **Visual Studio Code** (a.k.a. vscode):  https://code.visualstudio.com/
>
> This is a free code editor that can be used with a variety of programming languages including Python and supports Jupyter notebooks via extensions. As an advantage over vanilla Jupyter Lab, it has a handy variable browser and more advanced features. More detailed instructions on how to use Jupyter notebooks in vscode at the following link https://code.visualstudio.com/docs/datascience/jupyter-notebooks
>
> - **JupyterLab desktop**: https://github.com/jupyterlab/jupyterlab-desktop/releases
>
> This is a cross-platform desktop application for Jupyter Lab. It is exactly the same application that opens in the browser, but in an encapsulated application. You can find the user guide at the following link https://github.com/jupyterlab/jupyterlab-desktop/blob/master/user-guide.md



## 4. Managing Conda Environments

### 4.1 Listing, installing, removing and updating packages

```markdown
# list all Python packages and the versions installed in a specific environment:
conda list

# install a new package in a specific environment:
conda install <name of the package-s>

# uninstall a package
conda remove <name of the package>

# update a specific package
conda update <name of the package>

# update all packages in the environment ensuring compatibility
conda update --all

# clean all outdated packages (by default Conda does not delete
# previous versions of packages/libraries when upgrading).
conda clean --all
```



### 4.2 Managing environments

Conda environments let you isolate different sets of packages and Python versions. This is useful for testing, reproducibility, and avoiding conflicts. For example, you can use them to test a script on different versions of Python, or to maintain separate scientific libraries that may be compatible with different versions of Python.

```markdown
# Create a new environment with the latest Python version
conda create --name myenv python

# Create an environment with a specific Python version
conda create --name myenv python=3.11

# Create an environment with specific packages
conda create --name scienv numpy scipy matplotlib jupyterlab

# List all environments
conda env list

# Remove an environment (make sure you are not in the environment you want to remove)
conda env remove --name myenv
```

More info here: https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html

> [!TIP]
> You can use `-n` instead of `--name` for brevity.



### 4.3 Using Packages from Other Channels

Sometimes, a package is not available in the default Conda channel. This is usually done using `pip`, which is the general Python’s package installer or the channel `conda-forge`, a ommunity-maintained collection of Conda packages.

#### Case 1: using pip (Python’s package installer)

```markdown
# Create and activate a new environment (check the compatible Python version in the repository)
conda create --name customenv python
conda activate customenv

# Install using pip and follow developer instructions
pip install <package-name>
```

> [!CAUTION]
> You should never use pip to install packages into the Python environments that you use for general purposes, as this may cause compatibility issues between different versions of the environment. **Use `pip` only in isolated environments to avoid compatibility issues**.

#### Case 2: using conda-forge (community-maintained channel)

To install packages from the _conda-forge_ community channel, you must first activate it:

```markdown
# Append conda-forge to the list of channels (recommended)
conda config --append channels conda-forge
```

> [!CAUTION]
> Most online tutorials will include the following line to enable the _conda-forge_ channel: ``conda config --add channels conda-forge``. **We advise you not to do this**. Using `-add` gives `conda-forge` higher priority than the default channel, which can lead to unexpected upgrades and conflicts. Always use ``--append``.



To check or reset channel priorities:

```markdown
# Show current channels
conda config --show channels

# Describe channel priority
conda config --describe channel_priority

# Remove conda-forge if needed
conda config --remove channels conda-forge

# Re-add it safely
conda config --append channels conda-forge
```


### 4.4 Sharing and Reproducing Environments with `environment.yml`

A Conda environment can be saved and shared using an `environment.yml` file. This file lists all packages and their versions, making it easy to recreate the same environment on another machine or share it with collaborators. A YALM (.yml) file is simply a plain text file that looks like this:

![image-20221215134600921](https://github.com/marcoalopez/Python_course/blob/main/img/image-20221215134600921.png?raw=true)

#### Creating an `environment.yml` File

To export the current environment:

```markdown
# Activate the environment you want to export
conda activate myenv

# Export the environment to a file
conda env export > environment.yml
```

This creates a file named `environment.yml` in your current directory.

#### Creating an Environment from a YAML File

To recreate an environment from an `environment.yml` file:

```markdown
# Run this in the directory containing the file
conda env create -f environment.yml
```

This will create a new environment with the name and packages specified in the file.

> [!TIP]
> Sharing `environment.yml` files with your code helps ensure that others can reproduce your results exactly. This is a best practice in scientific computing.



## 5. List of common Conda commands

| Task                                                       | Command                                 |
| ---------------------------------------------------------- | --------------------------------------- |
| Create a new environment                                   | `conda create -name myenv python=3.11`  |
| Activate an environment                                    | `conda activate myenv`                  |
| List all environments                                      | `conda env list`                        |
| Install packages                                           | `conda install numpy matplotlib pandas` |
| List all the packages and their versions in an environment | `conda list`                            |
| Update all the packages in the environment                 | `conda update --all`                    |
| Obtain general information about an environment            | `conda info`                            |
