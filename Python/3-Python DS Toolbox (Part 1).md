PART 1: Writting your own functions 
[User-dfined functions] - 
  a. Built-in functions 
  b. defining a function
      def sqaure ():          #<-function header
        new_value = 4**2      #<-function body
        print(new_value)      #<-print out
        return new_value      #<-return new value
      square()                #<-call function
  c. Docstrings: """definition of functions"""
[Multiple parameter functions]
 a. def func_name(val1,val2):
    """descriptive for functions"""
    new_val = val1 ** val2
    return new_val
    func_name(a,b) 
  b. Tuples:
[Scope and user-defined functions]
  a. Scope:
      i. GLobal scope
     ii. Local scope
    iii. Built-in scope
  b. Nested Functions
     example functions 1：
     ```
        def outer(...):
          """..."""
          x= ...
          def inner(...)
          """..."""
          y=x**2
          return ...
     ```
PART 2: Default arguments, variable-length arguments and scope
PART 3: Lambda functions and error-handling 