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
