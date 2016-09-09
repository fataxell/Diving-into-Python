# Diving-into-Python
Python lesson 2: Data types, lists, indices, other arithmetic operators, and creating your own scripts

During the second week we will dive into Python and learn some basic elements of Python programming language. We will also continue learning how to use the
Course Environment and version control with GitHub. 

## Lesson overview 

- [Intro to version control and GitHub](Lesson/intro-to-GitHub.md) (30 minutes) - HT
- [Log into GitHub](Lesson/log-in-GitHub.md) 
- [Classroom for GitHub](Lesson/GitHub-classroom.md) (5 minutes) - DW
- [Intro to some basic elements of Python (part I)](Lesson/python-basic-elements1.md) (25 minutes) - DW
- [Writing script files](Lesson/writing-scripts.md) (10-15 minutes) - DW
- [Working on the assignments](Lesson/working-on-assignment.md)
- [Play time - Exercise 2](https://github.com/Python-for-geo-people/Exercise-2) (15-20 minutes) - DW/HT
 
### Notes for instructors
We should probably provide some kind of simple template here for writing **basic** Python scripts "the right way".
It could be a simplified version of [something like this](https://gist.github.com/nhoffman/3006600).
For me, this would include (at least):

1. A comment block at the start of the script using block comments (`'''`). This should give the basic information about what the script does in a semi-Pythonic way.
2. Inline comments (`#`) for the different sections of the code (and possibly on most lines) to clearly state how the code works.

To start, I think it would be good to avoid things like using a `main()` function and some of the other Python practices that might make it harder to understand how the script works in a simple way.
Avoiding `main()` is also nice because when students use **Spyder** they will be able to see the variable values in the variable browser.


# BELOW GOES TO NEXT WEEK!

## `for` loops
Loops allow parts of code to be repeated over some number of times.

1. Let's consider an example. Suppose we want to take a word and print out each letter of the word separately. We could do the following:

    ```python
    >>> word = 'rock'
    >>> print(word[0])
    r
    >>> print(word[1])
    o
    >>> print(word[2])
    c
    >>> print(word[3])
    k
    ```
But this is a bad idea. Why? Well there are two reasons. First, it does not scale nicely for long strings, and will take forever to type in. Second, it won't work if the word is not 4 characters long.

    ```python
    >>> word = 'ore'
    >>> print(word[0])
    o
    >>> print(word[1])
    r
    >>> print(word[2])
    e
    >>> print(word[3])
    ---------------------------------------------------------------------------
    IndexError                                Traceback (most recent call last)
    <ipython-input-14-e3303df6f566> in <module>()
    ----> 1 print(word[3])

    IndexError: string index out of range
    ```

2. We could do a much better job by using a `for` loop.

    ```python
    >>> word = 'rock'
    >>> for char in word:
    ...    print(char)
    ...
    r
    o
    c
    k
    ```
Note here that the `...` is displayed in the IPython window when entering code in a loop and you do not need to type in the `...`. Not only is this shorter, but it is also more flexible. Try out a different word such as `granite`. Still works, right?
3. `for` loops in Python have the general form below.

    ```python
    for variable in collection:
        do things with variable
    ```
The `variable` can be any name you like, and the statement of the `for` loop must end with a `:`. The code that should be executed as part of the loop must be indented beneath the `for` loop, and the typical indentation is 4 spaces. There is not additional special word needed to end the loop, just change the indentation back to normal.
4. Let's consider another example.

    ```python
    >>> length = 0
    >>> for letter in 'earthquake':
    ...    length = length + 1
    ...
    >>> print('There are', length, 'letters')
    There are 10 letters
    ```
Can you follow what happens in this loop?
5. Note that the variable used in the loop, `letter` in the case above is just a normal variable and still exists after the loop has completed with the final value given to letter.

    ```python
    >>> letter = 'x'
    >>> for letter in 'fault':
    ...     print(letter)
    ...
    f
    a
    u
    l
    t
    >>> print('After the loop, letter is', letter)
    ```
6. A loop can be used to iterate over any list of values in Python. So far we have considered only character strings, but we could also write a loop that performs a calculation a specified number of times.

    ```python
    >>> for number in range(5):
    ...     print(number)
    ...
    0
    1
    2
    3
    4
    ```
What happens here? Well, in this case, we use a special function called `range()` to give us a list of 5 numbers `[0, 1, 2, 3, 4]` and then print each number in the list to the screen. When given a integer (whole number) as an argument, `range()` will produce a list of numbers with a length equal to the specified number. The list starts at zero and ends with number-1. You can learn a bit more about range by typing

    ```python
    >>> help(range)
    ```
7. Often when you use `for` loops, you are looping over the values in an array and either calculating a new value or modifying the existing values. Let's consider an example.

    ```python
    >>> import numpy as np
    >>> myarray = np.zeros(10)
    >>> print(myarray)
    [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
    >>> for i in range(10):
    ...     myarray[i] = myarray[i] + i
    ...
    >>> print(myarray)
    [ 0.  1.  2.  3.  4.  5.  6.  7.  8.  9.]
    ```
So, what happened? We first create and array of length 10 and fill it with zeros using `np.zeros()`. Then, we loop over 10 values using the `range()` function and add each value to the existing location in `myarray`. What would happen if we ran this for loop a second time?

