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
like an ``int`` (5) or a ``str`` ("Hello"). The following are all legal Python expressions:

.. sourcecode:: python

    "Hello"
    hour - 1
    len(name)
    round(minute / 60)
    (5 + 9) * (15 - 7)

The relationship between statements and expressions is important to understand.
A statement is not the same thing as an expression. Rather, expressions appear
*inside* statements. Consider the following statements:

.. sourcecode:: python

    print("Hello")
    minutes = tot_seconds // 60
    print("Count is", count)

How many expressions appear in the statements? Can you pick them out? 

If you spotted ``"Hello"``, ``tot_seconds // 60``, ``"Count is"``, and ``count``, way to go! Assignment 
statements and print statements both contain expressions.

Remember the discussion of :ref:`formal languages <formal-and-natural-languages>`? Python has rules of
syntax that you must follow in order for the programs you write to be executed. An assignment statement
has the following syntax:

.. sourcecode:: python

    VARIABLE = EXPRESSION

This notation means that an assignment statement is made up of a variable on the left-hand side and an expression on the
right-hand side. This means that

.. sourcecode:: python

    a = b + 1

is a valid assignment statement, but

.. sourcecode:: python

    b + 1 = a    # Not legal

is not.

A ``print`` statement has the following syntax:

.. sourcecode:: python

    print( [ EXPRESSION ] [ , EXPRESSION... ] )

This syntax rule indicates that the print statement (or, more precisely, the call to the ``print`` function) requires a
list of 0 or more expressions, separated by commas, inside the parenthesis. (In the syntax notation, square brackets
indicate an optional element.)  This means that the following is not allowed:

.. sourcecode:: python

    print( "Count is: " count )   # Illegal

because ``"Count is: " count`` is not a legal expression. The programmer probably intended two expressions,
but omitted the comma that must come between.


**Check your understanding**

.. clickablearea:: stmtexpr_1
    :question: Click on all of the expressions in the code fragment below.
    :iscode:
    :feedback:

    :click-incorrect:print:endclick:( :click-correct:52 * 13:endclick: )
    :click-incorrect:print:endclick:( :click-correct:"The time is":endclick:, :click-correct:current_time:endclick: )
    :click-incorrect:count:endclick: = :click-correct:len( name ):endclick:

    


