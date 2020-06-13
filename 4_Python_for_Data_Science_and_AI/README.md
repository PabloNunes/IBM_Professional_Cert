# Python for Data Science and Artificial Intelligence - Summary

## Made by Pablo Nunes

----

## Types

- Integers -> Int
- Real Numbers -> Float
- Words -> str
- It's possible to use typecast to convert a type to another. Like a int to a float, even a str to a int, but be careful, errors can occur.
- Boolean -> Bool
- True or False

## Expresions and Variables

- Expressions are operations that python performs.
- Python follows mathematical conventions in order of operations
- Variables store values to later use
- It is good to use meaningful names
- Python normally use snake case

## Strings

- In Python, Strings are a sequence of characters.
- Used in single and double quotes
- Each character can be accessed by using its index
- You can use negative indexes
- Can split, concatenated, multiplied.

## List and Tuples

- Tuples are a ordered sequence
- Uses parentheses and separated by commas
- (1,2,3,4)
- All types can be inside a tuple
- Can be accessed by index, can be concatenated and split.
- Tuples are immutable
- List are a popular data structure in python
- [1, 3, 4]
- Lists can be nested, split, concatenated and changed.

## Dictionary

- Uses a key to correspond to a value
- {"Meme": 1912, "Key": 4}
- You can add values, see all the keys and values in a dictionary.

## Sets

- Are a type of collection
- Sets only have a unique type of elements
- {"1", "2", "4"}
- Sets can be added values, use mathematical operations like diagrams.
  
## Conditions and branching

- Comparison operators compares some value or operand then based in some condition, it produces a boolean.
- Logic Operations take boolean variables and transform into other boolean variables

## Loops

- The for iterate according to the range associated.
- Using enumerate serves a function to numerate each part of the list
- The while only stops when the condition is met!

## Functions

- Functions take some input, process, and give a certain output or not.
- It is a piece of code that can be reused
- Python has a lot of built-in functions
- Using triple quotes show us the documentation string, it shows using `help(function)`
- A function can have multiple parameters
- To mock a function, you can use `pass` in the body
- If a function returns nothing, in Python it returns a None
- It is possible to put a variable number of arguments using the `*`.
  - Ex: `def test_func(*names):`
- Global Scope vs. Local Scope

## Objects and Classes

- Object has a type and is an instance of a particular type.
- A method interact with a object.
- Classes define objects
- Using the `def __init__` makes the constructor of a class
- The `self` interact internally with some data of the object

## Manipulate Files

- We can use the python open function to read and obtain the data of objects.
- We should always close our files
- Using the command `with` automatically closes files for us.
- We can use the argument `r` to read, and `w` to write to the file. The argument `a` to append to the file.

## Pandas

- `import pandas as pd`
- You can use the `read_csv` function to read csv files or `read_excel` to read excel files
- Pandas use a dataframe to store and to process data
- Dataframes can be created with dictionaries as well
- You can create new dataframes by listing some columns present in a bigger dataframe
- `loc` vs `iloc` vs `ix`
  - `loc` takes the position and column name. Ex: `df.loc[0,'Artist']: 'Michael Jackson'`
  - `iloc` takes the positions in integers. Ex: `df.loc[0,0]: 'Michael Jackson'`
  - `ix` looks for a label, if does not find, returns an integer. It is deprecated.
  - It is possible to use `loc` and `iloc` to slice a dataframe
    - `new_df = df.loc[0:2, 'Artist':'Released]'`
    - `new_df = df.iloc[0:2, 0:3]'`
- List Unique elements: `.unique()`
- Select with condition: `df1 = df[df['Released']>=1980]`
  
## Numpy

- Numpy has a `numpy.ndarray` type and has a unique type inside it `int64`
- You can perform simple operations and linear algebra operations
- You can generate mathematical functions lie `np.sin()` or make a linear space with `np.linspace()`
- `A.shape` is useful to know the dimensions of the matrix

## API

- An API let two pieces of software talking to each other
- Representational State Transfer APIs or REST API are API that take usage of the Internet to use more resources
