
# Session 4 : Python Classes, Defining List Iterators, Regular Expressions 

---


## Dictionaries

Also known as:
* *Associate Array*
* *Map*
* *Hash Map*
* *Unordered Map*

### Demonstration
* *dictionaries.py*

```
#!/usr/bin/python3

d1 = {}

print ("----------I")
print (type(d1))

d2 = {'one': 1, 'two':2}

print ("----------II")
print (d2)
print ("----------III")
print (type(d2))
d3 = dict(one=2, three=4)
print ("----------IV")
print (d3)
print (type(d3))

d4 = dict([(1, 2), (3, 4)])
print ("----------V")
print (d4)


d5 = dict({1:2, 3:4})
print ("----------V")
print (d5)

```

### Methods on Dictionaries

* d.clear()
* d.copy()
* del k[d]
* dict.fromkeys(seq[, value])   (*demonstrate* - fromkeys.py)
* iteration/accessing elements of dictionaries
** for key in my_dictionary:
** for key, value in my_dictionary.items():
** for value in my_dictionary.values():
** iter(d) - works very well
** len(d)
** d.keys()
** d.values()
** d.items()
Also - discuss adding new entry into dictionary



### Quiz

* Create a List - "A"
* List may have repeated elements
* Create new "B", which has same element from "A" but all elements of "B" are Unique Elements
* Develop a function - to take generic list and return sorted, unique element list (we are still talking about integers) 

## Modules

* Modules are Python files with the .py extension.
* These files implement a set of functions and can have python statements.
* The modules can be imported from other modules using the import command.

The modules are best way to share your work, your tools with others. Those are available at - https://docs.python.org/3/library/ & https://docs.python.org/2/library/

### Demonstrate
* test_hello_module.py & hello_module.py

```
#!/usr/bin/python3
# 'hello_module.py'

def helloworld():
   print ("Hello World!")

def goodbye():
   print ("Good Bye Dear!")


```

and script to use above module:

```

#!/usr/bin/python3
# 'test_hello_module.py' 

from hello_module import goodbye

print ("------I")
print (goodbye)

print ("------II")
goodbye()


```

* How to find-out details of modules?  *dir*, *help* functions.

```

# python3
Python 3.5.2 (default, Nov 17 2016, 17:05:23) 
[GCC 5.4.0 20160609] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> dir(sys)
['__displayhook__', '__doc__', '__excepthook__', '__interactivehook__', '__loader__', '__name__', '__package__', '__spec__', '__stderr__', '__stdin__', '__stdout__', '_clear_type_cache', '_current_frames', '_debugmallocstats', '_getframe', '_home', '_mercurial', '_xoptions', 'abiflags', 'api_version', 'argv', 'base_exec_prefix', 'base_prefix', 'builtin_module_names', 'byteorder', 'call_tracing', 'callstats', 'copyright', 'displayhook', 'dont_write_bytecode', 'exc_info', 'excepthook', 'exec_prefix', 'executable', 'exit', 'flags', 'float_info', 'float_repr_style', 'get_coroutine_wrapper', 'getallocatedblocks', 'getcheckinterval', 'getdefaultencoding', 'getdlopenflags', 'getfilesystemencoding', 'getprofile', 'getrecursionlimit', 'getrefcount', 'getsizeof', 'getswitchinterval', 'gettrace', 'hash_info', 'hexversion', 'implementation', 'int_info', 'intern', 'is_finalizing', 'maxsize', 'maxunicode', 'meta_path', 'modules', 'path', 'path_hooks', 'path_importer_cache', 'platform', 'prefix', 'ps1', 'ps2', 'set_coroutine_wrapper', 'setcheckinterval', 'setdlopenflags', 'setprofile', 'setrecursionlimit', 'setswitchinterval', 'settrace', 'stderr', 'stdin', 'stdout', 'thread_info', 'version', 'version_info', 'warnoptions']
>>> help(sys)
Help on built-in module sys:

NAME
    sys

MODULE REFERENCE
    https://docs.python.org/3.5/library/sys.html

.
.
.    

```


** Modules as Scripts 
* Packages

## Objects and Classes

### Demonstrate - my_class.py

```
#!/usr/bin/python3
class MyClass(object):
    variable = "myvalue"

    def function(self):
        print("This is a message inside the class.")


myobj = MyClass()

print (type(myobj))
print (myobj.variable)


yourobj =  MyClass()
print (yourobj.variable)

yourobj.variable = "yourvalue"

print (yourobj.variable)
yourobj.function()

```

Objects are an encapsulation of variables and functions into a single entity. Objects get their variables and functions from classes. Classes are essentially a template to create your objects.

* __init__ is the constructor for a class. The self parameter refers to the instance of the object 

### Demonstrate -  my_advance_class.py

## Sorting Objects (Instances) 

### Demonstrate -  sort_person.py

```
#!/usr/bin/python3
from  Person import  Person


def byAge(Person):
   return Person.age

p1  = Person("Doland Trump", 70)
p2  = Person("Barack Obama", 55)
p3  = Person("G Bush", 62)
p4  = Person("Bill Clinton", 54)
p5  = Person("Ronald Reagan", 77)



presidents  = [p1, p2, p3, p4, p5] 

print (presidents)

sorted_presidents = sorted(presidents,  key=byAge)

print  (sorted_presidents)

```

Code of Person class is as follow:

```
class Person(object):
    def __init__(self, name, age):
          self.name = name
          self.age  = age
   
    def __repr__(self): 
        return "<Name: ====>  %s >, Age: %d \n"  % (self.name, self.age) 


```


### Quiz 
* Create Class - "City"
* Attributes  - [1] Population [2] Country
* Sort by Population 

## Revisiting Iterators

Python iterator objects are required to support two methods while following the iterator protocol.

* *__iter__* returns the iterator object itself. This is used in for and in statements.
* *__next__* method returns the next value from the iterator. If there is no more items to return then it should raise <nop>StopIteration exception.

### Demonstrate - Counter.py

```
class Counter(object):
    def __init__(self, low, high):
        self.current = low
        self.high = high

    def __iter__(self):
        'Returns itself as an iterator object'
        return self

    def __next__(self):
        'Returns the next value till current is lower than high'
        if self.current > self.high:
            raise StopIteration
        else:
            self.current += 1
            return self.current - 1


c = Counter(5,10)
for i in c:
   print (i, end='   ')

print ("\n")


class EvenNumber(object):
   def __init__(self, low):
        if low % 2 != 0:
           self.current =  low + 1
        else: 
           self.current = low

   def __iter__(self):
        'Returns itself as an iterator object'
        return self

   def __next__(self):
        'Returns the next value till current is lower than high'
        self.current += 2
        return self.current - 2

 
 
e = EvenNumber(2)

print (next(e))
print (next(e))
print (next(e))


```


### String Formatings 

Python supports string formatting. 

The "%" operator is used to format a set of variables enclosed in a "tuple" (a fixed size list), together with a format string, which contains normal text together with "argument specifiers", special symbols like "%s" and "%d".


* %s - String (or any object with a string representation, like numbers)
* %d - Integers
* %f - Floating point numbers
* %.<number of digits>f - Floating point numbers with a fixed amount of digits to the right of the dot.
* %x/%X - Integers in hex representation (lowercase/uppercase)

---+++ Demonstration 

```

>>> name = "Donalt"
>>> age = 72
>>> print ("%s is %d years old " % (name, age))
Donalt is 72 years old 
>>> 
>>> mylist = [1,2,3]
>>> print("A list: %s" % mylist)
A list: [1, 2, 3]
>>> 


```

Take a look at another example: 

```

>>> class Person(object):
...     def __init__(self, name, age):
...           self.age  = age
...           self.name = name
...     def __repr__(self):
...          return "Name: " + self.name + " Age: " + str(self.age)
... 
>>> p = Person('Donald', 80)
>>> print (p)
Name: Donald Age: 80
>>> print ("The person details are : %s" % p)
The person details are : Name: Donald Age: 80
>>> 
>>> print ("The person details are : {}".format(p))
The person details are : Name: Donald Age: 80

```

### Quiz

* Create class called "Share"
* Attributes to the "Share" are: opening price, maximum price, closing price, minimum price, date field (string at this moment) 
* Print share details via *__repr__ and format it nicely

## Regular Expressions
* Regex are text matching patterns described with a formal syntax. 
* The patterns are, actually set of rules, which are executed on text as input to produce either matching subset or modified version of original text.

Your friendship with re will always add advantage to your skills if you ever need to deal with Text Processing in your project.

### Demonstrate - simple_match.py

```

#!/usr/bin/python3
import re

pattern = 'Hello'
text = 'Hello Data Science Folks, How are you?'

match = re.search(pattern, text)

s = match.start()
e = match.end()

print('Found "{}" in "{}" from {} to {} ("{}")'.format(match.re.pattern, match.string, s, e, text[s:e]))

```

Python supports compilation of pattern - it's more efficient to compile the pattern and use it. 
The compile() function converts an expression string into a <nop>RegexObject.

Look at another examile : simple_compiled.py

```
#!/usr/bin/python3 
import re

# Precompile the patterns
regexes = [ re.compile(p) for p in ['Hello', 'Donald'] ]
text = 'Hello DataScience folks, How are you doing today?'

print('Text: {!r}\n'.format(text))

for regex in regexes:
    print (type(regex)) 
    print('Seeking "{}" ->'.format(regex.pattern), end=' ')

    if regex.search(text):
        print('Matchig!')
    else:
        print('No, I am not matching')

```


### Multiple Matches 

#### Demonstrate  - find_all.py
```
#!/usr/bin/python3
import re

text = 'abbaaabbbbaaaaa'

pattern = 'ab'

for match in re.findall(pattern, text):
    print (type(match) )
    print ('Found "%s"' % match)


```


*finditer()* returns an iterator that produces Match instances instead of the strings returned by *findall()*.

Another Script: find_iter.py

```
#!/usr/bin/python3

import re

text = 'abbaaabbbbaaaaa'

pattern = 'ab'

for match in re.finditer(pattern, text):
    print (type(match))
    s = match.start()
    e = match.end()
    print ('Found "%s" at %d:%d' % (text[s:e], s, e))


```


---+++ Matching Codes 

|Code|Meaning|
|\d|a digit|
|\D|a non-digit|
|\s|whitespace (tab, space, newline, etc.)|
|\S|non-whitespace|
|\w|alphanumeric|
|\W|non-alphanumeric|


---+++ search vs match 


