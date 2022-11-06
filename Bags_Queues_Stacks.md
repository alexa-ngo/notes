#Bags, Queues, and Stacks
### Fixed-capacity stack
* Push and pop operations take time independent of the stack size. For many applications, this is the method of choice because of its simplicity.


Iterator: An iterators is an object that uses methods like hasNext() and next(), like shown below:

```
public interface Iterator <Item> 
{
    boolean hasNext();
    Item next(); 
    void remove();
}
```