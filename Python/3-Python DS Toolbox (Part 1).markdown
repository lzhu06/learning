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
# PART 2: Default arguments, variable-length arguments and scope
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
###### Practice Example
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
##### Default and flexible arguments
* Add a default argument (sinlge and multiple)
```python
#note: *args & **kwargs
# Define gibberish
def gibberish(*args):
    """Concatenate strings in *args together."""

    # Initialize an empty string: hodgepodge
    hodgepodge = ""

    # Concatenate the strings in args
    for word in args:
        hodgepodge += word

    # Return hodgepodge
    return hodgepodge

# Call gibberish() with one string: one_word
one_word = gibberish("luke")

# Call gibberish() with five strings: many_words
many_words = gibberish("luke", "leia", "han", "obi", "darth")

# Print one_word and many_words
print(one_word)
print(many_words)
########output:
	luke
	lukeleiahanobidarth
################################
```
##### Put everything together
>Generalized functions:
	1. Count occurences for any column
	2. Count occurences for an arbitrary number of columns
* Practice option 1:
```python
	# Define count_entries()
	def count_entries(df, col_name='lang'):
    	"""Return a dictionary with counts of
    	occurrences as value for each key."""

   	 # Initialize an empty dictionary: cols_count
   	 cols_count = {}

    	# Extract column from DataFrame: col
    	col = df[col_name]
    
    	# Iterate over the column in DataFrame
    	for entry in col:

        	# If entry is in cols_count, add 1
        	if entry in cols_count.keys():
            	cols_count[entry] += 1

        	# Else add the entry to cols_count, set the value to 1
        	else:
            	cols_count[entry] = 1

    	# Return the cols_count dictionary
    	return cols_count

	# Call count_entries(): result1
	result1 = count_entries(tweets_df)

	# Call count_entries(): result2
	result2 = count_entries(tweets_df, col_name='source')

	# Print result1 and result2
	print(result1)
	print(result2)
```	
# PART 3: Lambda functions and error-handling 
### Lambda functions
### intro to error handling
* Passing invalid arguments
* Errors and exceptions
* Practice & Example
   ```python
   #Error and expectation
   def sqrt(x):
   """Returns the square root of a number"""
      try:
       return x ** 0.5
      except Type Error:
       print('x must be an int or float')
   ```
   ```python
   #Error handling by raising an error
   def sqrt(x):
   """Returns the square root of a number"""
   #Define shout_echo
   def shout_echo(word1, echo=1):
    """Concatenate echo copies of word1 and three
    exclamation marks at the end of the string."""
    #Raise an error with raise
    if echo<0:
        raise ValueError('echo must be greater than 0')
    #Concatenate echo copies of word1 using *: echo_word
    echo_word = word1 * echo
    #Concatenate '!!!' to echo_word: shout_word
    shout_word = echo_word + '!!!'
    # Return shout_word
    return shout_word
   # Call shout_echo
   shout_echo("particle", echo=5)
   ```
### Bring it all together
* Example & Practice No.1:filter and check bool value
   ```python
   # Select retweets from the Twitter DataFrame: result
   x=tweets_df['text']
   result = filter(lambda x: x[0:2]=='RT',x)

   # Create list from filter object result: res_list
   res_list = list(result)

   # Print all retweets in res_list for tweet in res_list:
       print(tweet)
   ```
* Example & Practice No.2: try-except 
   ```python
   # Define count_entries()
   def count_entries(df, col_name='lang'):
       """Return a dictionary with counts of
       occurrences as value for each key."""

       # Initialize an empty dictionary: cols_count
       cols_count = {}

       # Add try block
       try:
           # Extract column from DataFrame: col
           col = df[col_name]
        
           # Iterate over the column in dataframe
           for entry in col:
    
               # If entry is in cols_count, add 1
               if entry in cols_count.keys():
                   cols_count[entry] += 1
               # Else add the entry to cols_count, set the value to 1
               else:
                   cols_count[entry] = 1
     
           # Return the cols_count dictionary
           return cols_count

       # Add except block
       except TypeError:
           print('The DataFrame does not have a ' + col_name + 'column.')

   # Call count_entries(): result1
   result1 = count_entries(tweets_df, 'lang')

   # Print result1
   print(result1)
   ```
 * Example & Practice No.3: Raise an error
    ```python
       # Define count_entries()
   def count_entries(df, col_name='lang'):
       """Return a dictionary with counts of
       occurrences as value for each key."""
    
       # Raise a ValueError if col_name is NOT in DataFrame
       if col_name not in df.columns:
           raise ValueError('The DataFrame does not have a '+ col_name+' column.')

       # Initialize an empty dictionary: cols_count
       cols_count = {}
    
       # Extract column from DataFrame: col
       col = df[col_name]
    
       # Iterate over the column in DataFrame
       for entry in col:

           # If entry is in cols_count, add 1
           if entry in cols_count.keys():
               cols_count[entry] += 1
               # Else add the entry to cols_count, set the value to 1
           else:
               cols_count[entry] = 1
        
           # Return the cols_count dictionary
       return cols_count

   # Call count_entries(): result1
   result1 = count_entries(tweets_df, col_name='lang')

   # Print result1
   print(result1)
    ```
