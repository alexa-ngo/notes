# File Handling


###Persistence 

When we run programs, it generally runs for a brief amount of time, produce an output, and the data disappears once the program ends. If we decide to run the program again, it starts from a clean slate. Fortunately, we have persistent programs such as files and databases that keeps data in permanent storage such as a hard drive. Persistent storage allows us to pick up where we left off.

Operating systems and servers are forms of persistent programs that are constantly running whenever the computer is on. These persistent programs wait for requests to come in on the network. Tools such as databases and the pickle module, which serializes and deserializes data, used in Python makes it easy to store program data.


There are two main kinds of files, text files and binary files.
* text file: text file that is human readable
* binary file: files that are not human readable


###Read, Write, and Append 

We can read, write, and append files using 'r', 'w', 'a', and 'r+'. If we omit the mode argument, Python opens the file in read-only mode by default. If a file is opened in write mode and if the file does exist, Python will erase the contents of the file before returning the file object. 


**File Modes**
* read mode: 'r'
* write mode: 'w' 
* append mode: 'a'
* read and write: 'r+'



###Read from files

1. Read the file to memory: We can read the entire contents of a file, or one line at a time. 
2. Close: If a bug in the program prevents the `close()` method from being executed, the file may never close, which can cause data to be lost or corrupted. If we close the file too early, we can not access the file which leads to more errors. In Python, the file will close automatically when the `with` block finishes execution. 
3. Automatic string: In Python, when a text file is read, it interprets all text in the file as a string. If we read in a number and want to work with that value in a numerical context, we will have to cast (convert) it into an integer or a float. Python can only write strings to a text file, so if we want to store numerical data in a text file, we'll have to cast it into a string first. 
4. Open file: When we open a file, the first parameter of the open command is the name of the file. If the file is not in the same directory as the program, the path name needs to be included (e.g. 'C:\ProgramFiles\python\hello_world.py').

**Common methods when reading a file:**
* rstrip(): using `rstrip()` on each line in the `print()` call eliminates extra blank lines. 
* readlines(): takes each line from the file and stores it in a list
* repr(): takes any object as an argument and returns a string representation of the object. `repr()` will show "invisible" characters like `\n` and `\t`. 
* close()

```
filename = 'pi_digits.txt'

with open(filename) as file_object:
    lines = file_object.readlines()
print(lines)
```
Results: 
```
['3.1415926535\n', '8979323846\n', '2643383279\n', '\n']
```

**Example 1:**
```
filename = 'pi_digits.txt'

with open(filename) as file_object:
    lines = file_object.readlines()

pi_string = ''
for line in lines:
    pi_string += line.rstrip()

print(pi_string)
print(len(pi_string))
```
Results: 
```
3.141592653589793238462643383279
32
```

**Example 2:**

In Example 2, we are iterating through each line in the dog.txt file and using `strip()` to get rid of whitespace at the ends of a string. 

```
with open('dogs.txt', 'r') as infile:
    for line in infile:
        print(line.strip())
```
What happens if the file we are looking for is missing, or what we type is wrong? We can use a try..except to handle that exception to raise FileNotFoundError. 

```
try:    
  with open('dogs.txt', 'r') as infile:        
    for line in infile:            
      print(line.strip())
except FileNotFoundError:    
    print("The file was not found.")
```
__________

###Write to a File

When we write a file, we have to open and write the file with mode 'w' as a second parameter. 
```
fout = open('output.txt', 'w')

line1 = "Here is the first line,\n"
fout.write(line1)

line2 = "and here is the second line.\n"
fout.write(line2)

fout.close()
```
If the file already exists, opening it in write mode clears out the old data and starts fresh, so we have to be careful! If the file does not exist, a new file is created.
* The `open` returns a file object that provides methods for working with the file.
* The `write` method puts the data into the file. 
* The  `\n` is the newline character that works like an [enter].

**Example 1: Rainbow**

Here is an example that opens a file called 'rainbow.txt'. The program iterates through a list, writing each element to the file. The `with` statement will automatically close the file. 

```
rainbow_list = ['red', 'orange', 'yellow', 'green', 'blue', 'purple']

with open('rainbow.txt', 'w') as outfile:
    for color in rainbow_list:
        outfile.write(color + '\n')
```
* `\n`: The newline character advances us to the next line of the file
* FileNotFoundError: We do not have to worry if the file does not exist, because it will be created. If the file does exist, the data will be *overwritten* by the new contents.

**Example 2: Cast Number as String**

```
with open('nums.txt', 'w') as outfile:
    for num in range(10):
        outfile.write(str(num) + '\n')
```

### Format Operator

When we write to files, we have to write data as a string. 

In this example, we are working with the integer 52, however, in order to write it into a file we have to cast the number into a string first.

```
x = 52
fout.write(str(x))
```


We can format a string with the format operator `{}`. 

An our example, we will be collecting rent from our tenant. 
```
inserting = "This year, {}, rent has increased to {} dollars, and we have to let {} know.".format(2022, 3300, "The Big Corporation")
fout.write(inserting)
```


### Filenames and Paths

Files are organized into directories which are also called folders. We can find the current directory we are in by importing the `os` module in Python.

```
>>> import os
>>> cwd = os.getcwd()
>>> cwd
'/home/alexa/learning-python'
```

* `cwd`: stands for current working directory. 

1. File path: A file patch is a specific location where the program is stored.
2. Relative path: A relative path is a given location relative to the directory where the current running program file is stored. 
3. Absolute file path: An absolute file path is the exact location of where the program being executed is stored. We should use an absolute path if a relative path does not work. Absolute paths are usually longer than relative paths, so it is helpful to assign them a variable and then pass that variable to open(): `os.path.abspath('memo.txt')`

We can check if a path exists, is a directory, or a file.
* `os.path.exists('memo.txt')`
* `os.path.isdir('memo.txt')` or `os.path.isdir('/home/alexa')`
* `os.path.isfile`
* `os.listdir`: returns a list of files and other directories in the given directory.  
__________

### Databases

A database is an organized collection of structured information. The difference between a dictionary and a database is that the database is on permanent storage, so it is still there once the program ends.

In Python we can use the `dbm` module to create and update database files. 

Here is how we would open a database:

```
import dbm
db = dbm.open('captions', 'c')
```
* the 'c' means the database should be created if it doesn't already exist. When we create a new item, dbm updates the database file.

```
db['mountain.png'] = 'Photo of Mountain.'
```

When we access one of the items, `dbm` reads the file:
```
db['mountain.png']
b'Photo of Mountain.
```
Here is how we would iterate a for loop:
```
for key in db.keys():
    print(key, db[key])
```
And we can use `db.close()` to close the database when we are done.

___________
###Pickle Module

The `pickle` module translates almost any type of object into a string for storage in a database. It then translates the strings back into objects. This concept is known as serializing and deserializing. 

Pickling and unpickling has the same effect as copying, however, although the object has the same value, it is generally not the same object. 

Notice how we are using 'wb' and 'rb'. Why is there the letter 'b' in there? The reason being is that pickling reads binary files. 

**Example 1: t1 and t2**

```
import pickle

list = [1,2,3]

# Result of t1
t1 = pickle.dumps(list)
print('Results of t1:', t1)


# Loads t1
t2 = pickle.loads(t1)
print('Loading t2:', t2)

# Result of t2
t2 = pickle.dumps(t1)
print('Results of t2:', t2)


# Compare if t1 == t2
results = t1 is t2
print(results)
```

Here are the results:

```
Results of t1: b'\x80\x04\x95\x0b\x00\x00\x00\x00\x00\x00\x00]\x94(K\x01K\x02K\x03e.'
Loading t2: [1, 2, 3]
Results of t2: b'\x80\x04\x95\x1a\x00\x00\x00\x00\x00\x00\x00C\x16\x80\x04\x95\x0b\x00\x00\x00\x00\x00\x00\x00]\x94(K\x01K\x02K\x03e.\x94.'
False
```

**Example 2: Rainbow**

```
import pickle

rainbow_list = ['red', 'orange', 'yellow', 'green', 'blue', 'purple']
with open('rainbow.pkl', 'wb') as outfile:
    pickle.dump(rainbow_list, outfile)

with open('rainbow.pkl', 'rb') as infile:
    restored_list = pickle.load(infile)

rainbow_list == restored_list  # true
rainbow_list is restored_list  # false
```


**Example 3: Names**
```
import pickle

names = ['place_holder','William', 'Patrick', 'Jon', 'Tom', 'Peter', 'Colin', 'Sylvester',
         'Paul', 'Chris', 'David', 'Matt', 'Peter', 'Jodie']
dict = {}

with open('names.pkl', 'wb') as outfile:
    for each in range(0,13):
        dict[each] = names[each]
    pickle.dump(dict, outfile)

with open('names.pkl', 'rb') as infile:
    restored_dictionary = pickle.load(infile)

# check the restored_list
print(restored_dictionary)
```
_____

### JSON Module

If we are working only with Python, we would want to use pickle. However, if we need to exchange data between different computer languages, we need to use JSON. JSON files are text files that are human readable and is more secure than using pickling. 

**How json looks like:**

```
{
  "firstName": "John",
  "lastName": "Smith",
  "isAlive": true,
  "age": 27,
  "address": {
    "streetAddress": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postalCode": "10021-3100"
  },
  "phoneNumbers": [
    {
      "type": "home",
      "number": "212 555-1234"
    },
    {
      "type": "office",
      "number": "646 555-4567"
    }
  ],
  "children": [
      "Catherine",
      "Thomas",
      "Trevor"
  ],
  "spouse": null
}
```

The JSON module allows us to put simple data structures into a file and load the data from that file the next time the program runs. We can use json to share data between different program in a portable format. The JSON module saves user data so it is not lost when the program stops running.

**Example 1: Username**

```
import json

# Load the username, if it has been stored previously.
# Otherwise, prompt for the username and store it.

def get_stored_username():
    """ Get stored username if available. """
    filename = 'username.json'
    try:
        with open(filename) as f:
            username = json.load(f)
    except FileNameFoundError:
        return None
    else:
        return username

def get_new_username():
    """ Prompt for a new username. """
    username = input("What is your name? ")
    filename = 'username.json'
    with open(filename, 'w') as f:
        json.dump(username, f)
    return username

def greet_user():
    """ Greet the user by name. """
    username = get_stored_username()
    if username:
        print(f"Welcome back, {username}!")
    else:
        username = get_new_username()
        print(f"We'll remember you when you come back, {username}!")

greet_user()
```


* json.dump(): json.dump() takes two arguments (a piece of data to store and a file object it can use to store the data) 
* json.load(): json.load() loads the information stored in the json file
* exceptions: Exceptions are special objects to manage errors that arise while a program is running

```
import json

rainbow_list = ('red', 'orange', 'yellow', 'green', 'blue', 'purple')
with open('rainbow.json', 'w') as outfile:
    json.dump(rainbow_list, outfile)

with open('rainbow.json', 'r') as infile:
    restored_list = json.load(infile)
```

**Example 2: Rainbow JSON**

```
import json

rainbow_list = ('red', 'orange', 'yellow', 'green', 'blue', 'purple')
with open('rainbow.json', 'w') as outfile:
    json.dump(rainbow_list, outfile)

with open('rainbow.json', 'r') as infile:
    restored_list = json.load(infile)
```
So what is the **difference** between the pickle module and JSON? 

* module name
* file extension
* JSON writes to a text file instead of a binary file
* mapping is not perfectly one-to-one. If we save a tuple to a JSON file and then read it back in, we will get a list instead. However, most of the time we will get back the same type of object we saved it as.

**Example 3: Super Hero JSON**

Here is another practice example. Please create a new file named SuperSquad.json with the following:

```
{
  "squadName": "Super hero squad",
  "homeTown": "Metro City",
  "formed": 2016,
  "secretBase": "Super tower",
  "active": true,
  "members": [
    {
      "name": "Molecule Man",
      "age": 29,
      "secretIdentity": "Dan Jukes",
      "powers": [
        "Radiation resistance",
        "Turning tiny",
        "Radiation blast"
      ]
    },
    {
      "name": "Madame Uppercut",
      "age": 39,
      "secretIdentity": "Jane Wilson",
      "powers": [
        "Million tonne punch",
        "Damage resistance",
        "Superhuman reflexes"
      ]
    },
    {
      "name": "Eternal Flame",
      "age": 1000000,
      "secretIdentity": "Unknown",
      "powers": [
        "Immortality",
        "Heat Immunity",
        "Inferno",
        "Teleportation",
        "Interdimensional travel"
      ]
    }
  ]
}

```

Then use this Python Code to read the JSON file into a Python object:

```
with open('SuperSquad.json', 'r') as infile:
    squad = json.load(infile)
```

We can print out Madame Uppercuts third superpower with:

```
print(squad["members"][1]["powers"][2])
```

**Example 4: Names**

```
import json

names = ['place_holder','William', 'Patrick', 'Jon', 'Tom', 'Peter', 'Colin', 'Sylvester',
         'Paul', 'Chris', 'David', 'Matt', 'Peter', 'Jodie']
dict = {}

with open('names.json', 'w') as outfile:
    for each in range(0,13):
        dict[each] = names[each]
    json.dump(dict, outfile)

with open('names.json', 'r') as infile:
    restored_dictionary = json.load(infile)

# check the restored_list
print(restored_dictionary)
```

___

### Refactoring

There will be a point where the code we write will work, but we may be able to improve the code by breaking it up into a series of functions that have specific jobs. The process of breaking up existing code into cleaner, easier to understand, and easier to extend code is called *refactoring*.



* pickling: serializing and deserializing an object in Python. Serialization is the conversion of an object to a series of bytes, so that the object can be easily saved to persistent storage or streamed across a communication link. The byte stream can then be deserialized - converted into a replica of the original object.
* Python pickle module is a great way of storing python objects like tuple, dictionaries, lists, and even python classes and functions can be serialized and de-serialized 

#Resources
* Python Geeks - Python Serialization - https://pythongeeks.org/python-serialization/
