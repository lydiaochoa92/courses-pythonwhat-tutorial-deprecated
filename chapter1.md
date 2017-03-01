---
title       : Testing objects
description : Become a pythonwhat wizard
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf


--- type:NormalExercise lang:python xp:100 skills:2 key:4bf65ad83e

## int

[see test_object docs](http://pythonwhat.readthedocs.io/en/latest/simple_tests/test_object.html)

It is very common for submission correctness tests (SCTs) to check the following:

1. that someone defined a variable (e.g. `savings = 100`)
2. that the variable has the correct value

This is where `test_object` comes in.
If you need more fine grained control, use the functions `check_object`, `is_instance`, and `has_equal_value`.


*** =instructions
- Create a variable `savings` with the value 100.

*** =hint
- Type `savings = 100` to create the variable `savings`.

*** =pre_exercise_code
```{python}
```

*** =sample_code
```{python}
# Create a variable savings

```

*** =solution
```{python}
# Create a variable savings
savings = 100
```

*** =sct
```{python}
# test that savings is defined, and that its value matches the solution
# note: the variable 'savings' is checked in the submission and solution code
#       AFTER running all solution and submission code.
Ex().test_object("savings", 
                 incorrect_msg = "Assign `100` to the variable `savings`.",
                 undefined_msg = "Did you define the variable `savings`?")

# if we only included the above test, it would allow "savings = 100.0", which is a float :(.
# in order to be very particular, and select only an integer, you can use the more fine-grained
# check functions
# NOTE: comment out test_object above to see each piece in action.
Ex().check_object("savings", missing_msg = "Did you define the variable savings?") \
    .is_instance(int, "Is it an integer?") \
    .has_equal_value("Assign it the value `100`")
```

--- type:NormalExercise lang:python xp:100 skills:2 key:c7bbacb2a2

## float

In the previous exercise we tested that a variable, `savings` was defined as the integer `100`.

Here, we use the same SCTs to test the case where a new variable `factor` it should be the `float` `1.10`.


*** =instructions
- Create a variable `savings`, equal to `1.10`.

*** =hint
- To create the variable `savings`, use `savings = 1.10`.

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Create a variable savings
savings = 100

# Create a variable factor

```

*** =solution
```{python}
# Create a variable savings
savings = 100

# Create a variable factor
factor = 1.1
```

*** =sct
```{python}
# in case the student deletes the code for savings, this will tell them.
Ex().test_object("savings")

# this SCT will check that factor exists, and that the value of factor in
# the student and submission code are equal (i.e. compares with == operator). 
# see previous exercise for details on test_object.
Ex().test_object("factor")

# we can be more explicit that factor should be a float, using is_instance.
# unlike test_object above, the SCT below will ask if factor is a float.
# NOTE: comment out code above to see this SCT in action
Ex().check_object("factor").is_instance(float).has_equal_value()

```

--- type:NormalExercise lang:python xp:100 skills:2 key:e2cb3a665e
## strings and booleans

In the previous exercises, you worked with two Python data types:

- `int`, or integer: a number without a fractional part. `savings`, with the value `100`, is an example of an integer.
- `float`, or floating point: a number that has both an integer and fractional part, separated by a point. `factor`, with the value `1.10`, is an example of a float.

Next to numerical data types, there are two other very common data types:

- `str`, or string: a type to represent text. You can use single or double quotes to build a string.
- `bool`, or boolean: a type to represent logical values. Can only be `True` or `False`.

These types may be tested in the same way as `int` and `float`.

*** =instructions
- Create a new string, `desc`, with the value `"compound interest"`.
- Create a new boolean, `profitable`, with the value `True`.

*** =hint
- To create a variable in Python, use `=`. Make sure to wrap your string in single or double quotes.
- Only two boolean values exist in Python: `True` and `False`. `TRUE`, `true`, `FALSE`, `false` and other versions will not be accepted.

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Create a variable desc


# Create a variable profitable

```

*** =solution
```{python}
# Create a variable desc
desc = "compound interest"

# Create a variable profitable
profitable = True
```

*** =sct
```{python}
Ex().test_object("desc", incorrect_msg = 'Assign the value `"compound interest"` to the variable `desc`.')
Ex().test_object("profitable", incorrect_msg = 'Assign the value `True` to the variable `profitable`.')

# Why do the SCTs above pass when setting "profitable = 1"? -------------------------------------------------------

# If you only used the code above, then setting "profitable = 1" would also pass,
# since 1 == True. If you were a stickler about profitable being a bool instance,
# you could use the more fine-grained check functions, as shown below.
Ex().check_object("desc").is_instance(bool, "is_instance figured out that it is not a string").has_equal_value()
Ex().check_object("profitable").is_instance(bool, "is_instance figured out that it is not a bool").has_equal_value()

```


--- type:NormalExercise lang:python xp:100 skills:2 key:e6c527bf41
## list

As opposed to `int`, `bool` etc, a list is a **compound data type**: you can group values together:

```
a = "is"
b = "nice"
my_list = ["my", "list", a, b]
```

**Below is a potential scenario for teaching students to use a list.**

After measuring the height of your family, you decide to collect some information on the house you're living in. The areas of the different parts of your house are stored in separate variables for now, as shown in the script.

*** =instructions
- Create a list, `areas`, that contains the area of the hallway (`hall`), kitchen (`kit`), living room (`liv`), bedroom (`bed`) and bathroom (`bath`), in this order. Use the predefined variables.

*** =hint
- You can use the variables that have already been created to build the list: `areas = [hall, kit, ...]`.

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# area variables (in square meters)
hall = 11.25
kit = 18.0
liv = 20.0
bed = 10.75
bath = 9.50

# Create list areas

```

*** =solution
```{python}
# Area variables (in square meters)
hall = 11.25
kit = 18.0
liv = 20.0
bed = 10.75
bath = 9.50

# Create list areas
areas = [hall, kit, liv, bed, bath]
```

*** =sct
```{python}
# This test makes sure that students are warned if they delete parts of the sample code.
# Note that
#
#     Ex().test_object("hall")
#     Ex().test_object("kit")
#
# Is equivalent to
#
#     Ex().multi(test_object("hall"), test_object("kit"))
#
# MC-NOTE: should I remove multi change these to all using Ex().test1; Ex().test2; ...?
msg = "Don't remove or edit the predefined variables!"
Ex().multi(
        test_object("hall", undefined_msg = msg, incorrect_msg = msg),
        test_object("kit", undefined_msg = msg, incorrect_msg = msg),
        test_object("liv", undefined_msg = msg, incorrect_msg = msg),
        test_object("bed", undefined_msg = msg, incorrect_msg = msg),
        test_object("bath", undefined_msg = msg, incorrect_msg = msg)
        )

# This code checks that the variable "areas" was defined, and is the correct value
Ex().test_object("areas", incorrect_msg = "Define `areas` as the list containing all the area variables, in the correct order: `hall`, `kit`, `liv`, `bed` and `bath`. Watch out for typos. The list doesn't have to contain anything else.")

# Note: Try making the submission code equal to the solution code, and then
#       change "kit = 18.0" in the submission to "kit = 18". Why does the submission pass?
#       The answer is that pythonwhat uses "==" to test that a variable has the same value
#       between the student and solution results. In python the following evaluate to True
#           [1, 2, 3] == [1.0, 2, 3]
#           [1, 2, 3] == [True, 2, 3]
#
# If you wanted to be very specific, you could use one of the following tests.
# Option 1: see if string output is the same. This is similar to comparing str('areas').
Ex().check_object('areas').is_instance(list).has_equal_output()
```


--- type:NormalExercise lang:python xp:100 skills:2 key:7f08642d18
## list slicing

Selecting single values from a list is just one part of the story. It's also possible to _slice_ your list, which means selecting multiple elements from your list. Use the following syntax:

```
my_list[start:end]
```

The `start` index will be included, while the `end` index is _not_.

The code sample below shows an example. A list with `"b"` and `"c"`, corresponding to indexes 1 and 2, are selected from a list `x`:

```
x = ["a", "b", "c", "d"]
x[1:3]
```

The elements with index 1 and 2 are included, while the element with index 3 is not.

*** =instructions
- Use slicing to create a list, `downstairs`, that contains the first 6 elements of `areas`.
- Do a similar thing to create a new variable, `upstairs`, that contains the last 4 elements of `areas`.
- Print both `downstairs` and `upstairs` using [`print()`](https://docs.python.org/3/library/functions.html#print).

*** =hint
- Use the brackets `[0:6]` to build `downstairs`.
- Use the barckets `[6:10]` to build `upstairs`.
- Simply add two [`print()`](https://docs.python.org/3/library/functions.html#print) calls to the script to print out `downstairs` and `upstairs`.

*** =pre_exercise_code
```{python}
# no pec
```

*** =sample_code
```{python}
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Use slicing to create downstairs


# Use slicing to create upstairs


# Print out downstairs and upstairs
```

*** =solution
```{python}
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Use slicing to create downstairs
downstairs = areas[0:6]

# Use slicing to create upstairs
upstairs = areas[6:10]

# Print out downstairs and upstairs
print(downstairs)
print(upstairs)
```

*** =sct
```{python}
msg = "Don't remove or edit the predefined `areas` list."
test_object("areas", undefined_msg = msg, incorrect_msg = msg)

test_object("downstairs", incorrect_msg = "Your definition of `downstairs` is incorrect. Use `areas[...]` and slicing to select the elements you want. You could use `0:6` where the dots are, for example.")
test_object("upstairs", incorrect_msg = "Your definition of `upstairs` is incorrect. Use `areas[...]` and slicing to select the elements you want. You could use `6:10` where the dots are, for example.")

test_function("print", 1, incorrect_msg = "First, print out `downstairs` using `print(downstairs)`.")
test_function("print", 2, incorrect_msg = "First, print out `upstairs` using `print(upstairs)`.")

success_msg("Great!")
```



--- type:NormalExercise lang:python xp:100 skills:2 key:b67a5ea0d3
## dictionary

The `countries` and `capitals` lists are again available in the script. It's your job to convert this data to a dictionary where the country names are the keys and the capitals are the corresponding values. As a refresher, here is a recipe for creating a dictionary:

```
my_dict = {
   "key1":"value1",
   "key2":"value2",
}
```

In this recipe, both the keys and the values are strings. This will also be the case for this exercise.

*** =instructions
- With the strings in `countries` and `capitals`, create a dictionary called `europe` with 4 key:value pairs. Beware of capitalization! Make sure you use lowercase characters everywhere.
- Print out `europe` to see if the result is what you expected.

*** =hint
- Start with `{ "spain":"madrid", ... }`. Include three more key:value pairs in a similar fashion.
- Don't forget to use quotation marks for strings!

*** =sample_code
```{python}
# Definition of countries and capital
countries = ['spain', 'france', 'germany', 'norway']
capitals = ['madrid', 'paris', 'berlin', 'oslo']

# From string in countries and capitals, create dictionary europe


# Print europe

```

*** =solution
```{python}
# Definition of countries and capital
countries = ['spain', 'france', 'germany', 'norway']
capitals = ['madrid', 'paris', 'berlin', 'oslo']

# From string in countries and capitals, create dictionary europe
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin', 'norway':'oslo' }

# Print europe
print(europe)
```

*** =sct
```{python}

msg = "Did you correctly create the dictionary `europe`?"
test_object("europe", undefined_msg = msg, incorrect_msg = msg)

msg = "Have you correctly printed out `europe`?"
test_function("print", 1, not_called_msg = msg, incorrect_msg = msg)

success_msg("Great! Now that you've built your first dictionaries, let's get serious!")
```


--- type:NormalExercise lang:python xp:100 skills:2 key:6048cbed18
## dictionary item

If the keys of a dictionary are chosen wisely, accessing the values in a dictionary is easy and intuitive. For example, to get the capital for France from `europe` you can use:

```
europe['france']
```

Here, `'france'` is the key and `'paris'` the value is returned.

*** =instructions
- Check out which keys are in `europe` by calling the [`keys()`](https://docs.python.org/3/library/stdtypes.html#dict.keys) method on `europe`. Print out the result.
- Print out the value that belongs to the key `'norway'`.

*** =hint
- `europe.keys()` gives you the keys in `europe`. Make sure to wrap a [`print()`](https://docs.python.org/3/library/functions.html#print) call around it.
- To access the name of country use syntax similar to `country['capital']`.

*** =sample_code
```{python}
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin', 'norway':'oslo' }

# Print out the keys in europe


# Print out value that belongs to key 'norway'

```

*** =solution
```{python}
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin', 'norway':'oslo' }

# Print out the keys in europe
print(europe.keys())

# Print out value that belongs to key 'norway'
print(europe['norway'])
```

*** =sct
```{python}
test_function("europe.keys")

msg = "For the first printout, use `print(europe.keys())` to print out all keys of `europe`."
test_function("print", 1, not_called_msg = msg, incorrect_msg = msg)

msg = "For the second printout, use `print(europe['norway'])` to print out the value belonging to the key `'norway'`."
test_function("print", 2, not_called_msg = msg, incorrect_msg = msg)

success_msg("Good job, now you're warmed up for some more.")
```


--- type:NormalExercise lang:python xp:100 skills:2 key:84cab9d170
## numpy array

In this chapter, we're going to dive into the world of baseball. Along the way, you'll get comfortable with the basics of Numpy, a powerful package to do data science.

A list `baseball` has already been defined in the Python script, representing the height of some baseball players in centimeters. Can you add some code here and there to create a Numpy array from it?

*** =instructions
- Import the `numpy` package as `np`, so that you can refer to `numpy` with `np`.
- Use [`np.array()`](http://docs.scipy.org/doc/numpy-1.10.0/glossary.html#term-array) to create a Numpy array from `baseball`. Name this array `np_baseball`.
- Print out the type of `np_baseball` to check that you got it right.

*** =hint
- `import numpy as np` will do the trick. Now, you have to use `np.fun_name()` whenever you want to use a Numpy function.
- [`np.array()`](http://docs.scipy.org/doc/numpy-1.10.0/glossary.html#term-array) should take on input `baseball`. Assign the result of the function call to `np_baseball`.
- To print out the type of a variable `x`, simply type `print(type(x))`.

*** =pre_exercise_code
```{python}
import numpy as np
```

*** =sample_code
```{python}
# Create list baseball
baseball = [180, 215, 210, 210, 188, 176, 209, 200]

# Import the numpy package as np


# Create a Numpy array from baseball: np_baseball


# Print out type of np_baseball

```

*** =solution
```{python}
# Create list baseball
baseball = [180, 215, 210, 210, 188, 176, 209, 200]

# Import the numpy package as np
import numpy as np

# Create a Numpy array from baseball: np_baseball
np_baseball = np.array(baseball)

# Print out type of np_baseball
print(type(np_baseball))
```

*** =sct
```{python}
msg = "You don't have to change or remove the predefined variables."
test_object("baseball", undefined_msg = msg, incorrect_msg = msg)

test_import("numpy")

test_object("np_baseball", do_eval = False)
test_function("numpy.array", not_called_msg = "Be sure to call [`np.array()`](http://docs.scipy.org/doc/numpy-1.10.0/glossary.html#term-array).",
                             incorrect_msg = "You should call [`np.array()`](http://docs.scipy.org/doc/numpy-1.10.0/glossary.html#term-array) as follows: `np.array(baseball)`.")
test_object("np_baseball", incorrect_msg = "Assign the correct value to `np_baseball`.")

msg = "Make sure to print out the type of `np_baseball` like this: `print(type(np_baseball))`."
test_function("type", 1, incorrect_msg = msg)
test_function("print", 1, incorrect_msg = msg)

success_msg("Great job!")
```


--- type:NormalExercise lang:python xp:100 skills:2 key:fcb2a9007b
## numpy array slice

You've seen it with your own eyes: Python lists and Numpy arrays sometimes behave differently. Luckily, there are still certainties in this world. For example, subsetting (using the square bracket notation on lists or arrays) works exactly the same. To see this for yourself, try the following lines of code in the IPython Shell:

```
x = ["a", "b", "c"]
x[1]

np_x = np.array(x)
np_x[1]
```

The script on the right already contains code that imports `numpy` as `np`, and stores both the height and weight of the MLB players as Numpy arrays.

*** =instructions
- Subset `np_weight`: print out the element at index 50.
- Print out a sub-array of `np_height`: It contains the elements at index 100 up to **and including** index 110

*** =hint
- Make sure to wrap a [`print()`](https://docs.python.org/3/library/functions.html#print) call around your subsetting operations.
- Use `[100:111]` to get the elements from index 100 up to and including index 110.

*** =pre_exercise_code
```{python}
import pandas as pd
mlb = pd.read_csv("http://s3.amazonaws.com/assets.datacamp.com/course/intro_to_python/baseball.csv")
height = mlb['Height'].tolist()
weight = mlb['Weight'].tolist()
import numpy as np
```

*** =sample_code
```{python}
# height and weight are available as a regular lists

# Import numpy
import numpy as np

# Store weight and height lists as numpy arrays
np_weight = np.array(weight)
np_height = np.array(height)

# Print out the weight at index 50


# Print out sub-array of np_height: index 100 up to and including index 110

```

*** =solution
```{python}
# height and weight are available as a regular lists

# Import numpy
import numpy as np

# Store weight and height lists as numpy arrays
np_weight = np.array(weight)
np_height = np.array(height)

# Print out the weight at index 50
print(np_weight[50])

# Print out sub-array of np_height: index 100 up to and including index 110
print(np_height[100:111])
```

*** =sct
```{python}

test_import("numpy", same_as = False)

msg = "You don't have to change or remove the predefined variables."
test_object("np_height", undefined_msg = msg, incorrect_msg = msg)
test_object("np_weight", undefined_msg = msg, incorrect_msg = msg)

test_function("print", 1,
              incorrect_msg = "For the first printout, subset `np_weight` to select the 50th element.")

test_function("print", 2,
              incorrect_msg = "For the second printout, subset `np_height` to select the 100th to 110th element, included. You can use the slicing operator: `:`, just make sure to put in the correct ending index.")

success_msg("Nice! Time to learn something new: 2D Numpy arrays!")
```


--- type:NormalExercise lang:python xp:100 skills:2 key:532155cd37
## pandas data frame

Pandas is an open source library, providing high-performance, easy-to-use data structures and data analysis tools for Python. Sounds promising!

The DataFrame is one of Pandas' most important data structures. It's basically a way to store tabular data, where you can label the rows and the columns. One way to build a DataFrame is from a dictionary.

In the exercises that follow you will be working with vehicle data in different countries. Each observation corresponds to a country and the columns give information about the number of vehicles per capita, whether people drive left or right, and so on.

Three lists are defined in the script:
- `names`, containing the country names for which data is available.
- `dr`, a list with booleans that tells whether people drive left or right in the corresponding country.
- `cpc`, the number of motor vehicles per 1000 people in the corresponding country.

Each dictionary key is a column label and each value is a list which contains the column elements.

*** =instructions
- Import `pandas` as `pd`.
- Use the pre-defined lists to create dictionary, called `my_dict`. There should be three key value pairs:
  + key `'country'` and value `names`.
  + key `'drives_right'` and value `dr`.
  + key `'cars_per_cap'` and value `cpc`.
- Use [`pd.DataFrame()`](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html) to turn your dict into a DataFrame called `cars`.
- Print out `cars` and see how beautiful it is.

*** =hint
- `import pandas as pd` imports `pandas` under the local name `pd`.
- A dictionary with only the country names would look like this: `my_dict = { 'country':names }`. Can you add some more key:value pairs?
- `pd.DataFrame(my_dict)` will produce a DataFrame that you can store as `cars`.
- To print out a variable `x` type `print(x)` on a new line in your script.

*** =sample_code
```{python}
# Pre-defined lists
names = ['United States', 'Australia', 'Japan', 'India', 'Russia', 'Morocco', 'Egypt']
dr =  [True, False, False, False, True, True, True]
cpc = [809, 731, 588, 18, 200, 70, 45]

# Import pandas as pd


# Create dictionary my_dict with three key:value pairs: my_dict


# Build a DataFrame cars from my_dict: cars


# Print cars

```

*** =solution
```{python}
# Pre-defined lists
names = ['United States', 'Australia', 'Japan', 'India', 'Russia', 'Morocco', 'Egypt']
dr =  [True, False, False, False, True, True, True]
cpc = [809, 731, 588, 18, 200, 70, 45]

# Import pandas as pd
import pandas as pd

# Create dictionary my_dict with three key:value pairs: my_dict
my_dict = { 'country':names, 'drives_right':dr, 'cars_per_cap':cpc }

# Build a DataFrame cars from my_dict: cars
cars = pd.DataFrame(my_dict)

# Print cars
print(cars)
```

*** =sct
```{python}
msg = "You don't have to change or remove `names`, it was defined for you."
test_object("names", undefined_msg = msg, incorrect_msg = msg)

msg = "You don't have to change or remove `dr`, it was defined for you."
test_object("dr", undefined_msg = msg, incorrect_msg = msg)

msg = "You don't have to change or remove `cpc`, it was defined for you."
test_object("cpc", undefined_msg = msg, incorrect_msg = msg)

msg = "Have you correctly imported `pandas` as `pd`? Use `import pandas as pd`."
test_import("pandas", not_imported_msg = msg, incorrect_as_msg = msg)

msg = "You can create a dictionary as follows: `{'country': names, 'drives_right': dr, 'cars_per_cap':cpc}`. Make sure to assign it to `my_dict`."
test_object("my_dict", undefined_msg = msg, incorrect_msg = msg)

msg = "You can create a pandas DataFrame as follows: `pd.DataFrame(my_dict)`. Make sure to store it as `cars`."
test_object("cars", undefined_msg = msg, incorrect_msg = msg)

msg = "Don't forget to print out the `cars` DataFrame with [`print()`](https://docs.python.org/3/library/functions.html#print)."
test_function("print",  not_called_msg = msg, incorrect_msg = msg)

success_msg("Good job! Notice that the columns of `cars` can be of different types. This was not possible with 2D Numpy arrays!")
```