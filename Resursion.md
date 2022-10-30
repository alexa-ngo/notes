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

**Example 5: Recursive list merge** 

This recursive algorithm merges two lists. It takes the smaller head element of the two lists to be the lead element of the merged list, and makes a recursive call to merge the rest of the two lists.
```
def merge(list_1, list_2):
    """
    Takes two sorted lists and returns a new list that
    contains all elements from both lists in sorted order
    """
    if len(list_1) == 0:  # if list_1 is empty, return a copy of list_2
        return list(list_2)
    if len(list_2) == 0:  # if list_2 is empty, return a copy of list_1
        return list(list_1)
    if list_1[0] < list_2[0]:  # merge the smaller first element with the merge of the remaining elements
        return [list_1[0]] + merge(list_1[1:], list_2)
    else:
        return [list_2[0]] + merge(list_1, list_2[1:])

first = [1,3,6,7]
second = [2,4,5,8,9,10,11]
print(merge(first, second))
```

###Recusive Fibonacci Function
![Recusive Fibonacci Function](https://i.stack.imgur.com/QVSdv.png)
```
def fib(num): 
  print("calling fib(", num, ")", sep='')   
  if num == 1 or num == 2:        
    return 1    
  return fib(num-1) + fib(num-2)

print (fib(7))
```
The time complexity for this implementation is O(2^n^), which is terribly slow, compared to the iterative solution that is O(n). 

**Example 6: Iterative Fibonacci**
```
def rec_fib(counter, current=1, prev=1):   
  print("calling fib(", counter, ")", sep='')  
  if counter == 1:        
    return prev    
  return rec_fib(counter-1, current+prev, current)

def fib(num):
  return rec_fib(num, 1, 1)

print(fib(7))
```
**Example 8: Memoization**
```
def fib_mem(num, memo=None):
  if memo is None:
    memo = {}  
  if num not in memo:
    print("computing fib(", num, ")", sep='')
    if num == 1 or num == 2:
      memo[num] = 1
    else:
      memo[num] = fib_mem(num-1, memo) + fib_mem(num-2, memo)
  return memo[num]

print(fib_mem(7))
```

We give memo a default value of None to avoid mutable default arguments. This implementation also computes the n^th^ Fibonacci number on O(n) time. 


**Example 9: Recursive maze solver**

In recursion, the classic example is a maze example! This function below shows an example of recursive backtracking. Whenever this algorithm finds that the current route won't work, it rewinds back to the most recent decision point and tries the next possibility. It keeps doing this until it finds a route that works. 

```
def find_gold(maze, position):
    """
    maze is a list of lists that represents a square maze
    ' ' is an empty square
    '#' is a wall
    'G' is where the gold is hidden
    position is a tuple of the current row and column

    returns a list of coordinates that leads to the gold
    """
    row, col = position  # tuple unpacking
    if row < 0 or row >= len(maze):  # base case for row out of bounds
        return None
    if col < 0 or col >= len(maze[row]):  # base case for column out of bounds
        return None
    if maze[row][col] == '#':  # base case for hitting a wall
        return None
    if maze[row][col] == '.':  # base case for repeating a position
        return None
    if maze[row][col] == 'G':  # base case for finding the goal
        return [(row, col)]

    maze[row][col] = '.'  # mark current square to avoid revisiting
    partial_route = find_gold(maze, (row-1, col))  # try "up"
    if partial_route is not None:
        maze[row][col] = ' '  # unmark current square
        return [(row, col)] + partial_route
    partial_route = find_gold(maze, (row+1, col))  # try "down"
    if partial_route is not None:
        maze[row][col] = ' '  # unmark current square
        return [(row, col)] + partial_route
    partial_route = find_gold(maze, (row, col-1))  # try "left"
    if partial_route is not None:
        maze[row][col] = ' '  # unmark current square
        return [(row, col)] + partial_route
    partial_route = find_gold(maze, (row, col+1))  # try "right"
    if partial_route is not None:
        maze[row][col] = ' '  # unmark current square
        return [(row, col)] + partial_route
    maze[row][col] = ' '  # unmark current square


maiz = [[' ', '#', ' ', ' ', ' ', '#'],
        [' ', ' ', ' ', '#', ' ', '#'],
        ['#', '#', ' ', '#', ' ', '#'],
        [' ', ' ', ' ', '#', ' ', '#'],
        [' ', '#', ' ', '#', ' ', ' '],
        ['G', '#', '#', '#', '#', ' ']]

print(find_gold(maiz, (0,0)))
```

**Example 10: Recursive Sum**

```
def summer(a_list, pos):
    if pos == len(a_list):
        return 0
    return a_list[pos] + summer(a_list, pos + 1)

a_list = [1,2,3,4]
print(summer(a_list, 0))
```
**Example 10a: Recursive Sum Tests**
```
import unittest
class UnitTests(unittest.TestCase):
    def setUp(self):
        pass
    def tearDown(self):
        pass
    def test_summer_range10(self):
        l = [i for i in range(10)]
        s = summer(l)
        self.assertEqual(s, 45)
    def test_summer_empty(self):
        s = summer([])
        self.assertEqual(s, 0)
```
