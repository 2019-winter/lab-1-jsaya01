---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
**PUT YOUR FULL NAME(S) HERE**


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


**YOUR ANSWER HERE**


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np
arr = np.ones((6,4), int)*2
arr
```

## Exercise 2

```python
arr2 = np.ones((6,4), int)
np.fill_diagonal(arr2, 3)
arr2
```

## Exercise 3

```
You can multiply them together using * and this just preforms multiplicaiton on each pair of corresponding elements. However when using "dot" this attempts to preform matrix multiplication and because they are the same shape this will fail. 
```

## Exercise 4

```python
np.dot(arr, arr2.transpose())

np.dot(arr.transpose(), arr2)
```

The results are different because in both cases the inner dimensions will fade away while the outer dimentions will become the dimensions of the new matrix. For example if you are multiplying a 5x2 and a 2x5 matrix the resulting matrix will be 5x5. 


## Exercise 5

```python
def printSomething():
    print("here is something that is going to be printed")
    
printSomething()
```

## Exercise 6

```python
def randomArrays():
    for i in range(10):
        array = np.random.rand(100)
        print(np.mean(array))
        print(np.sum(array))

randomArrays()
```

## Exercise 7

```python
def countOnesLoop(a):
    num_ones = 0
    for i in a:
        if i == 1:
            num_ones += 1
    return num_ones

def countOnesWhere(a):
    x = np.array(a)
    return len(np.where(x == 1)[0])

a = [1, 2, 3, 2, 1, 2, 3, 5, 1, 1, 1, 5]
countOnesLoop(a)
countOnesWhere(a)
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd
arr = pd.DataFrame(np.ones((6,4), int)*2)
arr
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
arr2 = np.ones((6, 4), int)
np.fill_diagonal(arr2, 3)
arr3 = pd.DataFrame(arr2)
arr3
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
arr * arr2

np.dot(arr, arr2)
```

The same error occurs for the same reason that is stated in ex3.


## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
def countOnesWhere(a):
    x = pd.DataFrame(a)
    return len(x.where(x == 1).dropna())

a = [1, 2, 3, 2, 1, 2, 3, 5, 1, 1, 1, 5]
countOnesWhere(a)
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df["name"]
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
# titanic_df.set_index("sex",inplace=True)
titanic_df.loc['female']
titanic_df.loc['female'].size
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index()
```

```python

```
