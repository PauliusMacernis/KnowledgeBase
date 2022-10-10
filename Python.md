# Wanna chalange?

- https://www.hackerrank.com/domains/python
- https://www.codewars.com/

# Python: Intro


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

`jupyter nbconvert --to FORMAT mynotebook.ipynb` - convert notebook file from JSON (native ipynb format) to something else, e.g.: HTML, LaTeX, PDF, WebPDF, Reveal.js HTML slideshow, Markdown, Ascii, reStructuredText, executable script, notebook.  For example, `pip install nbconvert` + `jupyter nbconvert --to html mynotebook.ipynb`. p.s. If you wish to install any package in conda that is not available in Anaconda distribution, such as the Airbase package, use `pip install ...` instead of `conda install ...`. More info on nbconvert: https://nbconvert.readthedocs.io/en/latest/usage.html   

## Slideshow

.nbconvert may convert to slideshows too. Slides are full slides that you move through left to right. Sub-slides show up in the slideshow by pressing up or down. Fragments are hidden at first, then appear with a button press. You can skip cells in the slideshow with Skip and Notes leaves the cell as speaker notes. Test it: `jupyter nbconvert notebook.ipynb --to slides --post serve`

Don't forget to adjust each element of the notebook in order to have slides at all. In the menu bar, click View > Cell Toolbar > Slideshow to bring up the slide cell menu on each cell.


## Useful shortcuts:  

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

## Magic:  

- `%` (line magics) and `%%` (cell magics) - magic commands are preceded with one or two percent signs. For example, set up matplotlib to work interactively in the notebook with %matplotlib. For example:
  - `%timeit` - how long it takes to execute the line
  - `%%timeit` - how long it takes to execute the entire cell
  - `%matplotlib inline` - to render figures (aka. visualizations) directly in the notebook, e.g. tweak config afterwards `%config InlineBackend.figure_format = 'retina'` 
  - `%pdb` - turn on the interactive debugger (Python kernel only), when you cause an error, you'll be able to inspect the variables in the current namespace. More info https://docs.python.org/3/library/pdb.html  

More info on magic: https://ipython.readthedocs.io/en/stable/interactive/magics.html  


# LaTeX / Markdown

$y = mx + b$

$$
y = \frac{a}{b+c}
$$

for more info: https://latex-tutorial.com/  
even more info: https://www.authorea.com/users/77723/articles/110898-how-to-write-mathematical-equations-expressions-and-symbols-with-latex-a-cheatsheet  
also: http://www.personal.ceu.hu/tex/cookbook.html#inline  


# NumPy

NumPy stands for Numerical Python and it's a fundamental package for scientific computing in Python. NumPy provides Python with an extensive math library capable of performing numerical computations. At the core of NumPy is the ndarray, where nd stands for n-dimensional. An ndarray is a multidimensional array of elements **all of the same type**. **Remember, a NumPy array is homogeneous, meaning all elements will have the same data-type**. More info: https://numpy.org/doc/stable/ ,also http://scipy-lectures.org/intro/numpy/index.html  , and https://hal.inria.fr/inria-00564007/document, and the official user guide is here: https://numpy.org/devdocs/user/index.html  

NumPy handles more data types comparing to Python: https://docs.scipy.org/doc/numpy-1.13.0/user/basics.types.html  
ndarrays can hold strings as well. https://docs.scipy.org/doc/numpy-1.13.0/reference/arrays.dtypes.html#arrays-dtypes  


# Python (and extra)

**Python is case sensitive.**

## NumPy's ndarrays / Python's lists

More info: https://numpy.org/devdocs/user/basics.creation.html#array-creation  

```
import numpy as np
x = np.array([1, 2, 3, 4, 5], [6, 7, 8, 9, 10])  // https://numpy.org/devdocs/user/absolute_beginners.html#how-to-create-a-basic-array
y = np.array([1.5, 2.2, 3.7], dtype=np.int64)
print(x)
print(type(x))              // returns a tuple representing the array dimensions. https://numpy.org/doc/stable/reference/generated/numpy.ndarray.shape.html#numpy-ndarray-shape
print('x has dimensions:', x.shape)
print('x is an object of type:', type(x))
print('The elements in x are of type:', x.dtype)
x.size                      // returns the number of elements in the array

print(y)
y.dtype

np.save('my_array', x)      // save array to my_array.npy in the current directory
z = np.load('my_array.npy)  // load array from my_array.npy
print(z)

a = np.zeros((2, 3, 4))     // The tuple (2, 3, 4) passed represents the shape of the ndarray
a.ndim
```

```
my_list = [1, 2, 3]
np.array(my_list)

x = np.zeros((3,4))
// Result:
[[0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]]

x = np.zeros((3,4), dtype=int) // default is float64
// Result:
[[0 0 0 0]
 [0 0 0 0]
 [0 0 0 0]]

x = np.ones((3,4))
// Result:
[[1. 1. 1. 1.]
 [1. 1. 1. 1.]
 [1. 1. 1. 1.]]


x = np.full((3,4), 5) // creates 3x4 matrix and fills it with 5 while datatype matches the input number (5 is int64, in the example); use dtype=.. if otherwise is needed
// Result:
[[5 5 5 5]
 [5 5 5 5]
 [5 5 5 5]]


```

Identity matrix - matrix with "1" on the main diagonal and "0"s everywhere else.

```
x = np.eye(5) // creates 5x5 identity matrix
// Result:
[[1. 0. 0. 0. 0.]
 [0. 1. 0. 0. 0.]
 [0. 0. 1. 0. 0.]
 [0. 0. 0. 1. 0.]
 [0. 0. 0. 0. 1.]]
```

Diagonal matrix - matrix with any numbers (e.g. 10, 20, 30, 50) on the main diagonal and "0"s everywhere else.

```
x = np.diag([10, 20, 30, 50])
// Result:
[[10  0  0  0]
 [ 0 20  0  0]
 [ 0  0 30  0]
 [ 0  0  0 50]]
```

```
import numpy as np

stop = 10
np.arange(stop) // generates array with integer elements from 0 to (stop-1). 
// https://numpy.org/doc/stable/reference/generated/numpy.arange.html

start = 4
stop = 10
np.arange(start, stop) // generate array with integer numbers in the range of [4 - 10)
// https://numpy.org/doc/stable/reference/generated/numpy.arange.html


start = 1
stop = 14
step = 3
np.arange(start, stop, step) // generates [1, 4, 7, 10, 13]
// https://numpy.org/doc/stable/reference/generated/numpy.arange.html

start = 0
stop = 25
step = 10
np.linspace(start, stop, step) 
print(x) // prints: [ 0.    6.25 12.5  18.75 25.  ]
// https://numpy.org/doc/stable/reference/generated/numpy.linspace.html

start = 0
stop = 25
step = 5
x = np.linspace(start, stop, step, endpoint=False)
print(x) // prints: [ 0.  5. 10. 15. 20.]
// https://numpy.org/doc/stable/reference/generated/numpy.linspace.html

x = np.arange(10)
print(x) // [0 1 2 3 4 5 6 7 8 9]

x = np.reshape(x, (2, 5))
// https://numpy.org/doc/stable/reference/generated/numpy.reshape.html#numpy.reshape
print(x)
// [[0 1 2 3 4]
// [5 6 7 8 9]]


x = np.linspace(0, 50, 10, endpoint=False).reshape(2, 5) // chaining is possible
// https://numpy.org/doc/stable/reference/generated/numpy.linspace.html
print(x)
// [[ 0.  5. 10. 15. 20.]
// [25. 30. 35. 40. 45.]]

x = np.random.random((2,3))
// create an ndarray of the given shape with random floats in the half-open interval [0.0, 1.0)
print(x)
// [[0.09452831 0.70780988 0.20044412]
// [0.35266417 0.19310732 0.405911  ]]

x = np.random.randint(4, 15, (2,3))   // [from4 to15) in shape2x3 
print(x)
// [[ 7  9 10]
// [ 6 14  8]]

```

Random numbers in 1000x1000 array with average(mean) of 0 and standard deviation of 0.1:
(aka. "bell curve"? For more info: https://numpy.org/doc/stable/reference/random/generated/numpy.random.normal.html )

```
x = np.random.normal(0, 0.1, size=(1000, 1000))   
print(x)
print('mean: ', x.mean())
print('std: ', x.std())
print('max: ', x.max())
print('min: ', x.min())
print('# positive: ', (x > 0).sum())
print('# negative: ', (x < 0).sum())


Output:
[[ 0.22211229 -0.09417173  0.09590868 ...  0.08748733 -0.02216375
  -0.15646638]
 [-0.12373573  0.00762135  0.07135402 ...  0.11676525 -0.00262865
   0.05450677]
 [ 0.01612174 -0.01643322  0.00555448 ...  0.1450942   0.20641469
  -0.1510508 ]
 ...
 [ 0.0624178   0.03178409  0.12476258 ... -0.0579193   0.00641994
  -0.12065955]
 [-0.03009055 -0.01285134 -0.03614395 ...  0.00230765  0.06574115
   0.0248936 ]
 [-0.13395959 -0.00560614  0.05915297 ...  0.04710092 -0.16712507
   0.11446455]]
mean:  -5.935283900474698e-06
std:  0.09999118165037012
max:  0.4744202231255593
min:  -0.4993062728634641
# positive:  499865
# negative:  500135

```

Note: **np.arange is inclusive-exclusive while np.linspace is inclusive-inclusive**  
Note: **np.linspace - default step is 50 elements**  
Note: **np.linspace is about getting n amount of elements that fits within start and stop range where start is inclusive and stop may be inclusive/exclusive (depends on the flag passed)**  


Create a one-dimensional array with 16 elements where values are well ordered from 2 to 32 (both inclusive) and then make this one-dimensional array be 4x4 array (aka. matrix)

```
X = np.linspace(2, 32, 4*4).reshape(4,4)
print(X)
```


# Reserved words in Python

https://docs.python.org/3/reference/lexical_analysis.html#keywords  

## Data types

```
x = int(4.7)   # x is now an integer 4
y = float(4)   # y is now a float of 4.0
```

**Because the float, or approximation, for 0.1 is actually slightly more than 0.1, when we add several of them together we can see the difference between the mathematically correct answer and the one that Python creates.** More info: https://docs.python.org/3/tutorial/floatingpoint.html  

```
>>> print(.1 + .1 + .1 == .3)
False
```

## Python style  

- Style guide: https://peps.python.org/pep-0008/
- Linter: https://atom.io/packages/linter-python-pep8  
- Why is 80 characters the 'standard' limit for code width? https://softwareengineering.stackexchange.com/questions/148677/why-is-80-characters-the-standard-limit-for-code-width  

## Python error handling

- An Exception is a problem that occurs when the code is running, but a 'Syntax Error' is a problem detected when Python checks the code before it runs it. For more information, see the Python tutorial page on Errors and Exceptions: https://docs.python.org/3/tutorial/errors.html  


## True / False  

How George Boole’s zeroes and ones changed the world:  
https://www.irishtimes.com/news/science/how-george-boole-s-zeroes-and-ones-changed-the-world-1.2014673  


# Strings

You can define a string with either double quotes " or single quotes '  

```
>>> print(first_word * 5)

HelloHelloHelloHelloHello

>>> print(len(first_word))

5

>>> first_word[0]

H

>>> first_word[1]

e
```

`len` only works on a "sequence (such as a string, bytes, tuple, list, or range) or a collection (such as a dictionary, set, or frozen set),", more info: https://docs.python.org/2/library/functions.html#len  

## Methods available:

https://docs.python.org/3/library/stdtypes.html#string-methods

## Lists

```
>>> list_of_random_things = [1, 3.4, 'a string', True]

>>> list_of_random_things[-1] 
True
>>> list_of_random_things[-2] 
a string
```

### The lower index of a slice is inclusive and the upper index is exclusive. And leaving out the lower index starts the slice at 0, while leaving out the upper index ends the slice at the end of the list.   


```
>>> list_of_random_things = [1, 3.4, 'a string', True]
>>> list_of_random_things[1:2]
[3.4]
```

```
>>> list_of_random_things[:2]
[1, 3.4]
```

```
>>> list_of_random_things[1:]
[3.4, 'a string', True]
```

```
>>> 'this' in 'this is a string'
True
>>> 'in' in 'this is a string'
True
>>> 'isa' in 'this is a string'
False
>>> 5 not in [1, 2, 3, 4, 6]
True
>>> 5 in [1, 2, 3, 4, 6]
False
```

```
>>> my_lst = [1, 2, 3, 4, 5]
>>> my_lst[0] = 'one'
>>> print(my_lst)
['one', 2, 3, 4, 5]
# lists are mutable
```

```
>>> greeting = "Hello there"
>>> greeting[0] = 'M'
ERROR!!!
# strings are immutable
```

Lists are assigned "by reference", which means having two list variables made/assigned of the same list will result to both changing if any of the two change.

`len()` returns how many elements are in a list.  
`max()` returns the greatest element of the list. How the greatest element is determined depends on what type of objects are in the list. The maximum element in a list of numbers is the largest number. The maximum element in a list of strings is the element that would occur last if the list were sorted alphabetically. This works because the the max() function is defined in terms of the greater than comparison operator. The max() function is undefined for lists that contain elements from different, incomparable types.  
`min()` returns the smallest element in a list. min is the opposite of max, which returns the largest element in a list.  
`sorted()` returns **a copy of a list** in order from smallest to largest, leaving the list unchanged. Note again that for string objects, sorted smallest to largest means sorting in alphabetical order.  

### join

```
new_str = "\n".join(["fore", "aft", "starboard", "port"])
print(new_str)
Output:

fore
aft
starboard
port
```

```
new_str = "\n".join(["fore", 1, "starboard", "port"])
print(new_str)
Output:

ERROR, we can't join integer value
```

```
new_str = "\n".join(["fore", str(1), "starboard", "port"])
print(new_str)
Output:

fore
1
starboard
port
```

### append

```
letters = ['a', 'b', 'c', 'd']
letters.append('z')
print(letters)
Output:

['a', 'b', 'c', 'd', 'z']
```

## Tuples

Immutable & Ordered

A tuple is an immutable, ordered data structure that can be indexed and sliced like a list. Tuples are defined by listing a sequence of elements separated by commas, optionally contained within parentheses: ().  

```
location = (13.4125, 103.866667)
print("Latitude:", location[0])
print("Longitude:", location[1])

dimensions = 52, 40, 100
length, width, height = dimensions
print("The dimensions are {} x {} x {}".format(length, width, height))

length, width, height = 52, 40, 100
print("The dimensions are {} x {} x {}".format(length, width, height))
```

```
tuple_a = 1, 2
tuple_b = (1, 2)

print(tuple_a == tuple_b)
print(tuple_a[1])

# True
# 2
```

## Sets

Mutable & Unordered  

A set is a mutable data structure - you can modify the elements in a set with methods like add and pop. A set is an unordered data structure, so you can't index and slice elements like a list; there is no sequence of positions to index with!  
  
One of the key properties of a set is that it only contains unique elements. So even if you create a new set with a list of elements that contains duplicates, Python will remove the duplicates when creating the set automatically.  


```
numbers = [1, 2, 6, 3, 1, 1, 6]
unique_nums = set(numbers)
print(unique_nums)
# {1, 2, 3, 6}
```


```
fruit = {"apple", "banana", "orange", "grapefruit"}  # define a set

print("watermelon" in fruit)  # check for element

fruit.add("watermelon")  # add an element
print(fruit)

print(fruit.pop())  # remove a random element
print(fruit)

Output:
False
{'grapefruit', 'orange', 'watermelon', 'banana', 'apple'}
grapefruit
{'orange', 'watermelon', 'banana', 'apple'}
```

When you pop an element from a set a **random** element is removed (remember that sets, unlike lists, are unordered so **there is no "last element"**).

## Dictionaries

Mutable  

Stores mappings of unique keys to values.  

Dictionaries are mutable, but their **keys must be of immutable type**, like strings, integers, or tuples. Lists or alike would not work! Every key in a dictionary may have different type, e.g. `random_dict = {"abc": 1, 5: "hello"}`   

Each item in a dictionary contains two parts (a key and a value), the items in a dictionary are not ordered, dictionaries may be nested.  

Because dictionaries are not ordered, they are not sortable.  

```
elements = {"hydrogen": 1, "helium": 2, "carbon": 6}
print(elements["helium"]) # 2
elements["lithium"] = 3 
print(elements)
# {'hydrogen': 1, 'carbon': 6, 'helium': 2, 'lithium': 3}

print("carbon" in elements) # True

elements["whatever"] # ERROR!!!!!
print(elements.get("whatever"))  # None

n = elements.get("dilithium")
print(n is None) # True
print(n is not None) # False

```

```
>>> elements.get('dilithium')
None
>>> elements['dilithium']
KeyError: 'dilithium'
>>> elements.get('kryptonite', 'There\'s no such element!')
"There's no such element!"
```

List a and list b are equal and identical. List c is equal to a (and b for that matter) since they have the same contents. But a and c (and b for that matter, again) point to two different objects, i.e., they aren't identical objects. **That is the difference between checking for equality vs. identity**.

```
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(a == b)
print(a is b)
print(a == c)
print(a is c)

# True
# True
# True
# False
```

```
# create and sort a list of the dictionary's keys
sorted_keys = sorted(verse_dict.keys())
```


## Lists vs. Dictionaries

A set is defined with curly braces, {}, but it isn't the only data structure that does; dictionaries do as well! However, the difference is that a set is defined as a sequence of elements separated by commas:  
`set_example = {element1, element2, element3}`  
while a dictionary is defined as a sequence of key, value pairs marked with colons, separated by commas:  
`dict_example = {key1: value1, key2: value2, key3: value3}`  

Note: if you define a variable with an empty set of curly braces like this: a = {}, Python will assign an empty dictionary to that variable. You can always use set() and dict() to define empty sets and dictionaries as well.  


## Lists, Tuples, Sets, Dictionaries

```
Data Structure	Ordered	Mutable	Constructor	    Example
List	          Yes	    Yes	    [ ] or list()	  [5.7, 4, 'yes', 5.7]
Tuple	         Yes	    No	     ( ) or tuple()	 (5.7, 4, 'yes', 5.7)
Set	           No	     Yes	    {}* or set()	   {5.7, 4, 'yes'}
Dictionary	    No	     No**	   { } or dict()	  {'Jun': 75, 'Jul': 89}
```

* You can use curly braces to define a set like this: {1, 2, 3}. However, if you leave the curly braces empty like this: {} Python will instead create an empty **dictionary**. So to create an empty set, use set().  
** A dictionary itself is mutable, but each of its individual keys must be immutable.  

# If, Elif, Else

```
if season == 'spring':
    print('plant the garden!')
elif season == 'summer':
    print('water the garden!')
elif season == 'fall':
    print('harvest the garden!')
elif season == 'winter':
    print('stay indoors!')
else:
    print('unrecognized season')
```

**Indentation - 4 spaces!!!**


Here are most of the built-in objects that are considered False in Python:  

- constants defined to be false: None and False
- zero of any numeric type: 0, 0.0, 0j, Decimal(0), Fraction(0, 1)
- empty sequences and collections: '"", (), [], {}, set(), range(0)


# For

```
cities = ['new york city', 'mountain view', 'chicago', 'los angeles']
for city in cities:
    print(city)
print("Done!")
```

```
# Creating a new list
cities = ['new york city', 'mountain view', 'chicago', 'los angeles']
capitalized_cities = []

for city in cities:
    capitalized_cities.append(city.title())
```


```
cities = ['new york city', 'mountain view', 'chicago', 'los angeles']

for index in range(len(cities)):
    cities[index] = cities[index].title()
```

```
for word in book_title:
    word_counter[word] = word_counter.get(word, 0) + 1
```

