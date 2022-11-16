# Decorators

Decorators allow us to change the functionality of a function, method, or class without having to directly use subclasses or change the source of the function. This processes is called metaprogramming because a part of the program tries to modify another part of the program at compile time. Decorators are used as syntactic sugar to make code look cleaner. Functions and methods are called *callable* as they can be called.

* Functions are objects: Functions can be passed around and returned. Functions have all the attributes of an object. We can assign them to variables and pass them as arguments to other functions as arguments.
* Decorator takes a function, extends it, and returns. A function can return a function.
* Functions can be extended by wrapping them.
* Parameters can be used with decorators.

### First Class Function
We can assign a function to a variable, pass a function as an argument into another function, and return a function as a result of another function. 

An example of this would be:

**First Class Function Example 1**

```
def sum(num_1, num_2):
    """Adds two numbers"""
    return num_1 + num_2

add = sum 
print(add(11, 3))
```

**First Class Function Example 2**
```
def add(num_1, num_2):
    return num_1 + num_2

def multiply(num_1, num_2):
    return num_1 * num_2

def perform_binary_op(func, num_1, num_2):
    return func(num_1, num_2)

print(perform_binary_op(add, 7, 3))
print(perform_binary_op(multiply, 7, 3))

```

**First Class Function Example 3**
```
def double_plus_one(num):
    """ Returns 1 plus double the value of the argument. """
    def double(n):
        """ Returns double the value of the argument. """
        return n * 2
    return double(num) + 1
print(double_plus_one(5))     # Expected results: 11
```

* Double is the inner function, and can be used there. It does not exist outside the function, which means if we tried calling it, we'll get a NameError. However, it is possible to access it by returning it from the function.


**First Class Function Example 4**

In the function call: `get_double_func()`
* The parentheses means that we are calling the get_double_function() which executes its code. 
* Without parentheses would be referring to the function as an object. 

**Why we do it: Why define inner functions?**
* We mainly want to define an inner function to create a **closure**. 
* A closure is an inner function that has "captured" one or more of the outer function's local variables. A captured variable is accessible to the closure for as long as the closure exists. 

A closure looks like this:

```
def get_multiplier_by(factor):
    def multiplier(n):
        return n * factor
    return multiplier

mult7 = get_multiplier_by(7)
print(mult7(9))
```

# Decorators

Decorators give us additional behavior to a function without modifying the function itself.

**Example 1: Generic Decorator**

```
def generic_decorator(func):
    def wrapper():
        print("additional behavior before the function call")
        result = func()
        print("additional behavior after the function call")
        return result
    return wrapper

@generic_decorator
def greeting():
    return "hello world"

print(greeting())
```

1. define the decorator function. 
2. define an inner "wrapper" function that wraps up the original function together with the additional behavior we want. 
3. returns the wrapper
4. define the function we're going to decorate, which prints out "hello world". 
5. add special syntax for the generic_decorator using `@generic_decorator`

**Arguments:**
Now what if the function takes in arguments? The problem is we might want to use the same decorator for different functions that take in different numbers of arguments. What should we do then? We can use ***args** and ****kwargs**. 

Down below we can call `help(add_three)` without the decorator to see the docstring. However, if there is a decorator, we will get `wrapper(*args, **kwargs)` because the wrapper obscuring the `add_three` metadata of the function.
We can use the `functools` module to import a decorator that Python provides. 

```
import functools

def generic_decorator(func):
    """Adds printing of generic messages to func"""
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print("additional behavior before the function call")
        result = func(*args, **kwargs)
        print("additional behavior after the function call")
        return result
    return wrapper


@generic_decorator
def increment(num):
    """Increments num by 1"""
    return num + 1

@generic_decorator
def add_three(num_1, num_2, num_3):
    """Returns the sum of the three arguments"""
    return num_1 + num_2 + num_3

help(add_three)

x = add_three(2,14,1)
print(x)
```


### Real World Examples:

* Time measurement: A decorator can be used to measure how long a function takes to execute. 

```
def myFunction(n):
    time.sleep(n)

import time                                                                                                               
                                                                                                                          
def measure_time(func):                                                                                                   
                                                                                                                          
  def wrapper(*arg):                                                                                                      
      t = time.time()                                                                                                     
      res = func(*arg)                                                                                                    
      print("Function took " + str(time.time()-t) + " seconds to run")                                                    
      return res                                                                                                          
                                                                                                                          
  return wrapper                                                                                                          
                                                                                                                          
@measure_time                                                                                                             
def myFunction(n):                                                                                                        
  time.sleep(n)                                                                                                           
                                                                                                                          
if __name__ == "__main__":                                                                                                
    myFunction(2)   
```

* Web app: When we build a web app in Flask, we always write url routes. Every route is a certain page in the web app. Opening the page /about my call the about_page() method.
```
@app.route("/about")
def about_page():
    return "Website about the zoo."
```
The @ symbol is used for decoration.

There are functions that take other functions as arguments called *higher order* functions.

```
def inc(x):
    return x + 1

def dec(x):
    return x - 1

def operate(func, x):
    result = func(x)
    return result
```

Here is what we will get:
```
>>> operate(inc,3)
4
>>> operate(dec,3)
2
```

### Example of assigning function to a variable:
```
def site():
    print("The Alexa Website")

website = site

print(f"{site = }")
site()
print(f"{website = }")
website()
```
Results:
```
site = <function site at 0x7fd5e4107d90>
The Alexa Website
website = <function site at 0x7fd5e4107d90>
The Alexa Website
```

### Problems
```
# Define a decorator that prints five '%' signs before and after the function execution.

def dollar(func):
    def wrapper():
        print("$$$$$")
        func()
        print("$$$$$")
    return wrapper

def hello():
    print("Hello World!")

hello = dollar(hello)
hello()
```
Results:
```
$$$$$
Hello World!
$$$$$
```

Here is how we apply it:

```
@dollar
def the_border():
    print("Alexa ClubHouse")

the_border()
```
The Results:

```
$$$$$
Alexa ClubHouse
$$$$$
```

