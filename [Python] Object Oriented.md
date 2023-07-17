# Python Object Oriented

Python has been designed as an object-oriented language from the beginning, and because of this, it is very easy to create a class and object in Python. In this chapter we will introduce object-oriented programming in Python in detail. If you have not been exposed to object-oriented programming languages before, you may need to understand some basic features of object-oriented languages first, and form a basic object-oriented concept in your mind, which will help you learn Python more easily. Object-Oriented Programming. Next, let's briefly understand some basic characteristics of object-oriented.



## Introduction to Object-Oriented Technology

- **Class**: Used to describe a collection of objects with the same attributes and methods. It defines properties and methods common to every object in the collection. Objects are instances of classes.
- **Method**: A function defined in a class.
- **Class variables**: Class variables are common across instantiated objects. Class variables are defined within the class and outside the body of the function. Class variables are generally not used as instance variables.
- **Data members**: Class variables or instance variables are used to handle data related to the class and its instance objects.
- **Method rewriting**: If the method inherited from the parent class cannot meet the needs of the subclass, it can be rewritten. This process is called method override, also known as method rewriting.
- **Local variable**s: Variables defined in the method only apply to the class of the current instance.
- **Instance variable**: In the class declaration, attributes are represented by variables, which are called instance variables, and instance variables are variables modified with self.
- **Inheritance**: That is, a derived class (derived class) inherits the fields and methods of the base class (base class). Inheritance also allows an object of a derived class to be treated as an object of a base class. For example, there is such a design: an object of type Dog is derived from the Animal class, which simulates the "is-a" relationship (for example, Dog is an Animal).
- **Instantiation**: Create an instance of a class, a concrete object of the class.
- **Object**: An instance of a data structure defined by a class. Objects consist of two data members (class variables and instance variables) and methods.



## Class Definition

```python
class ClassName:
    <statement-1>
    .
    .
    .
    <statement-N>
```



## Class Object

Class objects support two operations: property reference and instantiation. Attribute references use the same standard syntax as all attribute references in Python: obj.name. After the class object is created, all names in the class namespace are valid attribute names. So if the class definition is like this:

```python
#!/usr/bin/python3
 
class MyClass:
    """simple class instance"""
    i = 12345
    def f(self):
        return 'hello world'
    
# Instantiate the class
x = MyClass()
 
# Access to class properties and methods
print("MyClass attributes  i is：", x.i)
print("MyClass method f output is：", x.f())
```

The above creates a new class instance and assigns the object to the local variable x, where x is an empty object. The output of executing the above program is:

```python
MyClass attributes  i is： 12345
MyClass method f output is： hello world
```

Classes have a special method (constructor) called __init__() that is called automatically when the class is instantiated, like so:

```python
def __init__(self):
    self.data = []
```

The class defines the __init__() method, and the instantiation of the class will automatically call the __init__() method. The class MyClass is instantiated as follows, and the corresponding __init__() method is called:

```python
x = MyClass()
```

Of course, the __init__() method can have parameters, and the parameters are passed to the instantiation operation of the class through __init__(). For example:

```python
#!/usr/bin/python3
 
class Complex:
    def __init__(self, realpart, imagpart):
        self.r = realpart
        self.i = imagpart
x = Complex(3.0, -4.5)
print(x.r, x.i)   # output：3.0 -4.5
```



### Self represents the instance of the class, not the class

Class methods have only one special difference from ordinary functions - they must have an additional first parameter name, which by convention is called self.

```py
class Test:
    def prt(self):
        print(self)
        print(self.__class__)
 
t = Test()
t.prt()
```



## Class Method

Inside the class, use the def keyword to define a method. Unlike general function definitions, a class method must contain a parameter self, which is the first parameter, and self represents an instance of the class.

```python
#!/usr/bin/python3
 
#Class definition
class people:
    #Define basic attributes
    name = ''
    age = 0
    #Define private attributes, private attributes cannot be directly accessed outside the class
    __weight = 0
    #Define the construction method
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s say: I am %d years old." %(self.name,self.age))
 
# instantiate class
p = people('lanyang',10,30)
p.speak()
```

```python
lanyang say: I am 10 years old.
```



## Inheritance

Python also supports inheritance of classes. If a language does not support inheritance, classes are meaningless. The derived class definition looks like this:

```python
class DerivedClassName(BaseClassName):
    <statement-1>
    .
    .
    .
    <statement-N>
```

The subclass (derived class DerivedClassName) inherits the properties and methods of the parent class (base class BaseClassName). BaseClassName (the base class name in the instance) must be defined in the same scope as the derived class. Instead of classes, expressions can also be used, which is useful when the base class is defined in another module:

```python
class people:
    name = ''
    age = 0
    __weight = 0

    def __init__(self, n, a, w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s say: I am %d years old." %(self.name,self.age))

class student(people):
    grade = ''
    def __init__(self, n, a, w, g):
        people.__init__(self,n,a,w)
        self.grade = g
    
    def speak(self):
        print("%s says: I am %d years old, I am in %d grade"
              %(self.name,self.age,self.grade))
              
s = student('ken',10,60,3)
s.speak()
```

```python
ken says: I am 10 years old, I am in 3 grade
```



## Multiple 

Python also has limited support for multiple inheritance forms. The class definition of multiple inheritance is as follows:

```python
class DerivedClassName(Base1, Base2, Base3):
    <statement-1>
    .
    .
    .
    <statement-N>
```

Pay attention to the order of the parent class in the parentheses. If the parent classes has the same method name, but it is not specified when the subclass is used, python searches from left to right, that is, when the method is not found in the subclass, it searches from left to right Whether the method is contained in the parent classes.

```python
class people:
    name = ''
    age = 0
    __weight = 0

    def __init__(self, n, a, w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s say: I am %d years old." %(self.name,self.age))

class student(people):
    grade = ''
    def __init__(self, n, a, w, g):
        people.__init__(self,n,a,w,)
        self.grade = g
    
    def speak(self):
        print("%s says: I am %d years old, I am in %d grade"
              %(self.name,self.age,self.grade))

class speaker():
    topic = ''
    name = ''
    def __init__(self,n,t):
        self.name = n
        self.topic = t
    def speak(self):
        print("My name is %s, I do speech, the topic is %s"
              %(self.name,self.topic))

class sample(speaker,student):
    a = ''
    def __init__(self,n,a,w,g,t):
        student.__init__(self,n,a,w,g)
        speaker.__init__(self,n,t)

test = sample("Tim",25,80,4,'python')
test.speak() 
```

```python
My name is Tim, I do speech, the topic is python
```



## Method Override

If the function of your parent class method cannot meet your needs, you can override the method of your parent class in the subclass, example is as follow:

```py
print('-------override------')
# Define parent class
class Parent:
    def myMethod(self):
        print('call parent class')

# Define subclass
class Child(Parent):
    def myMethod(self):
        print('Call subclass')

c = Child() # subclass instance
c.myMethod() # subclass override
super(Child,c).myMethod()
```

```python
-------override------
Call subclass
call parent class
```

[More documentation: Description of Python subclass inheriting parent class constructor]: https://www.runoob.com/w3cnote/python-extends-init.html



## Class Properties and Methods

- ### Class private properties

  `__private_attrs`: At the beginning of two underscores, the attribute is declared private and cannot be used or directly accessed outside the class. `self.__private_attrs` when used in a method inside a class.

  

- ### Class method

  Inside the class, use the def keyword to define a method. Different from the general function definition, the class method must contain the parameter self, which is the first parameter, and self represents the instance of the class. The name of self is not mandatory, you can also use this, but it is better to use self by convention.

  

- ### Class private method

  `__private_method`: Start with two underscores, declare the method as a private method, which can only be called inside the class, not outside the class. `self.__private_methods`.



### Example

**Examples of private properties of the class are as follows:**

```python
print('-----class properties-----')
class JustCounter:
    __secretCount = 0 # private variable
    publicCount = 0 # public variable

    def count(self):
        self.__secretCount += 1
        self.publicCount += 1
        print(self.__secretCount)

counter = JustCounter()
counter.count()
counter.count()
print(counter.publicCount)
print(counter.__secretCount) # Error no attribute '__secretCount'
```

```python
1
2
2
Traceback (most recent call last):
  File "test.py", line 16, in <module>
    print (counter.__secretCount)  
AttributeError: 'JustCounter' object has no attribute '__secretCount'
```



**The private method instance of the class is as follows:**

```python
print('-----The private method instance-----')
class Site:
    def __init__(self,name,url):
        self.name = name # public
        self.__url = url #private
    
    def who(self):
        print('name: ', self.name)
        print('Url: ', self.__url)

    def __foo(self):
        print('This is private method')

    def foo(self):
        print('This is public method')
        self.__foo()

x = Site('Lanyang', 'Python')
x.who() # output normally
x.foo() # output normally
x.__foo() # Error
```

```python
name:  Lanyang
Url:  Python
This is public method
This is private method
Traceback (most recent call last):       
  File "d:\10 Tech skill\Python\03 Branch structure\class.py", line 128, in <module>
    x.__foo() # error
AttributeError: 'Site' object has no attribute '__foo'
```



## The proprietary method of the class

- **`__init__ `:** Constructor, called when an object is generated
- **`__del__` :** Destructor, used when releasing an object
- **`__repr__` :** print, convert
- **`__setitem__` :** assign according to the index
- **`__getitem__`:** get the value by index
- **`__len__`:** Get the length
- **`__cmp__`:** comparison operation
- **`__call__`:** function call
- **`__add__`:** addition operation
- **`__sub__`:** Subtraction operation
- **`__mul__`:** multiplication operation
- **`__truediv__`:** division operation
- **`__mod__`:** remainder operation
- **`__pow__`:** power



## Operator Overloading

Python also supports operator overloading. We can overload the proprietary methods of a class.

```python
print('-----Operator Overloading-----')
class Vector:
    def __init__(self,a,b):
        self.a = a
        self.b = b

    def __str__(self) -> str:
        return 'Vector (%d, %d)' % (self.a, self.b)
    
    def __add__(self,other):
        return Vector(self.a + other.a, self.b +other.b)
    
v1 = Vector(2,10)
v2 = Vector(5,-2)
print(v1 + v2)
```

```python
Vector(7,8)
```



