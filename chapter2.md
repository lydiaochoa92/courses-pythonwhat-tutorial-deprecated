---
title       : Testing functions and packages
description : Insert the chapter description here

--- type:NormalExercise lang:python xp:100 skills:2 key:c422ee929b
## function calls

Out of the box, Python offers a bunch of built-in functions to make your life as a data scientist easier. You already know two such functions: [`print()`](https://docs.python.org/3/library/functions.html#print) and [`type()`](https://docs.python.org/3/library/functions.html#type). You've also used the functions [`str()`](https://docs.python.org/3/library/functions.html#func-str), [`int()`](https://docs.python.org/3/library/functions.html#int), [`bool()`](https://docs.python.org/3/library/functions.html#bool) and [`float()`](https://docs.python.org/3/library/functions.html#float) to switch between data type. These are built-in functions as well.

Calling a function is easy. To get the type of `3.0` and store the output as a new variable, `result`, you can use the following:

```
result = type(3.0)
```

The general recipe for calling functions is thus:

```
output = function_name(input)
```

*** =instructions
- Use [`print()`](https://docs.python.org/3/library/functions.html#print) in combination with [`type()`](https://docs.python.org/3/library/functions.html#type) to print out the type of `var1`.
- Use [`len()`](https://docs.python.org/3/library/functions.html#len) to get the length of the list `var1`. Wrap it in a [`print()`](https://docs.python.org/3/library/functions.html#print) call to directly print it out.
- Use [`int()`](https://docs.python.org/3/library/functions.html#int) to convert `var2` to an integer. Store the output as `out2`.

*** =hint
- Call the [`type()`](https://docs.python.org/3/library/functions.html#type) function like this: `type(var1)`.
- Call [`print()`](https://docs.python.org/3/library/functions.html#print) like you did so many times before. Simply put the variable you want to print in parentheses.
- `int(x)` will convert `x` to an integer.

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Create variables var1 and var2
var1 = [1, 2, 3, 4]
var2 = True

# Print out type of var1


# Print out length of var1


# Convert var2 to an integer: out2

```

*** =solution
```{python}
# Create variables var1 and var2
var1 = [1, 2, 3, 4]
var2 = True

# Print out type of var1
print(type(var1))

# Print out length of var1
print(len(var1))

# Convert var2 to an integer: out2
out2 = int(var2)
```

*** =sct
```{python}
msg = "You don't have to change or remove the predefined variables."
test_object("var1", undefined_msg = msg, incorrect_msg = msg)
test_object("var2", undefined_msg = msg, incorrect_msg = msg)

msg = "Make sure to print out the type of `var1` like this: `print(type(var1))`."
test_function("type", 1, incorrect_msg = msg)
test_function("print", 1, incorrect_msg = msg)

msg = "Make sure to print out the length of `var1` like this: `print(len(var1))`."
test_function("len", 1, incorrect_msg = msg)
test_function("print", 2, incorrect_msg = msg)

test_object("out2", do_eval = False)

test_function("int", not_called_msg = "Use [`int()`](https://docs.python.org/3/library/functions.html#int) to make an integer of `var2` and assign to `out2`.",
                     incorrect_msg = "Use [`int()`](https://docs.python.org/3/library/functions.html#int) with the correct variables. You should pass `var2` to it."
)
test_object("out2", incorrect_msg = "Make sure to assign the correct value to `out2`.")
success_msg("Great job! The [`len()`](https://docs.python.org/3/library/functions.html#len) function is extremely useful: it also works on strings to count the number of characters!")
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
## Testing method calls (TODO: appending to list)


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
