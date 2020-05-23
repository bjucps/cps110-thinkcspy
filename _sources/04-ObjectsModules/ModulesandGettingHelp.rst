..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: modules-1-
   :start: 1

.. index:: documentation online, Global Module Index
   module; standard, namespace

Modules
=======

The Python Standard Library, as you just learned, is composed of a set of definitions. The library is organized into
groups of definitions called modules. A **module** is a file containing Python variables, functions and classes intended
for use in Python programs. In this chapter, we'll explore some of the modules in Python's library.

The  `Python Documentation <https://docs.python.org/3/>`_ site for Python version
3 is an extremely useful reference for all aspects of Python. The site
contains a listing of all the standard modules that are available with Python
(see `Global Module Index <https://docs.python.org/3/py-modindex.html>`_). You
will also see that there is a
`Standard Library Reference <https://docs.python.org/3/library/index.html>`_
and a
`Tutorial <https://docs.python.org/3/tutorial/index.html>`_ as well as
installation instructions, how-tos, and frequently asked questions.  We
encourage you to become familiar with this site and to use it often.

If you have not done so already, take a look at the Global Module Index.  Here
you will see an alphabetical listing of all the modules that are available as
part of the standard library.  

Importing Modules
-----------------

In order to use the functions and classes in Python modules, you have to **import** them into a Python program. That
happens with an import statement like this::

   import math

This import statement tells the interpreter that you plan to use the capabilities of the module named ``math`` in your program.
Roughly translated to English, an import statement says "I want to use the functions, variables, and classes defined
in the math module in this program." 

You should usually put ``import`` commands at the very top of your file. They can be put elsewhere, but that can 
lead to confusion, so it's best to follow the convention.

.. admonition:: Be careful about what you name your programs!

    Do not save your programs with filenames that use names of standard library modules. For example, if you create a file
    ``math.py`` in the same folder as ``myprog.py``, and then myprog.py invokes ``import math``, it will import *your*
    math.py file rather than the standard library module. That's not usually what you want, and will lead to very confusing
    error messages, so be careful about how you name your python files! 

Using the ``math`` Module
-------------------------

The ``math`` module contains the kinds of mathematical functions you would typically find on your calculator, like
``sin`` (sine) and ``cos`` (cosine), and some mathematical constants like `pi` and `e`. 

Here's a short program that demonstrates some of the capabilities of the ``math`` module:

.. activecode:: chmodule_02

    import math

    print('math.pi is:', math.pi)
    print('math.e is:', math.e)

    print('The square root of 2 is:', math.sqrt(2))

    print('The sine of 90 degrees is:', math.sin(math.radians(90))) 

Notice that you access individual members of the math module by prefixing them with ``math`` and a dot. For example,
to access the value of the ``pi`` variable defined in the ``math`` module, we write ``math.pi``.  

For more details about additional members of the math module, check out the
`Math Module <http://docs.python.org/3/library/math.html#module-math>`_ Python Documentation.


Ways to Import Modules
----------------------

The ``import`` statement has a second form you can use. Take a look at this example:

.. sourcecode:: python

    from math import pi, e, sqrt

    print('math.pi is:', pi)
    print('math.e is:', e)

    print('The square root of 2 is:', sqrt(2))

You can import individual variables and functions from a module by writing a statement with this syntax::

   from MODULENAME import MEMBER1, MEMBER2, ...

This form of the import statement removes the need to prefix each member with the name of the module when you use it. In
the example above, the program accessed the members ``pi``, ``e``, and ``sqrt`` from the math module directly, without
prefixing them with ``math`` and a dot. This technique can reduce the amount of typing required and streamline the code. However,
it makes it less clear when looking at individual lines of the program which variables and functions are ones you have
defined in your program, and which are ones you have imported from a module. So, there is a tradeoff between brevity and
clarity.

To summarize, there are two ways to import a module.

1. The ``import`` statement. This gives the program access to all of the
   contents of the module, but accessing individual members of the module requires prefixing
   them with the name of the module.

2. The ``from`` ... ``import`` statement. This allows the program to access selected members
   of the module without the prefix.

In general, most professional Python programmers prefer the first approach, because of the improved
clarity it offers, so that is the technique used in most of the examples of this book. 

.. admonition:: Note: Python modules and limitations with activecode

   Many of the  modules available in standard Python will **not** work in the activecode environment used in this book.
   In fact, only ``turtle``, ``math``, ``random``, and a couple others have been ported at this point.  If you wish to
   explore any additional modules, you will need to run from the native python interpreter on your computer.

**Check your understanding**

.. mchoice:: question13_1_1
   :answer_a: A file containing Python definitions and statements intended for use in Python programs.
   :answer_b: A separate block of code within a program.
   :answer_c: One line of code in a program.
   :answer_d: A file that contains documentation about functions in Python.
   :correct: a
   :feedback_a: A module can be reused in different programs.
   :feedback_b: While a module is separate block of code, it is separate from a program.
   :feedback_c: The call to a feature within a module may be one line of code, but modules are usually multiple lines of code separate from the program.
   :feedback_d: Each module has its own documentation, but the module itself is more than just documentation.

   In Python a module is:

.. mchoice:: question13_1_2
   :answer_a: Go to the Python Documentation site.
   :answer_b: Look at the import statements of the program you are working with or writing.
   :answer_c: Ask the professor.
   :answer_d: Look in this textbook.
   :correct: a
   :feedback_a: The site contains a listing of all the standard modules that are available with Python.
   :feedback_b: The import statements only tell you what modules are currently being used in the program, not how to use them or what they contain.
   :feedback_c: While the professor knows a subset of the modules available in Python, chances are the professor will have to look up the available modules just like you would.
   :feedback_d: This book only explains a portion of the modules available.  For a full listing you should look elsewhere.

   To find out information on the standard modules available with Python you should:

.. mchoice:: question13_1_3
   :answer_a: True
   :answer_b: False
   :correct: b
   :feedback_a: Only a few modules have been ported to work in activecode at this time.
   :feedback_b: Only a few modules have been ported to work in activecode at this time.

   True / False:  All standard Python modules will work in activecode.

