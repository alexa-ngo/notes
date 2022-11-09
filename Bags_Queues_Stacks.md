#Linked Lists

| Data Structure|Advantage | Disadvantage  
| ------------- |:----------------:|:----------------:|
| Array | indexes gives immediate access to any item | need to know the size on initialization
| Linked List| uses space proportional to size | need reference to access an item



##Bags, Queues, and Stacks
### Fixed-capacity stack
* Push and pop operations take time independent of the stack size. For many applications, this is the method of choice because of its simplicity.

```
Start at the beginning of the first level
While you are not at the end of the first level
    If the current node has a child
        Append the child to the end of the first level
        Update the tail pointer 
    Advance to next node
```

Iterator: An iterators is an object that uses methods like hasNext() and next(), like shown below:
* we can use a list iterator to access elements inside a linked list.
* we have to be careful when calling `remove`, because it can be called only **once** after calling `next` or `previous`, and you cannot call it immediately after a call to `add`. If we call the method impropertly, it throws ain `IllegalStateException`.
* programmers who identify special cases as they are coding are likely to be more productive than those who find special cases through debugging. 

```
import java.til.Iterator;

public interface Iterator <Item> 
{
    boolean hasNext();
    Item next(); 
    void remove();
}
```

The `Iterator` is not part of java.lang.  

### Traversal
We can examining ever item in an array by traversing through the linked list by: 

```
for (Node x = first; x != null; x = x.next)
{
    // Process x.item. 
}
```

### Stacks and Queues

```class Stack:    
  """    
  An implementation of the Stack ADT that uses Python's built-in lists    
  """    
  def __init__(self):        
    self.list = []    
  
  def push(self, data):        
    self.list.append(data)    
    
  def pop(self):        
    val = self.list[-1]        
    del self.list[-1]        
    return val    
  
  def peek(self):        
    return self.list[-1]    
  
  def is_empty(self):        
    return len(self.list) == 0
    

class Queue:    
  """    
  An implementation of the Queue ADT that uses Python's built-in lists    
  """    
  def __init__(self):        
    self.list = []   
  
  def enqueue(self, data):        
    self.list.append(data)    
  
  def dequeue(self):        
    val = self.list[0]        
    del self.list[0]        
    return val    
  
  def is_empty(self):        
    return len(self.list) == 0
```