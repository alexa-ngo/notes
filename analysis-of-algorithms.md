# Analysis of Algorithms 🤓

1. [Algorithm Analysis](#algorithm-analysis)
2. [Order of Growth](#order-of-growth)
3. [Develop a Mathematical Model of Running Time](#develop-a-mathematical-model-of-running-time)
4. [Designing Faster Algorithms](#designing-faster-algorithms)
5. [Memory](#memory)
6. [Objects](#objects)
7. [Arrays](#arrays)
8. [Sorting](#sorting)
9. [Facts/Terms](#factsterms)

**Here is an important visualization**: [Comparison Sorting Algorithms - Visualization](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html) 🤓


# Algorithm Analysis

Analysis of algorithms is a branch of computer science that studies the performance of algorithms. We need to consider how much time we are using. The algorithm that we are using determines the order of growth. 
separating the algorithm from the implementation on a particular computer is a powerful concept because it allows us to develop knowledge about the performance of algorithms and then apply that knowledge to any computer. 
Are we more considered with the time, or using up the least amount of space (memory)? The analysis is to help us make detailed and accurate *predictions*. 

### Scientific Method
* observe
    * How long will my program take?
    * By how much it increases?
* hypothesis
* predict
* verify
* validate

D.E. Knuth postulated the total running time of a program is determined by two primary factors:
* The cost of executing each statement (property of the computer, Java complier, and the operating system)
* The frequency of execution of each statement (property of the program and the input)

If we know both for all instructions in the program, we can multiply them together and sum for all instructions in the program to get the running time. The challenging part is to find the *frequency of execution* of the statements.

We  can observe the running time using:
* Stopwatch() to create a stopwatch 
* double elapsedTime() to return elapsed time since creation

### Typical tilde approximation
|function       | tilde approx. | order of growth|
| ------------- |:-------------:| :-------------:| 
| N^3^/6 - N^2^/2 + N/3 | ~N^3^/6 | N^3^ |
| N^2^/2 - N/2 | ~N^2^/2| N^2^|
| lg N + 1 | ~ lg N | lg N |
| 3 | ~ 3 | 1 | 


### Order of Growth 
| Type       | Function   | Description |Example      | Application | Operations and Running Time|
| ------------- |:-------------:| :-------------:| :-------------:| :-------------:|:-------------:| 
|constant|O(1)|statement|add two numbers | most Java operations | fixed number of operations and does not depend on N
|logarithmic|**O(log N)**|divide in half| binary search | binary search |barely slower than a constant-time program
|linear|**O(N)**|loop|find the maximum| constant amount of time | running time proportional to N
|linearithmic|**O(N log N)** |divide and conquer | mergesort | Merge.sort() and Quick.sort() | base of the logarithm is not relevant with respect to order of growth
|quadartic|O(N^2^)| two nested loops | check all pairs |  Insertion.sort(), Bubble.sort(),  Selection.sort() 
|cubic| O(N^3^)|triple loop | check all triples | ThreeSum | three nested for loops
|exponential| 2^N^| exhaustive search | check all subsets | rarely run for a large problem | b^N^ for any constant *b* > 1


**Log-Log Plot** 

![log-log plot](http://4.bp.blogspot.com/-lSgfMcSfxPk/VfBecnA7ntI/AAAAAAAAATI/ozjV6p9vuHo/s1600/orderofgrowth.png)

**Time complexity is a machine-independent way to express how quickly the amount of time required increases as the problem size increases. Only the instructions that are executed the most frequently play a role in the final total. We refer to this instructions are the** *inner loop* **of the program.**

Although insertion sorts, bubble sorts, and selection sorts have the same complexity, insertion sort is usually much faster as its inner loop does not usually have to perform so many comparisons.

Sometimes the details of the hardware, the programming language, and the characteristics of the input make a big difference. For small problems, the order of growth is irrelevant. Algorithmic analysis is a useful tool. For large problems, the "better" algorithm is usually much better! 

### Develop a Mathematical Model of Running Time:
1. Develop an *input model*, including a definition of the problem size.
2. Identify the *inner loop*. 
3. Define a *cost model* that includes operations in the inner loop.
4. Determine the frequency of execution of those operations for the given input.

**Let's see this to practice using the binary search!**

```
def binary_search(a_list, target):    
  
    first = 0    
    last = len(a_list) - 1    
    while first <= last:        
        middle = (first + last) // 2        
        if a_list[middle] == target:  
            return middle          
        if a_list[middle] > target:            
            last = middle - 1        
        else:            
            first = middle + 1    
    return -1
```

* input model: a_list
* inner loop: statement within the while loop
* cost model: the compare operation (compare the values of two array entities)
* analysis: the number of compares is at most O(log N)
______________

# Designing Faster Algorithms

We can **predict performance** and determine the approximate order of growth of the running time of any program by:
* running doubling ratio experiments
* ask ourselves if the program will be able to process this given input data in a reasonable amount of time?
* how much faster can I solve the problem if I get a faster computer?
* consider the caveats such as large constants, nondominant inner loop, instruction time, system considerations, inputs, multiple parameters, and such.







# Memory

| Type | Bytes
| ------------- |:-------------:| 
|boolean  | 1
|byte | 1
|char | 1
|int | 4
|float| 4
|long | 8 
|double | 8

___________________________

# Objects

#### Typical Object Memory Requirements:


|**integer wrapper object** (24 bytes)|
| ------------- |
| object overhead (16 bytes)
| x integer value (4 bytes)|
| padding (4 bytes)

| **date object** (32 bytes)
| ------------- |
| object overhead (16 bytes)
| day (4 bytes)
| month (4 bytes)
| year (4 bytes)
| padding (4 bytes)

|**node object** (40 bytes)
| ------------- |
| object overhead (16 bytes)
| extra overhead (8 bytes)
| item (8 bytes)
| next (8 bytes)

# Arrays 
* Arrays in Java are implemented as objects typically with extra overhead for the length.
    * An array of N int values uses 24 + 4N bytes
    * An array of N double values uses 24 + 8N bytes
* An array of objects is an array of references to the objects 

# Sorting

**Here is an important visualization**: [Comparison Sorting Algorithms - Visualization](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html) 

Small data sets: insertion sort, selection sort
* insertion sort is generally faster than selection sort in practice since lists do not usually fall into the worst case of insertion sort and its inner loop does not have to perform so many operations. Shellsort is a variant of insertion sort that is more efficient for larger lists.
* insertion sort is generally faster than bubble sort.
* selection sort is an in-place comparison sort. It uses fewer writes and is used then write performance is a limiting factor

Large data set: heapsort, merge sort, or quicksort. 

* Shellsort is in-place, only needs a relatively small amount of code, and does not require use of the call stack. Shellsort is useful where memory is at a premium such as embedded systems and operating system kernels.

# Types of Searches
###Linear search
Linear search first starts at the first element of the list and compare it to the target value. If they are not equal, move to the next element of the list and compare again. We will keep doing this until either the target value is found, or we reach the end of the list without finding it. 
~~~
def linear_search(a_list, target):
    for index, el in enumerate(a_list):
        if el == target:
            return index
    return -1
~~~

###Binary Search
Binary search **assumes the elements of the list are in sorted order**. Then we look though half of the list, and half of it again, while not considering the other half. We repeat the same process that we know the value is in. 

```
def binary_search(a_list, target):    
  
    first = 0    
    last = len(a_list) - 1    
    while first <= last:        
        middle = (first + last) // 2        
        if a_list[middle] == target:  
            return middle          
        if a_list[middle] > target:            
            last = middle - 1        
        else:            
            first = middle + 1    
    return -1
```

###Bubble Sort

Bubble sort starts by comparing the first two values in the list. If they are in the wrong order, the algorithm swaps the values, otherwise it leaves them where they are. Next the bubble sort compares the second and third values and does the same thing. This sorting happens until the end of the list. Next, the bubble sort makes another pass through the list except the last value, which we know is in the correct place. At the end of the his pass, we know that the second-largest value is now in the correct place. Bubble sort **does not keep running to the end of the array**. At the end of i passes, i values will be in their correct places. Bubble sort makes n-1 passes (if all but one of the values are in the correct place, then the value must also be in the right place). 

``` 
def bubble_sort(a_list):    
  """    
  Sorts a_list in ascending order    
  """    
  for pass_num in range(len(a_list) - 1):        
    for index in range(len(a_list) - 1 - pass_num):            
      if a_list[index] > a_list[index + 1]:                
        temp = a_list[index]                
        a_list[index] = a_list[index + 1]                
        a_list[index + 1] = temp
```

### Insertion Sort 

Insertion sort works by pulling the second value up out of the list, then looks to the left of the "vacant" spot and "sliding over" all the values larger than the one we pulled out. Then it drops the value that was pulled out into whatever spot is now "vacant". Next it pulls the third value up out of the list and repeats what it did for the second value. It inserts the value into its correct position into the sorted list that is being built out from the left side of the array. This happens until every value has been inserted into the correct position. 

```
def insertion_sort(a_list):    
    """    
    Sorts a_list in ascending order    
    """    
    for index in range(1, len(a_list)):        
        value = a_list[index]        
        pos = index - 1        
        while pos >= 0 and a_list[pos] > value:            
            a_list[pos + 1] = a_list[pos]            
            pos -= 1        
        a_list[pos + 1] = value
```


#### Facts/Terms
* array of primitive-type values typically requires 24 bytes of header information (16 byes of object overhead, 4 bytes for the length, and 4 bytes of padding) plus the memory needed to store the values. 
* array of objects is an array of references to the objects, so we need to add the space for the references to the space required for the objects.
* crossover point is the problem size where two algorithms require the same run time or space.
* floor = the largest integer not greater than x
* ceiling = smallest integer not smaller than x 
* two-dimensional array is an array of arrays (each array is an object).
* extracting a substring takes either constant extra memory or linear extra memory depending on the underlying implementation. 
* garbage collection is a system process that reclaims its memory for the heap when every object no longer has references to it. 
* heap is the memory allocated when creating an object with new. This is a special area of memory. 
* machine model is specifying the machine model that is used to analyze the number of steps or operations an algorithm requires under a given model.  
* power law is a straight line in a log-log plot equivalent to the hypothesis that the data fits the equation T(N) = aN^b^. 
* properties are hypotheses about performance of implementations that can be checked through experimentation.
* proposition is the precise mathematical results about algorithms.
* leading term is the term with the highest exponent
* stack is a special area of memory (a system pushdown stack)
* worst case is an input that makes a given algorithm run slowest (or require the most space).