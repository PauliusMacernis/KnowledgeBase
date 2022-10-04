All the bellow applies to Linux (have been using Ubuntu 22.04), it will most likely work with macos as well.  

# Anaconda

Anaconda is a distribution of packages built for data science. It comes with conda, a package and environment manager. See https://anaconda.org/  
Anaconda is a program to manage (install, upgrade, or uninstall) packages and environments to use with Python.  
Anaconda comes with a bunch of data science packages. Over 160 scientific packages and their dependencies are also installed. If we install Anaconda, then a basic few packages are installed by default. However, you can install any more packages, if needed.  

If you are using Anaconda, you are in the `base(root)` environment by-default.  

Steps:

1. Download: https://www.anaconda.com/products/distribution
2. Install: https://docs.anaconda.com/anaconda/install/


## Anaconda Navigator

It is a graphical user interface that helps open up any installed applications, such as Jupyter notebook or VS code editor. See https://anaconda.org/anaconda/anaconda-navigator  

`anaconda-navigator` - to Open Anaconda Navigator GUI.  


## Conda

Package, dependency and environment management for any language—Python, R, Ruby, Lua, Scala, Java, JavaScript, C/ C++, Fortran, and more.  
Along with managing packages, Conda is also a virtual environment manager. It's similar to virtualenv and pyenv, other popular environment managers.  
Installing conda will also install Python, if not already present.  
See https://docs.conda.io/en/latest/

`conda --version` - find which version of Conda is in use.

`conda upgrade conda` and `conda upgrade --all` - update all the packages in the default environment

`conda update --all` - update all packages in an environment.

`conda env list` or `conda info --envs` - list all environments

`conda create -n tea_facts python=3` - to create Python 3 environment with Conda.  

`conda create -n env_name [python=X.X] [LIST_OF_PACKAGES]` - for example, `conda create -n my_env python=3.7 numpy Keras`  
 
`conda activate tea_facts` - to activate the environment for conda >=4.6.  
 `source activate tea_facts` - to activate the environment for conda <4.6.  
  
`conda list` or `conda list -n env_name` - list the packages installed. It's also possible to check if a specific package is installed, e.g. `conda list -n env_name scipy`

`conda env export` - see all the package-names, including the Python version present in the current environment. It's possible to output the result for sharing (e.g. git): `conda env export > environment.yaml` .To load the environment in, use `conda env create -f environment.yaml`
  
`conda install numpy pandas matplotlib` - install 3 libraries (numpy and pandas - to work with the data, matplotlib - for making visualizations). Conda also automatically installs dependencies. Note: Installing pandas by itself will also install numpy since numpy is a dependency of pandas.  

`conda install jupyter notebook` - install 2 more libraries to develop the code with

`conda install numpy=1.10` - specify which version of a package you want by adding the version number, if needed.

`conda remove PACKAGE_NAME` - remove a package.

`conda update package_name` - update a package.  

`conda search *SEARCH_TERM*` - search for a package to install, e.g. `conda search '*whateveryousearch*'` (note: shell may expand the wildcard `*` before running the conda command, use single or double quotes to fix this).  

`conda install nb_conda` - installs Notebook Conda package to help manage environments in Jupyter Notebooks.

*Quite usefull:*  

- `conda create -n py3_env python=3` - create Python3 general environment, e.g. not tied to any specific project
- `conda create -n py2_env python=2` - create Python2 general environment, e.g. not tied to any specific project

Deactivate the environment:  

- `conda deactivate` - for conda >=4.6
- `source deactivate` - for conda <4.6

Remove the environment:  

`conda env remove -n env_name`  

**In case of git usage, e.g. sharing the code to public**:  

- `conda env export > environment.yaml` and then `conda env create -f environment.yaml`  


More commands: https://conda.io/projects/conda/en/latest/commands.html


# Miniconda

It's a smaller version of Anaconda. It includes Conda and Python, no preinstalled packages. Install new packages with `conda install PACKAGENAME`. Upgrade from Miniconda to Anaconda with `conda install anaconda`. See https://docs.conda.io/en/latest/miniconda.html  


# pip

The conda and pip both are the Python package managers.  
In the newer version of Anaconda/Miniconda, both pip and conda package managers are included by default.

pip comes preinstalled with the Python 2 >=2.7.9 or Python 3 >=3.4.  

The available packages available from the Anaconda distribution in conda focus on data science, whereas pip is for general use.  

Pip can install both Python and non-Python packages. Pip can install any package listed on the Python Package Index (PyPI). See https://pypi.org/  

Pip has similar functionality with `pip freeze > requirements.txt` - export the list of packages in an environment to a file, to include that file with your code. This way it's possible to easily load all the dependencies for the code. You may then install it back with `python -m pip install -r requirements.txt`, see https://docs.python.org/3/tutorial/venv.html    

`pip --version` - check which pip version is installed.  

**In case of git usage, e.g. sharing the code to public**:  

- `pip freeze > requirements.txt` and then `python -m pip install -r requirements.txt`  

- pip vs. conda: https://jakevdp.github.io/blog/2016/08/25/conda-myths-and-misconceptions/  


# A Python environment

comprises a particular version of:  

- Python interpreter,
- Python-packages
- The utility scripts, e.g. pip


# Jupyter Notebooks

The notebook is a web application that allows you to combine explanatory text, math equations, code, and visualizations all in one easily sharable document. **Notebooks are also rendered automatically on GitHub.**, e.g. https://github.com/mcleonard/blog_posts/blob/master/body_fat_percentage.ipynb  

Notebooks are a form of literate programming proposed by Donald Knuth in 1984. See http://www.literateprogramming.com/  
**Just a small aside: recently, this idea of literate programming has been extended to a whole programming language, Eve.** See http://witheve.com/  

List of available kernels for Jupyter: https://github.com/jupyter/jupyter/wiki/Jupyter-kernels  

`jupyter notebook` - run it. If the default port 8888 is taken then the server will run on the next free port (incremented by 1), e.g. http://localhost:8888/ , then http://localhost:8889/ , then http://localhost:8890/ , etc.  


Useful shortcuts:  

- `ctrl` + `enter`
- `shift` + `enter`
- `shift` + `tab`
- `shift` + `tab` (twice)
- `A` (while in a command mode) - create a cell above the current cell
- `B` - create a cell below the currently selected cell
- `Y` - change from Markdown to a code cell
- `M` - switch from code to Markdown
- `L` - turn on line numbers
- `D` + `D` (aka. click `D` twice) - delete the cell
- `S` - save the book
- `Shift` + `Ctrl` + `P` - bring the shortcuts menu (do not work on Firefix and Edge)
- `S` - see the shortcuts  

Off-topic (on markdown + math):  

$y = mx + b$

$$
y = \frac{a}{b+c}
$$

for more info: https://latex-tutorial.com/  

