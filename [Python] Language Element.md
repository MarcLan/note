# language elements

## Command and Program

The hardware system of a computer usually consists of five major components, including: arithmetic unit, controller, memory, input device and output device. Among them, the combination of the arithmetic unit and the controller is what we usually call the central processing unit, and its function is to execute various calculations and control instructions and process data in computer software. What we usually call a program is actually a collection of instructions. Our program is to organize a series of instructions together in a certain way, and then use these instructions to control the computer to do what we want it to do. The computers we use most of the time today, although their components are becoming more and more sophisticated in workmanship and their processing capabilities are becoming more and more powerful, they still belong to the "von Neumann structure" computer in essence. There are two key points in the "Von Neumann structure". One is to separate the storage device from the central processing unit, and the other is to encode data in binary. Binary is a counting method of "every two to one", which is not substantially different from the "every ten to one" counting method used by us humans. Humans use the decimal system because they have ten fingers (because when counting After the ten fingers are used up, you can only carry. Of course, there are exceptions to everything. The Mayans may have counted their toes because they were barefoot for many years, so they used the 20-digit counting method. Under the guidance of this counting method, the Mayan calendar is different from the calendar we usually use. According to the Mayan calendar, 2012 is the last year of the last so-called "solar period", while 2013 is the new year. The beginning of the "Sun Period", and later this incident was misrepresented as "2012 is the end of the world predicted by the Mayans". Today we can boldly guess that the reason for the slow development of Maya civilization is probably related to the use of decimal notation). For computers, binary is the easiest to implement on physical devices (high voltage means 1, low voltage means 0), so computers in the "von Neumann structure" use binary. Although we don't need every programmer to be able to use a binary way of thinking to work, it is still useful to understand binary and its conversion relationship with the decimal system in our lives, as well as the conversion relationship between binary and octal and hexadecimal. necessary. If you are not familiar with this point, you can use Wikipedia or Baidu Encyclopedia to popularize it yourself.

## variables and types

In programming, a variable is a carrier for storing data. The variable in the computer is the actual data or a piece of memory space for storing data in the memory. The value of the variable can be read and modified, which is the basis of all calculations and controls. There are many types of data that computers can process. In addition to numerical values, they can also process various data such as text, graphics, audio, and video. Then different data need to define different storage types.

- **Integer type**: Integers of any size can be handled in Python (there are two types of integers in Python 2.x, int and long, but this distinction is of little significance to Python, so integers in Python 3. One), and supports binary (such as 0b100, converted to decimal is 4), octal (such as 0o100, converted to decimal is 64), decimal (100) and hexadecimal (0x100, converted to decimal is 256) Notation.
- **Floating-point type**: Floating-point numbers are also decimal numbers. The reason why they are called floating-point numbers is that when expressed in scientific notation, the decimal point position of a floating-point number is variable. In addition to mathematical notation (such as 123.456), floating-point numbers also have Support scientific notation (such as 1.23456e2).
- **String type**: A string is any text enclosed in single or double quotes, such as 'hello' and "hello". There are also raw string representation, byte string representation, and Unicode string representation , and can be written as multiple lines (start with three single quotes or three double quotes, end with three single quotes or three double quotes).
- **Boolean type**: Boolean values only have two values of True and False, either True or False. In Python, you can directly use True and False to represent Boolean values (please pay attention to capitalization), or they can be calculated by Boolean operations (for example 3 < 5 yields a boolean True, and 2 == 1 yields a boolean False).

### Variable Naming

For each variable we need to give it a name, just as each of us has our own famous name. In Python, variable naming needs to follow the following non-hard rules that must be followed and strongly recommended

- #### Hard rules:
  
  - A variable name consists of letters (generalized Unicode characters, excluding special characters), numbers, and underscores, and numbers cannot start with them.
  - Case sensitive (uppercase a and lowercase A are two different variables).
  - Do not conflict with keywords.
- #### PEP 8 requirements
  
  - Spell in lowercase letters and connect multiple words with an underscore.
  - Protected instance attributes start with a single underscore.
  - Private instance attributes start with two underscores.

Of course, as a professional programmer, it is also very important to be familiar with the names when naming variables (in fact, all identifiers).

### Use of Variables

Here are a few examples to illustrate the types of variables and the use of variables.

```python
"""
Use variables to hold data and perform addition, subtraction, multiplication, and division operations

Version: 0.1
Author: lanyang
"""
a = 321
b = 12
print(a + b)    # 333
print(a - b)    # 309
print(a * b)    # 3852
print(a / b)    # 26.75
```

In Python, you can use the type function to check the type of a variable. The concept of function in programming is consistent with the concept of function in mathematics. I believe everyone is familiar with the function in mathematics. It includes function name, independent variable and dependent variable

```python
"""
Check the type of a variable using type()

Version: 0.1
"""
a = 100
b = 12.345
c = 1 + 5j
d = 'hello, world'
e = True
print(type(a))    # <class 'int'>
print(type(b))    # <class 'float'>
print(type(c))    # <class 'complex'>
print(type(d))    # <class 'str'>
print(type(e))    # <class 'bool'>
```

Variable types can be converted using built-in functions in Python.

- `int()`: Convert a value or string to an integer, and you can specify the base.
- `float()`: Convert a string to a floating point number.
- `str()`: Convert the specified object into a string form, and the encoding can be specified.
- `chr()`: Convert an integer to a string (one character) corresponding to the encoding.
- `ord()`: Convert a string (a character) to the corresponding encoding (integer).

The following code implements arithmetic operations on two integers by entering two integers through the keyboard.

```python
"""
Use the input() function to get keyboard input (string)
Use the int() function to convert the input string to an integer
Use the print() function to output a string with placeholders

Version: 0.1
"""
a = int(input('a = '))
b = int(input('b = '))
print('%d + %d = %d' % (a, b, a + b))
print('%d - %d = %d' % (a, b, a - b))
print('%d * %d = %d' % (a, b, a * b))
print('%d / %d = %f' % (a, b, a / b))
print('%d // %d = %d' % (a, b, a // b))
print('%d %% %d = %d' % (a, b, a % b))
print('%d ** %d = %d' % (a, b, a ** b))
```

> Explanation: The string output in the above print function uses the placeholder syntax, where %d is the placeholder for integers, %f is the placeholder for decimals, and %% represents the percent sign (because the percent sign represents placeholder, so the percent sign must be written as %% in a string with a placeholder), the variable value followed by % after the string will replace the placeholder and output to the terminal, run the above program , look at the program execution results to understand.

## Operator

Python supports a variety of operators. The following table roughly lists all operators in order of priority from high to low. The priority of an operator refers to what operation to do first and then to do it when multiple operators appear at the same time. what operation.

| Operator                                        | Description                                                  |
| ----------------------------------------------- | ------------------------------------------------------------ |
| `[]` `[:]`                                      | subscript, slice                                             |
| `**`                                            | index                                                        |
| `~` `+` `-`                                     | bitwise negation, sign                                       |
| `*` `/` `%` `//`                                | Multiply, Divide, Modulo, Divide                             |
| `+` `-`                                         | add, subtract                                                |
| `>>` `<<`                                       | move right, move left                                        |
| `&`                                             | bitwise AND                                                  |
| `^` `|`                                         | bitwise exclusive or, bitwise or                             |
| `<=` `<` `>` `>=`                               | less than or equal to, less than, greater than, greater than or equal to |
| `==` `!=`                                       | equal to, not equal to                                       |
| `is` `is not`                                   | identity operator                                            |
| `in` `not in`                                   | member operator                                              |
| `not` `or` `and`                                | Logical Operators                                            |
| `=` `+=` `-=` `*=` `/=` `%=` `//=` `**=` `&=` ` | =` `^=` `>>=` `<<=`                                          |

> Note: In actual development, if you do not know the precedence of operators, you can use parentheses to ensure the execution order of operation

#### Assignment Operator

The assignment operator should be the most common operator, its function is to assign the value on the right to the variable on the left

```python
"""
Assignment Operators and Compound Assignment Operators

Version: 0.1
"""
a = 10
b = 3
a += b        # equals to ：a = a + b
a *= a + 2    # equals to：a = a * (a + 2)
print(a)      # Calculate what will be output here
```

### Comparison and Logical Operators

Some comparison operators are also called relational operators, including `==`，`!=`，`<`，`>`，`<=`，`>=v`

There are three logical operators, namely  `and`，`or`，`not`

```python
"""
Use of Comparison Operators and Logical Operators

Version: 0.1
"""
flag0 = 1 == 1
flag1 = 3 > 2
flag2 = 2 < 1
flag3 = flag1 and flag2
flag4 = flag1 or flag2
flag5 = not (1 != 2)
print('flag0 =', flag0)    # flag0 = True
print('flag1 =', flag1)    # flag1 = True
print('flag2 =', flag2)    # flag2 = False
print('flag3 =', flag3)    # flag3 = False
print('flag4 =', flag4)    # flag4 = True
print('flag5 =', flag5)    # flag5 = False
```

## Practice

### Exercise 1:  Convert Fahrenheit to Celsius.

> Tip: The conversion formula from Fahrenheit to Celsius is: $C=(F - 32) \div 1.8$.

```python
"""
Convert Fahrenheit to Celsius

Version: 0.1
"""
f = float(input('Please enter temperature in Fahrenheit:'))
c = (f - 32) / 1.8
print('%.1f Fahrenheit = %.1f Celsius' % (f, c))
```

### Exercise 2: Enter the radius of a circle to calculate the circumference and area.

```python
"""
Enter the radius to calculate the circumference and area of ​​a circle
""""
radius = float(input('Please enter the radius of the circle:'))
perimeter = 2 * 3.1416 * radius
area = 3.1416 * radius * radius
print('perimeter: %.2f' % perimeter)
print('area: %.2f' % area)
```

### Exercise 3: Enter the year to judge whether it is a leap year.

```python
"""
Enter the year to judge whether it is a leap year.
"""
year = int(input('enter the year: '))

is_leap = year % 4 == 0 and year % 100 != 0 or \
          year % 400 == 0
print(is_leap)	
```



