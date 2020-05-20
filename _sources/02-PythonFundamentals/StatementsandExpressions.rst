..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-6-
   :start: 1

.. index:: statement, function call statement, expression

Statements and Expressions
--------------------------

A **statement** is an instruction that the Python interpreter can execute. So far,
we have seen two types of statements: assignment statements, and print
statements. The print statement is actually a specific example of a more general
type of statement called a **function call statement**. We'll see several other
types of statements in later chapters.

An **expression** is a combination of values, variables, operators, and calls
to functions that yields a value. An expression can be as simple as a literal value,
like an ``int`` (5) or a ``str`` ("Hello"). The following are all legal Python expressions::

    "Hello"
    hour - 1
    len(name)
    round(minute / 60)
    (5 + 9) * (15 - 7)

The relationship between statements and expressions is important to understand.
A statement is not the same thing as an expression. Rather, statements *contain*
expressions. Consider the following statements:

.. sourcecode:: python

    print("Hello")
    minutes = tot_seconds // 60
    print("Count is", count)

How many expressions appear in the statements? Can you pick them out? 

If you spotted ``"Hello"``, ``tot_seconds // 60``, ``"Count is"``, and ``count``, way to go! Assignment 
statements and print statements both contain expressions.

.. clickablearea:: stmtexpr_1
    :question: Click on all of the expressions in the code fragment below.
    :iscode:
    :feedback:

    :click-incorrect:print:endclick:( :click-correct:52 * 13:endclick: )
    :click-incorrect:print:endclick:( :click-correct:"The time is":endclick:, :click-correct:current_time:endclick: )
    :click-incorrect:count:endclick: = :click-correct:len( name ):endclick:
    

Python Syntax
^^^^^^^^^^^^^

Remember the discussion of :ref:`formal languages <formal-and-natural-languages>`? Python has rules of
syntax that you must follow in order for the programs you write to be executed. An assignment statement
has the following syntax:

.. sourcecode:: python

    VARIABLE = EXPRESSION

This notation means that an assignment statement is made up of a single variable on the left-hand side and an expression
on the right-hand side. This means that

.. sourcecode:: python

    a = b + 1

is a valid assignment statement, but

.. sourcecode:: python

    b + 1 = a    # Not legal

is not, because ``b + 1`` is not a single variable.

A ``print`` statement has the following syntax:

.. sourcecode:: python

    print( [ EXPRESSION ] [ , EXPRESSION... ] )

This syntax rule indicates that the print statement (or, more precisely, the call to the ``print`` function) requires a
list of 0 or more expressions, separated by commas, inside the parenthesis. (In the syntax notation used here, square
brackets indicate an optional element.)  This means that the following is not allowed:

.. sourcecode:: python

    print( "Count is: " count )   # Illegal

because ``"Count is: " count`` is not a legal expression. The programmer probably intended two expressions,
but omitted the comma that must come between.

Understanding Python's rules of syntax is important, because it helps you write programs correctly,
and avoid unnecessary errors.

Expressions and Data Types
^^^^^^^^^^^^^^^^^^^^^^^^^^

One of the skills you must develop to be an effective programmer is the ability to determine what a program (or a
portion of a program) will do without actually running it. Like reading a passage of English and being able answer
questions about its meaning, you must be able to mentally execute lines of Python code in your mind and predict what the
computer will do when it executes a given line, based on your knowledge of the Python language. This skill is vital
to your ability to find and correct defects in a programs written by yourself and others.

Recall that every expression evaluates to a value, and that value belongs to a particular data type. As part of the
overall skill of reading and understanding Python programs, you should be able to look at an expression and figure out
both the value that it produces when evaluated, as well as the data type of that value. In this chapter, you've seen
several examples of expressions. Let's take a moment as we wrap up this chapter for you to practice just that.

.. dragndrop:: stmtexpr_2
   :match_1: b + 5|||float
   :match_2: 4 * int(c)|||int
   :match_4: "c is " + c|||str
   :match_3: "a is " + a|||illegal expression

   Determine the data type of each of the expressions on the left
   given the values of the following variables, and 
   drag them to the correct data type on the right: a = 4;
   b = 10.0; c = '13'

.. dragndrop:: stmtexpr_3
   :match_1: a / 2|||float
   :match_2: int(b) + 5|||int
   :match_4: "a is " + str(a)|||str
   :match_3: a + c|||illegal expression

   Determine the data type of each of the expressions on the left
   given the values of the following variables, and 
   drag them to the correct data type on the right: a = 4;
   b = 10.0; c = '13'



