.. qnum::
   :prefix: func-annotate
   :start: 1

.. index:: 
   type annotation
   
Type Annotations
----------------

Consider the following function definition:

.. sourcecode:: python

    def duplicate(msg):
        """Returns a string containing two copies of `msg`"""

        return msg + msg

This function is intended to duplicate a message; if called with the value 'Hello', it returns the value
'HelloHello'. If called with other types of data, however, it will not work properly. (What will the
function do if given an ``int`` or a ``float`` value?)

It would be helpful if there were a way to indicate to the programmer using the function that a ``str`` argument should
be passed, instead of other data. Python allows you to indicate the expected type of the parameter and return value using notation 
like this:

.. sourcecode:: python

    def duplicate(msg: str) -> str:
        """Returns a string containing two copies of `msg`"""

        return msg + msg

The notation ``msg: str`` indicates that the caller should pass a ``str`` value as an argument. The notation ``-> str``
indicates that the function will produce a ``str`` result. These notations are called type annotations. A **type
annotation** is a type of documentation. It tells the programmer using the function what kind of data to pass to the
function, and what kind of data to expect when the function returns a value.

Here are some more examples of functions with type annotations:

.. sourcecode:: python

    def add(x: int, y: int) -> int:
        """Returns the sum of `x` and `y`"""

        return x + y

    def get_number(msg: str) -> float:
        """Prompts with `msg` for input; returns numeric response."""

        return float(input(msg))

    def display_msg(msg: str):
        """Displays `msg` with dashed line underneath"""

        print(msg)
        print('-------------------------------------')


It's important to understand that adding type annotations to a function definition does not cause the Python interpreter
to check that the values passed to a function are the expected types, or cause the returned value to be converted to the
expected type. For example, if the function ``add`` in the example above is called like this::

    result = add('5', '15')

the function will receive two string values, concatenate them, and return the resulting string '515'. The ``int``
annotations are completely ignored by the Python interpreter. Type annotations are a special type of function
documentation, and have no effect on the program's behavior.

.. note::

    Type annotations are not supported in the activecode interpreter used in this book, so if you try to use them,
    the activecode interpreter will report an error. 

Type annotations are an optional aspect of documenting functions. Still, type annotations are an important tool to increase
the readability of your code, and you should use them in your programs.
