---
title: Lecture2
date: "2019-06-07T08:00:17+02:00"
url: "/slides/lecture2/"
image: "/slides/lecture2/cover.jpg"
description: ""
ratio: "16:9"
buildFuture : false
themes:
- apron
- adirondack
- descartes
classes:
- feature-math
- feature-justify
---

class: title, no-footer
background-image: url(cover.jpg)

# Hands-on Machine Learning
## Lecture2

---

class: title, no-footer, smokescreen

# Crash course on Python

---

class: compact
# Data Types
Integers (default for numbers)
```python
z = 5 / 2 # Answer is 2, integer division.
```

Floats
```python
x = 3.14
```

Booleans
```python
a = True # or False
```

Strings
- Can use `""` or `''` . For example: `"cat"` and `'cat'` is the same thing

---

class: roomy

# Basic code features

Assignment uses .color-orange[**`=`**] and comparison uses .color-orange[**`==`**]

- For numbers .color-orange[`+ - * / %`] are as expected.
    - Special use of `+` for string concatenation.
- Logical operators are words (`and`, `or`, `not`) 
- The first assignment to a variable creates it.
- Variable types don’t need to be declared.
	- Python figures out the variable types on its own.
- .color-orange[`#`] inserts a comment

---
class: compact
# Beware of the whitespace!
Whitespace and indentation (placement of newlines) is crucial in python
- The first line with less indentation is outside of the block
- The first line with more indentation starts a nested block
- Often a colon appears at the start of a new block (e.g for function and class definitions)

```
if z == 3.45 or y == 'Hello':
    x = x + 1         #Inside the if statement
    print(x)
    y = y + ' World' # Still inside
    print(y)

k = y+' outside' # Outside if
print(k)
```

---
# Type casting

You can check the type of an expression by the `type` command:
```python
type(2)
type(True)
```
You can change the type of an expression in Python; this is called **type-casting** 
- E.g: You can convert an `int` to a `float` or a `string` to an `int`

```Python
float(2) : 2.0
int("1") : 1
```

---

# Mathematical operations

Common mathematical operations are supported
- Addition, subtraction, multiplication division

```python
123 + 22 + 64 + 35  :   244
10 - 5              :   5
10 * 5              :   50
25 / 5              :   5.0  # Division results in float
25 / 4              :   6.25
25 // 4             :   6  # Division results in int
```

---

# Operations on strings

```python
# Select elements of a string in steps
a_name = 'Leonardo Da Vinci'
a_name[::2]

# Length of string
len(a_name)        :  17

# Adding strings
a_name + ' was a polymath'
```

Backslashes: `(\t \n \\)` for tab, newline and `\`. Try out useful commands:
```python
upper(), replace(<input>,<replacement>), find(<string>), lower(), strip()
```

---

# Operations on strings

Split function

```Python
name_toSplit = 'Leonardo Da Vinci'
name_toSplit.split() # splits by space and produces a list
name_toSplit.split('a') # splits by 'a' and produces a list
```

---

# Tuples
**Tuples** are an ordered sequence of comma separated elements within `()`
```python
a = ('python', 5.3, 10)

# Select an element
a[0]    :  'python'
a[-3]   :  'python'

# add two tuples together
b=('conda', 88, 55)
a + b   :   ('python', 5.3, 10, 'conda', 88, 55)
```

Tuples are **immutable**, which means we can't change them.<br> i.e b[0] = 1 does not work!

---

# Tuples

```python
# sorting by number
num_muons = (10,9,6,5,10,8,9,6,2)
sorted(num_muons)
```
Tuples can contain other tuples. Then you can access deeper elements by more []
```python
c = (10, 55, ('conda','anaconda','miniconda'), 3.14 )
print(c[2])
print(c[2][1])
print(c[2][1][0])
```

---

# Lists

Same as **tuples** except:
- comma separated elements within `[]`. 
- They are **mutable** which means you change them, i.e b[0] = 1 is allowed!

--

When we set one variable, `b` equal to `a`, both `a` and `b` are referencing the same list.
```python
a = [1, 2, 3] # a now references the list [1, 2, 3]
b = a # b now references what a references
a.append(4) # this changes the list a references
print (a)
print (b) 
```

---

# Lists

But you can override this behaviour is you create a clone of a list
```python
c = a[:] # b is a clone of a and points to different list
a.append(5) # this changes the list a references
print (a)
print (c) 
```

---

class: compact
# Sets

Sets are collections like lists and tuples but they are unordered:
- They do not record element position only have unique elements.
- They have only one of a particular element

```python
a = {'one','two','two','three'}
print (a)

{'one', 'two', 'three'}
```

Convert a list to a set using the `set()` function
```python

L= [1, 2, 3, 4, 5, 5, 5]
S = set(L)

{1, 2, 3, 4, 5}
```

---

# Operations on sets

Intersection
```python
set_1 = {'green','red','blue'}
set_2 = {'green','red','magenta','yellow'}
set_3 = set_1 & set_2
```

--

Union and subset
```python
set_3 = set_1.union(set_2) # Should return {'blue', 'green', 'magenta', 'red', 'yellow'}

set_1.issubset(set_3) # Should return True
```

---

# Dictionaries

Dictionaries store a mapping between a set of keys and a set of values.
- Keys should be unique and immutable
- Values can be any type or duplicates

You can define, modify, view, lookup, and delete the key-value pairs in the dictionary.
```
d = {'user':'dina', 'pwd':1234}
```
| key | value |
| --- | --- |
| `user` | `'dina'` |
| `pwd`  | `1234` |

---
class: compact
# Dictionaries
```Python
# replace a value of a key
d['user'] = 'dinos'

# add an element
d['age'] = 42

# list keys, values, pairs of keys-values
d.keys()  # List of keys
d.values()
d.items()

# delete an item 
del d['user']

# delete all
d.clear()
```

---

# Conditional statements

The `if` and `else` syntax is like this:
```
temperature=21
if temperature>17 and temperature<25:
	print('Not too warm not too cold')
elif temperature <= 17:
	print('It is cold')
else:
	print('Too hot!')
```

---
class: col-2, compact
# Loops
#### `for` loops
Notice the `enumerate` and `range`

```python
masses = [100,200,300]
for mass in masses:
	print('Mass',mass)

for i,mass in enumerate(masses):
	print('Point',i,'Mass',mass)

for i in range(0,10):
	print(i)

```

#### `while` loops
```
i = 1
while i < 6:
  print(i)
  i += 1
```

---

# Functions


```python
def my_test():
    var = 3
    print('In my_test',var)

my_test()
# print('Outside my_test',var) 
```

> `print(var)` creates a crash because `var` is out of scope. Try putting `global var` in the function and see what happens

---

# Classes

```python
class Circle(object):
    def __init__(self,radius,color):
        self.radius = radius
        self.color = color
```

___self___ : represents the instance of the class. Gives access to attributes and methods of the class

___init___ : like as a constructor in object oriented concepts. It is called when an object is created and initializes the attributes of the class

---

class: title, smokescreen

# NumPy
---

# What is Numpy?

.color-dodgerblue[Numpy](.color-dodgerblue[**Num**]erical .color-dodgerblue[**Py**]thon) is a library for scientific computing.
It contains among other things:
- a powerful N-dimensional array object
- sophisticated (broadcasting) functions
- useful linear algebra, Fourier transform, and random number capabilities

It has advantages like speed an memory and is also the basis for .color-dodgerblue[**pandas**]

---

# What is Numpy?

A .color-dodgerblue["numpy"] array or .color-dodgerblue["ndarray"] is similar to a list. It's usually fixed in size and each
element is of the same type

Create an ndarray
```Py
import numpy as np
a = np.array([1, 2, 3, 4, 5])

# you can also define the datatype of the array at creation. Look what happens in you select an int and have float values in it
another_array = np.array([3.14, 5, 6.4], dtype=np.int64)
print(another_array)
print(another_array.dtype)

# fix random seed for reproducibility
np.random.seed(123)
```

---
class: 

# Mathematical operations on arrays

It is very fast to do mathematical computations with numpy arrays rather than in simple python lists
```
v = np.array([1,0])
u = np.array([0,1])

# Addition
z = v+u

# adding a constant
w = z + 1 

# multiplication by scalar
w = 2*z 
```

---

# Mathematical operations on arrays

```
# multiplication of 2 arrays (done element wise)
q = z * w 
```
dot product is done as<br>
`q = np.dot(z,w)` i.e $$z^{T}w$$


---
class:  compact,img-right

# Useful numpy functions

>a = np.array([1, 2, 3, 4, 5])<br>
a.mean()<br>
a.max()<br>
np.pi <br>
np.sin(a)<br>

--

>\# very useful when defining bins in plots<br>
x = np.linspace(0.2 * np.pi,100) <br>

--

>y = np.sin(x)<br>
import matplotlib.pyplot as plt<br>
%matplotlib inline<br>
plt.plot(x,y)<br>

--

![](sin.png# b-4 absolute w-6)

---

class: compact

# 2-D arrays

You can also define 2 dimensional arrays in numpy. For example:
```
a=np.array([ [1,2,3], [4,5,6], [7,8,9] ])

[[1 2 3]
 [4 5 6]
 [7 8 9]]

a.ndim # number of nested lists - array dimension
2

a.shape # returns a tuple (num of nested lists(rows), num of elements in each list(columns))
(3,3)

a.size # number of elements ( rows x columns)
9
```
---
class: compact

# 2-D arrays


**You can think of a ROOT TTree containing variables as a NumPy array where every .color-red[row] is a different .color-red[event] and every .color-dodgerblue[column] is a different .color-dodgerblue[variable]**
```python
a=np.array([ [1,2,3], [4,5,6], [7,8,9] ])
b=np.array([ [10,11,12], [13,14,15], [16,17,18] ])

Try:
a+b
a-b
a*b
2*a
```
But if you want pure matrix multiplication you have to do:
```
np.dot(a,b)
```

---

class: title, smokescreen

# Pandas

---
class: compact
#Pandas DataFrames
http://pandas.pydata.org/

Pandas DF is an open source library providing high-performance, easy-to-use data structures and data analysis tools in Python. 

It is built on top of .color-dodgerblue[NumPy] 

Main advantages:
- Manipulation of .color-darkturquoise[heterogeneous data types] in an intuitive fashion
- Can combine large datasets using .color-darkorange[merge and join]
- Provides built-in .color-darkturquoise[visualizations]
- Descriptive .color-darkorange[statistics], by using simple functions --> simplifies exploratory data analysis
- Handles .color-darkturquoise[missing data] and data pivoting, easy data .color-darkturquoise[sorting], fast generation of data plots,and .color-darkorange[Boolean indexing]


---
#Pandas DataFrames

![](pandas_logo.png# center)

Basic Types: Pandas .color-limegreen[Series] and Pandas .color-mediumorchid[DataFrames]
- A .color-limegreen[series] is one one-dimensional array-like object that provides many ways to index data and supports many data types
- A .color-mediumorchid[DataFrame] is a 2-D data structure that supports heterogeneous data with labeled axis for rows and columns.
	- a container for series objects, where each row is a series.


---

class: compact
#Creating pandas

#### creating a Series
```
# Create a panda series. Index is 0,1,...
my_series = pd.Series(data=[100, 200, 300, 400])

# Custom indicies
my_series = pd.Series(data=[100, 200, 300, 400], index=['jet1', 'jet2', 'jet3', 'jet4'])

# but also different type of data
my_series = pd.Series(data=[100, 'abc', 300, 'jkl'], index=['jet1', 'jet2', 'jet3', 'jet4'])
```
#### List the indices
```
my_series.index
```

---

# Indices and basic selection accessing methods

1.  Access element at index `jet2`
```
my_series['jet2']
```
1. Access element by index with .color-limegreen[loc] (.color-red[recommended!!])
```
my_series.loc['jet2']
```
1. Access element by row-column number with .color-limegreen[iloc] (.color-red[recommended!!])
```
my_series.iloc[1]
```
.center[.color-darkcyan[More examples in the Jupyter Notebook]]

---
class: compact
# Methods to Import and Export Data

#### Import
- read_csv
- read_json
- read_html
- read_sql_query, read_sql_table
- read_pickle

#### Export
- to_csv
- to_excel
- to_json
- to_pickle


---

class: title, smokescreen

# Machine Learning

---

# What is Machine Learning?

Arthur Samuel (1959)
> Field of study that gives computers the ability to learn without being explicitly programmed.

Tom Mitchell (1998)
>A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E.
---
class: col-2,roomy

# Where is ML used?

- Natural Language Processing

--
- Speech and handwriting recognition

--
- Object recognition and computer vision

--
- Fraud detection

--
- Financial market analysis

--
- Search engines

--
- Spam and virus detection

--
- Medical diagnosis

--
- Robotics control

--
- Automation: energy usage, systems control, video games, self-driving cars

--
- Advertising

--
- Data Science

--
- Physics 

---

# Categories of ML

- Classification
	- Goal: Predict results in discrete categories

--
- Regression
	- Goal: Predict a numeric value. Predict results within a continuous output, meaning that we are trying to map input variables to some continuous function

--
- Cluster Analysis
	- Goal: Organize similar items into groups

--
- Dimensionality reduction
	- Goal: Reducing the number of variables under consideration, by obtaining a set of principal variables


---

# Learning techniques
**Learning**: estimate statistical model from data

- **Supervised**
--

	- The target (what model is predicting) is provided, i.e we know the relationship between the input and the output
	- The data is "Labeled"
		- Regression
		- Classification
--

- **Unsupervised**
--

	- The target is unknown or unavailable
	- The data is "Unlabeled"
		- Cluster analysis 
		- Dimensionality reduction

---

class: img-right, compact

# Terminology 

![](Samples-Features.png# center ft )
![](Categories.png#  b-10pct r-10pct w-30pct absolute )

.color-forestgreen[Sample]: A.k.a Row, event, record, instance

.color-orangered[Variable]: A.k.a Columns, Features, dimension, attribute

.color-deepskyblue[Variables' Data types]: Numeric, categorical, strings, ...

\\(x_i\\) : .color-orangered[input] variables<br>
\\(y_i\\) : .color-navy[output] or target variable<br>
\\((x_i, y_i)\\) : training example<br>
\\( \\{ (x_i, y_i); i = 1, . . .,m \\} \\) : training set of `m` examples

---

class: img-right

# Supervised Learning - How does it work?

![](LearningFlowGeneral.png# center )

Our goal is, given a training set, to learn a function .color-darkorchid[**`h`**] :  \\(X \rightarrow Y\\) so that .color-darkorchid[**`h(x)`**] is a good predictor for the corresponding value of .color-limegreen[`y`]. 

.color-darkorchid[**`h(x)`**]  is called hypothesis(model).
--

When .color-limegreen[`y`] is continuous, the learning problem is a .color-orange[regression] problem.

---

class: img-right

# Supervised Learning - How does it work?

![](LearningFlow.png# center )

Our goal is, given a training set, to learn a function .color-darkorchid[**`h`**] :  \\(X \rightarrow Y\\) so that .color-darkorchid[**`h(x)`**] is a good predictor for the corresponding value of .color-limegreen[`y`]. 

.color-darkorchid[**`h(x)`**]  is called hypothesis(model).

When .color-limegreen[`y`] can take on 2 discrete values the learning problem is a .color-orange[binary classification] problem.

---

class: img-right

# Supervised Learning - How does it work?

![](LearningFlow-MultiClass.png# center )

Our goal is, given a training set, to learn a function .color-darkorchid[**`h`**] :  \\(X \rightarrow Y\\) so that .color-darkorchid[**`h(x)`**] is a good predictor for the corresponding value of .color-limegreen[`y`]. 

.color-darkorchid[**`h(x)`**]  is called hypothesis(model).

When .color-limegreen[`y`] can take on more than 2 discrete values the learning problem is a .color-orange[multi-class classification] problem.

---

class: img-right

# Supervised Learning - Example of a model

![](Scatter-withX.png# center )

Lets say you have data of a movie ranking in IMDB and the views of this movie per month on Netflix 

Say you work for Netflix and want to predict the views of a movie if shown with ranking 7.8

---

class: img-right

# Supervised Learning - Example of a model

![](Scatter-withXandLine.png# center )

Lets say you have data of a movie ranking in IMDB and the views of this movie per month on Netflix 

Say you work for Netflix and want to predict the views of a movie if shown with ranking 7.8

A learning algorithm might want to put a .color-forestgreen[straight line] through the data

---

class: img-right

# Supervised Learning - Example of a model

![](Scatter-withXandCurve.png# center )

Lets say you have data of a movie ranking in IMDB and the views of this movie per month on Netflix 

Say you work for Netflix and want to predict the views of a movie if shown with ranking 7.8

A learning algorithm might want to put a straight line through the data

A better algorithm might fit a .color-forestgreen[quadratic function], or a .color-forestgreen[second-order polynomial] to this data

---
class: compact
# Supervised Learning - Building an ML model

![](FlowWithLoss.png# center h-5)

Model parameters are adjusted during model training to change input-output mapping.

- Design function with adjustable parameters
- Design a Loss function
- Find best parameters which minimize loss

---
class: compact
# Supervised Learning - Building an ML model

![](FlowWithLoss.png# center h-5)

Model parameters are adjusted during model training to change input-output mapping

- Use a labeled training-set to compute loss
- Adjust parameters to reduce loss function
- Repeat until parameters stabilize
- Estimate final performance on test-set

---
class: compact,col-2
# Colors 1
.color-aliceblue[aliceblue]
.color-antiquewhite[antiquewhite]
.color-aqua[aqua]
.color-aquamarine[aquamarine]
.color-azure[azure]
.color-beige[beige]
.color-bisque[bisque]
.color-black[black]
.color-blanchedalmond[blanchedalmond]
.color-blue[blue]
.color-blueviolet[blueviolet]
.color-brown[brown]
.color-burlywood[burlywood]
.color-cadetblue[cadetblue]
.color-chartreuse[chartreuse]
.color-chocolate[chocolate]
.color-coral[coral]
.color-cornflowerblue[cornflowerblue]
.color-cornsilk[cornsilk]
.color-crimson[crimson]
.color-cyan[cyan]
.color-darkblue[darkblue]
.color-darkcyan[darkcyan]
.color-darkgoldenrod[darkgoldenrod]
.color-darkgray[darkgray]
.color-darkgreen[darkgreen]
.color-darkgrey[darkgrey]
.color-darkkhaki[darkkhaki]
.color-darkmagenta[darkmagenta]
.color-darkolivegreen[darkolivegreen]
.color-darkorange[darkorange]
.color-darkorchid[darkorchid]
.color-darkred[darkred]
.color-darksalmon[darksalmon]
.color-darkseagreen[darkseagreen]
.color-darkslateblue[darkslateblue]
.color-darkslategray[darkslategray]
.color-darkslategrey[darkslategrey]
.color-darkturquoise[darkturquoise]
.color-darkviolet[darkviolet]
.color-deeppink[deeppink]
.color-deepskyblue[deepskyblue]
.color-dimgray[dimgray]
.color-dimgrey[dimgrey]
.color-dodgerblue[dodgerblue]
.color-firebrick[firebrick]
.color-floralwhite[floralwhite]
.color-forestgreen[forestgreen]
.color-fuchsia[fuchsia]
.color-gainsboro[gainsboro]
.color-ghostwhite[ghostwhite]
.color-gold[gold]
.color-goldenrod[goldenrod]
.color-gray[gray]
.color-green[green]
.color-greenyellow[greenyellow]
.color-grey[grey]
.color-honeydew[honeydew]
.color-hotpink[hotpink]
.color-indianred[indianred]
.color-indigo[indigo]
.color-ivory[ivory]
.color-khaki[khaki]
.color-lavender[lavender]
.color-lavenderblush[lavenderblush]
.color-lawngreen[lawngreen]
.color-lemonchiffon[lemonchiffon]
.color-lightblue[lightblue]
.color-lightcoral[lightcoral]
.color-lightcyan[lightcyan]
.color-lightgoldenrodyellow[lightgoldenrodyellow]
.color-lightgray[lightgray]
.color-lightgreen[lightgreen]
.color-lightgrey[lightgrey]
.color-lightpink[lightpink]
.color-lightsalmon[lightsalmon]
.color-lightseagreen[lightseagreen]
.color-lightskyblue[lightskyblue]
.color-lightslategray[lightslategray]
.color-lightslategrey[lightslategrey]
.color-lightsteelblue[lightsteelblue]
.color-lightyellow[lightyellow]
.color-lime[lime]
.color-limegreen[limegreen]
.color-linen[linen]
.color-magenta[magenta]
.color-maroon[maroon]
.color-mediumaquamarine[mediumaquamarine]
.color-mediumblue[mediumblue]
.color-mediumorchid[mediumorchid]
.color-mediumpurple[mediumpurple]
.color-mediumseagreen[mediumseagreen]
.color-mediumslateblue[mediumslateblue]
.color-mediumspringgreen[mediumspringgreen]
.color-mediumturquoise[mediumturquoise]
.color-mediumvioletred[mediumvioletred]

---

class: compact,col-2
# Colors 2

.color-midnightblue[midnightblue]
.color-mintcream[mintcream]
.color-mistyrose[mistyrose]
.color-moccasin[moccasin]
.color-navajowhite[navajowhite]
.color-navy[navy]
.color-oldlace[oldlace]
.color-olive[olive]
.color-olivedrab[olivedrab]
.color-orange[orange]
.color-orangered[orangered]
.color-orchid[orchid]
.color-palegoldenrod[palegoldenrod]
.color-palegreen[palegreen]
.color-paleturquoise[paleturquoise]
.color-palevioletred[palevioletred]
.color-papayawhip[papayawhip]
.color-peachpuff[peachpuff]
.color-peru[peru]
.color-pink[pink]
.color-plum[plum]
.color-powderblue[powderblue]
.color-purple[purple]
.color-rebeccapurple[rebeccapurple]
.color-red[red]
.color-rosybrown[rosybrown]
.color-royalblue[royalblue]
.color-saddlebrown[saddlebrown]
.color-salmon[salmon]
.color-sandybrown[sandybrown]
.color-seagreen[seagreen]
.color-seashell[seashell]
.color-sienna[sienna]
.color-silver[silver]
.color-skyblue[skyblue]
.color-slateblue[slateblue]
.color-slategray[slategray]
.color-slategrey[slategrey]
.color-snow[snow]
.color-springgreen[springgreen]
.color-steelblue[steelblue]
.color-tan[tan]
.color-teal[teal]
.color-thistle[thistle]
.color-tomato[tomato]
.color-turquoise[turquoise]
.color-violet[violet]
.color-wheat[wheat]
.color-white[white]
.color-whitesmoke[whitesmoke]
.color-yellow[yellow]
.color-yellowgreen[yellowgreen]
