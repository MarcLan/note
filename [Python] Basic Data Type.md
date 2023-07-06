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

print (list)            
print (list[0])         
print (list[1:3])       
print (list[2:])        
print (tinylist * 2)    
print (list + tinylist) 
```

Unlike Python strings, elements in lists can be changed

```PYTHON
>>> a = [1, 2, 3, 4, 5, 6]
>>> a[0] = 9
>>> a[2:5] = [13, 14, 15]
>>> a
[9, 2, 13, 14, 15, 6]
>>> a[2:5] = []   
>>> a
[9, 2, 6]
```

List has many built-in methods, such as append(), pop(), etc.

## Notice:

- List is written between square brackets, and elements are separated by commas.

- Like string, list can be indexed and sliced.
- Lists can be concatenated using the + operator.
- The elements in the List can be changed.

Python list truncation can receive the third parameter, which is the step size of the truncation. The following example is at the index 1 to index 4 and set the step size to 2 (one position apart) to truncate the string:

If the third parameter is negative, it means reverse reading, the following example is used to reverse the string:

```python
def reverseWords(input):
     
    # Separate the string delimiter by spaces to separate each word into a list
    inputWords = input.split(" ")
 
    # flip string
    # list of assumptions list = [1,2,3,4],  
    # list[0]=1, list[1]=2 ，而 -1 表示最后一个元素 list[-1]=4 ( the same as list[3]=4 )
    # inputWords[-1::-1] has three parameters
    # The first parameter -1 means the last element
    # The second parameter is empty, indicating to move to the end of the list
    # The third parameter is the step size, -1 means reverse
    inputWords=inputWords[-1::-1]
 
    # Reassemble the string
    output = ' '.join(inputWords)
     
    return output
 
if __name__ == "__main__":
    input = 'I like runoob'
    rw = reverseWords(input)
    print(rw)
```



# Tuple

A tuple is similar to a list, except that the elements of a tuple cannot be modified. Tuples are written in parentheses (), and elements are separated by commas. The element types in the tuple can also be different:

```python
#!/usr/bin/python3

tuple = ( 'abcd', 786 , 2.23, 'runoob', 70.2  )
tinytuple = (123, 'runoob')

print (tuple)             # output the full tuple
print (tuple[0])          # output the first element of the tuple
print (tuple[1:3])        # The output starts from the second element to the third element
print (tuple[2:])         # output all elements starting from the third element
print (tinytuple * 2)     # Output tuple twice
print (tuple + tinytuple) # connection tuple

('abcd', 786, 2.23, 'runoob', 70.2)
abcd
(786, 2.23)
(2.23, 'runoob', 70.2)
(123, 'runoob', 123, 'runoob')
('abcd', 786, 2.23, 'runoob', 70.2, 123, 'runoob')
```

In fact, you can think of strings as a special kind of tuple

```python
>>> tup = (1, 2, 3, 4, 5, 6)
>>> print(tup[0])
1
>>> print(tup[1:5])
(2, 3, 4, 5)
>>> tup[0] = 11  # Operations that modify tuple elements are illegal
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
>>>
```

Although the elements of a tuple are immutable, it can contain mutable objects, such as lists. Constructing tuples with 0 or 1 elements is special, so there are some additional syntax rules:

```python
tup1 = ()    # empty tuple
tup2 = (20,) # An element, you need to add a comma after the element
```

string, list and tuple all belong to sequence.

## Notice:

- Like strings, elements of tuples cannot be modified.
- Tuples can also be indexed and sliced, in the same way.

- Note the special syntax rules for constructing tuples containing 0 or 1 elements.
- Tuples can also be concatenated using the + operator.



# Set

A set is composed of one or several wholes of various shapes and sizes, and the things or objects that constitute a set are called elements or members. The basic functionality is to perform membership tests and remove duplicate elements.

To create an empty set you must use `set()` instead of `{ }`, because `{ }` is used to create an empty dictionary.

```python
sites = {'Google', 'Taobao', 'Runoob', 'Facebook', 'Zhihu', 'Baidu'}
print(sites)   # Output set, duplicate elements are automatically removed

# member test
if 'Runoob' in sites :
    print('Runoob 在集合中')
else :
    print('Runoob 不在集合中')


# set can perform set operations
a = set('abracadabra')
b = set('alacazam')

print(a)

print(a - b)     # difference of a and b

print(a | b)     # the union of a and b

print(a & b)     # the intersection of a and b

print(a ^ b)     # elements in a and b that are not present at the same time
```



# Dictionary

A dictionary is a mapping type, and a dictionary is marked with `{ }`,which is an unordered collection of key : value. Keys must use immutable types. Within the same dictionary, keys must be unique.

```python
dict = {}
dict['one'] = "1"
dict[2]     = "2"

tinydict = {'name':'runoob', 'code':1,'site':'www.runoob.com'}

print (dict['one'])       
print (dict[2])           
print (tinydict)          
print (tinydict.keys())   
print (tinydict.values()) 

1
2
{'name': 'runoob', 'code': 1, 'site': 'www.runoob.com'}
dict_keys(['name', 'code', 'site'])
dict_values(['runoob', 1, 'www.runoob.com'])
```

The dictionary type also has some built-in functions, such as clear(), keys(), values(), etc.

## Notice:

- A dictionary is a mapping type whose elements are key-value pairs.
- The keys of the dictionary must be immutable and cannot be repeated.
- To create an empty dictionary use { }.



# Bytes

In Python3, the bytes type represents an immutable binary sequence (byte sequence).

The bytes type is usually used to deal with binary data, such as image files, audio files, video files, and so on. In network programming, the bytes type is also often used to transmit binary data.

```python
x = bytes('hello', encoding = 'utf-8')
```

Similar to the string type, the bytes type also supports many operations and methods, such as slicing, concatenating, searching, replacing, and so on. At the same time, since the bytes type is immutable, a new bytes object needs to be created when performing a modification operation. For example:

```python
x = b"hello"
y = x[1:3] # slice operation, get b"el"
z = x + b"world" # Splicing operation, get b"helloworld"
```

It should be noted that the elements in the bytes type are integer values, so the corresponding integer values need to be used when performing comparison operations. For example:

```python
x = b"hello"
if x[0] == ord("h")
	print("The first element is 'h'")
```

where the `ord()` function is used to convert a character to its corresponding integer value.



# Python data type conversion

Sometimes, we need to convert the built-in data type, data type conversion, you only need to use the data type as the function name

| Function                                                     | Description                                                  |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [int(x [,base\])                                             | Convert x to an integer                                      |
| [float(x)](https://www.runoob.com/python3/python-func-float.html) | Convert x to a float                                         |
| [complex(real [,imag\])](https://www.runoob.com/python3/python-func-complex.html) | Create a plural                                              |
| [str(x)](https://www.runoob.com/python3/python-func-str.html) | Convert the object x to a string                             |
| [repr(x)](https://www.runoob.com/python3/python-func-repr.html) | Convert the object x to an expression string                 |
| [eval(str)](https://www.runoob.com/python3/python-func-eval.html) | Evaluates a valid Python expression in a string and returns an object |
| [tuple(s)](https://www.runoob.com/python3/python3-func-tuple.html) | Convert the sequence s to a tuple                            |
| [list(s)](https://www.runoob.com/python3/python3-att-list-list.html) | Convert the sequence s to a list                             |
| [set(s)](https://www.runoob.com/python3/python-func-set.html) | Convert to a mutable collection                              |
| [dict(d)](https://www.runoob.com/python3/python-func-dict.html) | Create a dictionary. d must be a sequence of (key, value) tuples. |
| [frozenset(s)](https://www.runoob.com/python3/python-func-frozenset.html) | Convert to immutable collection                              |
| [chr(x)](https://www.runoob.com/python3/python-func-chr.html) | Convert an integer to a character                            |
| [ord(x)](https://www.runoob.com/python3/python-func-ord.html) | Converts a character to its integer value                    |
| [hex(x)](https://www.runoob.com/python3/python-func-hex.html) | Convert an integer to a hexadecimal string                   |
| [oct(x)](https://www.runoob.com/python3/python-func-oct.html) | Converts an integer to an octal string                       |