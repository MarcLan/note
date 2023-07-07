# Python Operator

The Python language supports the following types of operators:

arithmetic operator Comparison (relational) operators assignment operator Logical Operators bitwise operator member operator identity operator operator precedence

- Arithmetic operator
- Comparison (relational) operators
- Assignment operator
- Logical Operators
- Bitwise operator
- Member operator
- Identity operator
- Operator precedence



## Arithmetic Operator

The following assumes variable a=10 and variable b=21:

| Operator | Description                                                  | Instance                     |
| :------- | :----------------------------------------------------------- | :--------------------------- |
| +        | add - add two objects                                        | a + b > 31                   |
| -        | multiply - multiply two numbers or return a string repeated several times | a - b > -11                  |
| *        | multiply - multiply two numbers or return a string repeated several times | a * b > 210                  |
| /        | Divide - x divided by y                                      | b / a > 2.1                  |
| %        | modulo - Returns the remainder of the division               | b % a > 1                    |
| **       | power - returns x raised to the power of y                   | a**b is 10 to the 21st power |
| //       | Divisible - Round to the smallest                            | `>>> 9//2 4 >>> -9//2 -5`    |

```python
#!/usr/bin/python3
 
a = 21
b = 10
c = 0
 
c = a + b
print ("1 - c：", c)
 
c = a - b
print ("2 - c：", c)
 
c = a * b
print ("3 - c：", c)
 
c = a / b
print ("4 - c：", c)
 
c = a % b
print ("5 - c：", c)
 
#  a 、b 、c
a = 2
b = 3
c = a**b 
print ("6 - c：", c)
 
a = 10
b = 5
c = a//b 
print ("7 - c：", c)
```

```python
1 - c ： 31
2 - c ： 11
3 - c ： 210
4 - c ： 2.1
5 - c ： 1
6 - c ： 8
7 - c ： 2
```



## Comparison Operator

The following assumes variable a is 10 and variable b is 20:

| Operator | Description                                                  | Instance              |
| :------- | :----------------------------------------------------------- | :-------------------- |
| ==       | equals - compares objects for equality                       | (a == b) Return False |
| !=       | not equal - compares if two objects are not equal            | (a != b) Return True  |
| >        | greater than - returns whether x is greater than y           | (a > b) Return False  |
| <        | less than - Returns whether x is less than y. All comparison operators return 1 for true and 0 for false. These are equivalent to the special variables True and False, respectively. Note the capitalization of these variable names. | (a < b) Return True   |
| >=       | greater than or equal to - Returns whether x is greater than or equal to y. | (a >= b) Return False |
| <=       | less than or equal to - Returns whether x is less than or equal to y. | (a <= b) Return True  |

```python
#!/usr/bin/python3
 
a = 21
b = 10
c = 0
 
if ( a == b ):
   print ("1 - a = b")
else:
   print ("1 - a != b")
 
if ( a != b ):
   print ("2 - a != b")
else:
   print ("2 - a = b")
 
if ( a < b ):
   print ("3 - a < b")
else:
   print ("3 - a >= b")
 
if ( a > b ):
   print ("4 - a > b")
else:
   print ("4 - a <= b")
 
# 修改变量 a 和 b 的值
a = 5
b = 20
if ( a <= b ):
   print ("5 - a <= b")
else:
   print ("5 - a >  b")
 
if ( b >= a ):
   print ("6 - b >= a")
else:
   print ("6 - b < a")
```

```python
1 - a != b
2 - a != b
3 - a >= b
4 - a > b
5 - a <= b
6 - b >= a
```



## Python assignment operator

The following assumes variable a is 10 and variable b is 20:

| operator | describe                                                     | example                                                      |
| :------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| =        | simple assignment operator                                   | c = a + b assign the operation result of a + b to c          |
| +=       | Additive assignment operator                                 | c += a is equivalent to c = c + a                            |
| -=       | subtraction assignment operator                              | c -= a is equivalent to c = c - a                            |
| *=       | multiplication assignment operator                           | c *= a is equivalent to c = c * a                            |
| /=       | division assignment operator                                 | c /= a is equivalent to c = c / a                            |
| %=       | modulo assignment operator                                   | c %= a is equivalent to c = c % a                            |
| **=      | power assignment operator                                    | c **= a is equivalent to c = c ** a                          |
| //=      | integer division assignment operator                         | c //= a is equivalent to c = c // a                          |
| :=       | The walrus operator, which can be used to assign values to variables inside expressions. **Python3.8 version adds new operators** . | In this example, the assignment expression avoids calling len() twice:`if (n := len(a)) > 10:    print(f"List is too long ({n} elements, expected <= 10)")` |

```python
#!/usr/bin/python3
 
a = 21
b = 10
c = 0
 
c = a + b
print ("1 - c value：", c)
 
c += a
print ("2 - c value：", c)
 
c *= a
print ("3 - c value：", c)
 
c /= a 
print ("4 - c value：", c)
 
c = 2
c %= a
print ("5 - c value：", c)
 
c **= a
print ("6 - c value：", c)
 
c //= a
print ("7 - c value：", c)
```

The output of the above example:

```python
1 - c value： 31
2 - c value： 52
3 - c value： 1092
4 - c value： 52.0
5 - c value： 2
6 - c value： 2097152
7 - c value： 99864
```



## Python bitwise operators

Bitwise operators perform calculations on numbers as if they were binary. The bitwise operation algorithm in Python is as follows:

In the table below, variable a is 60, and b is 13. The binary format is as follows:

```python
a = 0011 1100

b = 0000 1101

-----------------

a&b = 0000 1100

a|b = 0011 1101

a^b = 0011 0001

~a  = 1100 0011

```

| operator | describe                                                     | example                                                      |
| :------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| &        | Bitwise AND operator: Two values involved in the operation, if both corresponding bits are 1, the result of the bit is 1, otherwise it is 0 | (a & b) output result 12, binary interpretation: 0000 1100   |
| \|       | Bitwise OR operator: As long as one of the corresponding two binary bits is 1, the result bit is 1. | (a \| b) output result 61, binary interpretation: 0011 1101  |
| ^        | Bitwise XOR operator: When two corresponding binary bits are different, the result is 1 | (a ^ b) output 49, binary interpretation: 0011 0001          |
| ~        | Bitwise inversion operator: Inverts each binary bit of the data, that is, turns 1 into 0 and 0 into 1. **~x** is like **-x-1** | (~a) outputs -61, binary interpretation: 1100 0011, in two's complement form of a signed binary number. |
| <<       | Left shift operator: All the binary bits of the operand are shifted to the left by several bits, and the number of shifted bits is specified by the number on the right of "<<", the high bits are discarded, and the low bits are filled with 0. | a << 2 output result 240, binary interpretation: 1111 0000   |
| >>       | Right shift operator: Shift all the binary bits of the operand on the left of ">>" to the right by a certain number of bits, and the number on the right of ">>" specifies the number of bits to move | a >> 2 output result 15, binary interpretation: 0000 1111    |

The following examples demonstrate the operation of all bitwise operators in Python:

```python
#!/usr/bin/python3
 
a = 60            # 60 = 0011 1100 
b = 13            # 13 = 0000 1101 
c = 0
 
c = a & b        # 12 = 0000 1100
print ("1 - c value is：", c)
 
c = a | b        # 61 = 0011 1101 
print ("2 - c value is：", c)
 
c = a ^ b        # 49 = 0011 0001
print ("3 - c value is：", c)
 
c = ~a           # -61 = 1100 0011
print ("4 - c value is：", c)
 
c = a << 2       # 240 = 1111 0000
print ("5 - c value is：", c)
 
c = a >> 2       # 15 = 0000 1111
print ("6 - c value is：", c)
```

The output of the above example:

```python
1 - c value is： 12
2 - c value is： 61
3 - c value is： 49
4 - c value is： -61
5 - c value is： 240
6 - c value is： 15
```



## Python logical operators

The Python language supports logical operators. The following assumes that variable a is 10 and b is 20:

| operator | logical expression | describe                                                     | example                    |
| :------- | :----------------- | :----------------------------------------------------------- | :------------------------- |
| and      | x and y            | Boolean AND - x and y returns the value of x if x is False, otherwise returns the computed value of y. | (a and b) returns 20.      |
| or       | x or y             | Boolean OR - If x is True, it returns the value of x, otherwise it returns the computed value of y. | (a or b) returns 10.       |
| not      | not x              | Boolean "not" - Returns False if x is True. It returns True if x is False. | not(a and b) returns False |

```python
#!/usr/bin/python3
 
a = 10
b = 20
 
if ( a and b ):
   print ("1 - a and b is true")
else:
   print ("1 - Either of the variables a and b is not true")
 
if ( a or b ):
   print ("2 - Both variables a and b are true, or one of the variables is true")
else:
   print ("2 - Neither variables a nor b are true")
 
# 修改变量 a 的值
a = 0
if ( a and b ):
   print ("3 - variables a and b are both true")
else:
   print ("3 - Either of the variables a and b is not true")
 
if ( a or b ):
   print ("4 - Both variables a and b are true, or one of the variables is true")
else:
   print ("4 - Neither variables a nor b are true")
 
if not( a and b ):
   print ("5 - Both variables a and b are false, or one of the variables is false")
else:
   print ("5 - variables a and b are both true")
```



## Python membership operator

In addition to some of the above operators, Python also supports member operators, and the test instance contains a series of members, including strings, lists or tuples.

| operator | describe                                                     | example                                                      |
| :------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| in       | Returns True if the value is found in the specified sequence, otherwise returns False. | x is in the y sequence, returns True if x is in the y sequence. |
| not in   | Returns True if no value is found in the specified sequence, otherwise returns False. | x is not in the y sequence, returns True if x is not in the y sequence. |



## Python identity operator

The identity operator is used to compare the memory locations of two objects

| operator | describe                                                     | example                                                      |
| :------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| is       | is is to judge whether two identifiers refer to an object    | **x is y** , like **id(x) == id(y)** , returns True if they refer to the same object, otherwise returns False |
| is not   | is not is to judge whether two identifiers refer to different objects | **x is not y** , like **id(x) != id(y)** . Returns True if the reference is not the same object, False otherwise. |

**Note:** [The id()](https://www.runoob.com/python/python-func-id.html) function is used to obtain the memory address of the object.

The following examples demonstrate the operation of all of Python's identity operators:

```python
#!/usr/bin/python3 
a = 20 b = 20 
if ( a is b ) :
    print ( " 1 - a and b have the same identity " ) 
else :
    print ( " 1 - a and b do not have the same identity " ) 
if ( id ( a ) == id ( b ) ) :
    print ( " 2 - a and b have the same id " ) 
else :
    print ( "2 - a and b do not have the same identity " ) # Modify the value of variable b b = 30 if ( a is b ) :
    print ( " 3 - a and b have the same identity " ) 
else :
    print ( " 3 - a and b does not have the same identity " ) 
if ( a is not b ) :
    print ( " 4 - a and b do not have the same identity " )
else :
    print ( " 4 - a and b have the same identity " )
 
```

The difference between is and ==:

is is used to judge whether two variable reference objects are the same, and == is used to judge whether the values of reference variables are equal.

```python
>>> a = [ 1 , 2 , 3 ] 
>>> b = a 
>>> b is a True 
>>> b == a True 
>>> b = a [ : ] 
>>> b is a False 
> >> b == a True   
```



## Python operator precedence

The following table lists all operators from highest to lowest precedence, with operators within the same cell having the same precedence. Operators refer to binary operations, unless otherwise noted. Operators within the same cell are grouped from left to right (except that exponentiation is grouped from right to left):

| operator                                                     | describe                                                     |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| `(expressions...)`,`[expressions...]`, , `{key: value...}``{expressions...}` | parenthesized expressions                                    |
| `x[index]`, `x[index:index]`, `x(arguments...)`,`x.attribute` | read, slice, call, property reference                        |
| await x                                                      | await expression                                             |
| `**`                                                         | power (exponent)                                             |
| `+x`, `-x`,`~x`                                              | Positive, Negative, Bitwise NOT                              |
| `*`, `@`, `/`, `//`,`%`                                      | multiply, matrix multiply, divide, divisible, remainder      |
| `+`,`-`                                                      | add and subtract                                             |
| `<<`,`>>`                                                    | shift                                                        |
| `&`                                                          | bitwise AND                                                  |
| `^`                                                          | bitwise XOR                                                  |
| `|`                                                          | bitwise OR                                                   |
| `in,not in, is,is not, <, <=, >, >=, !=, ==`                 | Comparison operations, including membership checks and identification number checks |
| `not x`                                                      | logical NOT                                                  |
| `and`                                                        | Logic and AND                                                |
| `or`                                                         | logical OR                                                   |
| `if -- else`                                                 | conditional expression                                       |
| `lambda`                                                     | lambda expression                                            |
| `:=`                                                         | assignment expression                                        |

The following example demonstrates the operation of all Python operator precedence:

```python
#!/usr/bin/python3
 
a = 20
b = 10
c = 15
d = 5
e = 0
 
e = (a + b) * c / d       #( 30 * 15 ) / 5
print ("(a + b) * c / d operation result：",  e)
 
e = ((a + b) * c) / d     # (30 * 15 ) / 5
print ("((a + b) * c) / d operation result：",  e)
 
e = (a + b) * (c / d)    # (30) * (15/5)
print ("(a + b) * (c / d) operation result：",  e)
 
e = a + (b * c) / d      #  20 + (150/5)
print ("a + (b * c) / d operation result：",  e)
```

The output of the above example:

```python
(a + b) * c / d operation result： 90.0
((a + b) * c) / d operation result： 90.0
(a + b) * (c / d) operation result： 90.0
a + (b * c) / d operation result： 50.0
```

and has higher precedence:

```python
x = True y = False z = False 
if x or y and z :
     print ( " yes " )
else :
     print ( " no " )
```

```python
yes
```

**Note:** Python3 no longer supports the **<>** operator, you can use **!=** instead, if you must use this comparison operator, you can use the following method:

```python
>>> from __future__ import barry_as_FLUFL
>>> 1 <> 2 True   
```

