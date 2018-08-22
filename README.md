
<img src="python-logo.png">


# Notes based on LinkedIn/Lynda Python 3 Essential Training (pre 2018 version)
<font color="red">Note:</font>: The course has been updated which you can view here http://bit.ly/2MsGkWv
<a id='top'></a>

Table of Contents (chapters)
* [4. General Syntax](#section4)
    * [Try & Except](#section4a)
    * [Conditional Assignment](#section4b)
* [5. Varibale, Objects & Values](#section5)
    * [Using Numbers](#section5a)
    * [Using Strings](#section5b)
    * [Aggregate values with lists and tuples](#section5c)
    * [Creating associative list with dictionaries](#section5d)
    * [Finding an identity of a variable](#section5e)
    * [Specifying logical values with True and False](#section5f)
* [6. Conditionals](#section6)
    * [Altetrnatives to Switch Cases in Python](#section6a)
    * [Example of using Dictionary to make decisions](#section6b)
    * [Conditional Expression](#section6c)
* [7. Loops](#section7)
    * [While Loop](#section7a)
    * [Iterating with For](#section7b)
        * [readlines(), read() and readlin()](#section7b)
    * [Enumerating Iterators](#section7c)
    * [Break, Continue and Else](#section7d)
* [8. Operators](#section8)
    * [Operating on parts of a container with the slice operator](#section8a)
* [9. Regular Expressions](#section9)
    * [Searching](#section9a)
    * [Replacing](#section9b)
    * [re.compile](#section9c)
* [10. Exceptions](#section10)
    * [Raising Exceptions](#section10a)
* [11. Functions](#section11)
    * [Defining functions: Default values & None](#section11a)
    * [Using lists of arguments](#section11b)
    * [Using named function arguments](#section11c)
    * [Creating a sequence with a Generator Function](#section11d)
* [12. Classes](#section12)
    * [Using Methods](#section12a)
    * [Using object Data](#section12b)
    * [Inheritance](#section12c)
    * [Ploymorphism](#section12d)
    * [Using generators](#section12e)
    * [Using decorators](#section12f)
* [13. String Methods](#section13)
    * [Common String Methods](#section13a)
    * [Formatting Strings with str.format](#section13b)
    * [Splitting and Joining Strings](#section13c)
* [14. Containers](#section14)
    * [Operating on sequences with built-in methods](#section14a)
    * [Organizing data in dictionraies](#section14b)
    * [Operating on character data with bytes and byte arrays](#section14c)
* [15. File I/O](#section15)
    * [Reading and writing text files](#section15a)
    * [Reading and writing binary files](#section15b)
* [16. Databases](#section16)
    * [Creating a database with SQLite3](#section16a)
    * [Creating, retrieving, updating, and deleting records](#section16b)
    * [Creating a database object](#section16c)
* [17. Modules](#section17)
* [18. Debugging](#section18)
* [19. Building a Database Application](#section19)

<a id='section4'></a>
# 4. General Syntax

 `__main__` is the name of the scope in which top-level code executes. A module’s `__name__` is set equal to `__main__` when read from standard input, a script, or from an interactive prompt.

A module can discover whether or not it is running in the main scope by checking its own `__name__`, which allows a common idiom for conditionally executing code in a module when it is run as a script or with python -m but not when it is imported:

```python
if __name__ == "__main__":
    # execute only if run as a script
    main()
```

This is how we can call the `main()` function when script is executed and a chain of function execution occurs:

```python

def main():
    #call function add
    add()

def add():
    #call function printOut
    printOut()

def printOut():
    print("Hello World")

if __name__ == "__main__": main()
```


```python
def main():
    #call function add
    add()

def add():
    #call function printOut
    printOut()

def printOut():
    print("Hello World")

if __name__ == "__main__": main()
```

    Hello World


If we didn't have a main() function defined we wont be able to run functions that are defined __afterwards__. See example:

We are calling `egg()` function from within `main()` though it is defined afterwards.


```python
def main():
    print("This is the main function")
    egg()

def egg():
    print('egg')

if __name__ == "__main__": main()
```

    This is the main function
    egg


__Note:__
* If we didn't have a `main()` function we would get an error as shown below because we can't call `egg()` before it's defined
* Using `main()` function allows us to __<u>control the order of the functions</u>__ we can to call/run on execution 


```python
# del easterEgg
try:
    easterEgg()
except:
    print('ERROR: easterEgg is not defined')

def easterEgg():
    print('egg')
```

    ERROR: easterEgg is not defined


### Assigning Values


```python
# Assign multiple variables

firstName, lastName, homeCity = 'James', 'Bond', 'Kansas City'

print('{} {} is from {}'.format(firstName, lastName, homeCity))
```

    James Bond is from Kansas City



```python
subject, grade = "Math", 98

print("He got {} in {}".format(grade, subject))
```

    He got 98 in Math


__Making copies of variables__


```python
## making copy of varibales 
val_one = 1200
val_two = val_one
#if I change val_one it would not impact val_two
val_one = 1150

print('value one = {} and value two changes to = {}\n'.format(val_one, val_two))
print('memory address for val_one = {} \nmemory address for val_two = {}\n'.format(id(val_one), id(val_two)))

## making a copy of lists the wrong way (both pointing to the same memory address)
list_one = [1,2,3,4,5]
list_two = list_one
list_one.remove(2)

print('first list = {} and second list changes to = {}\n'.format(list_one, list_two))
print('memory address for val_one = {} \nmemory address for val_two = {}'.format(id(list_one), id(list_two)))
```

    value one = 1150 and value two changes to = 1200
    
    memory address for val_one = 4563873264 
    memory address for val_two = 4563873392
    
    first list = [1, 3, 4, 5] and second list changes to = [1, 3, 4, 5]
    
    memory address for val_one = 4563366728 
    memory address for val_two = 4563366728


### Example using Python for Swapping Values


```python
a, b = "A", "B"
a, b = b, a
print(a)
print(b)
```

    B
    A


## Printing in Python


```python
# print strings or numbers simple example
print(1)
print("hello world")
print(1+2+2)
```

    1
    hello world
    5



```python
#print variables
a = "Hello World"
b = 1
c = 1+2+3

print(a)
print(b)
print(c)
```

    Hello World
    1
    6


### Printing using `.format()`


```python
#Print examples using text and variables via Format
score1 = 100
score2 = 95

print("My score in math was {} and in physics was {}".format(score1, score2))
```

    My score in math was 100 and in physics was 95


## Printing memory address


```python
score3 = 80
id(score3)
```




    4527044016




```python
#using print() function
varA = 100

print("varA has a value = {} and a memory address = {}".format(varA, id(varA)))
```

    varA has a value = 100 and a memory address = 4527044656


<a id='section4b'></a>
### Conditional Assignment 


```python
def main():
    a, b = 0, 1
    s = "less than" if a < b else "not less than"
    print(s)

if __name__ == "__main__": main()
```

    less than



```python
print("I am in main()" if __name__ == "__main__" else "not in main")
```

    I am in main()



```python
a, b = 2, 3
c = a + b if a > 0 and b > 0 else 0
print(c)
```

    5


### how objects are created


```python
class Egg:
    def __init__(self, style='fried'):  #initializing 
        self.style = style
    
    def whatKind(self):
        return self.style

def main():
    fried = Egg()
    scrambled = Egg('scrambled')
    print(fried.whatKind())
    print(scrambled.whatKind())

if __name__ == '__main__': main()
```

    fried
    scrambled


<a id='section5'></a>

# 5. Varibales, Objects & Values
[Top](#top)

* Everthing in Python is an object
* Every object has an ID, Type and Value
    * ID uniquely identifies a particular instance of an object
    * Cannot change for the life of the object
    * Type identifies the Class of an object which cannot change for the life of the object
    

    


```python
#define varibale x
x = 49
#value of x
x
```




    49




```python
#id(x) a unique and constant for this object during its lifetime
id(x)
```




    4549812688




```python
type(x)
```




    int



**All varibales in Python are FIRST CLASS objects**


```python
x = 43 ## we are not changing the value, rather changing the reference hence the new id()
id(x)
```




    4549812496




```python
x = 49 ## if we switch back to the previous value we get the same id()/address
id(x)
```




    4549812688



**Most fundamental (primitive) types in Python are immutable :**
* numbers, string tupels

**Mutable objects include:**
* lists, dictionaries, other objects depending upon implementation

<a id='section5a'></a>
### Using Numbers
[Top](#top)


```python
def main():
    num = 42
    print('1.',type(num), num)
    num = 42.0
    print('2.',type(num), num)
    num = 42 / 9  # Floating point division
    print('3. floating point division', type(num), num)
    num = 42 // 9 # floor or integer division
    print('4. integer division', type(num), num)
    num = round(42 / 9)
    print('5. rounding',type(num), num)
    num = round(42 / 9, 2)
    print('6. rounding', type(num), num)
    num = 42 % 9
    print('7. Modulo/remainder', type(num), num)
    num = int(42.9)
    print('8. int() func', type(num), num)
    num = float(42)
    print('9. float() func', type(num), num)

if __name__ == "__main__": main()
```

    1. <class 'int'> 42
    2. <class 'float'> 42.0
    3. floating point division <class 'float'> 4.666666666666667
    4. integer division <class 'int'> 4
    5. rounding <class 'int'> 5
    6. rounding <class 'float'> 4.67
    7. Modulo/remainder <class 'int'> 6
    8. int() func <class 'int'> 42
    9. float() func <class 'float'> 42.0


<a id='section5b'></a>
### Using Strings
[Top](#top)


```python
#using \n for new line
s = 'this is a\nstring!'
rawString = r'this is a\nstring!' # this is called a raw string
print(s)
print(rawString)
```

    this is a
    string!
    this is a\nstring!


**Formatting**


```python
n = 42
s = 'this is a {} string'.format(n) #using format method of the string object
print(s)
```

    this is a 42 string



```python
# old way of doing this but will go away
n = 42
s = "this is a %s string" %n
print(s)
```

    this is a 42 string


**Creating a string that spans multiple lines**
* Using ''' ''' or """  """


```python
s = '''
this is a string
line after line
of text and more
text.
'''

print(s)
```

    
    this is a string
    line after line
    of text and more
    text.
    



```python
##escaping
s = '''\
this is a string \
line after line \
of text and more \
text.
'''
print(s)
```

    this is a string line after line of text and more text.
    


<a id='section5c'></a>
### Aggregating values with lists and tuples


```python
x = (1, 2, 3)
print(type(x), x)
try:
    x.append(5)
except:
    print('Sorry, can\'t append Tuples are immutable')

y = [1, 2, 3]
y.append(5)
y.insert(2,4)
print(type(y), y)

a = 'this is a string'
print(type(a), a[10:])
```

    <class 'tuple'> (1, 2, 3)
    Sorry, can't append Tuples are immutable
    <class 'list'> [1, 2, 4, 3, 5]
    <class 'str'> string


<a id='section5d'></a>
### Creating associative list with dictionaries


```python
d = {'one':1, 'two': 2, 'three': 3, 'four': 4, 'five': 5}
print(d, end='\n\n')

for k in d:
    print(k,d[k])

# to get it sorted
print('\n')
print('printing the dictionary sorted\n')
for k in sorted(d.keys()):
    print(k,d[k])
```

    {'three': 3, 'one': 1, 'five': 5, 'four': 4, 'two': 2}
    
    three 3
    one 1
    five 5
    four 4
    two 2
    
    
    printing the dictionary sorted
    
    five 5
    four 4
    one 1
    three 3
    two 2


**Using the dict() constructor to create a dictionary**


```python
d = dict(
    one = 1,
    two = 2,
    three = 3,
    four = 4,
    five = 5
)
print(d)
```

    {'three': 3, 'one': 1, 'five': 5, 'four': 4, 'two': 2}



```python
d['seven'] = 7
d
```




    {'five': 5, 'four': 4, 'one': 1, 'seven': 7, 'three': 3, 'two': 2}



<a id='section5e'></a>

### Finding the type of identity of a varibale
[Top](#top)

Remember:
**Varibales are references to objects**


```python
x = 42
print(id(x))
```

    4297149840



```python
y = 42
print(id(y))
```

    4297149840



```python
x == y # test for equality - compares VALUES
```




    True




```python
x is y # test if they are the same object - compares IDs
```




    True




```python
x = dict(x = 42)
x
```




    {'x': 42}




```python
id(x)
```




    4369898888




```python
y = dict( x= 42)
id(y)
```




    4369612424




```python
x == y
```




    True




```python
x is y # it's because a dictionary is immutable object
```




    False




```python
a = [1, 2, 3]
b = [1, 2, 3]
print(a is b) # not the same object
print(a == b) # same value
```

    False
    True


<a id='section5f'></a>

### Specifying logical values with True and False
[Top](#top)


```python
a, b = 0, 1
a == b
```




    False




```python
a < b
```




    True




```python
a is b
```




    False




```python
a = True
print(type(a))
print(id(a))
```

    <class 'bool'>
    4296767152



```python
b = True
print(id(b))
print(id(True))
print(id(False))
```

    4296767152
    4296767152
    4296767120


<a id='section6'></a>

# Conditionals

### IF-ELIF-ELSE    
[Top](#top)


```python
v = 'seven'

if v == 'one':
    print('it is ONE')
elif v == 'two':
    print('it is TWO')
elif v == 'three':
    print('it is THREE')
else:
    print('it is something else')
```

    it is something else


<a id='section6a'></a>

### Other strategies for multiple choices
#### Alternatives to Switch or Case options we can use Dictionaries              
[Top](#top)


```python
choices = dict(
one = 'first',
two = 'second',
three = 'third',
four = 'fourth',
five = 'fifth'
)

v = 'three'
print(choices[v])
```

    third


**issues with this approach if we use something outside the list it will generate an error 
Which we can catch with `Try` and `Except`**


```python
v = 'seven'
try:
    choices[v]
except:
    print('Did not find')
```

    Did not find


**another strategy using Dictionary .get() method**


```python
print(choices.get(v, 'Other')) #get method looks for value, if not found will print 'Other'
```

    Other


#### Another option is using dictionaries in this approach: 

```python
{ 'option1' : function1,
  'option2' : function2,
  'option3' : function3,
  'option4' : function4 }[value]()
```


```python
j = 'b'

result = {
    'a': lambda x: x * 5,
    'b': lambda x: x + 7,
    'c': lambda x: x - 2 
} [j](1)

# passing value 1 to function b which gives us 1 + 7 = 8
print(result)
```

    8


**One more example**  
we use the `.get()` which helps us define a default value


```python
def test(x):
    return {
        'a': 1,
        'b': 2,
        'c': 3
    }.get(x, 'nothing')
```


```python
i = 'b'
test(i)
```




    2




```python
test('c')
```




    3




```python
test(9)
```




    'nothing'




```python
choices = dict(
one = lambda x: x - 1,
two = lambda x: x- 2,
three = lambda x: x- 3,
four = lambda x: x- 4,
five = lambda x: x- 5
)

v = 'four'
print(choices.get(v, 'Nothing')(6))
```

    2


<a id='section6b'></a>
#### Example of using Dictionary to make decisions
[Top](#top)


```python
def display(x):
    return x**2

def root(x):
    return x**0.5

even = {
1: lambda x: display(x),
2: lambda x: display(x),
3: lambda x: display(x),
4: lambda x: root(x),
9: lambda x: root(x)
}

num = int(input())

try:
    print(even.get(num, 'Doesn\'t Exist')(num))
except:
    print(num * 1.5)
```

    3
    9


<a id='section6c'></a>
### Conditional Expression



```python
a , b = 0, 1
v = "a greater than b" if a > b else "a is less than b"
print(v)
```

    a is less than b


<a id='section7'></a>
# 7. Loops
[Top](#top)

<a id='section7a'></a>
### While Loop


```python
def main():
    # simple fibonacci series
    # the sum of two elements defines the next set
    a, b = 0, 1
    while b < 150:
        print(b, end=' ')
        a, b = b, a + b

if __name__ == "__main__": main()
```

    1 1 2 3 5 8 13 21 34 55 89 144 

<a id='section7b'></a>
### Iterating with` for`
Note: `readlines()` and `read().split('/n')` are equivalent
### Difference between `read()`, `readlines()` and `readline()`

#### `readlines( )`  
The method `readlines()` reads until EOF using `readline()` and returns a list containing the lines


```python
# Readlines() a list of strings for each line. 
fh = open('lines.txt')
content = fh.readlines()
fh.close()

print(content) #print all
print('\n')
print(content[0]) #show me first item of the list
print(content[-1]) #show me last item of the list
```

    ['This is the first line of text\n', 'This is the second line of text\n', 'This is the third line of text\n', 'This is the fourth line of text\n', 'This is the fifth line of text\n', 'This is the last line of text']
    
    
    This is the first line of text
    
    This is the last line of text



```python
#looping example
for i in content:
    print(i)
```

    This is the first line of text
    
    This is the second line of text
    
    This is the third line of text
    
    This is the fourth line of text
    
    This is the fifth line of text
    
    This is the last line of text


#### `readline( )`


```python
# Readline() - reads the first line only. So, looping will go through the characters from the first line
fh = open('lines.txt')
content = fh.readline()
fh.close()

print(content) #prints all content captured which is the first line
print(content[0]) #prints the firt character
print(content[-1]) #prints the last character in this case it is space so will look blank
```

    This is the first line of text
    
    T
    
    



```python
#looping example
for i in content:
    print(i)
```

    T
    h
    i
    s
     
    i
    s
     
    t
    h
    e
     
    f
    i
    r
    s
    t
     
    l
    i
    n
    e
     
    o
    f
     
    t
    e
    x
    t
    
    


#### `read( )`


```python
# Read() - reads the entire text 
# So, looping will go through the characters of the entire text
fh = open('lines.txt')
content =  fh.read()
fh.close()

print(content) #prints all content captured which is the first line
print('\n')
print(content[0]) #prints the firt character
print(content[-1]) #prints the last character in this case it is space so will look blank
```

    This is the first line of text
    This is the second line of text
    This is the third line of text
    This is the fourth line of text
    This is the fifth line of text
    This is the last line of text
    
    
    T
    t



```python
#looping example
for i in content:
    print(i)
```

    T
    h
    i
    s
     
    i
    s
     
    t
    h
    e
     
    f
    i
    r
    s
    t
     
    l
    i
    n
    e
     
    o
    f
     
    t
    e
    x
    t
    
    
    T
    h
    i
    s
     
    i
    s
     
    t
    h
    e
     
    s
    e
    c
    o
    n
    d
     
    l
    i
    n
    e
     
    o
    f
     
    t
    e
    x
    t
    
    
    T
    h
    i
    s
     
    i
    s
     
    t
    h
    e
     
    t
    h
    i
    r
    d
     
    l
    i
    n
    e
     
    o
    f
     
    t
    e
    x
    t
    
    
    T
    h
    i
    s
     
    i
    s
     
    t
    h
    e
     
    f
    o
    u
    r
    t
    h
     
    l
    i
    n
    e
     
    o
    f
     
    t
    e
    x
    t
    
    
    T
    h
    i
    s
     
    i
    s
     
    t
    h
    e
     
    f
    i
    f
    t
    h
     
    l
    i
    n
    e
     
    o
    f
     
    t
    e
    x
    t
    
    
    T
    h
    i
    s
     
    i
    s
     
    t
    h
    e
     
    l
    a
    s
    t
     
    l
    i
    n
    e
     
    o
    f
     
    t
    e
    x
    t


## Iterating over `readlines()` example

* using `readlines()` and `print(end="")` to avoid double `\n` since by default `print(end ="\n")`


```python
def main():
    fh = open('lines.txt')
    for line in fh.readlines():
        print(line, end="")
    fh.close()
if __name__ == "__main__": main()
```

    This is the first line of text
    This is the second line of text
    This is the third line of text
    This is the fourth line of text
    This is the fifth line of text
    This is the last line of text


```python
# or can be done using .strip()

def main():
    fh = open('lines.txt')
    for line in fh.readlines():
        print(line.strip())
    fh.close()
if __name__ == "__main__": main()

```

    This is the first line of text
    This is the second line of text
    This is the third line of text
    This is the fourth line of text
    This is the fifth line of text
    This is the last line of text


__`read()` with `print(end="")` sice it reads characater by character. This way it keeps reading until line ends via `'\n'`__


```python
fh = open('lines.txt')
for line in fh.read():
    print(line, end="")
fh.close()
```

    This is the first line of text
    This is the second line of text
    This is the third line of text
    This is the fourth line of text
    This is the fifth line of text
    This is the last line of text

__Same as above, but accomplishing similar results with `read()` and `.split('/n)`__


```python
fh = open('lines.txt')
for line in fh.read().split('/n'):
    print(line)
fh.close()
```

    This is the first line of text
    This is the second line of text
    This is the third line of text
    This is the fourth line of text
    This is the fifth line of text
    This is the last line of text


__using `readline()` and `split("/n")`__ 


```python
def main():
    fh = open('lines.txt')
    for line in fh.readline().split('/n'):
        print(line)
    fh.close()
if __name__ == "__main__": main()
```

    This is the first line of text
    


__using `readline()` with `print(end="")`__


```python
def main():
    fh = open('./07 Loops/lines.txt')
    for line in fh.readline():
        print(line, end="")
    fh.close()
if __name__ == "__main__": main()
```

    01 This is a line of text


### Enumerating Iterators
<a id='section7c'></a>


```python
def main():
    fh = open('lines.txt')
    for index, line in enumerate(fh.readlines()):
        print(index, line, end="")
    fh.close()
if __name__ == "__main__": main()
```

    0 This is the first line of text
    1 This is the second line of text
    2 This is the third line of text
    3 This is the fourth line of text
    4 This is the fifth line of text
    5 This is the last line of text


```python
s = 'this is a string'

for i, c in enumerate(s):
    if c == 's': print('index {} is on s'.format(i))
```

    index 3 is on s
    index 6 is on s
    index 10 is on s


### Controlling loop flow with Break, Continue, and Else
<a id='section7d'></a>

### Continue - to shortcut a for loop


```python
# to skip over letter 's'
s = 'this is a string'
for c in s:
    if c == 's': continue
    print(c, end='')
```

    thi i a tring

### Break


```python
# If I want to stop right at the first enconter of letter 's'
s = 'this is a string'
for c in s:
    if c == 's': break
    print(c, end='')
```

    thi

### Else


```python
# else used when iterators get out of stuff to iterate
s = 'this is a string'
for c in s:
    print(c, end='')
else:
    print(' else')
```

    this is a string else



```python
# else can be used when a condition becomes false
s = 'this is a string'
i = 0
while (i < len(s)):
    print(s[i], end='')
    i += 1
else:
    print(' else done')
```

    this is a string else done


<a id='section8'></a>
# 8. Operators
[Top](#top)


```python
5 // 2
```




    2




```python
5 % 2
```




    1




```python
5 / 2
```




    2.5




```python
divmod(5, 3) # gives the result and remainder as a tuple
```




    (1, 2)




```python
num = 2
num += 1
print(num)
```

    3



```python
num -= 1
print(num)
```

    2



```python
num *=5
print(num)
```

    10



```python
num //=5
print(num)
```

    2



```python
num *=5
num /= 5
print(num)
```

    2.0


### Bitwise values


```python
5
```




    5




```python
0b0101
```




    5




```python
# print out Binary Value
def b(n):
    print('{:08b}'.format(n))
```


```python
b(5)
```

    00000101



```python
x , y = 0x55, 0xaa
```


```python
b(x)
b(y)
b(x | y)
b(x & y)
b(x ^ y)
b(x ^ 0)
b(x ^ 0xff)
b( x << 4)
b( x >> 4)
b(~x)
```

    01010101
    10101010
    11111111
    00000000
    11111111
    01010101
    10101010
    10101010000
    00000101
    -1010110


### Comparing identities with IS and IS NOT
There are times when we need to compare Objects by comparing their IDs and not just their values


```python
x, y = 5, 6
```


```python
x is y
```




    False




```python
x is not y
```




    True




```python
y = 5
x is y
```




    True




```python
x, y = [5], [5]
x is y #not the same IDs
```




    False




```python
print(id(y))
print(id(x))
```

    4370870408
    4370898504



```python
x == y #same values
```




    True




```python
a = [1, 2, 3]
b = a #this points to the same object
a is b
```




    True




```python
#making a new copy
b = a[:]
a is b
```




    False



<a id='section8a'></a>
### Operating on parts of container with the slice operator


```python
list = []
list = [0,1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```


```python
s = list[0:5]
s
```




    [0, 1, 2, 3, 4]




```python
for i in range(0,10): print(i, end=', ')
```

    0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 


```python
list[:] = range(100)
print(list)
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99]



```python
list[27] #slice of one element
```




    27




```python
list[27:42] #slice with start and end
```




    [27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41]




```python
list[27:42:3] #slice with start and end for every third element
```




    [27, 30, 33, 36, 39]




```python
for i in list[27:43:3]: print(i)
```

    27
    30
    33
    36
    39
    42



```python
list[27:43:3] = [99,99,99,99,99,99]
print(list)
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 99, 28, 29, 99, 31, 32, 99, 34, 35, 99, 37, 38, 99, 40, 41, 99, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99]


<a id='section9'></a>
# 9. Regular Expressions
[Top](#top)

### Searching with Regular Expressions
<a id='section9a'></a>


```python
import re

def main():
    fh = open('raven.txt')
    for i, line in enumerate(fh.readlines()):
        if re.search('(Len|Neverm)ore', line): #matches Lenore or Nevermore
            print(i, line, end='')

if __name__ == "__main__": main()
    
```

    10 From my books surcease of sorrow--sorrow for the lost Lenore--
    11 For the rare and radiant maiden whom the angels name Lenore--
    31 And the only word there spoken was the whispered word, “Lenore!”
    32 This I whispered, and an echo murmured back the word, “Lenore!”--
    54 Quoth the raven “Nevermore.”
    61 With such name as “Nevermore.”
    68 Then the bird said “Nevermore.”
    82 Meant in croaking “Nevermore.”
    95 Respite--respite and nepenthe from thy memories of Lenore;
    96 Quaff, oh quaff this kind nepenthe and forget this lost Lenore!”
    97 Quoth the raven, “Nevermore.”
    104 Quoth the raven, “Nevermore.”
    109 It shall clasp a sainted maiden whom the angels name Lenore--
    110 Clasp a rare and radiant maiden whom the angels name Lenore.”
    111 Quoth the raven, “Nevermore.”
    118 Quoth the raven, “Nevermore.”



```python
import re

def main():
    fh = open('raven.txt')
    for i, line in enumerate(fh.readlines()):
        match = re.search('(Len|Neverm)ore', line)
        if match: #matches Lenore or Nevermore
            print(i, match.group())

if __name__ == "__main__": main()
    
```

    10 Lenore
    11 Lenore
    31 Lenore
    32 Lenore
    54 Nevermore
    61 Nevermore
    68 Nevermore
    82 Nevermore
    95 Lenore
    96 Lenore
    97 Nevermore
    104 Nevermore
    109 Lenore
    110 Lenore
    111 Nevermore
    118 Nevermore


### Replacing with Regular Expressions
<a id='section9b'></a>


```python
import re

def main():
    fh = open('raven.txt')
    for i, line in enumerate(fh.readlines()):
         match = re.search('(Len|Neverm)ore', line) #matches Lenore or Nevermore
         if match:
            print(i, line.replace(match.group(), '###'), end='')
if __name__ == "__main__": main()
```

    10 From my books surcease of sorrow--sorrow for the lost ###--
    11 For the rare and radiant maiden whom the angels name ###--
    31 And the only word there spoken was the whispered word, “###!”
    32 This I whispered, and an echo murmured back the word, “###!”--
    54 Quoth the raven “###.”
    61 With such name as “###.”
    68 Then the bird said “###.”
    82 Meant in croaking “###.”
    95 Respite--respite and nepenthe from thy memories of ###;
    96 Quaff, oh quaff this kind nepenthe and forget this lost ###!”
    97 Quoth the raven, “###.”
    104 Quoth the raven, “###.”
    109 It shall clasp a sainted maiden whom the angels name ###--
    110 Clasp a rare and radiant maiden whom the angels name ###.”
    111 Quoth the raven, “###.”
    118 Quoth the raven, “###.”


### Resusing Regular Expressions with re.compile
<a id='section9c'></a>


```python
import re

def main():
    fh = open('raven.txt')
    pattern = re.compile('(Len|Neverm)ore', re.IGNORECASE) # more efficient since we compile the pattern only once
    for i, line in enumerate(fh.readlines()):
        if re.search(pattern, line): #matches Lenore or Nevermore
            print(i, line, end='')

if __name__ == "__main__": main()
```

    10 From my books surcease of sorrow--sorrow for the lost Lenore--
    11 For the rare and radiant maiden whom the angels name Lenore--
    31 And the only word there spoken was the whispered word, “Lenore!”
    32 This I whispered, and an echo murmured back the word, “Lenore!”--
    54 Quoth the raven “Nevermore.”
    61 With such name as “Nevermore.”
    68 Then the bird said “Nevermore.”
    75 Of “Never--nevermore.”
    82 Meant in croaking “Nevermore.”
    89 _She_ shall press, ah, nevermore!
    95 Respite--respite and nepenthe from thy memories of Lenore;
    96 Quaff, oh quaff this kind nepenthe and forget this lost Lenore!”
    97 Quoth the raven, “Nevermore.”
    104 Quoth the raven, “Nevermore.”
    109 It shall clasp a sainted maiden whom the angels name Lenore--
    110 Clasp a rare and radiant maiden whom the angels name Lenore.”
    111 Quoth the raven, “Nevermore.”
    118 Quoth the raven, “Nevermore.”
    125 Shall be lifted--nevermore!


```python
import re

def main():
    fh = open('raven.txt')
    pattern = re.compile('(Len|Neverm)ore', re.IGNORECASE) # more efficient since we compile the pattern only once
    for i, line in enumerate(fh.readlines()):
        if re.search(pattern, line): #matches Lenore or Nevermore
            print(i, pattern.sub('###',line), end='')

if __name__ == "__main__": main()
```

    10 From my books surcease of sorrow--sorrow for the lost ###--
    11 For the rare and radiant maiden whom the angels name ###--
    31 And the only word there spoken was the whispered word, “###!”
    32 This I whispered, and an echo murmured back the word, “###!”--
    54 Quoth the raven “###.”
    61 With such name as “###.”
    68 Then the bird said “###.”
    75 Of “Never--###.”
    82 Meant in croaking “###.”
    89 _She_ shall press, ah, ###!
    95 Respite--respite and nepenthe from thy memories of ###;
    96 Quaff, oh quaff this kind nepenthe and forget this lost ###!”
    97 Quoth the raven, “###.”
    104 Quoth the raven, “###.”
    109 It shall clasp a sainted maiden whom the angels name ###--
    110 Clasp a rare and radiant maiden whom the angels name ###.”
    111 Quoth the raven, “###.”
    118 Quoth the raven, “###.”
    125 Shall be lifted--###!

<a id='section10'></a>
# 10. Exceptions
[Top](#top)


### Handling Excpetions


```python
def main():
    try:
        fh = open('lins.txt')
    except IOError as e:
        print('could not open the file. come back tomorrow: ', e)
    else:
        for line in fh: print(line.strip()) # removes trailing lines

if __name__ == "__main__": main()

```

    could not open the file. come back tomorrow:  [Errno 2] No such file or directory: 'lins.txt'


### Raising Exceptions
<a id='section10a'></a>


```python
def main():
    try:
        for line in readfile('lies.doc'): 
            print(line.strip()) # removes trailing lines
    except IOError as e:
        print('cannot read file: ', e)
    except ValueError as e:
        print('bad filename: ', e)
        

def readfile(filename):
    if filename.endswith('.txt'):
        fh = open(filename)
        return fh.readlines()
    else: 
        raise ValueError('Filename must end with .txt')

if __name__ == "__main__": main()
```

    bad filename:  Filename must end with .txt


<a id='section11'></a>
# 11. Functions
[Top](#top)

<a id='section11a'></a>
### Defining functions with arguments: Default values & None


```python
def main():
    testfunc()

def testfunc():
    print('This is a test function')

if __name__ == "__main__": main()
```

    This is a test function



```python
def main():
    testfunc()

def testfunc():
    pass #to avoid an error, can be used as a placeholder

if __name__ == "__main__": main()
```

#### Using Paremeters & default values
* Parameters can be required or optionals
* Function arguments must be initialized
* To avoid errors, we can use defaut values


```python
def main():
    testfunc(42, 1)

def testfunc(number = 1, another = 42, onemore= 75):
    print('This is a test function',number, another, onemore )

if __name__ == "__main__": main()
```

    This is a test function 42 1 75


#### Making the parameter options using None
None is a special value that we can also test for


```python
def main():
    testfunc(42, 1)
def testfunc(number = 1, another = None, onemore= 75):
    if another is None:
        another = 112
    print('This is a test function',number, another, onemore )

if __name__ == "__main__": main()
```

    This is a test function 42 1 75


<a id='section11b'></a>
### Using lists of arguments
We get a Tuple


```python
def main():
    testfunc(1, 2, 3, 4)

def testfunc(*args):
    print('This is a tuple')
    for n in args: print(n, end= ' ')

if __name__ == "__main__": main()
```

    This is a tuple
    1 2 3 4 


```python
def main():
    testfunc(1, 2, 3, 4)

def testfunc(number, another, *args):
    print('Your arguemnts: ', number, another, args)

if __name__ == "__main__": main()
```

    Your arguemnts:  1 2 (3, 4)


<a id='section11c'></a>
### Using named function arguments
using (**kwargs) = stands for Keyboard Arguments


```python
def main():
    testfunc(one = 1, two = 2, four = 42)

def testfunc(**kwargs):
    print('This is a test function', kwargs['one'], kwargs['two'], kwargs['four'])

if __name__ == "__main__": main()

```

    This is a test function 1 2 42


#### Combination of different argument types:


```python
def main():
    testfunc(5, 6, 7, 8, 9, 10, one = 1, two = 2, four = 42)

def testfunc(this, that ,other, *args, **kwargs):
    print('This is a test function', 
          this, that, other, args,
          kwargs['one'], kwargs['two'], kwargs['four'])

if __name__ == "__main__": main()
```

    This is a test function 5 6 7 (8, 9, 10) 1 2 42



```python
def main():
    testfunc(5, 6, 7, 8, 9, 10, one = 1, two = 2, four = 42)

def testfunc(this, that ,other, *args, **kwargs):
    for k in kwargs: print(k, kwargs[k]) #wont maintain order
    for n in args: print(n) #tuples do maintain order

if __name__ == "__main__": main()
```

    four 42
    one 1
    two 2
    8
    9
    10


#### Returning values from functions


```python
def main():
    for n in testfunc(): print(n, end= ' ')

def testfunc():
    return range(25)

if __name__ == '__main__': main()
```

    0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 

<a id='section11d'></a>
### Generator Function


```python
def main():
    print("This is the functions.py file.")
    for i in inclusive_range(2,25,3):
        print(i, end = ' ')

def inclusive_range(*args):
    numargs = len(args)
    if numargs < 1: raise TypeError('requires at least one argument')
    elif numargs == 1: 
        stop = args[0]
        start = 0
        step = 1
    elif numargs == 2:
        (start, stop) = args
        step = 1
    elif numargs == 3:
        (start, stop, step) = args
    else: 
        raise TypeError('inclusive_range expected at most 3 arguments, got {}'.format(numargs))
    
    i = start
    try:
        while i <= stop:
            yield i # next time it run it will resume
            i += step
    except TypeError as e:
        print(e)
    
if __name__ == "__main__": main()
```

    This is the functions.py file.
    2 5 8 11 14 17 20 23 

<a id='section12'></a>
# 12. Classes
[Top](#top)
* Classes are how we create our own objects
* A class is the blueprint for an object
* An object is an instance of a class


```python
class Duck:
    def quack(self):
        print('Quaaack!')

    def walk(self):
        print('Walks like a duck.')

def main():
    donald = Duck() #donals is an objet which is an instance of class Duck
    donald.quack()
    donald.walk()

if __name__ == "__main__": main()
```

    Quaaack!
    Walks like a duck.


### Using Methods
<a id='section12a'></a>
* methods are functions
* first argument is always (self) which is a refernce to the object
* **constructor method \__init__**
    * constructors are great for initializing values


```python
class Duck:
    def __init__(self, value):
        print('I am a Constructor')
        self._v = value #creating a local variable that is an attribute of the object i.e. donald
        
    def quack(self, value):
        print('Quaaack!', self._v, value) #now we can use the local varibale

    def walk(self):
        print('Walks like a duck.', self._v)

def main():
    donald = Duck(47) 
    donald.quack(12) #donald is being passed as self
    donald.walk()
    frank = Duck(100)
    frank.quack(10)
    frank.walk()
    

if __name__ == "__main__": main()
```

    I am a Constructor
    Quaaack! 47 12
    Walks like a duck. 47
    I am a Constructor
    Quaaack! 100 10
    Walks like a duck. 100


### Using Object Data
<a id='section12b'></a>
* It is recommended to access local varibales in a class using accessor methods 
    * Set and Get methods as an example


```python
class Duck:
    def __init__(self, color = 'white'):
        self._color = color # using _ is to help us remember that this is a local variable
        
        
    def quack(self):
        print('Quaaack!')

    def walk(self):
        print('Walks like a duck.')
        
    def set_color(self, color): 
        self._color = color
     
    def get_color(self):
        return self._color

def main():
    donald = Duck() #donals is an objet which is an instance of class Duck
    print(donald.get_color())
    donald.set_color('blue')
    print(donald.get_color())

if __name__ == "__main__": main()
```

    white
    blue


**If there are many setters that we need to use and call it can get overwhilming. Another option is to use Dictionary (keyword arguments)**


```python
class Duck:
    def __init__(self, **kwargs):
        self._color = kwargs.get('color','white') #having a default value         
        self._feet = kwargs.get('feet')
        
    def quack(self):
        print('Quaaack!')

    def walk(self):
        print('Walks like a duck.')
        
    def set_color(self, color): 
        self._color = color
     
    def get_color(self):
        return self._color
    
    def get_feet(self):
        return self._feet

def main():
    donald = Duck(color='blue')
    james = Duck()
    print(donald.get_color())
    print(james.get_color())
    smith = Duck(feet=2)
    print(smith.get_feet())
    

if __name__ == "__main__": main()
```

    blue
    white
    2


## Dictionary `.get()` built in function and defaults


```python
j = {'color': 'blue', 'feet': 4}
print(j.get('color', 'black'))

s = {'feet': 4}
print(s.get('color', 'black'))
```

    blue
    black


**instead of having differernt local varibales we can use a dictionary**


```python
class Duck:
    def __init__(self, **kwargs):
        self.varibales = kwargs
        
    def quack(self):
        print('Quaaack!')

    def walk(self):
        print('Walks like a duck.')
        
    def set_color(self, color): 
        self.varibales['color'] = color
    
    def set_feet(self, feet):
        self.varibales['feet'] = feet
     
    def get_color(self):
        return self.varibales.get('color', None)
    
    def get_feet(self):
        return self.varibales.get('feet', 4)

def main():
    donald = Duck(color='blue')
    james = Duck()
    print(donald.get_color())
    print(james.get_color())
    smith = Duck()
    print(smith.get_feet())
    

if __name__ == "__main__": main()
```

    blue
    None
    4


**Make the setters scale as well we can make another modification**

Storing Object data in a Dictionay - the code below is scalable and flexible


```python
class Duck:
    def __init__(self, **kwargs):
        self.varibales = kwargs
        
    def quack(self):
        print('Quaaack!')

    def walk(self):
        print('Walks like a duck.')
        
    def set_variables(self, k, v):
        self.varibales[k] = v
    
    def get_varibales(self, k):
        return self.varibales.get(k, None)

def main():
    donald = Duck(feet = 2)
    donald.set_variables('color','pink')
    print(donald.get_varibales('feet'))
    print(donald.get_varibales('color'))

    
if __name__ == "__main__": main()
```

    2
    pink


### Understanding Inheritance
<a id='section12c'></a>


```python
class Animal:
    def talk(self): print('I have something to say')
    def walk(self): print('Hey, I''m walking'' here!')
    def clothes(self): print('I have nice clothes')    

class Duck(Animal): #now Duck inherits all properties of animal
    def quack(self):
        print('Quaaack!')

    def walk(self):
        #if we want to access the paretn method we use super()
        super().walk()
        print('Walks like a duck.')

def main():
    donald = Duck()
    donald.quack()
    donald.walk() #the Duck walk overwrties the parent, to access both we used super()
    donald.clothes() #from parent
    donald.talk() # from parent

if __name__ == "__main__": main()
```

    Quaaack!
    Hey, Im walking here!
    Walks like a duck.
    I have nice clothes
    I have something to say



```python
class Dog(Animal):
    def clothes(self): print('I have brown and white fur')

fido = Dog()
fido.clothes()
fido.talk()
```

    I have brown and white fur
    I have something to say


### Applying polymorphism to classes
<a id='section12d'></a>


```python
class Duck:
    def quack(self):
        print('Quaaack!')

    def walk(self):
        print('Walks like a duck.')
    
    def bark(self):
        print('Duck cannot bark')
    
    def fur(self):
        print('The duck has feathers')


donald = Duck()
donald.quack()
donald.walk()

```

    Quaaack!
    Walks like a duck.



```python
class Dog:
    def bark(self):
        print('Woof!')
        
    def fur(self): 
        print('the dog has brown and white fur')
    
    def walk(self):
        print('Walks like a dog')
    
    def quack(self):
        print('The dog cannot quack')
        
fido = Dog()
fido.bark()
fido.fur()
```

    Woof!
    the dog has brown and white fur


#### By making both classes have common methods we now can 


```python
for o in (donald, fido):
    o.quack()
    o.walk()
    o.bark()
    o.fur()
```

    Quaaack!
    Walks like a duck.
    Duck cannot bark
    The duck has feathers
    The dog cannot quack
    Walks like a dog
    Woof!
    the dog has brown and white fur
    Duck cannot bark
    The duck has feathers
    The dog cannot quack
    Walks like a dog


#### Polymorphism


```python
def in_the_forest(dog):
    dog.bark()
    dog.fur()

def in_the_pond(duck):
    duck.quack()
    duck.walk()
    
in_the_forest(donald)
in_the_pond(fido)
```

    Duck cannot bark
    The duck has feathers
    The dog cannot quack
    Walks like a dog


### Using generators `__iter__`
<a id='section12e'></a>

An object that can be used in the context of itterable


```python
def main():
    o = range(25)
    for i in o: print(i, end = ' ')

if __name__ == "__main__": main()
```

    0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 


```python
class inclusive_range:
    def __init__(self, *args):
        numargs = len(args)
        if numargs < 1: raise TypeError('requires at least one argument')
        elif numargs == 1:
            self.stop = args[0]
            self.start = 0
            self.step = 1
        elif numargs == 2:
            (self.start, self.stop) = args
            self.step =1 
        elif numargs == 3:
            (self.start, self.stop, self.step) = args
        else: raise TypeError('expected at most 3 arguments, got {}'.format(numargs))

    
    def __iter__(self): #makes the object an iterable object
        i = self.start
        while i <= self.stop:
            yield i
            i += self.step
    
```


```python
for i in inclusive_range(5, 25, 5): print(i, end = ' ')
```

    5 10 15 20 25 

### Using decorators : Special functions that return other functions
<a id='section12f'></a>


```python
class Duck:
    def __init__(self, **kwargs):
        self.properties = kwargs

    def quack(self):
        print('Quaaack!')

    def walk(self):
        print('Walks like a duck.')

    def get_properties(self):
        return self.properties
    
    def set_property(self, key, value):
        print(key, value)
        self.properties[key] = value

    def get_property(self, key):
        return self.properties.get(key, None)

donald = Duck(color = 'blue')
print(donald.get_property('color'))



```

    blue



```python
donald.set_property('feet', 2)
print(donald.get_property('feet'))
```

    feet 2
    2


#### Using `@property` to start declaring `.setter` and `.deleter`


```python
class Duck:
    def __init__(self, **kwargs):
        self.properties = kwargs

    def quack(self):
        print('Quaaack!')

    def walk(self):
        print('Walks like a duck.')

    def get_properties(self):
        return self.properties
    
    def set_property(self, key, value):
        print(key, value)
        self.properties[key] = value

    def get_property(self, key):
        return self.properties.get(key, None)

    @property #turns this function as an accessor
    def color(self):
        return self.properties.get('color', None)
    
    @color.setter #declare a setter
    def color(self, c):
        self.properties['color'] = c
    
    @color.deleter
    def color(self):
        del self.properties['color']

donald = Duck()
donald.color = 'blue'
print(donald.color)
```

    blue


<a id='section13'></a>
# 13. String Methods
[Top](#top)

### Strings are objets
We can operate on a string like objects without using varibale assignment


```python
'This is a string'.upper()
```




    'THIS IS A STRING'




```python
'this is a string'.title()
```




    'This Is A String'




```python
'this is a string {}'.format(42)
```




    'this is a string 42'



<a id='section13a'></a>
### Common string methods
#### Example:   
`upper()`, `lower()`, `strip()`, `rstrip()`, `replace()`, `isalnum()`, `title()`, `isalpha()`, `isprintable()`, `isdigit()`, `capitalize()`, `format()`, `swapcase()`, `find()`


```python
s = 'this is a string'
```


```python
s.capitalize()
```




    'This is a string'




```python
s.upper()
```




    'THIS IS A STRING'




```python
'This Is A String'.swapcase()
```




    'tHIS iS a sTRING'




```python
s.find('is') #finds the position 
```




    2




```python
s.replace('this', 'that')
```




    'that is a string'



### String is immutable , so there methods return a new string while original is unchanged


```python
s #still the same
```




    'this is a string'




```python
id(s)
```




    4368522024




```python
newstring = s.upper()
id(newstring) # new id
```




    4368522888




```python
i = s
id(i) #same id
```




    4368522024




```python
'  this is a string   '.strip() #remove whitespace by default
```




    'this is a string'




```python
'    this is a string  '.rstrip() #remove white space in end
```




    '    this is a string'




```python
s1 = 'this is a string\n'
s1
```




    'this is a string\n'




```python
s1.strip() #remove the new line \n
```




    'this is a string'




```python
s1.rstrip('\n') #same effect
```




    'this is a string'




```python
s.isalnum() #returns False since the string contains spaces
```




    False




```python
'thisisastring'.isalnum()
```




    True




```python
'thisisstring'.isalpha()
```




    True




```python
'1234'.isdigit()
```




    True




```python
s.isdigit()
```




    False




```python
s.isprintable()
```




    True



<a id='section13b'></a>
### Formatting strings with str.format
Remember: Strings are immutable in Python so changes mean a new string is created


```python
a, b = 5, 42
print(a, b)
```

    5 42



```python
'this is {}, that is {}'.format(a, b)
```




    'this is 5, that is 42'




```python
s = 'this is {}, that is {}'
id(s)
```




    4368620256




```python
new = s.format(a, b)
id(new)
```




    4369101280




```python
j = s
id(j)
```




    4368620256



#### Changing positional order


```python
'this is {}, that is {}'.format(b, a) #change the varibale orders
```




    'this is 42, that is 5'




```python
'this is {0}, that is {1}'.format(a, b)
```




    'this is 5, that is 42'




```python
'this is {1}, that is {0}'.format(a, b)
```




    'this is 42, that is 5'




```python
'this is {1}, that is {1}'.format(a, b)
```




    'this is 42, that is 42'




```python
'this is {bob}, that is {fred}'.format(bob = a, fred = b)
```




    'this is 5, that is 42'




```python
d = dict(bob = a, fred = b)
'this is {bob}, that is {fred}'.format(**d)
```




    'this is 5, that is 42'



<a id='section13c'></a>
### Splitting and Joining Strings


```python
s = 'This is a string of words'
```


```python
s.split() #splits by whitespace by default
```




    ['This', 'is', 'a', 'string', 'of', 'words']




```python
s.split('i') #split on i
```




    ['Th', 's ', 's a str', 'ng of words']




```python
words = s.split()
for w in words: print(w)
```

    This
    is
    a
    string
    of
    words



```python
new = ':'.join(words)
new
```




    'This:is:a:string:of:words'




```python
','.join(words)
```




    'This,is,a,string,of,words'




```python
' '.join(words)
```




    'This is a string of words'



### Finding and using string methods
Python documentation


```python
s = 'this is a string'
new = s.center(80) #80 characters
new
```




    '                                this is a string                                '




```python
len(new)
```




    80



<a id='section14'></a>
# 14. Containers
[Top](#top)

**Tuples can be created using the comma operator like this**


```python
t = 1,2,3,4,5
t
```




    (1, 2, 3, 4, 5)



**How to create a tuple with ONE element?**


```python
t = (1) # this is not correct, it will produce an Int
print(t)
print(type(t))
```

    1
    <class 'int'>



```python
t = 1,
print(t)
print(type(t))
```

    (1,)
    <class 'tuple'>



```python
t = tuple(range(25))
print(t)
print(type(t))
```

    (0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24)
    <class 'tuple'>



```python
x = []
type(x)
```




    list




```python
x = list(range(25))
print(x)
print(type(x))
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24]
    <class 'list'>


<a id='section14a'></a>
### Operating on sequences with built-in methods


```python
t = tuple(range(25))
print(t)
```

    (0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24)



```python
10 in t
```




    True




```python
50 in t
```




    False




```python
50 not in t
```




    True




```python
x = list(range(20))
print(x)
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]



```python
10 in x
```




    True




```python
20 in x
```




    False




```python
t.count(4)
```




    1




```python
t.index(6)
```




    6




```python
x.append(100)
```


```python
x.extend(range(20))
print(x)
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 100, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]



```python
x.insert(0, 25)
print(x)
```

    [25, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 100, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]



```python
x.remove(12)
```


```python
print(x)
```

    [25, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 13, 14, 15, 16, 17, 18, 19, 100, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]



```python
del x[12]
print(x)
```

    [25, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 13, 14, 15, 16, 17, 18, 19, 100, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]



```python
x.pop()
```




    19




```python
print(x)
```

    [25, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 13, 14, 15, 16, 17, 18, 19, 100, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18]



```python
x.pop(0)
```




    25




```python
print(x)
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 13, 14, 15, 16, 17, 18, 19, 100, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18]


<a id='section14b'></a>
### Organizing data with dictionaries


```python
d = {'one': 1, 'two': 2, 'three': 3}
d
```




    {'one': 1, 'three': 3, 'two': 2}




```python
d = dict(one = 1, two = 2, three = 3)
d
```




    {'one': 1, 'three': 3, 'two': 2}




```python
x = dict(four = 4, five = 5, six = 6)
s = dict(**x, **d)
print(s)
```

    {'one': 1, 'five': 5, 'four': 4, 'three': 3, 'two': 2, 'six': 6}



```python
'four' in s
```




    True




```python
'four' in d
```




    False




```python
for k,v in s.items(): print(k,v)
```

    one 1
    five 5
    four 4
    three 3
    two 2
    six 6


**Getting exception and using `.get` to avoid**


```python
x['three']
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-112-05f923b6ba3c> in <module>()
    ----> 1 x['three']
    

    KeyError: 'three'



```python
x.get('three')
```


```python
x.get('three', 'not found')
```




    'not found'




```python
del x['four']
print(x)
```

    {'five': 5, 'six': 6}



```python
x.pop('five')
```




    5




```python
x
```




    {'six': 6}




```python
def printMe():
    print('hello world')

f = dict(one = printMe, two = printMe)
```


```python
for k in f.values() : print(k)
```

    <function printMe at 0x104848f28>
    <function printMe at 0x104848f28>



```python
for k in f.values() : print(k())
```

    hello world
    None
    hello world
    None


<a id='section14c'></a>
### Operating on character data with bytes and byte arrays


```python
def main():
    fin = open('./14 Containers/utf8.txt','r', encoding='utf_8')
    fout = open('utf8.html', 'w')
    outbytes = bytearray()
    for line in fin:
        for c in line:
            if ord(c) > 127:
                outbytes += bytes('&#{:04d};'.format(ord(c)), encoding = 'utf_8')
            else:
                outbytes.append(ord(c))
    outstr = str(outbytes, encoding = 'utf_8')
    print(outstr, file = fout)
    print(outstr)
    print('Done.')

if __name__ == "__main__": main()
```

    This is a UTF-8 file. 
    It has some interesting characters in it. 
    &#1641;(&#0865;&#3663;&#0815;&#0865;&#3663;)&#1782;
    
    Done.


<a id='section15'></a>
# 15. File I/O
[Top](#top)

## Opening Files


```python
def main():
    f = open('lines.txt') # read mode is the default r
    for line in f:
        print(line, end = '')

if __name__ == "__main__": main()
```

    This is the first line of text
    This is the second line of text
    This is the third line of text
    This is the fourth line of text
    This is the fifth line of text
    This is the last line of text


```python
def main():
    f = open('lines.txt', 'r') 
    for line in f.readlines():
        print(line, end = '')

if __name__ == "__main__": main()
```

    This is the first line of text
    This is the second line of text
    This is the third line of text
    This is the fourth line of text
    This is the fifth line of text
    This is the last line of text

<a id='section15a'></a>
## Reading and Writing Text files


```python
def main():
    infile = open('lines.txt') # read mode is the default r
    outfile = open('new.txt', 'w')
    for line in infile:
        print(line, file = outfile, end = '')
    print('Done.')

if __name__ == "__main__": main()
```

    Done.


**Working with big files**  
Reading in buffer bytes, for examples infile.read(50000) means read
at most 50000 bytes from infile, then read the next 50000 bytes. This
way we are reading in chunks instead of one line at a time.

**`file.read([size])`**  

Read at most size bytes from the file (less if the read hits EOF before obtaining size bytes). If the size argument is negative or omitted, read all data until EOF is reached. The bytes are returned as a string object. An empty string is returned when EOF is encountered immediately. (For certain files, like ttys, it makes sense to continue reading after an EOF is hit.) Note that this method may call the underlying C function fread() more than once in an effort to acquire as close to size bytes as possible. Also note that when in non-blocking mode, less data than was requested may be returned, even if no size parameter was given.

**buffer is not the file but what you last read from the file. len(buffer) will evaluate to False when buffer is empty, i.e. when there's no more data to read from the file.**


```python
def main():
    buffersize = 50000
    infile = open('bigfile.txt', 'r') 
    outfile = open('newbigfile.txt', 'w')
    buffer = infile.read(buffersize) #
    
    while len(buffer):
        outfile.write(buffer)
        print('.', end = '')
        buffer = infile.read(buffersize)
    print()
    print('Done.')

if __name__ == "__main__": main()
```

    ............................................
    Done.


<a id='section15b'></a>
## Reading and writing binary files 
There is a difference when working with Text files vs working with Binary files


```python
def main():
    buffersize = 50000
    infile = open('olives.jpg', 'rb')  #open in read binary mode
    outfile = open('new.jpg', 'wb')
    buffer = infile.read(buffersize)
                        
    while len(buffer):
        outfile.write(buffer)
        print('.', end = '')
        buffer = infile.read(buffersize)
    print()
    print('Done.')
    
if __name__ == "__main__": main()
```

    ..
    Done.


<a id='section16'></a>
# 16. Databases
[Top](#top)

<a id='section16a'></a>
### Creating a database with SQLite 3


```python
import sqlite3

def main():
    db = sqlite3.connect('test.db')
    db.execute('drop table if exists test')
    db.execute('create table test (t1 text, i1 int)')
    db.execute('insert into test (t1, i1) values (?,?)', ('one', 1))
    db.execute('insert into test (t1, i1) values (?,?)', ('two', 2))
    db.execute('insert into test (t1, i1) values (?,?)', ('three', 3))
    db.execute('insert into test (t1, i1) values (?,?)', ('four', 4))
    db.commit()
    cursor = db.execute('select i1, t1 from test order by i1')
    
    for row in cursor:
        print(row)  #data comes back in tuples
    
if __name__ == "__main__": main()

```

    (1, 'one')
    (2, 'two')
    (3, 'three')
    (4, 'four')


**row is an interable in the example below because we used row_factory to create a row object. We can convert it into a Dictionary**


```python
import sqlite3

def main():
    db = sqlite3.connect('test.db')
    db.row_factory = sqlite3.Row #created row objects
    db.execute('drop table if exists test')
    db.execute('create table test (t1 text, i1 int)')
    db.execute('insert into test (t1, i1) values (?,?)', ('one', 1))
    db.execute('insert into test (t1, i1) values (?,?)', ('two', 2))
    db.execute('insert into test (t1, i1) values (?,?)', ('three', 3))
    db.execute('insert into test (t1, i1) values (?,?)', ('four', 4))
    db.commit()
    cursor = db.execute('select i1, t1 from test order by i1')
    
    for row in cursor:
        print(dict(row))  #data comes back in tuples
    
if __name__ == "__main__": main()


```

    {'i1': 1, 't1': 'one'}
    {'i1': 2, 't1': 'two'}
    {'i1': 3, 't1': 'three'}
    {'i1': 4, 't1': 'four'}



```python
db = sqlite3.connect('test.db')
db.row_factory = sqlite3.Row
cursor = db.execute('select i1, t1 from test order by i1')
    
for row in cursor:
    print(row['t1'], row['i1'])  #data comes back in tuples
```

    one 1
    two 2
    three 3
    four 4


<a id='section16b'></a>
### Creating, retrieving, updating and deleting records (CRUD)


```python
import sqlite3

def insert(db, row):
    db.execute('insert into test (t1, i1) values (?, ?)', (row['t1'], row['i1']))
    db.commit()

def retrieve(db, t1):
    cursor = db.execute('select * from test where t1 = ?', (t1,))
    return cursor.fetchone()

def update(db, row):
    db.execute('update test set i1 = ? where t1 = ?', (row['i1'], row['t1']))
    db.commit()

def delete(db, t1):
    db.execute('delete from test where t1 = ?', (t1,))
    db.commit()

def disp_rows(db):
    cursor = db.execute('select * from test order by t1')
    for row in cursor:
        print('  {}: {}'.format(row['t1'], row['i1']))

def main():
    db = sqlite3.connect('test2.db')
    db.row_factory = sqlite3.Row
    print('Create table test')
    db.execute('drop table if exists test')
    db.execute('create table test ( t1 text, i1 int )')

    print('Create rows')
    insert(db, dict(t1 = 'one', i1 = 1))
    insert(db, dict(t1 = 'two', i1 = 2))
    insert(db, dict(t1 = 'three', i1 = 3))
    insert(db, dict(t1 = 'four', i1 = 4))
    disp_rows(db)

    print('Retrieve rows')
    print(dict(retrieve(db, 'one')), dict(retrieve(db, 'two')))

    print('Update rows')
    update(db, dict(t1 = 'one', i1 = 101))
    update(db, dict(t1 = 'three', i1 = 103))
    disp_rows(db)

    print('Delete rows')
    delete(db, 'one')
    delete(db, 'three')
    disp_rows(db)

if __name__ == "__main__": main()

```

    Create table test
    Create rows
      four: 4
      one: 1
      three: 3
      two: 2
    Retrieve rows
    {'i1': 1, 't1': 'one'} {'i1': 2, 't1': 'two'}
    Update rows
      four: 4
      one: 101
      three: 103
      two: 2
    Delete rows
      four: 4
      two: 2


<a id='section16c'></a>
### Creating a Database Object


```python
class database:
    def __init__(self, **kwargs):
        self.filename = kwargs.get('filename')
        self.table = kwargs.get('table', 'test')
    
    def sql_do(self, sql, *params):
        self._db.execute(sql, params)
        self._db.commit()
    
    def insert(self, row):
        self._db.execute('insert into {} (t1, i1) values (?, ?)'.format(self._table), (row['t1'], row['i1']))
        self._db.commit()
    
    def retrieve(self, key):
        cursor = self._db.execute('select * from {} where t1 = ?'.format(self._table), (key,))
        return dict(cursor.fetchone())
    
    def update(self, row):
        self._db.execute(
            'update {} set i1 = ? where t1 = ?'.format(self._table),
            (row['i1'], row['t1']))
        self._db.commit()
    
    def delete(self, key):
        self._db.execute('delete from {} where t1 = ?'.format(self._table), (key,))
        self._db.commit()

    def disp_rows(self):
        cursor = self._db.execute('select * from {} order by t1'.format(self._table))
        for row in cursor:
            print('  {}: {}'.format(row['t1'], row['i1']))

    def __iter__(self):
        cursor = self._db.execute('select * from {} order by t1'.format(self._table))
        for row in cursor:
            yield dict(row)

    @property
    def filename(self): return self._filename

    @filename.setter
    def filename(self, fn):
        self._filename = fn
        self._db = sqlite3.connect(fn)
        self._db.row_factory = sqlite3.Row

    @filename.deleter
    def filename(self): self.close()

    @property
    def table(self): return self._table
    @table.setter
    def table(self, t): self._table = t
    @table.deleter
    def table(self): self._table = 'test'

    def close(self):
            self._db.close()
            del self._filename

def main():
    db = database(filename = 'test.db', table = 'test')

    print('Create table test')
    db.sql_do('drop table if exists test')
    db.sql_do('create table test ( t1 text, i1 int )')

    print('Create rows')
    db.insert(dict(t1 = 'one', i1 = 1))
    db.insert(dict(t1 = 'two', i1 = 2))
    db.insert(dict(t1 = 'three', i1 = 3))
    db.insert(dict(t1 = 'four', i1 = 4))
    for row in db: print(row)

    print('Retrieve rows')
    print(db.retrieve('one'), db.retrieve('two'))

    print('Update rows')
    db.update(dict(t1 = 'one', i1 = 101))
    db.update(dict(t1 = 'three', i1 = 103))
    for row in db: print(row)

    print('Delete rows')
    db.delete('one')
    db.delete('three')
    for row in db: print(row)

if __name__ == "__main__": main()
```

    Create table test
    Create rows
    {'i1': 4, 't1': 'four'}
    {'i1': 1, 't1': 'one'}
    {'i1': 3, 't1': 'three'}
    {'i1': 2, 't1': 'two'}
    Retrieve rows
    {'i1': 1, 't1': 'one'} {'i1': 2, 't1': 'two'}
    Update rows
    {'i1': 4, 't1': 'four'}
    {'i1': 101, 't1': 'one'}
    {'i1': 103, 't1': 'three'}
    {'i1': 2, 't1': 'two'}
    Delete rows
    {'i1': 4, 't1': 'four'}
    {'i1': 2, 't1': 'two'}


<a id='section17'></a>
# 17. Modules
[Top](#top)

### Using Standard Library Modules 
### Example: `sys`, `os`, `urllib`, `random`, `datetime`


```python
import sys

def main():
    print('Python version {}.{}.{}'.format(*sys.version_info))
    print('Platform Name: ', sys.platform)
    
    import os #can import modules selectively inside a function for example
    print('OS Name: ', os.name)
    print(os.getenv('PATH'))
    print('Working Directory: ', os.getcwd())
    print('set of random bytes : ', os.urandom(25))
    


if __name__ == "__main__": main()
```

    Python version 3.5.5
    Platform Name:  darwin
    OS Name:  posix
    /anaconda3/bin:/Library/TeX/texbin:/Applications/Genymotion.app/Contents/MacOS/tools:/Users/tarekatwan/.nvm/versions/node/v9.2.0/bin:/anaconda3/bin:/Users/tarekatwan/bin:/usr/local/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/Library/TeX/texbin:/opt/X11/bin
    Working Directory:  /Users/tarekatwan/Documents/GitHubRepos/Learn-Python-3
    set of random bytes :  b'\x0e\x89m\x14sx\x84O\xf8\xb8r\x12\xc9\x05\x83\x08m\xa9`\xaf\x9e\xe6/\xe9c'



```python
import urllib.request
url = "http://bw.org/"
page = urllib.request.urlopen(url)

for line in page: print(str(line, encoding = 'utf_8'), end = '')
```

    <title> Bill Weinman </title>
    
    <link rel="SHORTCUT ICON" href="https://i.bw.org/bw/bw.ico" />
    <link rel="alternate" type="application/rss+xml" title="Bill Weinman's Technology Blog" href="http://billweinman.wordpress.com/feed/" />
    <link rel="stylesheet" type="text/css" href="https://i.bw.org/css/main.css" />
    <!--
        This is what old klugifed legacy code looks like. Horrible, ain't it? 
    -->
    </head>
    
    <body bgcolor=white background="https://i.bw.org/bw/bw-bg.png" text="#000000" link="#333333" vlink="#333333" alink="#663333"
      leftmargin=8>
    
    <a name="top"></a>
    <table cellpadding=0 cellspacing=0 border=0><tr><td height=5></td><tr></table>
    
    <table width=800 height="75%" cellspacing=0 cellpadding=0 border=0>
      <tr valign=top>
        <td width=100 valign=top align=center>
    
    <a href="https://bw.org/"><img src="https://i.bw.org/bw/bw-logo-100.gif" width=100 height=50 alt="BW" border=0></a>
    
    <table cellpadding=0 cellspacing=0 border=0><tr><td height=10></td><tr></table>
    
              <!-- menu -->
          <table cellpadding=0 cellspacing=0 border=0><tr><td bgcolor=white>
          <table cellpadding=0 cellspacing=1 border=0>
            <tr><td width=100 bgcolor=black>
            <table width="100%" cellpadding=0 cellspacing=2 border=0>
            <tr><td bgcolor=black width="100%" align=center>
              <span class="menu-title">Main Menu</span>
            </td></tr>
            <tr><td bgcolor=white width="100%" align=left class=small>
              <font face="verdana,helvetica,arial" size=1 color=black>
              <a class=menu href="http://bw.org/" title="BW Home">Home</a><br>
              <a class=menu href="http://bw.org/contact/">Contact Bill</a><br>
              <a class=menu href="http://bw.org/ldcfaq">lynda.com FAQ</a><br>
              <a class=menu href="http://bw.org/u/fb01" title="BW on Facebook">Facebook</a><br>
              <a class=menu href="http://bw.org/u/li01" title="BW on Linked In">Linked In</a><br>
              <a class=menu href="http://bw.org/u/tw01" title="BW on Twitter">Twitter</a><br>
              <a class=menu href="http://amtp.bw.org/" title="AMTP -- a replacement for SMTP">AMTP</a><br>
              <a class=menu href="http://bw.org/bio.html" title="About Bill">Bio</a><br>
              <a class=menu href="http://bw.org/available/">Hire Bill</a><br>
              <a class=menu href="http://music.bw.org/" title="Original Music by Bill Weinman">Bill&rsquo;s Music</a><br>
              <a class=menu href="http://whois.bw.org/">BW Whois</a><br>
              <a class=menu href="http://bw.org/ube/boulder.html">Boulder Pledge</a><br>
              <a class=menu href="http://bw.org/ube/" title="UBE-Related (Anti-Spam) Work">UBE-Related</a><br>
              <a class=menu href="http://blog.bw.org/" title="Bill&rsquo;s Blog">Blog</a><br>
              <a class=menu href="http://cgi.bw.org/" title="Bill&rsquo;s Simple CGI Scripts">CGI Scripts</a><br>
              <a class=menu href="http://cms.bw.org/" title="Content Management System">CMS Project</a><br>
              <a class=menu href="http://webmusicdb.com/" title="The Web Music Database (webmusicdb.com)">Music DB</a><br>
              <a class=menu href="http://htmlbook.com/" title="Creative HTML Design">Creative HTML</a><br>
              <a class=menu href="http://cgibook.com/">The CGI Book</a><br>
              <a class=menu href="http://perlbook.com/" title="Bill&rsquo;s New Perl Book (in progress)">Perl Book</a><br>
              <a class=menu href="http://www.weinman.com/wew/" title="Bill&rsquo;s original splash page">BillyDos</a><br>
              <a class=menu href="http://bw.org/privacy.html" title="Privacy Statement">Privacy</a><br>
              <a class=menu href="http://bw.org/end/" title="The end of the Internet">The End</a><br>
              <table cellpadding=0 cellspacing=0 border=0>  <!-- vertical spacer -->
                 <tr><td height=5></td></tr></table> 
            </td></tr></table></td></tr>
          </table>
          </td></tr></table>
    
    
    
    <table cellpadding=0 cellspacing=0 border=0><tr><td height=5></td><tr></table>
    
    <!-- paypal donation button -->
    <table cellpadding=0 cellspacing=0 border=0><tr><td bgcolor=black>
    <table cellpadding=2 cellspacing=2 border=0><tr><td bgcolor=white>
      <form action="https://www.paypal.com/cgi-bin/webscr" method="post">
      <input type="hidden" name="cmd" value="_xclick">
      <input type="hidden" name="business" value="opensource@bw.org">
      <input type="hidden" name="item_name" value="BW Open Source Donation">
      <input type="hidden" name="no_shipping" value="1">
      <input type="hidden" name="return" value="https://bw.org/donation-thankyou.html">
      <input type="hidden" name="cancel_return" value="https://bw.org/">
      <input type="image" vspace=2 hspace=5 align=left src="https://i.bw.org/bw/paypal-donate.gif" border="0" name="submit" 
        alt="Make payments with PayPal - it's fast, free and secure!">
      </form>
    </td></tr></table>
    </td></tr></table>
    <!-- end paypal donation button -->
    
    
    
    <table cellpadding=0 cellspacing=0 border=0><tr><td height=5></td><tr></table>
    
    <!-- Sponsored Links -->
    
      <table cellpadding=0 cellspacing=0 border=0 width=100><tr><td bgcolor=white>
      <table cellpadding=0 cellspacing=1 border=0>
        <tr><td width=100 bgcolor=black>
        <table width="100%" cellpadding=0 cellspacing=2 border=0>
        <tr><td bgcolor=black width="100%" align=center>
          <font face="tahoma,verdana,helvetica,arial" size=2 color=white>
          <b><a href="http://bw.org/donate.html" class="menu-title">&middot; Sponsors &middot; </a></b>
          </font>
        </td></tr>
        <tr><td bgcolor=white width="100%" align=center>
    
        <table cellpadding=0 cellspacing=0 border=0>
        <tr><td height=5></td></tr>
    
        <tr><td align=center class="textad"><a class="textad" target="_blank" 
          href="http://bw.org/u/ldc00">lynda.com video tutorials</a>
    
        <tr><td align=center class="textad"><a class="textad" target="_blank" 
          href="http://www.amazon.com/?_encoding=UTF8&tag=bw-org-20">amazon.com</a>
    
        <tr><td align=center class="textad"><a class="textad" target="_blank" 
          href="http://www.ConqueringArthritis.com/">Rheumatoid Arthritis</a></td></tr>
    
        <td height=5></td><tr>
        </table>
    
        </td></tr></table></td></tr>
      </table>
      </td></tr></table>
    
    <!-- end Sponsored Links -->
    
    
    
    <table cellpadding=0 cellspacing=0 border=0><tr><td height=5></td><tr></table>
    
    <table width=100 cellpadding=0 cellspacing=0 border=0><tr><td align=center>
    <table cellpadding=0 cellspacing=0 border=0><tr><td bgcolor=white>
    <table cellpadding=0 cellspacing=1 border=0>
      <tr><td bgcolor=black>
        <table cellpadding=0 cellspacing=2 border=0 width="100%">
          <tr><td bgcolor=white align=center>
            <a href="https://bw.org/"><img src="https://i.bw.org/bw/bw-designed-by.gif"
              width=100 height=26 border=0 
              alt="Site Design: Bill Weinman" Title="Site Design: Bill Weinman"></a></td></tr>
        </table>
      </td></tr>
    </table>
    </td></tr></table>
    </td></tr></table>
    
    <table cellpadding=0 cellspacing=0 border=0><tr><td height=10></td><tr></table>
    
    <div class="outer">
    <div id="copyright">
        <p>
            &copy;&nbsp;1972&ndash;2018 <a href="http://bhg.bw.org/" class="no-highlight">BHG&nbsp;LLC</a>
        </p>
    </div>
    </div>
    
    
      </td>
      <td width=20><img src="https://i.bw.org/bw/blank.gif" width=20 height=1 border=0></td> <!-- space between columns --> 
    
      <td id="mainBody" width=668 align=left valign=top>
    
    
    <p id="updated">
        updated 16 December 2014
    
    </p>
    
    <div id="socialMedia">
    <p class="small text" style="text-align: center"> Connect with Bill </p>
    <p>
    <a href="https://bw.org/u/fb01" target="_blank" title="Facebook"><img 
        src="https://bw.org/images/icons/Facebook-24x24.png" width="24" height="24" border="0" alt="Facebook"></a>
    <a href="https://bw.org/u/li01" target="_blank" title="Linked In"><img 
        src="https://bw.org/images/icons/Linked-In-24x24.png" width="24" height="24" border="0" alt="Linked In"></a>
    <a href="https://bw.org/u/tw01" target="_blank" title="Twiter Feed"><img 
        src="https://bw.org/images/icons/Twitter-24x24.png" width="24" height="24" border="0" alt="Twitter Feed"></a><br/>
    </p></div>
    
    
    <h1 id="heading"> Bill Weinman </h1>
    
    <p class="first">
    Bill Weinman is a programmer, author, musician, and technologist, in no particular order. 
    See Bill's <a href="bio.html">biography</a> and his <a href="resume/">r&eacute;sum&eacute;/<span style="font-size: 85%">CV</span></a> for more information. 
    </p>
    
    <iframe
        src="https://www.facebook.com/plugins/likebox.php?id=194622569546&amp;width=292&amp;connections=10&amp;stream=true&amp;header=false&amp;height=587"
        scrolling="no"
        frameborder="0"
        style="float: right; border:none; overflow:hidden; width:292px; height:587px; padding-left: 3px;"
        allowTransparency="true">
    </iframe>
    
    <h2>
    <a href="/u/ldc00" class="noshade" target="_blank">lynda.com</a>
    Courses
    <span class="small">[<a class="noshade" href="/ldcfaq/">FAQ</a>]</a>
    </h2>
    
    <p>
      Bill is currently writing and delivering online courses for
      <a href="/u/lynda.com">lynda.com</a>,
      the 
      <a href="/u/lynda.com">premier source for online training.</a>
      Some of his courses include:
    </p>
    
    <ul>
        <li> <a href="http://u.bw.org/ldc-cpp" target="_blank">C++ Essential Training</a> <span class="small highlight">NEW! December 2014</span> </li>
        <li> <a href="http://u.bw.org/ldc-cppcc" target="_blank">C++ Code Clinic</a> <span class="small highlight">NEW! July 2014</span> </li>
        <li> <a href="http://u.bw.org/ldc-mysql2014" target="_blank">MySQL Essential Training</a> <span class="small highlight">NEW! May 2014</span> </li>
        <li> <a href="http://u.bw.org/ldc-sql2014" target="_blank">SQL Essential Training</a> <span class="small highlight">NEW! March 2014</span> </li>
        <li> <a href="http://u.bw.org/ldc-iossys" target="_blank">iOS 6: iOS System Resources</a> <span class="small">August 2013</span> </li>
        <li> <a href="http://u.bw.org/ldc-x4esst" target="_blank">Xcode 4 Essential Training</a> <span class="small">March 2013</span> </li>
        <li> <a href="http://u.bw.org/ldc-iossql" target="_blank">iOS SDK and SQLite: Building Data-Driven Apps</a> <span class="small">January 2013</span> </li>
        <li> <a href="http://u.bw.org/ldc-h5e12" target="_blank">HTML Essential Training</a> <span class="small ">September 2012</span> </li>
        <li> <a href="http://u.bw.org/ldc-h5msg" target="_blank">HTML5: Messaging and Communications in Depth</a> <span class="small">January 2012</span> </li>
        <li> <a href="http://u.bw.org/ldc-docedit" target="_blank">HTML5: Document Editing in Depth</a> <span class="small">January 2012</span> </li>
        <li> <a href="http://u.bw.org/ldc-h5workers" target="_blank">HTML5: Background Processing with Web Workers</a> <span class="small">January 2012</span> </li>
        <li> <a href="http://u.bw.org/ldc-pgsql" target="_blank">PostgreSQL 9 with PHP Essential Training</a> <span class="small">November 2011</span> </li>
        <li> <a href="http://u.bw.org/ldc-h5dnd" target="_blank">HTML5: Drag and Drop in Depth</a> <span class="small">July 2011</span> </li>
        <li> <a href="http://u.bw.org/ldc-h5ls" target="_blank">HTML5: Local Storage and Offline Applications in Depth</a> <span class="small">June 2011</span> </li>
        <li> <a href="http://u.bw.org/ldc-iosstore" target="_blank">Distributing iOS Applications Through the App Store</a> <span class="small">Feb 2011</span> </li>
        <li> <a href="http://u.bw.org/ldc-macstore" target="_blank">Distributing Mac OSX Applications Through the App Store</a> <span class="small">Feb 2011</span> </li>
        <li> <a href="http://u.bw.org/ldc-ios4data" target="_blank">iOS SDK 4: Building Data-Driven Applications </a> <span class="small">Dec 2010</span> </li>
        <li> <a href="http://u.bw.org/ldc-sqlite3esst" target="_blank">SQLite 3 with PHP Essential Training</a> <span class="small ">Oct 2010</span> </li>
        <li> <a href="http://u.bw.org/ldc-python3esst" target="_blank">Python 3 Essential Training</a>  <span class="small "> Aug 2010 </span> </li>
        <li> <a href="http://u.bw.org/ldc-perl5esst" target="_blank">Perl 5 Essential Training</a> <span class="small"> Apr 2010 </span> </li>
        <li> <a href="http://u.bw.org/ldc-css4dev" target="_blank">CSS For Developers</a> <span class="small">Feb 2010</span> </li>
        <li> <a href="http://u.bw.org/ldc-cgiesst" target="_blank">CGI Essential Training</a> <span class="small">Jan 2010</span> </li>
        <li> <a href="http://u.bw.org/ldc-dynamenus" target="_blank">Creating Dynamic Menus</a> <span class="small">Dec 2009</span> </li>
        <li> <a href="http://u.bw.org/ldc-css" target="_blank">CSS Positioning</a> <span class="small">Aug 2009</span> </li>
        <li> <a href="http://u.bw.org/ldc-mysql" target="_blank">MySQL Essential Training</a> <span class="small">2009</span>  </li>
        <li> <a href="http://u.bw.org/ldc-xhtml" target="_blank">XHTML/HTML Essential Training</a> <span class="small">2009</span> </li>
        <li> <a href="http://u.bw.org/ldc-sql" target="_blank">SQL Essential Training</a> <span class="small">2009</span> </li>
        <li> <a href="http://u.bw.org/ldc-spam" target="_blank">Managing Spam Essential Training</a> <span class="small">2008</span> </li>
    </ul>
    
    <p>
        If you have questions or comments about any of Bill's courses on lynda.com, please read the
        <a href="/ldcfaq/">lynda.com FAQ</a>
        before
        <a href="/contact/">writing to him</a>
        about them. 
    </p>
    
    <h2>
        <a href="http://bhg.bw.org/" class="noshade" target="_blank">Contract Programming</a>
    </h2>
    
    <p>
        After more than 30 years of working on long-term projects Bill has shifted his focus to
        smaller jobs to better support his writing and open-source projects. 
    </p>
    <p>
        Please feel free to <a href="/contact/">contact Bill</a> with your small project needs. 
    </p>
    
    <h2>
        <a href="http://whois.bw.org/" class="noshade" target="_blank">BW Whois</a>
    </h2>
    
    <p>
        <a href="http://whois.bw.org/" target="_blank">BW Whois</a> is Bill's open-source 
        whois client. Originally released in December 1999, and still in active development,
        BW Whois has evolved into a full-featured
        command-line/web client with rich security features, caching and database support.
    </p>
    
    <h2>
        <a class="noshade" href="/books/" target="_blank">Books and Writings</a>
    </h2>
    
    <p> 
    Mr. Weinman has written five books, including
    <a href="http://www.cgibook.com/" target="_blank">The CGI Book</a> and,
    with his sister <a href="/u/ldc-lynda" target="_blank">Lynda</a>,
    <a href="http://www.htmlbook.com/" target=_blank>Creative HTML Design</a>.
    He has contributed to other books on programming and web design and has written articles 
    for various computer-related periodicals. Recently his writing has been focused on 
    developing courseware for <a href="/u/ldc00 " target="_blank">lynda.com</a>.
    </p>
    
    <h2>
        <a href="http://amtp.bw.org/" class="noshade" target="_blank">AMTP</a>
    </h2>
    
    <p> 
    <a href="http://amtp.bw.org/" target="_blank">AMTP</a>
    (Authenticated Mail Transfer Protocol) is Bill's solution to the SPAM problem. 
    See the 
    <a href="http://amtp.bw.org/" target="_blank">AMTP web site</a>
    for more information. 
    </p>
    
    <h2>
        <a href="http://music.bw.org/" class="noshade" target="_blank">Bill's Music</a>
    </h2>
    
    <p>
        Bill is an extremely talented guitarist and composer. While he has been focused 
        on non-music pursuits of late, you can always hear and download his music 
        <a href="http://music.bw.org/" target="_blank">here</a>. 
    </p>
    
    <h2>
        <a href="http://bearheart.wordpress.com/" class="noshade" target="_blank">BearHeart</a>
    </h2>
    
    <p>
        BearHeart is Bill's spiritual alter-ego. He is studying native american shamanic medicine 
        and has aspirations of becoming a teacher in the 
        <a href="http://www.dtmms.org/" target="_blank">Sweet Medicine Sundance</a> path. 
        BearHeart has recently begun a <a href="http://bearheart.wordpress.com/" target="_blank">blog</a>. 
    </p>
    
    <h2>
        <a href="http://blog.bw.org/" class="noshade" target="_blank">Blog</a>
    </h2>
    
    <p> Bill occasionally scribbles in his 
    <a href="http://blog.bw.org/" target="_blank">blog</a>. 
    </p>
    
    <p class=small> <u>NOTE</u>: Because of Bill's
    <a href="http://whois.bw.org/">bw-whois</a> program, some people seem 
    to think that he has some control over the registration of domains. Unless you are a 
    client or a personal friend, Bill 
    <a href="http://whois.bw.org/registration-issues.html">does not</a>
    have anything to do with your domain so please 
    do not write to him about it (and please do not call him at home about it!) 
    He cannot help you, and due to the surprisingly large volume of requests, he probably will not answer your message. 
    </small>
    
    
        </td></tr>
        <tr><td colspan=2></td><td height=40 align=center valign=middle>
          <table cellpadding=0 cellspacing=0 border=0>
            <tr><td height=25></td></tr>
            <tr><td bgcolor="#999999" height=1></td></tr>
            <tr><td align=center class="small">Eezz beeg trouble for moose and squirrel.</td></tr>
            <tr><td height=15></td></tr>
            <tr><td align=center class="small">At BHG Worldwide Headquarters it is now six till two, on Wednesday, 22 August 2018.
    </td></tr>
            <tr><td height=15></td></tr>
            <tr><td align="center"><img src="https://i.bw.org/bw/yy-31.png"
              width="31" height="31" alt="&middot;/." title="&middot;/."></td></tr>
          </table>
        </td></tr>
    </table>
    </body>
    </html>
    
    
    



```python
import random

print(random.randint(1, 1000))


```

    564
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24]



```python
x = list(range(25))
print(x)
random.shuffle(x)
print(x)
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24]
    [23, 4, 15, 8, 5, 24, 7, 9, 10, 19, 22, 21, 1, 17, 0, 6, 3, 12, 18, 11, 14, 16, 13, 2, 20]



```python
import datetime
now = datetime.datetime.now()
print(now)
```

    2017-06-07 18:25:55.802692



```python
print(now.year, now.month, now.day)
```

    2017 6 7


### conditions


```python
i = 2

if i == 2:
    print('it is number two')
elif i % 2 == 0:
    print('it is also an even number')
else:
    print('do not know')
```

    it is number two



```python
i = 2

if i == 2:
    print('it is number two')
if i % 2 == 0:
    print('it is also an even number')
if i != 2:
    print('do not know')
```

    it is number two
    it is also an even number

