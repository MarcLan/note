# Python Basic Data Type

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



Math Function

| function                                                     | return value (description)                                   |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [abs(x)](https://www.runoob.com/python3/python3-func-number-abs.html) | Returns the absolute value of a number, such as abs(-10) returns 10 |
| [ceil(x)](https://www.runoob.com/python3/python3-func-number-ceil.html) | Returns the upper integer of the number, such as math.ceil(4.1) returns 5 |
| cmp(x, y)                                                    | Returns -1 if x < y, 0 if x == y, and 1 if x > y. **Deprecated in Python 3, use (x>y)-(x<y) instead** . |
| [exp(x)](https://www.runoob.com/python3/python3-func-number-exp.html) | Return e to the power of x (e x ), such as math.exp(1) returns 2.718281828459045 |
| [fabs(x)](https://www.runoob.com/python3/python3-func-number-fabs.html) | Returns the absolute value of a number as a floating point number, such as math.fabs(-10) returns 10.0 |
| [floor(x)](https://www.runoob.com/python3/python3-func-number-floor.html) | Returns the rounded integer of a number, such as math.floor(4.9) returns 4 |
| [log(x)](https://www.runoob.com/python3/python3-func-number-log.html) | Such as math.log(math.e) returns 1.0, math.log(100,10) returns 2.0 |
| [log10(x)](https://www.runoob.com/python3/python3-func-number-log10.html) | Returns the logarithm of x in base 10, such as math.log10(100) returns 2.0 |
| [max(x1, x2,...)](https://www.runoob.com/python3/python3-func-number-max.html) | Returns the maximum value of the given argument, which can be a sequence. |
| [min(x1, x2,...)](https://www.runoob.com/python3/python3-func-number-min.html) | Returns the minimum value of the given argument, which can be a sequence. |
| [modf(x)](https://www.runoob.com/python3/python3-func-number-modf.html) | Returns the integer part and fractional part of x. The numerical signs of the two parts are the same as x, and the integer part is represented by floating point. |
| [pow(x, y)](https://www.runoob.com/python3/python3-func-number-pow.html) | The value after x**y operation.                              |
| [round(x[,n\])](https://www.runoob.com/python3/python3-func-number-round.html) | Returns the rounded value of the floating-point number x, or, if n is given, the number of digits rounded to the decimal point.**In fact, it is accurate to say that the reserved value will be reserved to the end closer to the previous one.** |
| [sqrt(x)](https://www.runoob.com/python3/python3-func-number-sqrt.html) | Returns the square root of the number x.                     |

## random number function

Random numbers can be used in mathematics, games, security and other fields, and are often embedded in algorithms to improve algorithm efficiency and program security.

Python includes the following commonly used random number functions:

| function                                                     | describe                                                     |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [choice(seq)](https://www.runoob.com/python3/python3-func-number-choice.html) | Randomly pick an element from the elements of the sequence, such as random.choice(range(10)), randomly pick an integer from 0 to 9. |
| [randrange ([start,\] stop [, step])](https://www.runoob.com/python3/python3-func-number-randrange.html) | Obtain a random number from the set within the specified range and incremented by the specified radix, the default value of the radix is 1 |
| [random()](https://www.runoob.com/python3/python3-func-number-random.html) | Randomly generate the next real number, which is in the range [0,1). |
| [seed([x\])](https://www.runoob.com/python3/python3-func-number-seed.html) | Change the seed of the random number generator. If you don't understand its principle, you don't have to set the seed specifically, Python will help you choose the seed. |
| [shuffle(lst)](https://www.runoob.com/python3/python3-func-number-shuffle.html) | randomize all elements of a sequence                         |
| [uniform(x, y)](https://www.runoob.com/python3/python3-func-number-uniform.html) | Randomly generate the next real number in the range [x,y].   |



## Trigonometric functions

Python includes the following trigonometric functions:

| function                                                     | describe                                                     |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [acos(x)](https://www.runoob.com/python3/python3-func-number-acos.html) | Returns the arccosine radian value of x.                     |
| [asin(x)](https://www.runoob.com/python3/python3-func-number-asin.html) | Returns the arcsine of x in radians.                         |
| [atan(x)](https://www.runoob.com/python3/python3-func-number-atan.html) | Returns the arctangent of x in radians.                      |
| [atan2(y, x)](https://www.runoob.com/python3/python3-func-number-atan2.html) | Returns the arctangent of the given X and Y coordinates.     |
| [cos(x)](https://www.runoob.com/python3/python3-func-number-cos.html) | Returns the cosine of x in radians.                          |
| [hypot(x, y)](https://www.runoob.com/python3/python3-func-number-hypot.html) | Returns the Euclidean norm sqrt(x*x + y*y).                  |
| [sin(x)](https://www.runoob.com/python3/python3-func-number-sin.html) | Returns the sine of x in radians.                            |
| [tan(x)](https://www.runoob.com/python3/python3-func-number-tan.html) | Returns the tangent of x in radians.                         |
| [degrees(x)](https://www.runoob.com/python3/python3-func-number-degrees.html) | Convert radians to angles, such as degrees(math.pi/2), return 90.0 |
| [radians(x)](https://www.runoob.com/python3/python3-func-number-radians.html) | Convert angles to radians                                    |

------



## mathematical constant

| constant | describe                                                     |
| :------- | :----------------------------------------------------------- |
| p        | The mathematical constant pi (pi, generally expressed in π)  |
| e        | The mathematical constant e, e is the natural constant (natural constant). |



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



## Python escape characters

**Python escapes characters with backslash \** when special characters need to be used within characters . As shown in the following table:

| escape character           | describe                                                     | example                                                      |
| :------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| \ (at the end of the line) | continuation character                                       | `>>> print("line1 \ print ( "line1\ ...line2\ ...line3")) line1 line2 line3 >>>>>>  ` |
| \\                         | backslash symbol                                             | `>>> print("\\") print ( "\\" ) \`                           |
| \'                         | apostrophe                                                   | `>>> print('\'') print ( '\'' ) '' `                         |
| \"                         | Double quotes                                                | `>>> print("\"") print ( "\"" ) ""`                          |
| \a                         | ring the bell                                                | `>>> print("\a") print ( "\a" )`The computer beeps after execution. |
| \b                         | Backspace                                                    | `>>> print("Hello \b World!") print ( "Hello \b World!" ) Hello World!Hello World ! ` |
| \000                       | null                                                         | `>>> print("\000") print ( "\000" ) >>>>>>  `                |
| \n                         | new line                                                     | `>>> print("\n") print ( "\n" )  >>>>>>`                     |
| \v                         | vertical tab                                                 | `>>> print("Hello \v World!") print ( "Hello \v World!" ) hellohello        World!World ! >>>>>>` |
| \t                         | horizontal tab                                               | `>>> print("Hello \t World!") print ( "Hello \t World!" ) Hello World!Hello World !     >>>>>>` |
| \r                         | Press Enter to move the content behind **\r** to the beginning of the string, and replace the characters at the beginning one by one until the content behind **\r is completely replaced.** | `>>> print("Hello\rWorld!") print ( "Hello\rWorld!" ) World!World ! >>> print('google runoob taobao\r123456')>>> print ( 'google runoob taobao\r123456' )  123456 runoob taobao123456 runoob taobao ` |
| \f                         | change page                                                  | `>>> print("Hello \f World!") print ( "Hello \f World!" ) hellohello        World!World ! >>>>>>  ` |
| \yyy                       | Octal number, y stands for characters from 0 to 7, for example: \012 stands for newline. | `>>> print("\110\145\154\154\157\40\127\157\162\154\144\41") print ( "\110\145\154\154\157\40\127\157\162\154\144\41" ) Hello World!Hello World ! ` |
| \xyy                       | Hexadecimal number, starting with \x, the character represented by y, for example: \x0a represents newline | `>>> print("\x48\x65\x6c\x6c\x6f\x20\x57\x6f\x72\x6c\x64\x21") print ( "\x48\x65\x6c\x6c\x6f\x20\x57\x6f\x72\x6c\x64\x21" ) Hello World!Hello World ! ` |
| \other                     | Other characters are output in normal format                 |                                                              |

## string operators

The value of instance variable a in the following table is the string "Hello", and the value of variable b is "Python":

| operator | describe                                                     | example                                                      |
| :------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| +        | string concatenation                                         | a + b output: HelloPython                                    |
| *        | Repeat output string                                         | a*2 output result: HelloHello                                |
| []       | Get characters in a string by index                          | a[1] output result **e**                                     |
| [ : ]    | Intercept a part of the string, follow the principle of **left-closed-right-open** , str[0:2] does not contain the third character. | a[1:4] output result **ell**                                 |
| in       | Membership operator - returns True if the given character is contained in the string | **'H' in a** outputs True                                    |
| not in   | Membership operator - returns True if the given character is not contained in the string | **'M' not in a** output True                                 |
| r/R      | Raw Strings - Raw Strings: All strings are used literally, without escaping special or unprintable characters. **Raw strings have almost the same syntax as normal strings, except that the letter r** (upper and lower case) is added before the first quotation mark in the string . | `print( r'\n' )( r '\n' )  print( R'\n' )print ( R '\n' )  ` |
| %        | format string                                                | Please see the next section.                                 |

## string formatting

Python supports the output of formatted strings. Although this allows for very complex expressions, the most basic use is to insert a value into a string with the string format character %s.

In Python, string formatting uses the same syntax as the sprintf function in C.

## Example (Python 3.0+)

```python
\#!/usr/bin/python3 print ( " My name is %s and I am %d years old this year! " % ( ' Xiao Ming ' , 10 ) )
```

string formatting symbols:



| symbol | describe                                                     |
| :----- | :----------------------------------------------------------- |
| %c     | Formatting characters and their ASCII codes                  |
| %s     | format string                                                |
| %d     | format integer                                               |
| %u     | format unsigned integer                                      |
| %o     | Format an unsigned octal number                              |
| %x     | Format an unsigned hexadecimal number                        |
| %X     | format unsigned hexadecimal number (uppercase)               |
| %f     | Format floating point numbers, you can specify the precision after the decimal point |
| %e     | Format floating point numbers in scientific notation         |
| %E     | Same as %e, format floating point numbers in scientific notation |
| %g     | Shorthand for %f and %e                                      |
| %G     | Shorthand for %f and %E                                      |
| %p     | format the address of a variable with a hexadecimal number   |

Formatting operator auxiliary instructions:

| symbol | Function                                                     |
| :----- | :----------------------------------------------------------- |
| *      | Define width or decimal point precision                      |
| -      | for left alignment                                           |
| +      | Display a plus sign ( + ) in front of positive numbers       |
| <sp>   | display spaces before positive numbers                       |
| #      | Display zero ('0') in front of octal numbers, '0x' or '0X' in front of hexadecimal numbers (depending on whether 'x' or 'X' is used) |
| 0      | Displayed numbers are preceded by '0' instead of the default space |
| %      | '%%' outputs a single '%'                                    |
| (var)  | map variable (dictionary parameter)                          |
| mn     | m is the minimum total width of the display, n is the number of digits after the decimal point (if available) |

[Starting from Python2.6, a new format string function str.format()](https://www.runoob.com/python/att-string-format.html) has been added , which enhances the string formatting function.

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

## f-string

f-string is added after python3.6, it is called literal format string, and it is a new format string syntax.

We used to use the percent sign (%) before:

```python
>>> name = 'Runoob'
>>> 'Hello %s' % name
'Hello Runoob'
```

**The f-string** format string starts with **f** , followed by a string. The expression in the string is wrapped in curly braces {}, which will replace the calculated value of the variable or expression. Examples are as follows:

```python
>>> name = 'Runoob'
>>> f 'Hello {name}'  # substitute variable
'Hello Runoob'
>>> f '{1+2}'         # use expression
'3'

>>> w = { ' name' : 'Runoob' , 'url' : 'www.runoob.com' }
>>> f '{w["name"]}: {w["url"]}'
'Runoob: www.runoob.com '
```



## string built-in functions

Python's commonly used built-in functions for strings are as follows:



| serial number | Method and description                                       |
| :------------ | :----------------------------------------------------------- |
| 1             | [capitalize()](https://www.runoob.com/python3/python3-string-capitalize.html) converts the first character of a string to uppercase |
| 2             | [center(width, fillchar)](https://www.runoob.com/python3/python3-string-center.html)Returns a string with the specified width width centered, fillchar is the filled character, and the default is a space. |
| 3             | [count(str, beg=0, end=len(string))](https://www.runoob.com/python3/python3-string-count.html) Returns the number of occurrences of str in the string, if beg or end is specified, returns the number of occurrences of str within the specified range |
| 4             | [bytes.decode(encoding="utf-8", errors="strict")](https://www.runoob.com/python3/python3-string-decode.html) There is no decode method in Python3, but we can use the decode() method of the bytes object to decode the given bytes object, which can be encoded and returned by str.encode(). |
| 5             | [encode(encoding='UTF-8', errors='strict')](https://www.runoob.com/python3/python3-string-encode.html) Encode the string in the encoding format specified by encoding. If an error occurs, a ValueError exception will be reported by default, unless errors specify 'ignore' or 'replace' |
| 6             | [endswith(suffix, beg=0, end=len(string))](https://www.runoob.com/python3/python3-string-endswith.html) checks whether the string ends with suffix, if beg or end is specified, checks whether the specified range ends with suffix, if yes, returns True, otherwise returns False. |
| 7             | [expandtabs(tabsize=8)](https://www.runoob.com/python3/python3-string-expandtabs.html) Convert the tab symbols in the string string into spaces, and the default number of spaces for tab symbols is 8. |
| 8             | [find(str, beg=0, end=len(string))](https://www.runoob.com/python3/python3-string-find.html) Check whether str is included in the string, if the specified range beg and end, check whether it is included in the specified range, if it is included, return the index value of the beginning, otherwise return -1 |
| 9             | [index(str, beg=0, end=len(string))](https://www.runoob.com/python3/python3-string-index.html) Same as the find() method, except that an exception will be reported if str is not in the string. |
| 10            | [isalnum()](https://www.runoob.com/python3/python3-string-isalnum.html) Returns True if the string has at least one character and all characters are letters or numbers, otherwise returns False |
| 11            | [isalpha()](https://www.runoob.com/python3/python3-string-isalpha.html) Return True if the string has at least one character and all characters are letters or Chinese characters, otherwise return False |
| 12            | [isdigit()](https://www.runoob.com/python3/python3-string-isdigit.html) Returns True if the string contains only numbers, otherwise returns False.. |
| 13            | [islower()](https://www.runoob.com/python3/python3-string-islower.html) Returns True if the string contains at least one case-sensitive character and all of those (case-sensitive) characters are lowercase, otherwise returns False |
| 14            | [isnumeric()](https://www.runoob.com/python3/python3-string-isnumeric.html) Returns True if the string contains only numeric characters, otherwise returns False |
| 15            | [isspace()](https://www.runoob.com/python3/python3-string-isspace.html) Returns True if the string contains only whitespace, otherwise returns False. |
| 16            | [istitle()](https://www.runoob.com/python3/python3-string-istitle.html) Returns True if the string is titled (see title()), otherwise returns False |
| 17            | [isupper()](https://www.runoob.com/python3/python3-string-isupper.html) Returns True if the string contains at least one case-sensitive character and all of those (case-sensitive) characters are uppercase, otherwise returns False |
| 18            | [join(seq)](https://www.runoob.com/python3/python3-string-join.html) Merge all elements (string representations) in seq into a new string with the specified string as the delimiter |
| 19            | [len(string)](https://www.runoob.com/python3/python3-string-len.html) Returns the length of the string |
| 20            | [ljust(width[, fillchar\])](https://www.runoob.com/python3/python3-string-ljust.html) Return a new string with the original string left-aligned and padded to length width with fillchar. fillchar is a space by default. |
| twenty one    | [lower()](https://www.runoob.com/python3/python3-string-lower.html) Converts all uppercase characters in a string to lowercase. |
| twenty two    | [lstrip()](https://www.runoob.com/python3/python3-string-lstrip.html) Truncates spaces or specified characters from the left of a string. |
| twenty three  | [maketrans()](https://www.runoob.com/python3/python3-string-maketrans.html) Create a character mapping conversion table. For the simplest calling method that accepts two parameters, the first parameter is a string representing the character to be converted, and the second parameter is also a string representing the conversion target. |
| twenty four   | [max(str)](https://www.runoob.com/python3/python3-string-max.html) Returns the largest letter in the string str. |
| 25            | [min(str)](https://www.runoob.com/python3/python3-string-min.html) Returns the smallest letter in the string str. |
| 26            | [replace(old, new [, max\])](https://www.runoob.com/python3/python3-string-replace.html) Replace old in the string with new. If max is specified, the replacement will not exceed max times. |
| 27            | [rfind(str, beg=0, end=len(string))](https://www.runoob.com/python3/python3-string-rfind.html) Similar to the find() function, but searches from the right. |
| 28            | [rindex(str, beg=0, end=len(string))](https://www.runoob.com/python3/python3-string-rindex.html) Similar to index(), but starts from the right. |
| 29            | [rjust(width,[, fillchar\])](https://www.runoob.com/python3/python3-string-rjust.html) Returns a new string with the original string right-aligned and filled to length width using fillchar (default space) |
| 30            | [rstrip()](https://www.runoob.com/python3/python3-string-rstrip.html) Removes spaces or specified characters from the end of a string. |
| 31            | [split(str="", num=string.count(str))](https://www.runoob.com/python3/python3-string-split.html) Use str as the delimiter to intercept the string, if num has a specified value, only num+1 substrings will be intercepted |
| 32            | [splitlines ([keepends\])](https://www.runoob.com/python3/python3-string-splitlines.html) Separated by line ('\r', '\r\n', \n'), return a list containing each line as an element, if the parameter keepends is False, do not include newline characters, if True, keep newline characters. |
| 33            | [startswith(substr, beg=0, end=len(string))](https://www.runoob.com/python3/python3-string-startswith.html) Checks if the string starts with the specified substring substr, returns True if yes, otherwise returns False. If beg and end specify values, check within the specified range. |
| 34            | [strip([chars\])](https://www.runoob.com/python3/python3-string-strip.html) Perform lstrip() and rstrip() on strings |
| 35            | [swapcase()](https://www.runoob.com/python3/python3-string-swapcase.html) Convert uppercase to lowercase in a string, and convert lowercase to uppercase |
| 36            | [title()](https://www.runoob.com/python3/python3-string-title.html) Returns a "titled" string, that is, all words start with uppercase and the rest are lowercase (see istitle()) |
| 37            | [translate(table, deletechars="")](https://www.runoob.com/python3/python3-string-translate.html) Convert the characters of string according to the table given by table (contains 256 characters), and put the characters to be filtered out into the deletechars parameter |
| 38            | [upper()](https://www.runoob.com/python3/python3-string-upper.html) Convert lowercase letters in a string to uppercase |
| 39            | [zfill (width)](https://www.runoob.com/python3/python3-string-zfill.html) Returns a string of length width, the original string is right-aligned, and the front is filled with 0 |
| 40            | [isdecimal()](https://www.runoob.com/python3/python3-string-isdecimal.html) Checks if the string contains only decimal characters, returns true if yes, false otherwise. |



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