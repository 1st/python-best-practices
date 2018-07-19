# Python best practices

Here you will find some ideas how to use Python language to make your life easier in the long run.

## Pass only keyword arguments

It's easy to be confused when you see something like this: `do_something(1, 'abc')`. Because you do not know what is
behind these two parameters - you need to open definition of the function and then return back with idea about what
each parameter means. But you can **always** use keyword parameters to make your Python program stronger.

```python
do_something(start_position=1, string='abc')
```

Now it's more obvious that the function doing something with the string. Now, imagine that you have made change in
your code and function `do_something` now applies one new parameter:

```python
def do_something(string, start_position=0, end_position=None): ...
```

In case if you used the positional arguments, it colud create problems with math parameters. If you have names - you
know what parameters you are passing there, code becomes more readable. If you will need to find all functions that use
some parameter, or rename this parameter - you can do it easily.

## Use type annotaions

When you need change big part of your project it becomes hard to achieve this without introducing new bugs. But if you
do not know what type of argument you applying in the function *(or need pass to the function)* it becomes much harder
and slower to make such change.

It's why [type annotations](https://docs.python.org/3/library/typing.html) have been added to Python. You can be more
confident about your code and your changes to this code. If you wil use it only in some places it may be not give you
the best results. If you start new project - use them in all places. If you adding it to existing project - try to use
them in all places where you change code to cover code more and more.

When you use type annotation - try to be precise and do not use wider range of types. For example, instead of `Iterable`
use `List` if you know that now you can handle only list of values, not any iterable type. And use `List(basestring)`
if you know that your function can handle *only strings*. It will help user of your function to understand how it works
without look inside it. If user assumes *"I can pass an iterable, nd it will be used efficiently"* but you actually will
made a list from it and will keep all data in memory - it may confuse the user why don't you apply list instead.
