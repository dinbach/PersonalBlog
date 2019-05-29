---
title: Lecture2
date: "2019-06-07T08:00:17+02:00"
url: "/slides/lecture3/"
image: "/slides/lecture2/cover.jpg"
description: ""
ratio: "16:9"
buildFuture : false
themes:
- apron
- adirondack
- descartes
classes:
- feature-hyphenate
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
upper(), replace(<input>,<replacement>), find(<string>)
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

# Split function

```Python
name_toSplit = 'Leonardo Da Vinci'
name_toSplit.split() # splits by space and produces a list
name_toSplit.split('a') # splits by 'a' and produces a list
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

A .color-dodgerblue["numpy" array] or .color-dodgerblue["ndarray"] is similar to a list. It's usually fixed in size and each
element is of the same type
```python
[5, 'blue', 3.14, 10] # List
[1, 2, 3, 4, 5]  # numpy array
```


---
class: title, smokescreen

# Pandas

---
class: compact
#Pandas DataFrames
http://pandas.pydata.org/

Pandas DF is an open source library providing high-performance, easy-to-use data structures and data analysis tools in Python. It is similar in many aspects to NumPy.

---








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















