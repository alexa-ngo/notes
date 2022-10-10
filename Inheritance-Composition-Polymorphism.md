#Inheritance, Composition, Polymorphism

##Inheritance

Inheritance is when we define one class as being a subtype of another class. Inheritance is defined as an IS-A relationship where one class is the subclass of another class. 

For example:  
* a duck is-a bird
* a laptop is-a computer
* a house is-a building

If we already defined a Bird class, then having our new Duck class inherit from Bird lets it inherit methods that have already been defined in the Bird class. 

```class Duck: ```

We would have 
```class Duck(Bird): ```


There are different kinds of relationships between classes: 
* HAS-A relationship: A HAS-A relationship is when the instances of one class contain references to instances of the other.
* IS-A relationship: An IS-A relationship is the relationship between a child class and its parent.

*Here is an example of a Square class that inherits a Rectangle class (since a square is-a rectangle):

**Inheritance Version**

``` 
class Rectangle:
    """
    Represents a geometric rectangle.
    """
    def __init__(self, length, width):
        self._length = length
        self._width = width

    def area(self):
        return self._length * self._width

    def perimeter(self):
        return 2 * self._length + 2 * self._width

class Square(Rectangle):
    """
    Represents a geometric square.
    Inherits from Rectangle.
    """
    def __init__(self, side):
        self._length = side
        self._width = side

```

Here the: 
* Square is the subclass or "child" of Rectangle.
* Rectangle is the superclass or "parent" of Square.

Square has inherited the area and perimeter methods of Rectangle, so they do not need to be defined in the Square class. However we need to re-define the constructor in Square because it needs to behave differently than the Rectangle constructor. This is an example of **overriding** a method. To override a method, we need to define it, using the same name, in the child class.

Even if we override a method, we can sometimes still make use of the parent's version of the method. We can do this with **super()**, which gives us a temporary object of the parent class that we can use to call its meethods. We can use super() to rewrite the Square class like this: 

```
class Square(Rectangle):
    """
    Represents a geometric square. 
    Inherits from Rectangle.
    """
    def __init__(self, side):
        super().__init__(side, side)
```

Using super() lets us call a method of the superclass to uses its implementation of that method.
We can then do whatever we need to in the overridden version of the method including initializing new data members or defining additional methods.

We can define as many levels of inheritance as we like. 

For example: Animal class -> Mammal class --> Dog class --> Greyhound class
* We can have a Husky class that could inherit from the Dog class.
* We can have a Cat class that could also inherit from Mammal class. 


#####Liskov Substitution Principle (LSP)
 
When we override a method, the interface of the new method should be the same as the old. 
It should take the same parameters, return the same type, and *obey* the same preconditions and post conditions. The general idea of LSP, in other words, we want to have objects of our subclasses behaving the same way as the objects of our superclass.

#####Terms
* encode: Encode is to define a mapping. For example, for a deck of cards Jack can be mapped to 11, Queen to 12, and King to 13.
* inheritance: Inheritance is the ability to define a new class that is a modified version of the previously defined class. 
* multiplicity: Multiplicity is a notation in a class diagram that shows, for a HAS-A relationship, how many references there are to instances of another class.

#Composition

Object composition is when one class contains an object of another class as one of its data members. This is a **has-a** relationship. **With composition a class is *using* an object of another class instead of *being* an object of another class.** 

For example a:
* duck has-a beak
* laptop has-a battery
* house has-a roof

###Deciding between composition and inheritance

In this version, the Cube has the area and perimeter methods it inherits from Square, which does not make sense for a cube. 
It is true that a cube has-a square - it has six of them, one for each face. If the project includes other classes for three-dimensional shapes, then we want an inheritance hierarchy of three-dimensional shapes, separate from the inheritance hierarchy of two-dimensional shapes.  

```
class Cube(Square):
    """
    Represents a geometric cube
    """
    def surface_area(self):
        return super().area() * 6

    def volume(self):
        return super().area() * self._length
```
**Here is a better version than having Cube inherit from Square.**

**Inheritance Version**

```
File Name: shapes.py

class Rectangle:
    """
    Represents a geometric rectangle.
    """

    def __init__(self, length, width):
        self._length = length
        self._width = width

    def get_length(self):
        return self._length

    def area(self):
        return self._length * self._width

    def perimeter(self):
        return 2 * self._length + 2 * self._width

class Square(Rectangle):
    """
    Represents a geometric square.
    Inherits from Rectangle
    """
    def __init__(self, side):
        self._length = side
        self._width = side
```



```
File Name: main.py

from shapes import Square

class Cube:
    """
    Represents a geometric cube.
    """

    def __init__(self, side):
        self.face = Square(side)   # face is a data member of type Square

    def surface_area(self):
        return self.face.area() * 6

    def volume(self):
        return self.face.area() * self.face.get_length()
```
* In the inheritance version of the volume() method, we accessed the private length attribute directly, because it was inherited by cube and was part of its *self*. 
* In the composition version of volume(), the length attribute is not a data member of Cube, so we needed to add a get_length method and use that to access the length. 



#Polymorphism

Polymorphism means "many shapes". Polymorphism is an object-oriented programming (OOP) concept when code can operate on objects of different types in the same way, but with results specific to the actual object being operated on. This refers to the ability of a variable, function or object to take on multiple forms. Functions that work with different data types is called polymorphic and allows for us to reuse code. 

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
This function also works for lists, tuples, and even dictionaries, as long as the elements of s are hashable, so they can be used as keys in d. 

```
t = ['apple', 'banana', 'grapes', 'mango', 'apple', 'mango',]
print(histogram(t))
```

Different languages have different ways of implementing polymorphism. In some languages we can only get polymorphism via inheritance. In others it is either inheritance or an interface/protocol(not found with Python). 

### Duck Typing ###
Python uses the approach of "duck typing". If it walks like a duck and quacks like a duck, then it must be a duck. If a piece of code wants to call certain methods on an object, it will work as long as those methods are defined for that object, regardless of the actual type of the object.

* If class B inherits from class A, then it has the same methods, so a function can operate on objects of both clases in the same way. 

However, inheritance is not required for polymorphism in Python. 

* If class A and class B are two unrelated classes, but both have defined whatever methods a function wants to use with them, then the function can still operate on objects of both classes in the same way. 

**Example of polymorphism without inheritance:**
* If we have a Movie class and a LawnMower class, both have a start() method. However, there is no relationship between those two things. There is no reason for them to be part of the same inheritance hierarchy. 

```
File Name: main.py

from things import Lawnmower, Movie

def start_things(thing_list):
    """ Starts each thing in thing_list """
    for thing in thing_list:
        thing.start()

jeff = Lawnmower()
inception = Movie()

stuff = [jeff, inception]
start_things(stuff)
```

This main.py file will automatically use the correct version of start() for each object.

```
#File Name: things.py

class Lawnmower:
    """
    Represents a machine that cuts grass.
    """
    def start(self):
        print("Ready to cut grass")

class Movie:
    """
    Represents a motion picture
    """
    def start(self):
        print("Movie has started.")
```