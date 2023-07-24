# Python Regular Expression

A regular expression is a special sequence of characters that helps you easily check whether a string matches a certain pattern.



## re.match function

re.match Attempts to match a pattern from the beginning of the string. If the match is not at the beginning, match() returns none.

```python
re.match(pattern, string, flags=0)
```

Description of function parameters:

| parameter | description                                                  |
| --------- | ------------------------------------------------------------ |
| pattern   | matched regular expression                                   |
| string    | The string to match                                          |
| flags     | The flag bit is used to control the matching mode of the regular expression, such as: whether to be case-sensitive, multi-line matching, etc. See: Regex Modifiers - Optional Flagshttps://www.runoob.com/python3/python3-reg-expressions.html#flags |

The re.match method returns a matching object if the match is successful, otherwise it returns None.

Use the group(num) or groups() match object functions to obtain match expressions.

| match object method | description                                                  |
| ------------------- | ------------------------------------------------------------ |
| group(num=0)        | The string that matches the entire expression, group() can be fed multiple group numbers at once, in which case it will return a tuple containing the values corresponding to those groups. |
| groups()            | Returns a tuple containing all group strings, from 1 to the group number contained in . |

```python
import re
print(re.match('www','www.lanyang.com').span())
print(re.match('com','www.lanyang.com'))
```

```python
(0,3)
None
```

