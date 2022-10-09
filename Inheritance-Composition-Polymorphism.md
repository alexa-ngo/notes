#Inheritance, Composition, Polymorphism

##Inheritance

Class Diagram: A class diagram is abstract representation of the structure of the program. A class diagram does not show the individual objects but the classes and relationships between them.

There are different kinds of relationships between classes: 
* HAS-A relationship: A HAS-A relationship is when the instances of one class contain references to instances of the other.
* IS-A relationship: An IS-A relationship is the relationship between a child class and its parent.

**Debugging Inhertance**

Debug the method that was used on an object:

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


#####Liskov Substitution Principle (LSP)

When we override a method, the interface of the new method should be the same as the old. 
It should take the same parameters, return the same type, and *obey* the same preconditions and post conditions. The general idea of LSP, in other words, we want to have objects of our subclasses behaving the same way as the objects of our superclass.

#####Terms
* encode: Encode is to define a mapping. For example, for a deck of cards Jack can be mapped to 11, Queen to 12, and King to 13.
* inheritance: Inheritance is the ability to define a new class that is a modified version of the previously defined class. 
* multiplicity: Multiplicity is a notation in a class diagram that shows, for a HAS-A relationship, how many references there are to instances of another class.

#Composition

# BLANKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKk

#Polymorphism

Polymorphism is an object-oriented programming (OOP) concept that refers to the ability of a variable, function or object to take on multiple forms. Polymorphism is a Greek word that means "many-shaped". Functions that work with different data types is called polymorphic and allows for us to reuse code. 

An example of this is:

```
def histogram(s):
    d = dict()
    for c in s:
        if c not in d:
            d[c] = 1
        else:
            d[c] = d[c] + 1
    return d
```
This function also works for lists, tuples, and even dictionaries, as long as the elenets of s are hashable, so they can be used as keys in d. 

```
t = ['apple', 'banana', 'grapes', 'mango', 'apple', 'mango',]
print(histogram(t))
```
