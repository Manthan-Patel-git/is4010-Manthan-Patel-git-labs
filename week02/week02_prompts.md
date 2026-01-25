# Lab 02: Prompt Engineering Solutions

## Problem 1: Debugging

**My Prompt:** You are a Senior Python Developer. I have a function that is supposed to sum only even numbers, but it's currently summing odd numbers instead. Please find and fix the logical error. Provide the corrected code in a single Python block followed by a brief explanation of the fix.

**AI's Corrected Code:**
```python
def sum_of_evens(numbers):
    """Calculate the sum of all even numbers in a list.

    Parameters
    ----------
    numbers : list of int
        A list of integers.

    Returns
    -------
    int
        The sum of all even numbers in the list.
    """
    total = 0
    for num in numbers:
        if num % 2 == 0:  # Fixed: check if even (remainder 0), not odd
            total += num
    return total 
```
  
**What I learned:** num % 2 == 1 checks for odd numbers (remainder),  while num % 2 == 0 checks for even numbers (remainder 0).



## Problem 2: Refactoring

**My Prompt:** I have a function that uses a for i in range loop to filter a list of user dictionaries based on age. Act as a Senior Python Developer who prioritizes clean and understandable code. Task: Refactor this function to be more concise and "Pythonic," specifically using a list comprehension, better iteration patterns, and clearer variable names. Provide the refactored code block and a short list of the specific changes you made.

**AI's Corrected Code:**
```python
def get_names_of_adults(users):
    """Given a list of user dictionaries, returns a list of names of users
    who are 18 or older.

    Parameters
    ----------
    users : list of dict
        List of user dictionaries with 'name' and 'age' keys.

    Returns
    -------
    list of str
        Names of users who are 18 or older.
    """
    return [user['name'] for user in users if user['age'] >= 18]
```

**What I learned:** You can replace manual loop with list comprehension so the code is more concise, readable, and Pythonic. Also learned that you should replace for i in range(len(users)) with direct iteration for user in users to make it clearer.



## Problem 3: Documenting a function

**My Prompt:** I have a Python function calculate_area(length, width) that calculates the area of a rectangle and raises a ValueError if inputs are non-positive. Act as a Technical Documentation Specialist. 
Task: Write a professional NumPy-style docstring for this function. 
Provide the full code block including the new docstring. Ensure it has sections for Parameters, Returns, and Raises.

**AI's Corrected Code:**
```python
def calculate_area(length, width):
    """Calculate the area of a rectangle.

    Parameters
    ----------
    length : float
        The length of the rectangle. Must be a positive number.
    width : float
        The width of the rectangle. Must be a positive number.

    Returns
    -------
    float
        The area of the rectangle (length × width).

    Raises
    ------
    ValueError
        If length or width is less than or equal to zero.

    Examples
    --------
    >>> calculate_area(5, 4)
    20
    >>> calculate_area(0, 5)
    Traceback (most recent call last):
        ...
    ValueError: Length and width must be positive numbers.
    """
    if length <= 0 or width <= 0:
        raise ValueError("Length and width must be positive numbers.")
    return length * width
```

**What I learned:** NumPy-style docstrings provide an organized way to document code, which makes it easier for other developers to understand what inputs are expected, the function outputs, and what errors might occur.