# Python3 Data Type Conversion

Sometimes, we need to convert the built-in data type, data type conversion, in general, you only need to use the data type as the function name. Python data type conversion can be divided into two types:

- Implicit type conversions - auto-completion
- Explicit type conversion - need to use type function to convert

## Implicit type conversion

The lower data type (integer) is converted to the higher data type (float) to avoid data loss.

```python
num_int = 123
num_flo = 1.23

num_new = num_int + num_flo

print("datatype of num_int:",type(num_int))
print("datatype of num_flo:",type(num_flo))

print("Value of num_new:",num_new)
print("datatype of num_new:",type(num_new))
```

```python
num_int data type: <class 'int'>
num_flo data type: <class 'float'>
num_new: value: 124.23
num_new data type: <class 'float'>
```

### Code analysis:

- In the example, we add two variables `num_int` and `num_flo` of different data types and store them in the variable `num_new`.

```python
num_int = 123
num_str = "456"

print("Data type of num_int:",type(num_int))
print("Data type of num_str:",type(num_str))

print(num_int+num_str)
```

## Explicit type conversion

In explicit type conversion, the user converts the data type of the object to the desired data type. We use predefined functions like int(), float(), str() etc. to perform explicit type conversions.

- `int()` casts to an integer:

  ```python
  x = int(1)   # x output value is 1
  y = int(2.8) # y output value is 2
  z = int("3") # z output value is 3
  ```

- `float()` coerces to a float:

  ```python
  x = float(1)     # x output value is 1.0
  y = float(2.8)   # y output value is 2.8
  z = float("3")   # z output value is 3.0
  w = float("4.2") # w output value is 4.2
  ```

- `str()` casts to a string type:

  ```python
  x = str("s1") # x output value is 's1'
  y = str(2)    # y output value is '2'
  z = str(3.0)  # z output value is '3.0'
  ```

- Operations on integer and string types can be done with casts:

  ```python
  num_int = 123
  num_str = "456"
  
  print("num_int data type:",type(num_int))
  print("before type conversion，num_str data type:",type(num_str))
  
  num_str = int(num_str)    
  print("after type conversion，num_str data type:",type(num_str))
  
  num_sum = num_int + num_str
  
  print("num_int 与 num_str The result of adding is:",num_sum)
  print("sum data tpye:",type(num_sum))
  ```

  ```python
  num_int num_int data type: <class 'int'>
  before type conversion，num_str data type: <class 'str'>
  after type conversion，num_str data type: <class 'int'>
  num_int 与 num_str The result of adding is: 579
  sum data tpye: <class 'int'>
  ```

  



























