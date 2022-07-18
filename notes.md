# Functions  
Author: Elia Deppe  
Editor: Name Here  

## Defining Functions

So far we know a few built-in functions, like `print`, `input`, `int`, `len`, etc. Each of these functions perform a single, specific, well-defined task. However, the standard library is quite small, and we may need functions to do specific jobs for our program that aren't covered by the standard library. This is where **custom functions** come in to play.

Below is an example of a custom function that returns the square of a number.

```python
def square(x):
    """
    calculate the square of a number
    
    :param x: integer. number to be squared.
    :return: integer. the number squared.
    """
    return x ** 2

```

The `def` keyword signals to the interpreter the start of a function definition. This is followed by the name of the function, an open and closed parenthesis, and any parameters inside. Bodies of a function are indented, just like if Statements and for Loops.

### Docstrings

The lines you see that contains the triple quoted strings are known as docstrings. All functions should have a docstring. This should contain a description of the function, along with a description of any parameters or return values.

### Return Values

Often times we want functions to result into some value. This is where the `return` keyword comes in. By using `return` we are able to return a value from a function, effectively giving it a result.

When a return statement is executed, the function exits immediately, and will not run any more code inside the function, even if there is more code past the return line.

### Local Variables

Variables within a function are known as local variables. These variables are locally scoped to the function, meaning they are inacessible outside the function. This allows us to use same variable names in different functions. It also means data is not shared between functions unless explicitly declared done so via arguments.

### Code
Create the following functions according to the specifications listed below:

#### even_or_odd  
> Define a function that accepts one parameter, x, and determines if this function is even or odd. The function should return the value 'even' if the number is even and 'odd' if the number is odd.

#### reverse
> Define a function that accepts one parameter, text, and returns the reverse of that string. If text = 'cat', then the function should return 'tac'

#### prime
> Define a function that accepts one parameter, x, and determines if the number is prime or not. A number is prime if the number is divisible by 1 and itself, and only those two values. 1 is not a prime number.

#### palindrome
> Define a function that determines if a given string is a palindrome or not. A palindrome is a word that is the same backwards as it is forwards. 'madam' and 'radar' are considered to be palindromes.

#### pangram
> Define a function that determines if a given string is a pangram or not. A pangram is a word or sentence that contain every letter of the alphabet.

## Functions with Multiple Parameters

```python
def maximum(value1, value2, value3):
    """
    Return the maximum of 3 values.
    
    :param value1: The first value passed in.
    :param value2: The second value passed in.
    :param value3: The third value passed in.
    :returns: The maximum of 3 values.
    """
    max_value = value1
    
    if value2 > max_value:
        max_value = value2
    if value3 > max_value:
        max_value = value3
        
    return value3
```

### Code

#### minimum
> Define a function that accepts 5 arguments as parameters. Find the minimum value of these five arguments, and return that value.

#### in_range
> Define a function that accepts 3 parameters, x, hi, and lo. Determine if x is within or outside the range between lo and hi. Return 'in range' if so, otherwise return 'out of range'

#### gcd
> Define a function that accepts 2 parameters, x and y. Find the greates common divisor between x and y, and return that value.

## Random-Number Generation

### Rolling a Six-Sided Die
```python
import random

for roll in range(10):
    print(random.randint(1, 6), end=' ')
```

Which results in:

```python
4 2 5 1 6 3 2 4 5 2
```

Or any combination of 10 random numbers between 1 and 6.

In order to use random numbers, we must first import the random module. Once that is done, we can access said module for its functions like `randint`, `randrange`, and other functions.

### Code

Mini Project: In this project you will be examining random probability and how scale can affect distribution of results. Create a program according to the following specifications. Be sure to utilize functions when creating said program.

Create a program that will track the number of dice rolls made by the computer. The program will display the results of 3 different sets of roles:
- A set of 10 dice rolls.
- A set of 10000 dice rolls.
- A set of 1000000 dice rolls.

For each set, be sure to output the following:
1. The number of rolls for each face of the die.
2. The percentage of rolls for each face of the die.
3. The face that showed the most (if multiple, show all)

## Python Standard Library

There are plenty of modules out there waiting to be discovered and used. Lets take a look here: https://docs.python.org/3/library/

## Default Parameter Values

```python
def rectangle_area(length=2, width=2):
    """
    Return the area of a rectangle.
    
    :param length: The length of the rectangle.
    :param width: The width of the rectangle.
    :returns: The area of the rectangle.
    """
    return length * width
```

When defining a function, you can specify that a parameter has a default value. When calling the function, if you omit that parameter, the default value will be used.

Default parameters must be set to the right of any parameters that do not have defaults.

To call the above function, we would right:

```python
print(rectangle_area(length=5, width=20))
```

## Arbitrary Argument Lists

Functions with arbitrary argument lists, such as built-in functions `min` and `max`, can receive any number of arguments.

```python
print(max(4, 2, 1, 5))
print(max(2, 1))
print(max(2, 4, 5, 8, 4, 1, 9, 5, 8, 4))
```

We can create an arbitrary argument list like so:

```python
def average(*args):
    return sum(args) / len(args)
```

If we are passing a list, then we would need to unpack those arguments before passing them to the function. This can be done like so:

```python
grades = [88, 90, 75, 95, 84]

print(average(*grades))
```

The * operator unpacks the list to be passed to the function.

## Methods: Functions that Belong to Objects

A **method** is simply a function that you call on an object using the form:

`object_name.method_name(arguments)`

Methods can result in a value or modify the original object. Which one depends on the method being used.

Here are some example string methods:

```python
>>> text = 'Hello my friend!'
>>> text.lower()
'hello my friend!'
>>> text.upper()
'HELLO MY FRIEND!'
>>> text
'Hello my friend!'
```

Note that text itself is unchanged, and `lower` and `upper` have returned a copy of the string in its lowercase and uppercase form respectively.

## Scope Rules

Each identifier has a scope that determines where you can use it in your program. For that portion of the program, the identifier is said to be in scope.

### Local Scope

A local variable's identifier has local scope. It's "in scope" only from it's definition to the end of the function's block. It "goes out of scope" when the function returns to it's caller. So, a local variable can only be used inside the function that defines it.

### Global Scope

Identifiers defined outside any function (or class) have **global scope** - These may include functions, variables, and classes. Variables with global scope are known as global variables. Identifiers with global scope can be used in a .py file or interactive session anywhere after they're defined.

Global variables can be accessed inside a function:

```python
x = 7

def access_global():
    print('x printed from access_global:', x)
```

However, by default, you can not modify a global variable in a function, instead this will create a new variable.

## `import`: A Deeper Look

You've imported modules so far with a statement like:

`import module_name`

You can also import a specific identifier from the module like so:

`from module_name import identifier`

This will allow you to use specific functionality from a module without needing to import the entire thing.

If you wish to import multiple identifiers, then you use a comma separated list:

`from module_name import id1, id2, id3, ...`

When importing via the `from` statement, you do not need to reference the module name when using the identifier.

You can technically import everything from a module using the * identifier, representing all.

`from module_name import *`

However, this may not always be efficient or make sense. It may also cause you to lose access to certain identifiers that you may want to use.

## Recursion

Let's write a program to perform a famous mathematical calculation. Consider the factorial of a positive integer n, which is written n! and pronounced "n factorial." This is the product:

`n * (n - 1) * (n-2) * ... * 1`

with 1! equal to 1 and 0! defined to be 1. For example 5! is 5 * 4 * 3 * 2 * 1 which results in 120.

### Iterative Approach

```python
factorial = 1

for number in range(5, 0, -1):
    factorial *= number

print(factorial)
```

Recursive problem-solving approaches have several elements in common. When you call a recursive function to solve a problem, it's actually capable of solving onl the simplest case(s), or **base case(s)**. If you call the function with a base case, it immediately returns a result. If you call the function with a more complex problem it typically divides the problem into two pieces: one that it knows how to do and one that it does not know how to do. Because this new problem resembles the original, the function calls a fresh copy of itself to work on the smaller problem - this is referred to as a recursive call and is also called the recursion step.

```python
def factorial(number):
    if number <= 1:
        return 1
    else:
        return number * factorial(number - 1)  # recursive call
```

### Code

#### natural_numbers
> Create a recursive function that will print all natural numbers up till a given parameter x. Natural numbers are all integer numbers.

#### prime
> Create a recursive function that will find if a number, x, is prime or not.

#### fibonacci
> Create a recursive function that accepts one argument n, and prints the fibonacci sequence up till the nth number.
