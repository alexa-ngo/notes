#Recursion

Recursion is the process in which a function calls itself directly or indirectly, and the corresponding function is called a recursive function. In recursion, we use recursion to call itself to solve part of the problem until it reaches a base case, and then the function will stop calling itself. If we don't have a base case, the program will keep going until the computer runs out of memory. 

The return statement exits the function. The flow of execution immediately returns to the caller, and the remaining lines of the function don't run. We have to watch out for an infinite recursion is when recursion never reaches a base case, and the program never terminates.

```
def countdown(n):
    if n<=0:
        print('Blastoff!')
    else:
        print(n)
        countdown(n-1)
```

###Stack Diagrams
* Frame: every time a function gets called a frame is created to contain the local variable and parameter of the function. 

**Stack Diagram**

| __main__|        |  
| ------- |:------:|
|countdown| n --> 3
|countdown| n --> 2
|countdown| n --> 1
|countdown| n --> 0
* main is empty because we did not create any variables in ```__main__``` or pass any arguments in it.
* where n=0 is called the base case where it does not have to make any a recursive call, so there are no more frames


 

###Keys to Writing Recursive Functions 
* make sure recursion stops and it includes a non-recursive path
* use safety counters to prevent infinite recursion
* limit recursion to one routine. If we are cyclic recursion, we can usually redesign the routines to be a single routine. 
* keep an eye on the stack. We can use a safety counter by setting a limit, or work for allocation of local variables in recursive functions, especially memory-intensive objects. We can use *new* to create objects on the heap rather than letting the complier create auto objects on the stack. 
* don't use recursion for factorials or Fibonacci numbers
* consider alternatives to recursion before using it

**Example 1: Say Hello**
```
def print_n(s, n):
    if n <=0:
        return
    print(s)
    print_n(s, n-1)

s = 'Hello'
n = 3
print_n(s, n)
```

Here is the result:
```
Hello
Hello
Hello
```

**Example 2: isPalindrome(str)**
```
def isPalindrome(str):

    if str == '':
        return True
    first_last = str[0] == str[-1]
    return isPalindrome(str[1:-1]) and first_last

print(isPalindrome('racecar'))
```
* This recursive function uses slices which means we are using up memory.

**Example 3: Reverse a String**
```
def reverse(string):
    if(len(string) == 0):
        return ''
    return string[1:] + string[0]
```

**Example 4: Binary Search**
```
from math import floor

def rec_binary_search(a_list, target, first, last):
    """
    Searches a_list for an occurrence of target
    If found, returns the index of its position in the list
    If not found, returns -1, indicating the target value isn't in the list
    """
    if first > last:
        return -1

    middle = floor((first + last) / 2)
    if a_list[middle] == target:
        return middle
    if a_list[middle] > target:
        return rec_binary_search(a_list, target, first, middle-1)
    else:
        return rec_binary_search(a_list, target, middle+1, last)

def binary_search(a_list, target):
    return rec_binary_search(a_list, target, 0, len(a_list)-1)


my_list = [5, 10, 32, 67, 98, 112, 113]
print(binary_search(my_list, 112))
```
* Here we use a helper function because the recursive function needs extra parameters. We can't use default arguments because the initial value of the last parameter needs to make use of the value passed from the a_list parameter, and we can't do that with a default argument. 