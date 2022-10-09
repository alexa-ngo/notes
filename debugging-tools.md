#Debugging Tools

###Attribute

We can use these built-in functions to see if an object has a particular attribute.
* ```hasattr``` 
* ```getattr```: 
* ```vars``` : takes  an object and returns a dictionary that maps from attribute names (as strings) to their values:
``` 
p = Point(3,4)
vars(p)
{'y': 4. 'x': 3}
```

___

###Inheritance

The def_finding_class method many be applied to an object to find the class the method applies to.

```def find_defining_class(obj, meth_name):
    for ty in type(obj).mro():
        if meth_name in ty.__dict__:
            return ty
```
Here is an example:

```
hand = Hand()
find_defining_class(hand, 'shuffle')
<class '__main__'.Deck'>
```

So the shuffle method for this Hand is the one in `Deck`.
The `mro` (method resolution order) method gets a list of class objects (types) that will be searched for methods. 
