# Python-Bootcamp-Notes

### Decorator

acts as on/off switch for additional functionality in a function. instead of having to write multiple functions that copy code, etc.  
they use the @ operator and are placed on top of the original function

```
@some_decorator
def simple_func():
  # do simple stuff return something
```

Later on you can go in and just delete the @ line to remove the additional functionality

involves assigning a function to another function:  

```
def hello():
    return "hello!"
```

if you run `hello` you get `function __main__.hello()>`

then you run
```
greet = hello
greet()
```
which returns `'hello!` EVEN IF you delete the hello() function  

can have something like:
```
def hello(name = 'jose'):
    print('the hello() function has been executed!')
    
    def greet():
        return '\t This is the greet() func inside hello!'
    
    def welcome():
        return '\t This is welcome() inside hello'
    
    print('I am going to return a function!')
    
    if name == 'jose':
        return greet
    else:
        return welcome
```

and then if you run `mynewfunc = hello('jose')` this assigns the returned FUNCTION to mynewfunc, so now if you call `mynewfunc()` you get what the `greet` function returns!


### Basic Premise of the Decorator

```
def newdecorator(original_func):
    
    def wrapfunc():
        print('some extra code, before the original function')
        
        original_func()
        
        print('some extra code, after the original function')
    
    return wrapfunc
```

These are called 'decorators' because they kind of wrap up the target function with additional code. 

# Generator

Allow us to write a function that can send back a value and then later resume to pick up where it left off.  
Generate a sequence of values over time. Main difference is use of a `yield` statement.  
  
When called, becomes an object that supports an iteration. When called into code they don't actually return a value and then exit. Automatically suspend and resume thei rexecution and state aroud the last point of value generation. Instead of having to generate a whole series of values upfront, allows you to wait until next one is called for.

This is how the `range()` function works. Instead of making a giant array of say 1,000,000 numbers and taking up a lot of memory, it keeps track of the last number and step size, to provide a flow of numbers.

```
def gensquares(N):
  for i in range(N):
    yield i**2

for x in gensquares(10):
  print(x)
```

In this case `gensquares(10)` is a generator object, so you can either iterate through it with a `for` loop as shown above or call `next(gensquares(N))` to get each next value from it.  

You can also turn something into an iterator by using `iter()`  

For instance,
```
s = 'hello'
#can't iterate through this as a generator bc it hasnt been declared as such, let's cast!
s_iter = iter(s)
next(s_iter) #works
```




## List Comprehension vs Generator Comprehension

```
mylist = [1,2,3,4,5]

lcomp = [item for item in mylist if item > 3]
gencomp = (item for item in mylist if item > 3)
```

lcomp computes the whole list and returns it. gencomp becomes a generator you can call `next()` on.
