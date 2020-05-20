..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-2-
   :start: 1

.. index::
    class
    data type
    type

.. _values-and-types:

Values and Data Types
---------------------

Computers exist to process information. The earliest computers were created to perform numerical calculations, and many
early users thought of computers primarily in terms of their usefulness as fast number crunchers. But, in a somewhat
ironic turn of events, relatively few people in the twenty-first century use computers primarily for numeric processing
tasks. Instead, they use them to listen to music, watch videos, shop, consume information on the web, and so on.
Although all of that information is ultimately represented internally within the computer using numbers, the computer
exposes the underlying numeric information to users in many different forms. 

Programs organize the data that they process into individual values. A **value** is one of the fundamental things ---
like a word or a number --- that a program manipulates. We often refer to values as **objects** and we will use the
words *value* and *object* interchangeably.

Just as computers expose information to users in different forms, individual values are classified into different
**classes**, or **data types**.  A **data type** (or **type**, or **class**) is a category of values. (This is a key
definition, so take a moment to note it.)

In the previous section, you encountered two classes of data: ``int`` and ``float``. Examples of values in the ``int``
class include ``2``, ``-53``, and ``0``. Examples of values in the ``float`` class include ``2.0``, ``-13.5``, and
``0.0``. Note that although ``2`` and ``2.0`` are mathematically equivalent values, they are members of different data
types in Python, and are stored and processed differently (as you saw with regard to precision).

So far, you've seen only numeric data. But as observed above, computers these days are often used more to process
textual information than numeric. It's time for you to see how Python interacts with textual information.

The ``str`` data type
^^^^^^^^^^^^^^^^^^^^^

In chapter one, you saw an example of a simple "Hello, world" program. Here it is again:

.. activecode:: vdt_hello
    :nocanvas:

    print("Hello, world!")

This program displays a brief message on the screen. The message is textual, not numeric. Although it consists of
two words, plus some punctuation, to the computer the message is a *single value*. The value "Hello, world!" is a
string value; that is, it is a member of the ``str`` data type. A **string** is a sequence of zero or more characters
(letters, digits, spaces, punctuation, and other symbols). 

When you write string values, you must enclose them in quotes (either single or double quotes works). Try removing the quotes
from the print statement above and see what happens when you run it.

Just as you can use strings in print commands, you can experiment with strings in the Python shell. Why don't you fire up
the Python shell and follow along as we explore what you can do with strings.

First, experiment with entering simple numeric and string values into the shell:

.. sourcecode:: python

    >>> 53
    53
    >>> '53'
    '53'
    >>> "53"
    '53'
    >>> print('Hi')
    Hi
    >>>

The first value evaluated is the integer 53; the interpreter displays its value with no quotes, because it is an
integer, not a string. The second and third values evaluated are strings, not integers, because they are quoted. Can you
spot the difference between the two string examples? I used single quotes around the first, and double quotes around the
second. In both cases, Python evaluated the string and spit it back out surrounded by single quotes. This demonstrates
an important idea: although you must use quotes around string values when you type them into the interpreter or when
writing a program, the quotes are not part of the string value itself. 

It's easy to be confused on this point, because when Python displays string values in the interpreter, it includes the
quotes, so that you can differentiate between values like ``53`` (an ``int``) and ``'53'`` (a ``str``). But when you use
the print command to display string values, the quotes are not included, because the print command displays only the
*content* of the string. Let's look at a couple of additional examples to try to demonstrate clearly that quotes are not
part of the string:

.. sourcecode:: python

    >>> len('Hi there!')
    9
    >>> len(' ')
    1
    >>> len("")
    0
    >>> 

Here, we've used the built-in ``len`` function to compute the number of characters in a string. Note that the quotes are not
included in the length. Note that spaces within the quotes *are* included in the length; hitting the space bar on your keyboard
inserts a space character, which takes up one position in the string.

Now, look at this:

.. sourcecode:: python

    >>> len('53')
    2
    >>> len(53)
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: object of type 'int' has no len()
    >>>

This example demonstrates that the values ``'53'`` and ``53`` mean different things to Python. ``'53'`` is a string, and
has a length. The ``len`` function computed its length, and the interpreter displayed the result. However, the ``len``
function cannot operate on ``int`` data, and an error occurred when we tried to compute the length of the integer
``53``. More on this in a moment.

Concatenating Strings
^^^^^^^^^^^^^^^^^^^^^

Try this out in your shell:

.. sourcecode:: python

    >>> 3 + 4
    7
    >>> 'abc' + 'def'
    'abcdef'
    >>> 'abc' + 'def' + 'ghi'
    'abcdefghi'
    >>>

The + operator has two uses. It can add two numbers together. But when used with strings, it joins two string values
together to form a single string, in an operation called **concatenation**.  

String concatenation is an extremely useful operation, although you can't tell it from this first example. We'll do more with
it in the next section.

More on String Quoting
^^^^^^^^^^^^^^^^^^^^^^

Strings in Python can be enclosed in either single quotes (``'``) or double
quotes (``"`` - the double quote character), or three of the same separate quote characters (``'''`` or ``"""``).
The triple quotes are especially helpful when you need to include quotations inside the string. Triple quotes
also allow you to write a message that spans several lines. 

.. activecode:: ch02_4
    :nocanvas:

    print('This is a string.') 
    print("And so is this.") 
    print('''He said, "She yelled, 'Gezundheit!'"''') 
    print("""This message will span
    several lines
    of the text.""")

Python doesn't care whether you use single or double quotes or the
three-of-a-kind quotes to surround your strings.  Once it has parsed the text of
your program or command, the way it stores the value is identical in all cases,
and the surrounding quotes are not part of the value.


The type function
^^^^^^^^^^^^^^^^^

At the beginning of this section, we introduced the concept of a data type. Understanding the concept of a data type is
important because programs perform work by manipulating data values, and the operations that a program can perform on a
particular data value are determined by the value's data type. For example, a program can multiply two ``int`` values,
but it can't multiply two ``str`` values (try it and see what happens). You can compute the length of a ``str`` value
using the ``len`` function, but you can't compute the length of an ``int`` value``. You can concatenate two
``str`` values, but you can't concatenate two ``int`` values. We will spend a good bit of time in
this book describing the operations that are supported by the various data types you will use in Python.

If you are not sure what class a value falls into, Python has a function called **type** which can tell you. For example:

.. sourcecode:: python

    >>> type(2)
    <class 'int'>
    >>> type(2.5)
    <class 'float'>
    >>> type(2 + 2.0)
    <class 'float'>
    >>> type('2.5')
    <class 'str'>
    >>>


**Check your understanding**

.. mchoice:: test_question2_1_1
   :practice: T
   :answer_a: Print out the value and determine the data type based on the value printed.
   :answer_b: Use the type function.
   :answer_c: Use it in a known equation and print the result.
   :correct: b
   :feedback_a: You may be able to determine the data type based on the printed value, but it may also be deceptive; when a string prints, there are no quotes around it.
   :feedback_b: The type function will tell you the class the value belongs to.
   :feedback_c: Only numeric values can be used in equations.

   How can you determine the data type of a value?

