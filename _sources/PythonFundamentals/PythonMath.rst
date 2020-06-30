..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-ops-
   :start: 1

.. index::
   single: +; addition
   single: - 
   single: *; multiplication of numbers
   single: **
   single: ( ); grouping
   multiplication
   operators
   operands
   expression

Python Math
===========

It's time to dive into the details of the Python programming language. In this chapter, you will use both the activecode
Python interpreter built into this book, as well as the Python shell that you have installed on your computer, to experiment
with the concepts. Although the interpreter built into the textbook is convenient to use when you are reading the book,
it's important for you to learn to use the Python shell as well, because the shell in some ways is an even better environment
for experimenting with short fragments of Python code to learn what they do.

**Key Terms:** **operator**, **operand**, **expression**, **evaluate**, **function**, **argument**, **int**, **float**

In this section, we'll introduce several important terms. I suggest that you consider writing the definitions
down in your own words in your notes (you're taking notes, right?). You can do this either as you read, or at the
end of the section. 

Meet the Interpreter
--------------------

Let's begin our journey by exploring Python's basic math capabilities. The short video below demonstrates how to use the
Python shell to perform mathematical calculations. If you've installed Python on your computer, follow along with the
video and see if you can repeat in your own computing environment what is being demonstrated in the video. 

.. youtube:: oaq96ILu3sY
    :divid: meetinterpreter
    :height: 315
    :width: 560
    :align: left

Math Expressions
----------------

As demonstrated in the video, you can use Python to perform mathematical computations by entering math expressions
involving operators and operands into the Python shell. **Operators** are symbols that perform computations like
addition, multiplication and division. The values the operator works on are called **operands**.

==========  =========== 
Operator    Description
==========  =========== 
``+``       Addition
``-``       Subtraction
``*``       Multiplication
``/``       Division (``float`` result)
``//``      Division (``int`` result)
``%``       Modulus / Remainder
``**``      Exponentiation
==========  ===========

The operators ``+`` and ``-``, and the use of parenthesis for grouping, mean in Python what they mean in mathematics.
The asterisk (``*``) is the operator for multiplication, slash (``/``) is the usual operator for division, and ``**`` is
the operator for exponentiation (raising a number to a power). There are two operators for division (more on that in a
moment). Addition, subtraction, multiplication, division, and exponentiation all do what you expect. The modulus
operator (``%``) computes the remainder of an integer division; we'll discuss it later in this chapter. 

We call a mathematical computation like ``5 + 3 * 26`` an **expression**. The term *expression* is such an important
concept that I'm going to define it in a box:

.. admonition:: Expression

    An **expression** is a combination of operators and operands that produces a value. 

Python **evaluates** expressions to compute values. When you type an expression into the Python shell, the shell
evaluates the expression by performing the specified operations on the operand values. The evaluation results in a
single value, which is displayed by the shell. For example, the following shows how the shell evaluates the expression
``2 ** 3`` by computing 2\ :sup:`3`, producing the value 8:

.. sourcecode:: python

    >>> 2 ** 3
    8
    >>>

The following are all legal Python expressions::

    20 + 32.5
    2 ** 3
    -2 + 3 * 6
    (2 * (5 + 2)) * (15 - 7)

Python respects the standard order of operations of mathematics; for example, in the expression ``-2 + 3 * 6``,
Python will perform the multiplication first, then the addition. You can use parenthesis to force Python to
perform the operations in a different order.

Try starting the Python shell on your computer and typing the expression above in to see Python compute their values.

.. note::
    I demonstrate how to start the Python shell on a Windows 10 computer in the video at the top of this page.
    
    .. TODO: Demonstrate how to start it on a Mac

If you ask Python to ``print`` an expression, the interpreter **evaluates** the expression and displays the result.
Look at the following program. On paper, write down the values you expect it to display when it runs. Then, run the
program and see if the results match what you think they should. If they don't, re-read the material above.

.. activecode:: ch02_15
    :nocanvas:

    print(2 + 3)
    print(2 - 3)
    print(2 + 4 * 3)
    print(2 ** 3)
    print(3 ** 2)

Expressions must be correctly formed in order for Python to be able to evaluate them. Try deleting one of the 3's from the
example above and note the error that occurs when you attempt to run the faulty program.

.. index::
   division /  //  

Division
--------

Unlike many computer languages, Python provides two operators for division: ``/`` and ``//``. To understand
the difference between them, execute this example:

.. activecode:: meetint_div
    :nocanvas: 

    print(8 / 3)
    print(8 // 3)

The expression ``8 / 3`` yields a number with a fractional amount (approximately ``2.7``), and the expression ``8 // 3``
yields an integer (``2``). Both the ``/`` and the ``//`` operators perform a division. The difference is that
the integer division operator ``//`` performs a division, and then yields an integer result. 
Notice that ``/`` does not round the result to the nearest integer; it drops (or *truncates*) the
fractional portion, leaving just the integer result. 

Now, take a look at the following example:

.. sourcecode:: python

    >>> 8 / 2
    4.0
    >>> 8 // 2
    4
    >>>

This is interesting! The result of dividing 8 by 2 is an integer (``4``). However, the result is expressed differently,
depending on which form of the division operator is used. Keep reading to explore this difference in more depth.

Integer and Floating-Point Calculations
---------------------------------------

Let's look at another example, this time with a different operator:

.. sourcecode:: python

    >>> 2.5 + 2
    4.5
    >>> 2 + 2
    4
    >>> 2.0 + 2.0
    4.0
    >>> 2.0 + 2
    4.0
    >>>

The results of the first two calculations in this example probably come as no surprise. The final calculation is more
interesting, because it demonstrates how Python differentiates between two types of numbers: integers (ex. ``2``), also
called **ints**, and floating-point numbers (ex. ``2.5`` and ``2.0``), also called *floats*. In standard mathematics, there
is no difference between the values ``2`` and ``2.0``. Both represent the same value. However, in Python, the values
``2`` and ``2.0`` are different. They are stored differently internally, and have different capabilities, as we'll see shortly.

In Python, calculations involving only integers always yield an integer result (as long as you stick with integer division).
Calculations involving only floats, or a mixture of floats and integers, always yield a float result. Here are some more
examples to illustrate this point. Look at the examples carefully and take a moment with each to see if you can explain
why each result turned out the way it did:

.. sourcecode:: python

    >>> 1 + 2 * 3
    7
    >>> 1 + 2.0 * 3
    7.0
    >>> 5 // 2
    2
    >>> 5.0 // 2
    2.0
    >>>

The last example is particularly interesting. Perhaps you would have expected the integer division operator to produce
the result ``2``. Here's what happened. The ``//`` operator divided 5 by 2, and then dropped the fractional portion, yielding
the integer 2. However, since the calculation involves a mixture of floats and integers, the result was expressed as a float, not
an int. 

If you found that a little tricky to follow, that's understandable. However, it's important that you grasp that Python
uses very precise rules to determine the outcome of mathematical computations. The rules make sense, once you understand them,
but occasionally the results can surprise you.

Now, let's discuss an important difference between integer and floating-point calculations in Python. Calculations involving
only integers can yield results with extremely high precision. However, calculations involving floating-point numbers
are much more limited in their precision. Try executing the following program:

.. activecode:: meetint_intfloat
    :nocanvas: 

    print(20000 + 1)
    print(20000.0 + 1)
    print(2000000000000000000000 + 1)
    print(2000000000000000000000.0 + 1)

As you can see, both integer calculations produced a completely precise result. However, the second floating
point calculation could not represent the complete result; Python expressed it in scientific notation as 2e+21 
(2 × 10\ :sup:`21`), which is an approximation of the correct result.

So, if you're operating on large numbers and need high amounts of precision, it's important to perform integer
calculations using integer values when possible. Introducing even one float into your calculation causes Python to
switch from integer processing to floating point calculations, which can result in a significant loss of precision. For
the types of programs you will be writing in this course, you won't need highly precise calculations. I'm really
pointing this out to highlight the fact that the difference between integer and floating point data is significant.

.. index::
   argument
   function
   round

Rounding
--------

Recall that integer division operator drops the fractional portion of the result, and does not round. Suppose that you
want the result *rounded* to the nearest integer instead. To do that, you must use the ``round`` function, like this:

.. sourcecode:: python

    >>> round(8 / 3)
    3
    >>>

``round`` is a function that rounds its argument to the nearest integer. A **function** performs a computation on a 
value that you supply in parenthesis, called the **argument**. In this example, the argument is the value that results
from the calculation ``8 / 3``. You could also supply a literal value as the argument to ``round``, like this:

.. sourcecode:: python

    >>> round(2.666665)
    3
    >>>

Here, the argument is the literal value ``2.666665``. 

Functions are similar to the concept of operators that we covered at the beginning of this section. Both perform a
computation on data. One difference between them is that operators are typically special symbols written in between the
values they operate on, while functions are named and operate on values supplied in parenthesis. (However, you'll
eventually meet the boolean operators, which are named.) Another difference involves language extensibility. Operators
are usually built in to the language, and you usually can't add new ones. In contrast, while Python provides several
built-in functions, it also allows programmers to extend the language by creating new ones. 

We'll explore functions in much more depth in a later chapter in this book. For now, note that Python
provides many built-in functions that you can use in your programs to manipulate data in various ways. Later in this
chapter, you will meet more built-in functions. 

Key Terms
---------

Did you take the advice I gave you at the beginning of this chapter about writing down definitions of key terms? If you
haven't, I suggest taking a moment to do it now. These terms will be used a lot in the sections to come, and it is
important that you solidify your understanding of those concepts now before going on. Don't just copy and paste the
definitions into your notes; that will do very little to help you retain them. Write them in your own words. There's a short
:ref:`glossary <fundamentals-glossary>` at the end of this chapter to aid your review.


**Check your understanding**

.. mchoice:: test_question2_6_1
   :practice: T
   :answer_a: 4.5
   :answer_b: 5
   :answer_c: 4
   :answer_d: 2
   :correct: a
   :feedback_a: The / operator does exact division and returns a floating point result.
   :feedback_b: The / operator does exact division and returns a floating point result.
   :feedback_c: The / operator does exact division and returns a floating point result.
   :feedback_d: The / operator does exact division and returns a floating point result.
   
   What value is printed when the following statement executes?

   .. code-block:: python

      print(18 / 4)



.. mchoice:: test_question2_6_2
   :practice: T
   :answer_a: 4.25
   :answer_b: 5
   :answer_c: 4
   :answer_d: 2
   :correct: c
   :feedback_a: - The // operator does integer division and returns an integer result
   :feedback_b: - The // operator does integer division and returns an integer result, but it truncates the result of the division.  It does not round.
   :feedback_c: - The // operator does integer division and returns the truncated integer result.
   :feedback_d: - The // operator does integer division and returns the result of the division on an integer (not the remainder).
   
   What value is printed when the following statement executes?

   .. code-block:: python

      print(18 // 4)


.. mchoice:: test_question2_6_4
   :practice: T
   :answer_a: Illegal calculation
   :answer_b: 9.0
   :answer_c: 9
   :correct: b
   :feedback_a: It is legal to mix ints and floats in a calculation.
   :feedback_b: A calculation with at least one float results in a float.
   :feedback_c: A calculation with at least one float results in a float.

   What value is printed when the following statement executes?

   .. code-block:: python

      print(5 + 2.0 + 2)

