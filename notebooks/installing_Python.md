# How to install Python for Data Science using anaconda



TODO



## Conda environments

TODO

``conda env list``

### Create an environment

to create a new environment using conda the general procedure is as follows (in the anaconda prompt)

``conda create --name nameofmyenv <list of packages>``

some examples below

```
create an empty environment
>>> conda create --name myenv

create an environment with the last version of Python supported by conda
>>> conda create --name myenv python

create an environment with a specific version of Python
conda create --name new_env python=3.10

create an environment with the libraries numpy, scipy, matplolib and jupyterlab (conda will include all the necessary dependencies)
>>> conda create --name myscienv numpy scipy matplolib jupyterlab

create an environment with the library scikit-image and all the neccesary dependencies
>>> conda create --name image scikit-image
```



### Once you have your environment

#### Install new packages/libraries

TODO



#### Update the...

TODO



#### Clean old...

TODO



### Using a environment.ylm file

``conda env create -f environment.yml``



