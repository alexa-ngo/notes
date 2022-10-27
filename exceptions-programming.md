# Exceptions

Exceptions are special objects used to manage errors that come up when executing a program. When a program does not know what to do next when it is executing, it creates an exception object. 
* If we write code to *handle* this exception, the code will keep running. 
* If we don't handle the exception, the program will stop and show a *traceback*, which will include a report of the except that was raised. 
* Using Exceptions to Prevent Crashes 

### try-except blocks
We handle exceptions with try-except blocks. A try-except block ask the program to do something, and it will tell the language what to do if an exception is raised. 

**Here is a try-except block using Python**
```
try:
  print(x)
except NameError:
  print("Variable x is not defined")
except:
  print("Something else went wrong")
```
### Handling the ZeroDivisionError Exception

Let's try dividing 5 by zero! 
```
Traceback (most recent call last):
  File "division_calculator.py", line 1, in <module>
    print(5/0)
ZeroDivisionError: division by zero
```
* The ZeroDivisionError is an exception object and it is created when the program can't do what we ask it to. Python will stop the program and tell us the kind of exception that was raised. We can use this information and enhance our program. We can tell Python what to do when this kind of exception occurs and so if it happens again, we can be prepared.

### The else Block

```
try: 
  answer = int(first_number) / int(second_number)
except ZeroDivisionError:
  print("You can't divide by 0!")
else: 
  print(answer)
```

###How the try-except-else block works:
1. ```try``` block: the program tries to run the code in the try block. The only code that should be in the try block is code that might cause an error to be raised.
2. ```else``` block: sometimes we'll have additional code that should run only if the try block was successful. This code goes in the else block.
3. ```except``` block: the except block will tell the program what to do in case a certain exception arises when it tries to run the code in the try block. 

**Example #1: opening file with try and except**
```
def count_words(filename):
    """ Count the approximate number of words in a file."""

    try:
        with open(filename, encoding='utf-8') as f:
            contents = f.read()
    except FileNotFoundError:
        print(f"Sorry, the file {filename} does not exist.")
    else:
        # Count the approximate number of words in the file.
        words = contents.split()
        num_words = len(words)
        print(f"The file {filename} has about {num_words} words.")

filenames = ['filename.txt', 'news.txt', 'computer.txt']
for filename in filenames:
    count_words(filename)
```

We can spice up this program like this.. where we go through a list of files!