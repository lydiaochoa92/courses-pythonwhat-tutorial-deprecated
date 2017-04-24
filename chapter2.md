---
title       : Testing functions and packages
description : Insert the chapter description here

--- type:NormalExercise lang:python xp:100 skills:2 key:c422ee929b
## function calls

This exercise will consider two ways in which a function call can be used:

1. a straightforward expression. e.g. `max(1,2)`.
2. within another function call. e.g. `print(type(3.0))`.

The SCT for the example below will show how to test both these types of calls.

**Example exercise below**

Calling a function is easy. To get the type of `3.0` and store the output as a new variable, `result`, you can use the following:

```
result = type(3.0)
```

The general recipe for calling functions is thus:

```
output = function_name(input)
```

*** =instructions
- Use `int()` to convert `var1` to an integer. Store the output as `out`.
- Use `print()` in combination with `type()` to print out the type of `var2`.
- Use `print()` in combination with `len()` to get the length of the list `var2`.

*** =hint

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Create variables var1 and var2
var1 = True
var2 = [1, 2, 3, 4]

# Convert var1 to an integer: out


# Print out type of var2


# Print out length of var2


```

*** =solution
```{python}
# Create variables var1 and var2
var1 = True
var2 = [1, 2, 3, 4]

# Convert var1 to an integer: out
out = int(var1)

# Print out type of var2
print(type(var2))

# Print out length of var2
print(len(var2))
```

*** =sct
```{python}

# test instruction 1, int(var1) ----------------------------------------------------------------------
msg_missing_int = "Use `int()` to make an integer of `var1` and assign to `out`."
msg_incorrect_int = "Use `int()` with the correct variables. You should pass `var1` to it."

(Ex() 
    # SCT below will fail the submission if int() wasn't used.
    # if it was used, it selects the code for the 1st int() call
    .check_function("int", 0, missing_msg =  msg_missing_int)
    # SCT below checks that the contents of the function call have the same
    # abstract syntax tree (AST) code representation in the submission and solution
    # (e.g. `type(var1)` in solution matches submission)
    .has_equal_ast(msg_incorrect_int))

# use test_object after checking the int() call, to make sure it returned the correct results.
Ex().test_object("out", incorrect_msg = "Make sure to assign the correct value to `out`.")

# test instruction 2 ---------------------------------------------------------------------------------
msg = "Make sure to print out the type of `var2` like this: `print(type(var2))`."
# SCT below gets the first instance where type was used, then gets its first argument.
#     has_equal_value runs the code for that argument (i.e. `var2` in the solution code), and
#     verifies the submission and solution results are the equal.
Ex().check_function("type", 0).check_args(0).has_equal_value(msg)

# Similar to above, but the first argument to print should be equivalent to type(var2),
# which we check using has_equal_value
Ex().check_function("print", 0).check_args(0).has_equal_value(msg)

# test instruction 3 ---------------------------------------------------------------------------------
msg = "Make sure to print out the length of `var2` like this: `print(len(var2))`."
# SCTs below are similar to above, except they test the value of the whole function call
# rather than a single argument
Ex().check_function("len", 0).has_equal_value(msg)
Ex().check_function("print", 1).has_equal_value(msg)
```


--- type:NormalExercise lang:python xp:100 skills:2 key:7432a6376f
## Import package

As a data scientist, some notions of geometry never hurt. Let's refresh some of the basics.

For a fancy clustering algorithm, you want to find the circumference $C$ and area $A$ of a circle. When the radius of the circle is `r`, you can calculate $C$ and $A$ as:

$$C = 2 \pi r$$
$$A = \pi r^2 $$

To use the constant `pi`, you'll need the `math` package. A variable `r` is already coded in the script. Fill in the code to calculate `C` and `A` and see how the [`print()`](https://docs.python.org/3/library/functions.html#print) functions create some nice printouts.

*** =instructions
- Import the `math` package. Now you can access the constant `pi` with `math.pi`.
- Calculate the circumference of the circle and store it in `C`.
- Calculate the area of the circle and store it in `A`.

*** =hint
- You can simply use `import math`, and then refer to `pi` with `math.pi`.
- Use the equation in the assignment to find `C`. Use `*`
- Use the equation in the assignment to find `A`. Use `*` and `**`.

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Definition of radius
r = 0.43

# Import the math package


# Calculate C
C = 0

# Calculate A
A = 0

# Build printout
print("Circumference: " + str(C))
print("Area: " + str(A))
```

*** =solution
```{python}
# Definition of radius
r = 0.43

# Import the math package
import math

# Calculate C
C = 2 * r * math.pi

# Calculate A
A = math.pi * r ** 2

# Build printout
print("Circumference: " + str(C))
print("Area: " + str(A))
```

*** =sct
```{python}
msg = "You don't have to change or remove the predefined variables."
test_object("r", undefined_msg = msg, incorrect_msg = msg)
test_import("math", same_as = False)
test_object("C", incorrect_msg = "Your calculation of `C` is not quite correct. You should use `pi` of the `math` package using the dot notation (`.`).")
test_object("A", incorrect_msg = "Your calculation of `A` is not quite correct. You should use `pi` of the `math` package using the dot notation (`.`).")
msg = "You don't have to change or remove the predefined `print()` functions at the end."
test_function("print", 1, not_called_msg = msg, incorrect_msg = msg)
test_function("print", 2, not_called_msg = msg, incorrect_msg = msg)
success_msg("Nice!")
```



--- type:NormalExercise lang:python xp:100 skills:2 key:fe65eff50a
## Import y from x

General imports, like `import math`, make **all** functionality from the `math` package available to you. However, if you decide to only use a specific part of a package, you can always make your import more selective:

```
from math import pi
```

Let's say the Moon's orbit around planet Earth is a perfect circle, with a radius `r` (in km) that is defined in the script.

*** =instructions
- Perform a selective import from the `math` package where you only import the `radians` function.
- Calculate the distance travelled by the Moon over 12 degrees of its orbit. Assign the result to `dist`. You can calculate this as $r * \phi$, where $r$ is the radius and $\phi$ is the angle in radians. To convert an angle in degrees to an angle in radians, use the [`radians()`](https://docs.python.org/3/library/math.html#math.radians) function, which you just imported.
- Print out `dist`.

*** =hint
- Use `from math import radians` to do the selective import.
- You can simply use the [`radians()`](https://docs.python.org/3/library/math.html#math.radians) function now. Pass the function the number 12 to get the angle in radians.
- To print out a variable `x`, simply type `print(x)`.

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Definition of radius
r = 192500

# Import radians function of math package


# Travel distance of Moon if 12 degrees. Store in dist.


# Print out dist

```

*** =solution
```{python}
# Definition of radius
r = 192500

# Import radians function of math package
from math import radians

# Travel distance of Moon if 12 degrees. Store in dist.
dist = r * radians(12)

# Print out dist
print(dist)
```

*** =sct
```{python}
msg = "You don't have to change or remove the predefined variables."
test_object("r", undefined_msg = msg, incorrect_msg = msg)

test_import("math.radians", not_imported_msg = "Be sure to import [`radians()`](https://docs.python.org/3/library/math.html#math.radians) from the `math` package. You should use the `from ___ import ___` notation.", incorrect_as_msg = "Don't set any alias for [`radians()`](https://docs.python.org/3/library/math.html#math.radians). Just type `from math import radians`.")

test_object("dist", do_eval = False)
test_function("math.radians", 1, incorrect_msg = "Call [`radians()`](https://docs.python.org/3/library/math.html#math.radians) with argument `12`.", not_called_msg = "Your calculation of `dist` is not quite correct. You should use [`radians()`](https://docs.python.org/3/library/math.html#math.radians) from the `math` package. If you imported correctly, you don't have to use the dot (`.`) notation.")
test_object("dist", incorrect_msg = "Assign the result of your calculations to `dist`.")

test_function("print", incorrect_msg = "Make sure to print out `dist` using `print(dist)`.")

success_msg("Nice! Head over to the next exercise.")
```

--- type:NormalExercise lang:python xp:100 skills:2 key:497811536f
## Testing method calls

Often exercises can get pretty hairy. For example, checking a chain of indexing a method calls.
For example, the chain below...

```
x[0].append('c')
```

Gets the first element of `x`, and then calls that element's append method.
In the example below, we should how to use `has_equal_ast` as a quick and dirty
way to examine this style of method call chaining.


*** =instructions

*** =hint

*** =pre_exercise_code
```{python}

```

*** =sample_code
```{python}
x = [['a', 'b'],['x', 'y']]

x[0].append('c')
```

*** =solution
```{python}
x = [['a', 'b'],['x', 'y']]

x[0].append('c')
```

*** =sct
```{python}
# for the SCT below, 
#    code specifies the code whose AST must be in the solution
#    exact = False, says that it just needs to be contained in the solution somewhere,
#            like using 'a' in 'a b c' rather than 'a' == 'a b c'
#
# note that these submissions would work also:
#   x[0].append("c")
#   x[0].append( """c""" )
# but these solutions fail (produce different ASTs)
#   x[0] += ['c']
code = "x[0].append('c')"
msg = "Make sure you used `%s`" % code
Ex().has_equal_ast(code=code, exact=False)

# note that you can also check an earlier piece of a statement
# to visualize ast, see:
#       https://sqlwhat-viewer.herokuapp.com/static/index.html#/editor?grammar=python
#
# comment SCTs above to see these in action...
Ex().has_equal_ast("did you use `x[0]`?", code = "x[0]", exact = False)
Ex().has_equal_ast("did you use `x[0].append`?", code = "x[0].append", exact = False)
```

--- type:NormalExercise lang:python xp:100 skills:2 key:fd9099d8c4
## Testing function call result

In this example, we have the student define a custom function, in which they should call `max`.
The order of the arguments to `max` don't matter, so both versions below should pass:

* `max(input, 0)`
* `max(0, input)`

Note that the variable `input` is a parameter in the custom function, so it is not defined after running
the solution script. In order to test the output of the `max` function call, we use the SCT to define `input`
beforehand.


*** =instructions

*** =hint

*** =pre_exercise_code
```{python}

```

*** =sample_code
```{python}
def relu(input):
    # order of arguments doesn't matter
    output = max(____, ____)
    
    return(output)
```

*** =solution
```{python}
def relu(input):
    # order of arguments doesn't matter
    output = max(0, input)
    
    return(output)
```

*** =sct
```{python}
# Note: check_function_def explained in chapter user defined functions
#       the key here is that the line below gets the body of the function `relu`
relu_body = Ex().check_function_def('relu').check_body()
# Get the 'max' function, then test its output with different values of the input variable
# see http://pythonwhat.readthedocs.io/en/latest/expression_tests.html
relu_body.check_function('max', 0, signature = False) \
         .has_equal_value(extra_env = {'input': 1}) \
         .has_equal_value(extra_env = {'input': -.5})

```
