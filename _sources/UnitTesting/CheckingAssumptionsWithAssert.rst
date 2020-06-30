..  Copyright (C)  Stephen Schaub.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


Checking Assumptions With ``assert``
=====================================

.. index:: assert

Checking Preconditions 
----------------------




Python provides a statement called ``assert``.

- Following the word assert there will be a python expression.
- If that expression evaluates to the Boolean ``False``, then the interpreter will raise a runtime error.
- If the expression evaluates to ``True``, then nothing happens and the execution goes on to the next line of code.

Why would you ever want to write a line of code that can never compute anything useful for you, but sometimes causes a runtime error? For all the reasons we described above about the value of automated tests. You want a test that will alert that you that some condition you assumed was true is not in fact true. It's much better to be alerted to that fact right away than to have some unexpected result much later in your program execution, which you will have trouble tracing to the place where you had an error in your code.

Why doesn't ``assert`` print out something saying that the test passed? The reason is that you don't want to clutter up your output window with the results of automated tests that pass. You just want to know when one of your tests fails. In larger projects, other testing harnesses are used instead of ``assert``, such as the python ``unittest`` module. Those provide some output summarizing tests that have passed as well as those that failed. In this textbook, we will just use simple ``assert`` statements for automated tests.

To write a test, we must know what we *expect* some value to be at a particular point in the program's execution. In the rest of the chapter, we'll see some examples of ``assert`` statements and ideas for what kinds of assertions one might want to add in one's programs.



Checking Types
--------------

Unlike some other programming languages, the Python interpreter does not enforce restrictions about the data types of
objects that can be bound to particular variables. For example, in Java, before assigning a value to a variable, the
program would include a declaration of what type of value (integer, float, Boolean, etc.) that the variable is allowed
to hold. The variable ``x`` in a python program can be bound to an integer at one point and to a list at some other
point in the program execution.

That flexibility makes it easier to get started with programming in Python. Sometimes, however, type checking could
alert us that something has gone wrong in our program execution. For example, consider the following function:

