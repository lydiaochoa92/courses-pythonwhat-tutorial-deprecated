---
title       : Control flow
description : Insert the chapter description here


--- type:NormalExercise lang:python xp:100 skills:2 key:3f7ec57dda
## for loop


*** =instructions
Write a `for` loop that iterates over all elements of the `areas` list and prints out every element separately.

*** =hint

*** =sample_code
```{python}
# areas list
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Code the for loop

```

*** =solution
```{python}
# areas list
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Code the for loop
for area in areas :
    print(area)
```

*** =sct
```{python}
# get code of for loop
msg = "Make sure to loop over `areas`"
for_loop = Ex().check_for_loop(0)

# for loop iterator
for_loop.check_iter().has_equal_value(incorrect_msg = msg)

# for loop body
# note that we can't use has_equal_value below, because the body of a for loop
# is not necessarily a single python expression (i.e. it doesn't return a value)
msg = "Print out `area`"
for_loop.check_body().has_equal_output(incorrect_msg = msg, context_vals = ["test"])

# alternatively, could do
# for_loop.check_body().set_context(area = "test").has_equal_output(incorrect_msg = msg)

```


--- type:NormalExercise lang:python xp: skills: key:8da0db3df3
## list comprehension

You now have all the knowledge necessary to begin writing list comprehensions! Your job in this exercise is to write a list comprehension
that produces a list of the squares of the numbers ranging from 0 to 9. 

*** =instructions
- Using the range of numbers from `0` to `9` as your iterable and `i` as your iterator variable, write a list comprehension that produces a list of numbers consisting of the squared values of `i`. 

*** =hint
- The basic syntax for a list comprehension is `[`_output expression_ `for` _iterator variable_ `in` _iterable_`]`. The _output expression_ here is `i**2`, the _iterator variable_ is `i`, and the iterable is `range(0,10)`.
 

*** =pre_exercise_code
```{python}

```

*** =sample_code
```{python}
# Create list comprehension: squares
squares = [____ for ____ in ____]

```

*** =solution
```{python}
# Create list comprehension: squares
squares = [i**2 for i in range(0,10)]

```

*** =sct
```{python}
# Spec2 
Ex().test_list_comp(iter_vars_names=True)
list_comp = Ex().check_list_comp(0, missing_msg="Did you use a list comprehension to turn the list of lists into a list of dicts?")
list_comp.check_body().set_context(i=4).has_equal_value('Are you squaring each value of `i`?', error_msg='Are you squaring each value of `i`?')
#list_comp.check_body().test_student_typed('i\*\*2', not_typed_msg='Are you squaring each value of `i`?')
list_comp.check_iter().has_equal_value('Are you iterating over `range(0,10)`?') 
           
```


--- type:NormalExercise lang:python xp:100 skills:2 key:8e9ef7d8a3
## list comprehension w/ conditional

You've been using list comprehensions to build lists of values, sometimes using operations to create these values. 

An interesting mechanism in list comprehensions is that you can also create lists with values that meet only a certain condition. One way of doing this is by using conditionals on iterator variables. In this exercise, you will do exactly that!

Recall from the video that you can apply a conditional statement to test the iterator variable by adding an `if` statement in the optional _predicate expression_ part after the `for` statement in the comprehension: 

`[` _output expression_ `for` _iterator variable_ `in` _iterable_ `if` _predicate expression_ `]`. 

You will use this recipe to write a list comprehension for this exercise. You are given a list of strings `fellowship` and, using a list comprehension, you will create a list that only includes the members of `fellowship` that have 7 characters or more.

*** =instructions
- Use `member` as the iterator variable in the list comprehension. For the conditional, use `len()` to evaluate the iterator variable. Note that you only want strings with 7 characters or more.

*** =hint
- You don't have to perform any additional operations on `member` for the output expression. You should also start the conditional with the keyword `if` followed by the boolean expression for evaluating the iterator variable.

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Create a list of strings: fellowship
fellowship = ['frodo', 'samwise', 'merry', 'aragorn', 'legolas', 'boromir', 'gimli']

# Create list comprehension: new_fellowship
new_fellowship = [____ for ____ in fellowship ____]

# Print the new list
print(new_fellowship)

```

*** =solution
```{python}
# Create a list of strings: fellowship
fellowship = ['frodo', 'samwise', 'merry', 'aragorn', 'legolas', 'boromir', 'gimli']

# Create list comprehension: new_fellowship
new_fellowship = [member for member in fellowship if len(member) >= 7]

# Print the new list
print(new_fellowship)

```

*** =sct
```{python}

# Test: fellowship object
test_object(
    "fellowship",
    undefined_msg="You don't have to change any of the predefined code.",
    incorrect_msg="You don't have to change any of the predefined code."
)

# Test: list comprehension
Ex().test_list_comp(iter_vars_names=True)
list_comp = Ex().check_list_comp(0, missing_msg="Did you create the list comprehension?")
list_comp.check_body().set_context(member='samwise').has_equal_value('Did you use `member` as your iterator variable?', error_msg='Did you use `member` as your iterator variable?')
list_comp.check_iter().has_equal_value(error_msg='Are you using `fellowship` as your iterable?')
list_comp.check_ifs(0).multi(set_context(member='samwise').has_equal_value(incorrect_msg='Did you create a list that only includes strings with 7 characters or more?', error_msg='Did you compute the length of each string using `len(member)`?'), set_context(member='frodoo').has_equal_value(incorrect_msg ='Did you create a list that only includes strings with 7 characters or more?', error_msg='Did you create a list that only includes strings with 7 characters or more?'))

success_msg("Great work!")

```



--- type:NormalExercise lang:python xp:100 skills:2 key:f8cb706e3f
## list comprehension w/ conditional 2

In the previous exercise, you used an `if` conditional statement in the _predicate expression_ part of a list comprehension to evaluate an iterator variable. In this exercise, you will use an `if-else` statement on the _output expression_ of the list.

You will work on the same list, `fellowship` and, using a list comprehension and an `if-else` conditional statement in the output expression, create a list that keeps members of `fellowship` with 7 or more characters and replaces others with an empty string. Use `member` as the iterator variable in the list comprehension. 

*** =instructions
- In the output expression, keep the string as-is **if** the number of characters is >= 7, **else** replace it with an _empty string_.

*** =hint
- The first part of the conditional is an `if` statement followed by the boolean expression for evaluating the iterator variable. The second part is an `else` statement.

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Create a list of strings: fellowship
fellowship = ['frodo', 'samwise', 'merry', 'aragorn', 'legolas', 'boromir', 'gimli']

# Create list comprehension: new_fellowship
new_fellowship = [____ for ____ in fellowship]

# Print the new list
print(new_fellowship)

```

*** =solution
```{python}
# Create a list of strings: fellowship
fellowship = ['frodo', 'samwise', 'merry', 'aragorn', 'legolas', 'boromir', 'gimli']

# Create list comprehension: new_fellowship
new_fellowship = [member if len(member) >= 7 else '' for member in fellowship]

# Print the new list
print(new_fellowship)

```

*** =sct
```{python}

# Test: fellowship object
test_object(
    "fellowship",
    undefined_msg="You don't have to change any of the predefined code.",
    incorrect_msg="You don't have to change any of the predefined code."
)

# Test: list comprehension
Ex().test_list_comp(iter_vars_names=True)
list_comp = Ex().check_list_comp(0, missing_msg="Did you create the list comprehension?")
list_comp.check_body().set_context(member='samwise').check_if_exp(0).multi(set_context(member='samwisee').has_equal_value('Are you setting the string to be empty if it is greater than equal to 7 characters?', error_msg='Are you using `member` as your iterator variable?'), set_context(member='frodoo').has_equal_value('Are you setting the string to be empty if it is greater than or equal to 7 characters?', error_msg='Are you setting the string to be empty if it is greater than or equal to 7 characters?'), set_context(member = '').has_equal_value('test', error_msg='test'))
list_comp.check_iter().has_equal_value(error_msg='Did you use `fellowship` as your iterable?')

# Test: new_fellowship object
test_object(
    "new_fellowship",
    do_eval=False
)

# Test: print() call
#test_function(
#    "print",
#    not_called_msg="You don't have to change any of the predefined code.",
#    incorrect_msg="You don't have to change any of the predefined code."
#)

success_msg("Great work!")

```



--- type:NormalExercise lang:python xp:100 skills:2 key:92d979a1ca
## nested list comprehensions

Great! At this point, you have a good grasp of the basic syntax of list comprehensions. Let's push your code-writing skills a little further. In this exercise, you will be writing a list comprehension _within_ another list comprehension, or nested list comprehensions. It sounds a little tricky, but you can do it!

Let's step aside for a while from strings. One of the ways in which lists can be used are in representing multi-dimension objects such as **matrices**. Matrices can be represented as a list of lists in Python. For example a 5 x 5 matrix with values `0` to `4` in each row can be written as:

```
matrix = [[0, 1, 2, 3, 4],
          [0, 1, 2, 3, 4],
          [0, 1, 2, 3, 4],
          [0, 1, 2, 3, 4],
          [0, 1, 2, 3, 4]]
```

Your task is to recreate this matrix by using nested listed comprehensions. Recall that you can create one of the rows of the matrix with a single list comprehension. To create the list of lists, you simply have to supply the list comprehension as the **output expression** of the overall list comprehension:

`[`[_output expression_] `for` _iterator variable_ `in` _iterable_`]`

Note that here, the **output expression** is itself a list comprehension. 


*** =instructions
- In the inner list comprehension - that is, the **output expression** of the nested list comprehension - create a list of values from `0` to `4` using `range()`. Use `col` as the iterator variable. 
- In the **iterable** part of your nested list comprehension, use `range()` to count 5 rows - that is, create a list of values from `0` to `4`. Use `row` as the iterator variable; note that you won't be needing this to create values in the list of lists.

*** =hint
- The basic syntax for a list comprehension is `[`_output expression_ `for` _iterator variable_ `in` _iterable_`]`.
- Use the first list comprehension as the **output expression** of the second list comprehension

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Create a 5 x 5 matrix using a list of lists: matrix
matrix = [[____] ____]

# Print the matrix
for row in matrix:
    print(row)

```

*** =solution
```{python}
# Create a 5 x 5 matrix using a list of lists: matrix
matrix = [[col for col in range(5)] for row in range(5)]

# Print the matrix
for row in matrix:
    print(row)

```

*** =sct
```{python}
# Test: nested comprehension
Ex().test_correct(test_object('matrix',undefined_msg='Did you create a list of values from `0` to `4` using `range()`?', incorrect_msg='Did you create a list of values from `0` to `4` using `range()`?'),check_list_comp(0).check_body().check_list_comp(0).check_iter().test_function('range', incorrect_msg='Did you create a list of values from `0` to `4` using `range()`?',not_called_msg='Did you create a list of values from `0` to `4` using `range()`?'))
Ex().check_list_comp(0).check_body().test_list_comp(iter_vars_names=True)
Ex().check_list_comp(0).check_body().check_list_comp(0).check_body().test_student_typed('col', not_typed_msg='Did you use `col` for the iterator variable?')

Ex().test_correct(test_object('matrix', undefined_msg='Did you create a list of values from `0` to `4` using `range()`?', incorrect_msg='Did you create a list of values from `0` to `4` using `range()`?'),check_list_comp(0).check_iter().test_function('range'))
Ex().check_list_comp(0).test_list_comp(iter_vars_names=True)

Ex().check_for_loop(0).check_iter().has_equal_value('You do not need to modify the provided `for` loop.', error_msg='You do not need to modify the provided `for` loop.')
Ex().check_for_loop(0).check_body().test_function('print', incorrect_msg='You do not need to modify the provided `print()` function.', not_called_msg='You do not need to modify the provided `print()` function.')

success_msg("Great work!")

```

--- type:NormalExercise lang:python xp:100 skills:2 key:721dc6b47c
## dict comprehensions

Comprehensions aren't relegated merely to the world of lists. There are many other objects you can build using comprehensions, such as dictionaries, pervasive objects in Data Science. You will create a dictionary using the comprehension syntax for this exercise. In this case, the comprehension is called a **dict comprehension**.

Recall that the main difference between a _list comprehension_ and a _dict comprehension_ is the use of _curly braces_ `{}` instead of `[]`. Additionally, members of the dictionary are created using a colon `:`, as in _key_`:`_value_.

You are given a list of strings `fellowship` and, using a **dict comprehension**, create a dictionary with the members of the list as the _keys_ and the length of each string as the corresponding _values_.

*** =instructions
- Create a dict comprehension where the _key_ is a string in `fellowship` and the _value_ is the length of the string. Remember to use the syntax _key_`:`_value_ in the _output expression_ part of the comprehension to create the members of the dictionary. Use `member` as the iterator variable.

*** =hint
- A basic dict comprehension has the same syntax as a list comprehension, except with `{}`: `{` _output expression_ `for` _iterator variable_ `in` _iterable_ `}`.

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Create a list of strings: fellowship
fellowship = ['frodo', 'samwise', 'merry', 'aragorn', 'legolas', 'boromir', 'gimli']

# Create dict comprehension: new_fellowship
new_fellowship = ____

# Print the new list
print(new_fellowship)

```

*** =solution
```{python}
# Create a list of strings: fellowship
fellowship = ['frodo', 'samwise', 'merry', 'aragorn', 'legolas', 'boromir', 'gimli']

# Create dict comprehension: new_fellowship
new_fellowship = {member:len(member) for member in fellowship}

# Print the new list
print(new_fellowship)

```

*** =sct
```{python}

# Test: fellowship object
test_object(
    "fellowship",
    undefined_msg="You don't have to change any of the predefined code.",
    incorrect_msg="You don't have to change any of the predefined code."
)

# Test: dict comprehension
Ex().test_dict_comp(iter_vars_names=True)
dict_comp = Ex().check_dict_comp(0, missing_msg="Did you create a dict comprehension?")
dict_comp.check_key().set_context(member='samwise').has_equal_value('Are you using `member` as your iterator variable?', error_msg='Are you using `member` as your iterator variable?')
dict_comp.check_value().test_function('len', do_eval=False)
dict_comp.check_iter().has_equal_value('Did you use `fellowship` as your iterable?')


# Test: new_fellowship object
test_object(
    "new_fellowship",
    do_eval=False
)

# Test: print() call
test_function(
    "print",
    not_called_msg="You don't have to change any of the predefined code.",
    incorrect_msg="You don't have to change any of the predefined code."
)

success_msg("Great work!")

```



--- type:NormalExercise lang:python xp:100 skills:2 key:bbcf36c345
## if-else (TODO)


*** =instructions

*** =hint

*** =pre_exercise_code
```{python}

```

*** =sample_code
```{python}

```

*** =solution
```{python}

```

*** =sct
```{python}

```



--- type:NormalExercise lang:python xp:100 skills:2 key:d6419711b9
## if-else within a for loop

Weights can be added to edges in a graph, typically indicating the "strength" of an edge. In NetworkX, the weight is indicated by the `'weight'` key in the metadata dictionary.

Before attempting the exercise, use the IPython Shell to access the dictionary metadata of `T` and explore it, for instance by running the commands `T.edge[1][10]` and then `T.edge[10][1]`. Note how there's only one field, and now you're going to add another field, called `'weight'`.

*** =instructions
- Set the `'weight'` attribute of the edge between node `1` and `10` of `T` to be equal to `2`. Refer to the following template to set an attribute of an edge: `network_name.edge[node1][node2]['attribute'] = value`. This is because NetworkX graphs are dictionaries of dictionaries (of dictionaries). 
- Set the weight of every edge involving node `293` to be equal `1.1`. To do this:
    - Using a `for` loop, iterate over all the edges of `T`, including the `metadata`. 
    - If `293` is involved in the list of nodes `[u, v]`:
        - Set the weight of the edge between `u` and `v` to be `1.1`.

*** =hint
- To set an attribute of an edge, use the command `network_name.edge[node1][node2]['attribute'] = value`. Here, the network is `T`, `node1` is `1`, `node2` is `10`, `'attribute'` is `'weight'`, and the `value` is `2`.
- In the `for` loop, you need to iterate over `T.edges(data=True)`. If `293` is present in the list `[u, v]`, then set its `'weight'` attribute to be `1.1` just as you did above where you set the `'weight'` of the edge between `1` and `10` to be `2`. 

*** =pre_exercise_code
```{python}
# pec
import networkx as nx
import requests

# Download the pickle file.
pkl_url = 'http://s3.amazonaws.com/assets.datacamp.com/production/course_1822/datasets/ego-twitter.p'
r = requests.get(pkl_url, stream=True)

# Create a local binary file with the downloaded content.
with open('ego-twitter.p', 'wb') as f:
    f.write(r.content)

# Read the graph from local disk.
T = nx.read_gpickle('ego-twitter.p')
__T = nx.read_gpickle('ego-twitter.p')

print('The Twitter network has been loaded as `T`.')
```

*** =sample_code
```{python}
# Set the weight of the edge
____ = 2

# Iterate over all the edges (with metadata)
for u, v, d in ____:

    # Check if node 293 is involved
    if 293 in ____:
    
        # Set the weight to 1.1
        ____ = 1.1
```

*** =solution
```{python}
# Set the weight of the edge
T.edge[1][10]['weight'] = 2

# Iterate over all the edges (with metadata)
for u, v, d in T.edges(data=True):

    # Check if node 293 is involved
    if 293 in [u, v]:
    
        # Set the weight to 1.1
        T.edge[u][v]['weight'] = 1.1
```

*** =sct
```{python}
pc = """T = __T"""

for_loop = Ex().check_for_loop(0)

for_loop.check_iter().test_expression_result(pre_code=pc)
for_body = for_loop.check_body().check_if_else(0)

for_body.check_test().has_equal_value(context_vals=[293,29200000])
for_body.check_test().has_equal_value(context_vals=[2920000000,293])
for_body.check_body().has_equal_value(expr_code="T.edge[232][293]['weight']")

success_msg("Excellent job! Being able to iterate over graphs like this to explore and alter their metadata is an important skill.")
```



--- type:NormalExercise lang:python xp:100 skills:2 key:3ba794b4e4
## If else within for loop within with

In the previous exercise, you processed a file line by line for a given number of lines. What if, however, we want to to do this for the entire file? 

In this case, it would be useful to use **generators**. Generators allow users to [_lazily evaluate_ data](http://www.blog.pythonlibrary.org/2014/01/27/python-201-an-intro-to-generators/). 
This concept of _lazy evaluation_ is useful when you have to deal with very large datasets because it lets you generate values in an efficient manner by _yielding_ only chunks of data at a time instead of the whole thing at once.

In this exercise, you will define a generator function `read_large_file()` that produces a generator object which yields a single line from a file each time `next()` is called on it. The csv file `'world_dev_ind.csv'` is in your current directory for your use.

*** =instructions
- In the function `read_large_file()`, read a line from `file_object` by using the method `readline()`. Assign the result to `data`.
- In the function `read_large_file()`, `yield` the line read from the file `data`.
- In the context manager, create a generator object `gen_file` by calling your generator function `read_large_file()` and passing `file` to it.
- Print the first three lines produced by the generator object `gen_file` using `next()`.

*** =hint
- To apply a method `x()` to an object `y`, do: `y.x()`.
- Make sure you produce the line read from the file by using `yield data` inside the `while` loop.
- Pass `file` as an argument to `read_large_file()`.
- In the call to `next()`, pass the generator object `gen_file`. Pass this call to the three `print()` calls to print one line after another.

*** =pre_exercise_code
```{python}
from urllib.request import urlretrieve

filename = 'https://s3.amazonaws.com/assets.datacamp.com/production/course_1342/datasets/Indicators_red.csv'
urlretrieve(filename, 'world_dev_ind.csv')

```

*** =sample_code
```{python}
# Define read_large_file()
def read_large_file(file_object):
    """A generator function to read a large file lazily."""

    # Loop indefinitely until the end of the file
    while True:

        # Read a line from the file: data
        data = ____

        # Break if this is the end of the file
        if not data:
            break

        # Yield the line of data
        
# Open a connection to the file
with open('world_dev_ind.csv') as file:

    # Create a generator object for the file: gen_file
    gen_file = ____

    # Print the first three lines of the file
    print(____)
    print(____)
    print(____)

```

*** =solution
```{python}
# Define read_large_file()
def read_large_file(file_object):
    """A generator function to read a large file lazily."""

    # Loop indefinitely until the end of the file
    while True:

        # Read a line from the file: data
        data = file_object.readline()

        # Break if this is the end of the file
        if not data:
            break

        # Yield the line of data
        yield data

# Open a connection to the file
with open('world_dev_ind.csv') as file:

    # Create a generator object for the file: gen_file
    gen_file = read_large_file(file)

    # Print the first three lines of the file
    print(next(gen_file))
    print(next(gen_file))
    print(next(gen_file))

```

*** =sct
```{python}

# Test: read_large_file() definition
fn_def = Ex().check_function_def('read_large_file')

fn_body = fn_def.check_body()

fn_body.check_while(0).check_test().has_equal_value("Are you looping indefinitely until the end of the file?")

fn_body.check_while(0).check_body().test_function('file_object.readline')

fn_body.check_while(0).check_body().test_student_typed('yield data', not_typed_msg = "Did you yield the line of `data` at the end of your while loop?")

Ex().check_with(0).check_context(0).check_function('open', index=0).check_args(0).has_equal_value('Did you pass in the correct file name to `open()`?', error_msg='Did you pass in the correct file name to `open()`?')
Ex().check_with(0).check_context(0).has_equal_ast()
Ex().test_with(index=1, context_vals=True)

with_body = Ex().check_with(0).check_body()

with_body.test_function('read_large_file', do_eval=False)
with_body.test_function('next', index=1, do_eval=False)
#with_body.test_function('print', index=1)
with_body.test_function('next', index=2, do_eval=False)
#with_body.test_function('print', index=2)
with_body.test_function('next', index=3, do_eval=False)
#with_body.test_function('print', index=3)

success_msg("Great work!")

```
