# Python Comprehension

Python comprehension is a unique data processing method that can construct another new data sequence structure from one data sequence. Python supports comprehensions for various data structures:

- list comprehension

- Dictionary (dict) comprehension

- set comprehension

- tuple comprehension

  

## List Comprehension

- out_exp_res: List generation element expression, which can be a function with a return value
- for out_exp in input_list: Iterate over input_list passing out_exp into out_exp_res expression
- if condition: Conditional statement, which can filter values that do not meet the condition in the list.

**Filter out a list of strings with length less than or equal to 3, and convert the rest to uppercase:**

```python
names = ['Bob','TOm','alice','Jerry','Wendy','Smith']
new_names = [name.upper()for name in names if len(name)>3]
print(new_names)
```

**Compute integers up to 30 divisible by 3:**

```python
multiples = [i for i in range(30) if i % 3 == 0]
>>> print(multiples)
[0, 3, 6, 9, 12, 15, 18, 21, 24, 27]
```



## Dictionary Comprehension

Create a dictionary with strings and their lengths:

```python
listdemo = ['google','lanyang','Taobao']
newdict = {key:len(key) for key in listdemo}
newdict
```



## set comprehension

Compute the squares of the numbers 1,2,3:

```python
>>> setnew = {i**2 for i in (1,2,3)}
>>> setnew
{1, 4, 9}
```

Judge the letters that are not abc and output:

```python
>>> a = {x for x in 'abracadabra' if x not in 'abc'}
>>> a
{'d', 'r'}
>>> type(a)
<class 'set'>
```



## Tuple Comprehensions (generator expressions)

Tuple comprehension can use data types such as range intervals, tuples, lists, dictionaries, and sets to quickly generate a tuple that meets specified requirements. 

Basic format of tuple comprehension:

```python
>>> a = (x for x in range(1,10))
>>> a
<generator object <genexpr> at 0x7faf6ee20a50>  # Returns a generator object

>>> tuple(a)       # Generator objects can be directly converted into tuples using the tuple() function
(1, 2, 3, 4, 5, 6, 7, 8, 9)
```

