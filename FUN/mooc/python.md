Python is an interpreted programming language, featuring structured and object-orientated programming, as well as some functional programming capabilities. 
It has the particularity to be both strongly and dynamically typed. This basically means that it has strict rules regarding memory management, but can handles 
them automatically (they are mostly transparent to the programmer).

Note that the standard extension for Python files in *.py. We provide bellow some code examples for basic structures in Python.

- OFFICIAL DOCUMENTATION
The official documentation of Python 3 is located here -> https://docs.python.org/3/reference/

- TRY IT YOURSELF!
If you properly installed the software described here (or use our virtual machine), you can use the Spyder3 IDE to test pieces of codes and sharpen your skills in Python!

- ADDING COMMENTS

```
 #Comments are preceded with a sharp.
```
   
- IMPORTING A MODULE
Modules in Python are the equivalent of libraries in most other programming language. A module stores a collection of class and/or functions, that we can conveniently 
call from our program using the keyword import.

```
import numpy
```

Sometimes, modules are grouped together in packages.

```
from os import *   #Import ever module from package os
from os import I2C #Import the module I2C of package os
```

Once a module has been imported, we can call its elements using the following syntax:
```
import numpy

numpy.zeros(2) #We call function zeros() of module numpy
```

- VARIABLE DECLARATION
Variables can store a variety of data: strings, integer, floating point values, lists, etc. A value is assigned to a variable using the keyword "=", and this this value
can be changed anytime.

A variable name can contain lower and/or upper-case letter from "A" to "Z", underscores "_" and, except for the first character, digits from "0" to "9".

```
myvar = myvalue
mystring = 'A string'
myint = 4
myfloat = 4.0
mylist = [elem1, elem2, elem3]

mylist[0] #Use this syntax to access the first element of mylist
mylist[i] #Use this syntax to access the (i+1)th element of mylist
```

- DISPLAY TEXT
Use the command "print" to display some text, or the content of a variable. Note that you can assemble (concatenate) several strings using the operator "+". Also, you may convert most variables to strings using the keywork "str".
```
print('Hello, world!')

x=21
print('This is the value of x:' + str(x) + '!')
#Use end='str' so add str to the end of the line
print('A sentence begins with a capital letter and ends with a point', end='.')

print('Hello ', end='')
print('world!')

#Use flush=True to ensure that the text is display as soon as possible
print('Hello, world faster!', flush=True)
```

IF STATEMENT
If statements are used to conditionally execute one or multiple instructions. A condition is an expression that reduces to "True" of "False".

```
if condition:
    #Executed only if condition is True
    statement_1
    statement_2
    #...
elif else_condition:
    #Executed only if condition is False and else_condition is True
    statement_3
    #...
else:
    #Executed only if all the the above conditions are False
    statement_4
    #....

```

Notes:

      You can add any number of else conditions ("elif"). Also, "elif" and "else" are optionals.
      Instructions to be executed under an "if"/"elif"/"else" are tabulated.
      Some examples of conditions:

      A = True
      B = False

      #And
      condition = A and A # = True
      condition = A and B # = False
      condition = B and B # = False

      #Or
      condition = A or A # = True
      condition = A or B # = True
      condition = B or B # = False

      #Not
      condition = not A # = False
      condition = not B # = True
      FOR LOOP
      For loops are used whenever we need to repeat statements for a defined number of times. It can also be used to iterate other the elements of a list.

#Repeat statements 10 times

```
for i in range(0,10): #i takes values from 0 up to N-1 = 9
    print(i)
```


#Iterate over a list

```
mylist = ['a', 'b', 'c']
for letter in mylist:
    print(letter)
```

Note that instructions to be repeated by the loop are tabulated.

- WHILE LOOP
While loops are used whenever we need to repeat statements for a certain number of times, that we do not know in advance.

``` 
while condition:
    statement_1
    statement_2
    #...
```

- Note that instructions to be repeated by the loop are tabulated.

Below is an example of repeating an action during 10 seconds using a while loop. This would have not be possible with a for loop, as we do not know in advance how much 
time is required to execute the instructions within the loop.

```
import time

duration = 10 #We want to wait during 10s

#time.time() gives the number of seconds elapsed since your machine's start
stop_time = time.time() + duration
while(time.time() < stop_time):
    print('.', end='', flush=True)
    time.sleep(0.1) #Do nothing during 0.1 seconds

print(str(duration) + ' seconds elapsed!')
```

- FUNCTION DECLARATION
Functions are useful when a portion of code is reused multiple times. It is also considered good practice to split big chunks of code into multiple functions, as it
improves readability and ease the debugging process.

In a python file, once a function is defined, it may be called anywhere in the rest of the file. If it its defined in an other file in the same directory, say "func.py",
you can still use the function by importing the file: "import func".

```
#Function definition
def add_and_double(arg1, arg2):
    result = (arg1 + arg2)*2
    
    return result

#Function call
val = add_and_double(2, 3) # = 10 

```

Notes :
      Use "return val" to return a value (here "val"). But in case you do not want to return anything, you can omit the "return" statement.
      The instructions belonging to the function are tabulated.


- CLASS DECLARATION AND OBJECT INSTANTIATION
An object is a structure that owns variables (in this context, they are called attributes), and has functions (in this context, they are called methods)that generally 
use and/or modify these attributes. The definition of attributes and methods of an object are given by its class (objects are also called instance of a class), but the 
values of its attributes are unique to itself.

Let us give you an insight of how objects can be useful by giving an examples. Let say that we have access to two identical temperature and humidity sensors. Without objects,
temperature measurement may be achieved in the following way:

```
def measure(sensor_id):
    #Code for measurement
    #...
    return [temperature, humidity]

#Perform measurements
[temp0, hum0] = measure(0)
[temp0, hum0] = measure(1)

#Print values
print('Temperature values: ' + str(temp0) + ', ' + str(temp1))
print('Humidity values: ' + str(hum0) + ', ' + str(hum1))
Using objects, we can achieve the same behaviour:
```


class sensor:
```
    def __init__(self, sensor_id): #Do not forget 'self' as first argument
        self.sensor_id = sensor_id
        self.temperature = None
        self.humidity = None

    def measure(self): #Do not forget 'self' as first argument
        #Code for measurement
        #No need for a sensor_id argument as it can use self.sensor_id
        #...
        self.temperature = temperature
        self.humidity = humidity
        
#Instantiate sensor objects
sensor0 = sensor(0)
sensor1 = sensor(1)

#Perform measurements
sensor0.measure()
sensor1.measure()

#Print values
print('Temperature values: ' + str(sensor0.temperature) + ', ' + str(sensor1.temperature))
print('Humidity values: ' + str(sensor0.humidity) + ', ' + str(sensor1.humidity))        

```

While this code is longer, the main advantage here is that every action (measurement or reading) performed on a particular sensor is done by invocation is associated object.
Furthermore instead of having the four variables (temp0, temp1, hum0 and hum1), we now only have two (sensor0 and sensor1), from which we can access the temperature and 
humidity values.

Let us elaborate a bit on this last piece of code:

        "self" is a Python keyword used by an object to designate itself within the class ("self" is an instance of itself, hence the name).
        "__init__(self, sensor_id)" is the constructor. It is called upon instantiation of an object ("sensor0 = sensor(0)").
        "self.sensor_id = sensor_id" takes the value of "sensor_id" passed as an argument of the constructor, and stores it as an attribute of the object. This attribute is available for every method of the object using "self.sensor_id". From outside the object, it is also possible to retrieve it in the following way "id0 = sensor0.sensor_id".
        Every method in the class takes "self" as their first argument. Apart from that, they are defined as regular functions.
        Every piece of code belonging to the class is tabulated.
