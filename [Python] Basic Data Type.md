# Basic Data Type

Variables in Python do not need to be declared. Each variable must be assigned a value before use, and the variable will not be created until the variable is assigned. In Python, a variable is just a variable, it doesn't have a type, what we mean by "type" is the type of object in memory that the variable refers to.

The equal sign (=) is used to assign values to variables. The left side of the equal sign (=) operator is a variable name, and the right side of the equal sign (=) operator is the value stored in the variable. For example:

```python
#!/usr/bin/python3

counter = 100          # int
miles   = 1000.0       # float
name    = "runoob"     # string

print (counter)
print (miles)
print (name)
```

Executing the above program will output the following results:

```python
100
1000.0
runoob
```

multiple variable assignment

```python
a = b = c = 1
```

Multiple variables can be specified for multiple objects

```py
a, b, c = 1, 2, "runoob"
```

## Standard Data Type

- Number
- String
- Bool
- List
- Tuple
- Set
- Dictionary

Among the six standard data types of Python3:

- Immutable data (3): Number, String, Tuple

- Variable data (3): List, Dictionary, Set

  

# Number

Python3 supports int, float, bool, complex, the built-in type() function can be used to query what type of object a variable refers to.

```python
>>> a, b, c, d = 20, 5.5, True, 4+3j
>>> print(type(a), type(b), type(c), type(d))
<class 'int'> <class 'float'> <class 'bool'> <class 'complex'>
```

In addition, isinstance can also be used to judge:

```python
>>> a = 111
>>> isinstance(a, int)
True
>>>
```

The difference between `isinstance` and `type` is:

- `type()` will not consider the subclass to be a superclass type. 

- `isinstance()` will consider the child class to be a parent class type.

```python
>>> class A:
...     pass
... 
>>> class B(A):
...     pass
... 
>>> isinstance(A(), A)
True
>>> type(A()) == A 
True
>>> isinstance(B(), A)
True
>>> type(B()) == A
False
```

Number objects are created when you specify a value:

```python
var1 = 1
var2 = 10
```

You can also delete some object references using the `del` statement.

```python
del var1[,var2[,vvar3[...,varN]]]
```

Single or multiple objects can be deleted by using the `del` statement

```python
del var
del var_a, var_b
```

## Numerical operations

```python
>>> 5 + 4  # addition
9
>>> 4.3 - 2 # subtraction
2.3
>>> 3 * 7  # multiplication
21
>>> 2 / 4  # division, to get a floating point number
0.5
>>> 2 // 4 # division to get an integer
0
>>> 17 % 3 # Take the remainder
2
>>> 2 ** 5 # power
32
```

### Notice: 

- Python can assign values to multiple variables at the same time, such as a, b = 1, 2. 
- A variable can point to different types of objects through assignment. 
- Numerical division contains two operators: / returns a floating point number, // returns an integer. 
- During mixed calculations, Python will convert integers to floating-point numbers.

## Numeric type instance

| int    | float      | complex    |
| :----- | :--------- | :--------- |
| 10     | 0.0        | 3.14j      |
| 100    | 15.20      | 45.j       |
| -786   | -21.9      | 9.322e-36j |
| 080    | 32.3e+18   | .876j      |
| -0490  | -90.       | -.6545+0J  |
| -0x260 | -32.54e100 | 3e+26J     |
| 0x69   | 70.2E-12   | 4.53e-7j   |

Python also supports complex numbers. A complex number consists of a real part and an imaginary part. It can be represented by a + bj, or complex(a,b). The real part a and the imaginary part b of a complex number are both floating-point types.



# String

Strings in Python are enclosed in single quotes `' `or double quotes` " `while special characters are escaped with a backslash `\` .

```python
variable [head subscript: tail subscript]
```

The plus sign `+` is the connector of the string, the asterisk `*` means to copy the current string, and the number combined with it is the number of times to copy. Examples are as follows:

```python
str = 'lanyang'

print (str)          
print (str[0:-1])    
print (str[0])       
print (str[2:5])     
print (str[2:])      
print (str * 2)      
print (str + "TEST") 
```

Python uses the backslash `\` to escape special characters. If you don’t want the backslash to be escaped, you can add an `r` in front of the string to represent the original string:

```python
print('lanya\ng')
print(r'lanya\ng')
```

In addition, the backslash (\) can be used as a continuation character, indicating that the next line is a continuation of the previous line. You can also use """...""" or '''...''' to span multiple lines. Note that Python does not have a separate character type, a character is a string of length 1.

```python
>>> word = 'Python'
>>> print(word[0], word[5])
P n
>>> print(word[-1], word[-6])
n P
```

Unlike C strings, Python strings cannot be changed. Assigning a value to an index position, such as `word[0] = 'm' `will cause an error.

## Notice: 

- Backslashes can be used for escaping, and r can be used to prevent backslashes from escaping. 
- Strings can be concatenated with the + operator and repeated with the * operator. 
- Strings in Python have two indexing methods, starting with 0 from left to right, and starting with -1 from right to left. 
- Strings in Python cannot be changed.



# Bool

Boolean is True or False.

In Python, True and False are both keywords that represent Boolean values.

The Boolean type can be used to control the flow of a program, such as judging whether a certain condition is true, or executing a certain piece of code when a certain condition is met.

Boolean type features:

- The Boolean type has only two values: True and False.

- The boolean type can be compared with other data types, such as numbers, strings, etc. Python treats True as 1 and False as 0 when comparing.

- Boolean types can be used with logical operators, including and, or, and not. These operators can be used to combine multiple Boolean expressions to produce a new Boolean value.

- Boolean types can also be converted to other data types such as integers, floats, and strings. When converting, True will be converted to 1 and False will be converted to 0.

  ```py
  a = True
  b = False
  
  # Comparison operator
  print(2 < 3)   # True
  print(2 == 3)  # False
  
  # Logical operators
  print(a and b)  # False
  print(a or b)   # True
  print(not a)    # False
  
  # Type conversion
  print(int(a))   # 1
  print(float(b)) # 0.0
  print(str(a))   # "True"
  ```

## Note:

In Python, all non-zero numbers and non-empty strings, lists, tuples, and other data types are considered True, and only 0, empty strings, empty lists, empty tuples, etc. are considered False. Therefore, when performing Boolean type conversion, you need to pay attention to the authenticity of the data type.



# List

- List (list) is the most frequently used data type in Python.

- Lists can complete the data structure implementation of most collection classes. The types of elements in the list can be different, it supports numbers, strings can even contain lists (so-called nesting)
- A list is a comma-separated list of elements written between square brackets [].

- Like strings, lists can also be indexed and truncated. After the list is truncated, a new list containing the required elements is returned.

- The syntax format of list interception is as follows:

  ```python
  variable [head subscript: tail subscript]
  ```

The plus sign `+` is the list concatenation operator and the asterisk `*` is the repetition operation. Examples are as follows:

```python
list = [ 'abcd', 786 , 2.23, 'runoob', 70.2 ]
tinylist = [123, 'runoob']

print (list)            # 输出完整列表
print (list[0])         # 输出列表第一个元素
print (list[1:3])       # 从第二个开始输出到第三个元素
print (list[2:])        # 输出从第三个元素开始的所有元素
print (tinylist * 2)    # 输出两次列表
print (list + tinylist) # 连接列表
```

