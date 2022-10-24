# File Handling

**Persistence** 

When we run programs, it generally runs for a brief amount of time, produce an output, and the data disappears once the program ends. If we decide to run the program again, it starts from a clean slate. Fortunately, persistent programs such as files and databases keep data in permanent storage (a hard drive, for example). When we turn off our computer, we get to pick up where we left off.


We can read, write, and append files using 'r', 'w', 'a', and 'r+'. If we omit the mode argument, Python opens the file in read-only mode by default. If a file is opened in write mode and if the file does exist, Python will erase the contents of the file before returning the file object. 


**File Modes**
* read mode: 'r'
* write mode: 'w' 
* append mode: 'a'
* read and write: 'r+'



# Read from files

###Read
1. Read the file to memory: We can read the entire contents of a file, or one line at a time. 
2. Close: If a bug in the program prevents the close() method from being executed, the file may never close, which can cause data to be lost or corrupted. If we close the file too early, we can not access the file which leads to more errors. In Python, the file will close automatically when the `with` block finishes execution. 
3. Automatic string: In Python, when a text file is read, it interprets all text in the file as a string. If we read in a number and want to work with that value in a numerical context, we will have to convert it into an integer or a float. Python can only write strings to a text file, so if we want to store numerical data in a text file, we'll have to convert it into a string first. 

**Common methods when reading a file:**
* rstrip(): using rstrip() on each line in the print() call eliminates extra blank lines. 
* readlines(): takes each line from the file and stores it in a list

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

**Here is another example:**
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

__________

# Write to a File
* newline character: use a newline character ```\n``` to have each string appear on its own line.






###File Paths
3. File path: A file patch is a specific location where the program is stored.
4. Relative path: A relative path is a given location relative to the directory where the current running program file is stored. 
5. Absolute file path: An absolute file path is the exact location of where the program being executed is stored. We should use an absolute path if a relative path does not work. Absolute paths are usually longer than relative paths, so it is helpful to assign them a variable and then pass that variable to open():

__________


### Pickle Module

### JSON Module

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

The JSON module allows us to put simple data structures into a file and load the data from that file the next time the program runs. We can use json to share data between different program in a portable format. The JSON module saves user data so it is not lost when your program stops running.

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




### Refactoring

There will be a point where the code we write will work, but we may be able to improve the code by breaking it up into a series of functions that have specific jobs. The process of breaking up existing code into cleaner, easier to understand, and easier to extend code is called *refactoring*.



* pickling: serializing and deserializing an object in Python. Serialization is the conversion of an object to a series of bytes, so that the object can be easily saved to persistent storage or streamed across a communication link. The byte stream can then be deserialized - converted into a replica of the original object.
* Python pickle module is a great way of storing python objects like tuple, dictionaries, lists, and even python classes and functions can be serialized and de-serialized