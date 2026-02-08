# Lab 04: Data Structures 

## Problem 1: Finding Common Items

**My Prompt:** You are a Senior Python Developer. I have two very large lists of product IDs from different suppliers. I need to find the common elements between them efficiently. The order of the final list does not matter. 

Task: Recommend the most efficient Python data structure and method to find these common items and explain why it is better than a standard list loop. State the recommended data structure clearly, explain the reasoning, and provide the Python code for the function.

**AI's Corrected Code:**
```python
def find_common_elements(list1, list2):
    """Find the common elements between two lists.

    This function should take two lists and return a new list containing
    only the elements that are present in both input lists. The final
    list can be in any order.

    Parameters
    ----------
    list1 : list
        The first list of elements.
    list2 : list
        The second list of elements.

    Returns
    -------
    list
        A list of elements common to both list1 and list2.
    """
    return list(set(list1) & set(list2))
```
**Reasoning:**
Converts both lists to sets (O(n + m) time).
Uses the & operator for set intersection (optimized C code).
Converts result back to a list (per the return requirement).



## Problem 2: User Profile Lookup

**My Prompt:** Act as a Backend Software Architect focused on high-performance data retrieval.I have a list of user profile dictionaries, each containing a unique 'name', 'age', and 'email'. I need to frequently look up a user's full profile using their name.

Task: Recommend the best Python data structure for mapping unique usernames to their profile data to ensure $O(1)$ lookup time.

Identify the data structure, explain why it is superior to searching through a list, and provide the code to implement the lookup.

**AI's Corrected Code:**
```python
def find_user_by_name(users, name):
    """Find a user's profile by name from a list of user data.

    Parameters
    ----------
    users : list of dict
        A list of dictionaries, where each dictionary represents a user
        and has 'name', 'age', and 'email' keys. It is recommended to
        convert this list into a more efficient data structure for lookups.
    name : str
        The name of the user to find.

    Returns
    -------
    dict or None
        The dictionary of the found user, or None if no user is found.
    """
    user_map = {u['name']: u for u in users if isinstance(u, dict) and 'name' in u}
    return user_map.get(name)
```
**Reasoning:** 
Using a dictionary comprehension with a conditional filter. This allows to build a high-performance lookup table ($O(1)$) while simultaneously verifying that each item is a valid dictionary containing the required 'name' key. This is much more efficient than searching the original list every time, which would have a time complexity of $O(n)$.



## Problem 3: Listing even numbers in order

**My Prompt:**
Act as a Python Developer focused on readable and efficient code.

I am given a list of integers representing sensor readings. I need to filter this list to include only the even numbers and they must be presented in the exact same order they were received.

Task: Recommend the best data structure and approach for filtering these items while preserving order. 
Provide the Python code, explain the reasoning and thought process. 

**AI's Corrected Code:**
```python
def get_list_of_even_numbers(numbers):
    """Return a new list containing only the even numbers from the input list.

    The order of the numbers in the output list must be the same as the
    order of the even numbers in the input list.

    Parameters
    ----------
    numbers : list of int
        A list of integers.

    Returns
    -------
    list of int
        A new list containing only the even integers from the input list.
    """
    # Preserve input order; filter only integers that are even.
    return [n for n in numbers if isinstance(n, int) and n % 2 == 0]
```

**Reasoning:**
Order Preservation: Lists in Python are ordered, which is essential for sensor data that must be reported in the sequence it was received.

Filtering: List comprehensions provide an efficient $O(n)$ way to iterate through the data and filter out only the even numbers in a single step.

Data Integrity: By adding a check for isinstance(n, int), the code ensures it only attempts mathematical operations on valid integers.