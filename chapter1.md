---
title       : Testing objects
description : Become a pythonwhat wizard
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf


--- type:NormalExercise lang:python xp:100 skills:2 key:4bf65ad83e

## int

In Python, a variable allows you to refer to a value with a name. To create a variable use `=`, like this example:

```
x = 5
```

You can now use the name of this variable, `x`, instead of the actual value, `5`.

*** =instructions
- Create a variable `savings` with the value 100.
- Check out this variable by typing `print(savings)` in the script.

*** =hint
- Type `savings = 100` to create the variable `savings`.
- After creating the variable `savings`, you can type `print(savings)`.

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Create a variable savings


# Print out savings

```

*** =solution
```{python}
# Create a variable savings
savings = 100

# Print out savings
print(savings)
```

*** =sct
```{python}
test_object("savings", incorrect_msg = "Assign `100` to the variable `savings`.")

# MC-Note: Can remove test_function below and mentions of print, since this is first ex in tutorial
test_function("print", incorrect_msg = "Print out `savings`, the variable you created, using `print(savings)`.")
success_msg("Great! Let's try to do some calculations with this variable now!")
```

--- type:NormalExercise lang:python xp:100 skills:2 key:c7bbacb2a2

## float

Remember how you calculated the money you ended up with after 7 years of investing $100? You did something like this:

```
100 * 1.10 ** 7
```

Instead of calculating with the actual values, you can use variables instead. The `savings` variable you've created in the previous exercise represents the $100 you started with. It's up to you to create a new variable to represent `1.10` and then redo the calculations!

*** =instructions
- Create a variable `factor`, equal to `1.10`.
- Use `savings` and `factor` to calculate the amount of money you end up with after 7 years. Store the result in a new variable, `result`.
- Print out the value of `result`.

*** =hint
- To create the variable `factor`, use `factor = 1.10`.
- In the example code block of the assignment, replace `100` with `savings` and `1.10` with `factor`: `savings * factor ** 7`.
- Use the [`print()`](https://docs.python.org/3/library/functions.html#print) function to print the value of a variable.

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Create a variable savings
savings = 100

# Create a variable factor


# Calculate result


# Print out result
```

*** =solution
```{python}
# Create a variable savings
savings = 100

# Create a variable factor
factor = 1.1

# Calculate result
result = savings * factor ** 7

# Print out result
print(result)
```

*** =sct
```{python}
test_object("savings", undefined_msg = "The variable `savings` was defined for you, don't remove it!",
                       incorrect_msg = "The variable `savings` should be `100`, like it was defined for you.")
test_object("factor", incorrect_msg = "The value of `factor` should be `1.1`.")
test_object("result", incorrect_msg = "Have you used `*` and `**` to calculate `result`?")
msg = "Don't forget to print out `result` after assigning it."
test_print(not_called_msg = msg, incorrect_msg = msg)
success_msg("Great!")
```

--- type:NormalExercise lang:python xp:100 skills:2 key:e2cb3a665e
## strings and booleans

In the previous exercise, you worked with two Python data types:

- `int`, or integer: a number without a fractional part. `savings`, with the value `100`, is an example of an integer.
- `float`, or floating point: a number that has both an integer and fractional part, separated by a point. `factor`, with the value `1.10`, is an example of a float.

Next to numerical data types, there are two other very common data types:

- `str`, or string: a type to represent text. You can use single or double quotes to build a string.
- `bool`, or boolean: a type to represent logical values. Can only be `True` or `False`.

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
test_object("desc", incorrect_msg = "Assign the value `\"compound interest\"` to the variable `desc`.")
test_object("profitable", incorrect_msg = "Assign the value `True` to the variable `profitable`.")

success_msg("Nice!")
```


--- type:NormalExercise lang:python xp:100 skills:2 key:e6c527bf41
## list

As opposed to `int`, `bool` etc, a list is a **compound data type**: you can group values together:

```
a = "is"
b = "nice"
my_list = ["my", "list", a, b]
```

After measuring the height of your family, you decide to collect some information on the house you're living in. The areas of the different parts of your house are stored in separate variables for now, as shown in the script.

*** =instructions
- Create a list, `areas`, that contains the area of the hallway (`hall`), kitchen (`kit`), living room (`liv`), bedroom (`bed`) and bathroom (`bath`), in this order. Use the predefined variables.
- Print `areas` with the [`print()`](https://docs.python.org/3/library/functions.html#print) function.

*** =hint
- You can use the variables that have already been created to build the list: `areas = [hall, kit, ...]`.
- Put `print(areas)` in your script to print out the list when submitting.

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


# Print areas


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

# Print areas
print(areas)
```

*** =sct
```{python}
msg = "Don't remove or edit the predefined variables!"
test_object("hall", undefined_msg = msg, incorrect_msg = msg)
test_object("kit", undefined_msg = msg, incorrect_msg = msg)
test_object("liv", undefined_msg = msg, incorrect_msg = msg)
test_object("bed", undefined_msg = msg, incorrect_msg = msg)
test_object("bath", undefined_msg = msg, incorrect_msg = msg)

test_object("areas", incorrect_msg = "Define `areas` as the list containing all the area variables, in the correct order: `hall`, `kit`, `liv`, `bed` and `bath`. Watch out for typos. The list doesn't have to contain anything else.")

test_function("print", incorrect_msg = "Print out the `areas` list you created by using `print(areas)`.")

success_msg("Nice! A list is way better here, isn't it?")
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