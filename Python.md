All the bellow applies to Linux (have been using Ubuntu 22.04), it will most likely work with macos as well.  

# Anaconda

Anaconda is a distribution of packages built for data science. It comes with conda, a package and environment manager. See https://anaconda.org/  
Anaconda is a program to manage (install, upgrade, or uninstall) packages and environments to use with Python.  
Anaconda comes with a bunch of data science packages. Over 160 scientific packages and their dependencies are also installed. If we install Anaconda, then a basic few packages are installed by default. However, you can install any more packages, if needed.


## Anaconda Navigator

It is a graphical user interface that helps open up any installed applications, such as Jupyter notebook or VS code editor. See https://anaconda.org/anaconda/anaconda-navigator  


## Conda

Package, dependency and environment management for any language—Python, R, Ruby, Lua, Scala, Java, JavaScript, C/ C++, Fortran, and more. See https://docs.conda.io/en/latest/

`conda --version` - find which version of Conda is in use.

`conda create -n tea_facts python=3` - to create Python 3 environment with Conda.  
  
`source activate tea_facts` - to activate the environment.  
  
`conda list` - list the packages installed.  
  
`conda install numpy pandas matplotlib` - install 3 libraries (numpy and pandas - to work with the data, matplotlib - for making visualizations).  

`conda install jupyter notebook` - install 2 more libraries to develop the code with


# Miniconda

It's a smaller version of Anaconda. It includes Conda and Python, no preinstalled packages. Install new packages with `conda install PACKAGENAME`. Upgrade from Miniconda to Anaconda with `conda install anaconda`. See https://docs.conda.io/en/latest/miniconda.html  


