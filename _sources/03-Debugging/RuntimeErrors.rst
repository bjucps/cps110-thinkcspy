..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: intro-8-
   :start: 1

.. index:: error;runtime, runtime error

Runtime Errors
--------------

The second type of error is a **runtime error**. A program with a runtime error
is one that passed the interpreter's syntax checks, and started to execute.
However, during the execution of one of the statements in the program, an error
occurred that caused the interpreter to stop executing the program and display
an error message. Runtime errors are also called **exceptions** because they usually 
indicate that something exceptional (and bad) has happened.

The following program contains a runtime error. Can you spot the problem?
After locating the error, run the program to see the error message.

.. activecode:: debug_rterr

    subtotal = input("Enter total before tax:")
    tax = .08 * subTotal
    print("tax on", subtotal, "is:", tax)

The interpreter displays the following error::

   NameError: name 'subTotal' is not defined on line 2

A ``NameError`` is an example of a runtime error. The problem is that the variable ``subtotal``
is capitalized differently on line 2 than it is on line 1, and to Python, two variables that are
spelled the same but capitalized differently are different variables. The interpreter thinks that
you are trying to use a variable to which you haven't yet assigned a value, and that is illegal.
You'll also encounter a ``NameError`` when you misspell a function name, like typing ``prnt`` instead of
``print``. When you see a ``NameError``, you should think to yourself: "Oh, I misspelled something!"
and double-check your spelling and capitalization of variables or functions.

Fix the problem by changing the variable name on line 2 to ``subtotal``, to match line 1. Then, run
the program again. This time you should see a different error::

   TypeError: can't multiply sequence by non-int of type 'float' on line 2

A ``TypeError`` is an example of a runtime error that occurs when you attempt to perform operation on a value that is
the wrong data type. Take a moment to identify and correct the problem. Ask for a tip if you need one:

.. reveal:: rte_typetip
   :showtitle: Give me a tip
   :modal:
   :modalTitle: Here's a tip!

   Remember that ``input`` returns string data. Line 2 is attempting to multiply a float (``.08``) with a string (the
   value in ``subtotal``). Modify either line 1 or line 2 to use the ``float`` type conversion function. 
   
   If you need a refresher on how to do this, see the previous sections on :ref:`input` or :ref:`type-conversion`.

A third type of runtime error that you are likely to encounter is a ``ValueError``. To see this in action, after
you've corrected the program above, run it and type in the value ``abc``. You should see a message
similar to the following::

   ValueError: could not convert string to float: 'abc' on line 2

A ``ValueError`` occurs when the value of a variable has the correct data type, but is outside of the legal set of values
required by the operation. In this situation, the ``float`` function is attempting to convert string data to a float.
The data type (``str``) is correct, but the value of that data (``abc``) is not a sequence of symbols that can be converted
to a float.

Notice the following important differences between syntax errors and runtime errors that can help you as you try to diagnose
and repair the problem:

1. If the error message mentions ``SyntaxError``, you know that the problem has to do with syntax: the structure of the code,
   the punctuation, etc.

2. If the program runs partway and then crashes, you know the problem is a runtime error. Programs with syntax errors
   don't execute even one line.



**Check your understanding**

.. mchoice:: question1_7_1
   :practice: T
   :answer_a: Attempting to divide by 0.
   :answer_b: Forgetting a colon at the end of a statement where one is required.
   :answer_c: Forgetting to divide by 100 when printing a percentage amount.
   :correct: a
   :feedback_a: Python cannot reliably tell if you are trying to divide by 0 until it is executing your program (e.g., you might be asking the user for a value and then dividing by that value - you cannot know what value the user will enter before you run the program).
   :feedback_b: This is a problem with the formal structure of the program.  Python knows where colons are required and can detect when one is missing simply by looking at the code without running it.
   :feedback_c: This will produce the wrong answer, but Python will not consider it an error at all.  The programmer is the one who understands that the answer produced is wrong.

   Which of the following is a run-time error?



