# Branch Structure

## Application Scenario

So far, the Python code we have written is executed sequentially one by one. This code structure is usually called a sequential structure. However, the sequence structure alone cannot solve all problems. For example, if we design a game, the condition for clearing the first level of the game is that the player obtains 1000 points. In the second level, tell the player "Game Over", two branches will be generated here, and only one of these two branches will be executed. There are many similar scenarios, and we call this structure "branch structure" or "selection structure".

## Use of if statement

In Python, to construct a branch structure you can use`if`、`elif` and `else`keywords.The so-called **keywords** are words with special meanings, such as if and else are keywords specially used to construct branch structures, obviously you cannot use it as a variable name (in fact, it is not allowed to be used as other identifiers)

```python
username = input('Input username: ')
password = input('Input password: ')
# If the user name is admin and the password is 123456, the authentication is successful; otherwise, the authentication fails
if username == 'admin' and password == '123456':
    print('Authentication successful!')
else:
    print('Authentication failed!')
```

It should be noted that unlike C/C++, Java and other languages, Python does not use curly braces to construct code blocks but uses indentation to represent the hierarchical structure of code, If ifyou need to execute multiple statements when the if condition is true, just keep the multiple statements with the same indentation. In other words, if consecutive codes maintain the same indentation, they belong to the same code block, which is equivalent to a whole of execution. Any number of spaces can be used for indentation, but 4 spaces are usually used. It is recommended that you do not use the tab key or set your code editing tool to automatically change the tab key to 4 spaces.

```python
		3x - 5 ( x > 1)
f(x) =  x + 2   (-1 <= x <= 1)
		5x + 3  (x < -1)
    
x = float(input('x = '))
if x > 11:
    y = 3 * x - 5
elif x >= -1:
    y = x + 2
else:
    y = 5 * x + 3
print('f(%.2f) = %.2f' % (x, y))
```

Of course, according to the needs of actual development, the branch structure can be nested. For example, after judging whether to pass the level, you will be given a level according to the number of treasures or props you have obtained (such as lighting up two or three stars). Then we need to construct a new branch structure inside `if.` Similarly, new branches can also be constructed in `elif` and `else`. We call it a nested branch structure, which means that the above code can also be written as follows look.

```Python
				3X - 5 (x > 1)
f(x) = x + 2	(-1 <= x <= 1)
				5x + 3 (x < -1)
    
x = float(input('x = '))
if x > 1:
    y = 3 * x -5
else:
    if x >= -1:
        y = x + 2
    else:
        y= 5 * x + 3
print('f(%.2f) = %.2f' % (x, y))
```

> Explanation: You can feel for yourself which of these two writing methods is better. In the Zen of Python we mentioned earlier, there is such a sentence "Flat is better than nested." Readability, so don't use nesting when you can use a flat structure.

## Practice

### Exercise 1: Exchange the imperial unit inches with the metric unit centimeters.

```python
value = float(input('enter the length: '))
unit = input('Please enter the unit: ')
if unit == 'in' or unit == 'inch':
    print('%f inch = %f cm' % (value, value * 2.54))
elif unit == 'cm' or unit == 'cm':
    print('%f cm = %f inch' % (value, value / 2.54))
else:
    print('Please enter a valid unit')
```

### Exercise 2: Convert percentile grades to grade grades.

Requirements: If the input score is above 90 points (including 90 points), output A; 80 points-90 points (excluding 90 points) output B; 70 points-80 points (excluding 80 points) output C; 60 points-70 points Points (excluding 70 points) output D; 60 points or less output E.

```python
score = float(input('Enter score: '))
if score >= 90:
    grade = 'A'
elif score >= 80:
    grade = 'B'
elif score >= 70:
    grade = 'C'
elif score >= 60:
    grade = 'D'
else:
    grade = 'E'
print('The grade is: ', grade)
```

### Exercise 3: Enter the lengths of three sides, and calculate the perimeter and area if a triangle can be formed.

```python
a = float(input('a = '))
b = float(input('b = '))
c = float(input('c = '))
if a + b > c and a + c > b and b + c > a:
    print('perimeter: %f' % (a + b + c))
    p = (a + b + c) / 2
    area = (p * (p - a) * (p - b) * (p - c)) ** 0.5
    print('area: %f' % (area))
else:
    print('cannot form a triangle')
```













