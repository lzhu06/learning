# PART 1: Writting your own functions 
## User-dfined functions
* Built-in functions 
* Defining a function:
	```python
	def sqaure ():          #<-function header
	new_value = 4**2      #<-function body
	print(new_value)      #<-print out
	return new_value      #<-return new value
	square()              #<-call function
	```
* Docstrings: """definition of functions"""
## Multiple parameter functions
```python
def func_name(val1,val2):
"""descriptive for functions"""
  new_val = val1 ** val2
 	return new_val
func_name(a,b) 
```
## Scope and user-defined functions
##### Scope:
* GLobal scope
* Local scope
* Built-in scope
##### Nested Functions
* example functions:
	```python
		# option 1 - tradition way
		def mod2plus5(x1,x2,x3)
		"""Returns the remainder plus 5 of three values."""
		new_x1 = x1 % 2 + 5
		new_x2 = x2 % 2 + 5
		new_x3 = x3 % 2 + 5
		return (new_x1,new_x2,new_x3)
		# option 2 - inner function
		def mod2plus5(x1,x2,x3)
		"""returns the remainder plus 5 of three values."""
			def inner(x)
			"""returns the remainder plus 5 of a value."""
			return x % 2 + 5
		return (inner(x1),inner(x2),inner(x3))
		print(mod2plus5(1,2,3))
	```
* Returning functions
	```python
		def raise_val(n):
		"""return the inner function."""
		def inner(x):
		"""raise x to the power of n."""
			raised = x ** n
			return raised
		return inner
		square = raise_val(2)
		cube = raise_val(3)
		print(square(2),cube(4))
		# Output: 4 64
	```
* Using nonlocal: will change the outer and inner value.
> Summary: Scope Searched: Local scope, enclosing functions, global, built-in called LEGB rules. 
##### Practice Example
* Nested functions
```python
# Define three_shouts
def three_shouts(word1, word2, word3):
    """Returns a tuple of strings
    concatenated with '!!!'."""

    # Define inner
    def inner(word):
        """Returns a string concatenated with '!!!'."""
        return word + '!!!'

    # Return a tuple of strings
    return (inner(word1),inner(word2),inner(word3))

```
# PART 2: Default arguments, variable-length arguments and scope
# PART 3: Lambda functions and error-handling 
