# Python Style Guide
---
Having good style conventions is important when reading and debugging your code. Please use the guidelines below when formatting your python
code. These guidelines are a brief summary of the more in depth [PEP 8 Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/).

## Spacing
* Line length should be no longer than 80 characters
* Separate your function declarations by a new line
* Avoid whitespace:
  * immediately inside parentheses
    * Do: ```("AB" + "8")```
    * Don’t: ```( "AB" + "8" )```
  * before colons, commas and brackets
    * Do: ```ab[4]```
    * Don’t: ```ab [4]```
    
* Put a newline after branching and looping statements
    * Do:
```python
if class == 4:
    print("It’s ABC!")
else:
    print("Not ABC.")
```
* Don’t:
```python
if a > 4: print("It’s ABC!")
else: print("Not ABC.")
```

## Naming
* Functions and variables should be written in all lowercase letters with
underscore separating words
  * Examples: ```lower_case, my_function, distance, num_times```
* Constants should be written in all capital letters with underscores separating
words
  * Examples: ```CONSTANT_CASE, HEIGHT, BORDER_WIDTH, MAX_VALUE```
* Class names (and exceptions) should be written with the ”CamelCase”
convention
  * Examples: ```CamelCaseClass, MyAwesomeClass, LibraryBook```
* Modules should have short, lowercase names.
  * Examples: ```module, algos, lower```
  
## Commenting
* Write docstrings for every class, function, module and method. The
docstring should briefly describe what the function does as well as list
inputs and outputs.
```python
def multiply(a, b):
    """
    Multiply two numbers together and return the product.
    """
    return a*b
```
* Comments should be used sparingly to explain complex code

## Others
* Place your imports at the start of the file, and give each import its own
line.
    * Do:
```python
import module1
import module2
import module3
```
* Don't:
```python
import module1, module2, module3
```
* Do not write compound statements
    * Do:
```python
function1()
function2()
function3()
```
* Don’t:
    
```python
function1(); function2(); function3()
```
