# Generators in Python

Generators are special routines that help us control the behavior of a function. 

Generators are similar to a function returning an array. It has parameter, which is called and generates a sequence of numbers. Unlike functions, generators yields one value at a time instead of a whole array, which requires less memory.

A python function containing the word, `yield` may be called a generator. A normal python function will start executing from the first line until it gets a return statement, exception, or the end of the function. Any local variables created during the function scope are destroyed and no longer be accessed. When the program encounters a yield keyword, the program is frozen, and all the variables are stored in memory until the generator is called again. A generator will give us performance benefits only if we do not intend to use the set of generated values more than once. 

We can use the generator with an iterator or it can be called using the `next` keyword. To get values from a generator, we can use either `next()` or `__next__()`.

###Example of next() in Python
```
def the_numbers():
    num = 1
    while num <= 10:
        yield num
        num += 1

print(the_numbers())

my_numbers = the_numbers()

print(next(my_numbers))
print(next(my_numbers))
print(next(my_numbers))
```
###Output
```
<generator object the_numbers at 0x7efd57ed68c0>
1
2
3
```


Generally generators in Python:

* Defined with the def keyword
* Use the yield keyword(s)
* Returns an iterator 

### Generators are used when:
* stream processing of handing large data files such as logs
* space-efficient method for data processing. 

###Generators with Iterators

```
def generator_iter():
    yield 'xyz'
    yield 456
    yield 123.99

for i in generator_iter():
    print(i)

generator_iter()
```

###Output
```
xyz
456
123.99
```

### Generator using next
```
def generator_iter():
    yield 'xyz'
    yield 456
    yield 123.99

g = generator_iter()
print(g.__next__())
print(g.__next__())
print(g.__next__())
print(g.__next__())
print(g.__next__())
print(g.__next__())

```

###Output
```
xyz
456
123.99
Traceback (most recent call last):
  File "<pyshell#14>", line 13, in <module>
    print(g.__next__())
StopIteration
```
###Example without generator:
```
def print_square():
    n = 2000000
    number_list = range(1, n+1)
    for i in number_list:
        print(i*i)

```

###Example with generator:
```
def num_generator(n):
    num = 1
    while True:
        yield num
        if num == n:
            return
        else:
            num += 1

for i in num_generator(2000000):
    print(i*i)
```

###Generators and list() in Python:
```
def the_numbers():
    num = 1
    while num <= 10:
        yield num
        num += 1

values = list(the_numbers())
print(values)

the_numbers()
```

###Output
```
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

### List Comprehension
We can even create a generator similar to list comprehension. Instead of using square brackets, we would use parentheses. 

###Generator expression in Python
```
def print_numbers():
    the_numbers = (n for n in range(1, 10))
    my_numbers = list(the_numbers)
    print(my_numbers)

print_numbers()
```

###Output
```
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### Even_Odd Example
```
def even_odd():

    for n in range(2, 11, 2):
        yield n

    for n in range(1, 11, 2):
        yield n

obj = even_odd()
print(next(obj))
print(next(obj))
print(next(obj))
print(next(obj))
print(next(obj))
print(next(obj))
print(next(obj))
print(next(obj))
print(next(obj))
print(next(obj))
```

###Output:
```
2
4
6
8
10
1
3
5
7
9
```

Here is how we would print a list:

###Print even_odd in list
```
def even_odd():
   for n in range(2, 11, 2):
       yield n

values = list(even_odd())
print(values)
```

### Alphabet
```
alphabets = list((chr(i) for i in range(97, 123)))
print(alphabets)
```
### Output
```
['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']
```
