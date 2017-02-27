---
title       : Tutorial
description : Become a pythonwhat wizard
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf


--- type:NormalExercise lang:python xp:100 skills:2 key:4bf65ad83e
## Testing objects (int)

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
