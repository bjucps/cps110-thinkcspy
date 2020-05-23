..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: whatislang-1-
   :start: 1

.. index:: programming language

What is a Programming Language?
===============================

Before I can explain how to use some of the nifty built-in capabilities of Python we'll explore in this chapter, I need to answer an important
question: What exactly is a programming language, anyway?

If you're thinking, "it's a language used to write computer programs," of course that's correct. Let me word the question a little more
precisely: How are programming languages defined? In other words, how does a programming language designer specify the rules of the language?

Programming languages are typically defined when a language designer creates a programming language definition. A **programming language
definition** is a document that is composed of two main sections:

1. A **language specification**, which lays out the rules of syntax that dictate the notation programmers use to write
   instructions in the language, together with the semantics ("meaning") of that syntax, along with a few built-in
   functions and classes; and 

2. The **standard library**, which defines additional built-in functions and classes that are available to use in
   programs written in that language.  

To explain the difference between the language specification and the library, consider the following short program:

.. sourcecode:: python

   import math

   x = math.sqrt(3)
   print(x + 5)

The Python language specification defines rules of syntax that specify how you write assignment statements like ``x =
math.sqrt(3)`` and function call statements like ``print(x + 5)``. It also defines certain built-in functions, like
``print``, ``len``, and ``input``. However, let's look at line 3. That line invokes a function named ``sqrt`` that is defined in the math
section of the Python Standard Library. The Python Standard Library is a collection of function and class definitions
that you can make use of when you write Python programs. In order to use the standard library, you must write ``import``
statements, such as the example on line 1. More on that shortly.

.. admonition: What's a function definition?

   If the notion of a function definition is a little fuzzy, that's because you haven't seen one yet. Later in this book there is a whole chapter
   devoted to defining your own functions. But to help add some concreteness to this discussion, let me give you a sneak peak and show you
   a function definition:

   .. sourcecode:: python

      def printsum(x, y):
         sum = x + y
         print(sum)

   This fragment of Python defines a function named ``printsum``. A **function definition** associates a name with a set of Python instructions. 
   The idea is that, once the function is defined, you can have Python carry out the instructions inside by invoking the function using a function
   call statement like this::

      printsum(2, 3)

   Python executes the instructions in the ``printsum`` definition, adding together the numbers you supplied in parenthesis and printing the sum.

When you're learning a language, you have to learn aspects of both the language specification and the standard library. Up to now, we've been
focused primarily on mastering basic aspects of the language specification, like how to create variables and perform calculations with mathematical
and string operations. In this chapter, our focus shifts to the standard library.

