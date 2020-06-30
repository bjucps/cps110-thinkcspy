..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: select-4-
   :start: 1

.. index:: heading, body, selection, if, else, pass, compound statement, conditional statement
   statement; if
   statement; pass
   comparison; numbers
   single:  <; numbers
   single:  <=; numbers
   single:  >; numbers
   single:  >=; numbers
   single:  ==; numbers
   single:  !=; numbers


The ``if`` Statement
====================

.. youtube:: _sTOMb-40RY
    :divid: vid_ifstmt
    :height: 315
    :width: 560
    :align: left

.. videonotes: Explain if statement using simple x is zero / x is not zero example

In order to write useful programs, we almost always need the ability to check
conditions and change the behavior of the program accordingly. **Selection statements**, sometimes
also referred to as **conditional statements**, give us this ability. In Python, the **if statement**
is the only selection statement. Other languages have a wider variety of selection statements.

The following example asks the user for an integer, and tells the user
whether the integer is even or odd using an ``if`` statement.

.. activecode:: ch05_4

    x = int(input('Enter an integer:'))

    if x % 2 == 0:
        print(x, "is even")
    else:
        print(x, "is odd")


This example works by using the modulus operator to compute the remainder of a division by 2. The program compares the
result of the modulus operation with the number ``0``; if the two values are equal, the program concludes that the number is even;
otherwise, it must be odd.

An ``if`` statement has the following form:

.. sourcecode:: python

    if CONDITION:
        STATEMENTS_1        # executed if condition evaluates to True
    else:
        STATEMENTS_2        # executed if condition evaluates to False

As with other compound statements like ``for``, the ``if`` statement consists of a header line and a body. The header
line begins with the keyword ``if`` followed by a boolean *CONDITION* and ends with a colon (:). Each of the statements
inside the first block of statements is executed in order if the boolean expression evaluates to ``True``. The entire
first block of statements is skipped if the boolean expression evaluates to ``False``, and instead all the statements
under the ``else`` clause are executed. Since there are two possible paths of execution, the ``if`` statement performs what is
called **binary selection**.

There is no limit on the number of statements that can appear under the two clauses of an
``if`` statement, but there has to be at least one statement in each block.

Here's a flowchart that shows how the flow branches to execute either STATEMENTS_1
or STATEMENTS_2, depending on the outcome of the condition:

.. image:: Figures/flowchart_if_else.png

Comparison Operators
--------------------

The equality operator used in the example above, ``==``, compares two values and produces the value **True** if they are
equal, and **False** if they are not. The ``==`` operator is one of six common **comparison operators**; the others are:

.. sourcecode:: python

    x != y               # x is not equal to y
    x > y                # x is greater than y
    x < y                # x is less than y
    x >= y               # x is greater than or equal to y
    x <= y               # x is less than or equal to y

Although these operations are probably familiar to you, the Python symbols are
different from the mathematical symbols. A common error is to use a single
equal sign (``=``) instead of a double equal sign (``==``). Remember that ``=``
is an assignment operator and ``==`` is a comparison operator. Also, there is
no such thing as ``=<`` or ``=>``.

Omitting the `else` Clause: Unary Selection
-------------------------------------------

The ``else`` clause can be omitted from ``if`` statements. This creates what is sometimes called **unary selection**.
In this case, when the condition evaluates to ``True``, the statements are
executed.  Otherwise the flow of execution continues to the statement after the body of the ``if``.

.. activecode:: ch05_unaryselection

    x = 10
    if x < 0:
        print("The negative number ",  x, " is not valid here.")
    print("This is always printed")


What would be printed if the value of ``x`` is negative?  Try it.

Here is a flowchart that depicts how the the if statement works if the else clause is omitted:

.. image:: Figures/flowchart_if_only.png


.. admonition:: Optional Lab

    * `Approximating Pi with Simulation <../Labs/montepi.html>`_ In this guided lab exercise we will work
      through a problem solving exercise related to approximating the value of pi using random numbers.


**Check your understanding**

.. mchoice:: test_question6_4_1
   :practice: T
   :answer_a: Just one.
   :answer_b: Zero or more.
   :answer_c: One or more.
   :answer_d: One or more, and each must contain the same number.
   :correct: c
   :feedback_a: Each block may also contain more than one.
   :feedback_b: Each block must contain at least one statement.
   :feedback_c: Yes, a block must contain at least one statement and can have many statements.
   :feedback_d: The blocks may contain different numbers of statements.

   How many statements can appear in each block (the if and the else) in a conditional statement?

.. mchoice:: test_question6_4_2
   :practice: T
   :answer_a: TRUE
   :answer_b: FALSE
   :answer_c: TRUE on one line and FALSE on the next
   :answer_d: Nothing will be printed
   :correct: b
   :feedback_a: TRUE is printed by the if-block, which only executes if the conditional (in this case, 4+5 == 10) is true.  In this case 5+4 is not equal to 10.
   :feedback_b: Since 4+5==10 evaluates to False, Python will skip over the if block and execute the statement in the else block.
   :feedback_c: Python would never print both TRUE and FALSE because it will only execute one of the if-block or the else-block, but not both.
   :feedback_d: Python will always execute either the if-block (if the condition is true) or the else-block (if the condition is false).  It would never skip over both blocks.

   What does the following code print (choose from output a, b, c or nothing)?

   .. code-block:: python

     if 4 + 5 == 10:
         print("TRUE")
     else:
         print("FALSE")


.. mchoice:: test_question6_4_3
   :practice: T
   :answer_a: Output a
   :answer_b: Output b
   :answer_c: Output c
   :answer_d: Output d
   :correct: c
   :feedback_a: Although TRUE is printed after the if-else statement completes, both blocks within the if-else statement print something too.  In this case, Python would have had to have skipped both blocks in the if-else statement, which it never would do.
   :feedback_b: Because there is a TRUE printed after the if-else statement ends, Python will always print TRUE as the last statement.
   :feedback_c: Python will print FALSE from within the else-block (because 5+4 does not equal 10), and then print TRUE after the if-else statement completes.
   :feedback_d: To print these three lines, Python would have to execute both blocks in the if-else statement, which it can never do.

   What does the following code print?

   .. code-block:: python

     if 4 + 5 == 10:
         print("TRUE")
     else:
         print("FALSE")
     print("TRUE")

   ::

      a. TRUE

      b.
         TRUE
         FALSE

      c.
         FALSE
         TRUE
      d.
         TRUE
         FALSE
         TRUE


.. mchoice:: test_question6_5_1
   :practice: T
   :answer_a: Output a
   :answer_b: Output b
   :answer_c: Output c
   :answer_d: It will cause an error because every if must have an else clause.
   :correct: b
   :feedback_a: Because -10 is less than 0, Python will execute the body of the if-statement here.
   :feedback_b: Python executes the body of the if-block as well as the statement that follows the if-block.
   :feedback_c: Python will also execute the statement that follows the if-block (because it is not enclosed in an else-block, but rather just a normal statement).
   :feedback_d: It is valid to have an if-block without a corresponding else-block (though you cannot have an else-block without a corresponding if-block).

   What does the following code print?

   .. code-block:: python

     x = -10
     if x < 0:
         print("The negative number ",  x, " is not valid here.")
     print("This is always printed")

   ::

     a.
     This is always printed

     b.
     The negative number -10 is not valid here
     This is always printed

     c.
     The negative number -10 is not valid here


.. mchoice:: test_question6_5_2
   :practice: T
   :answer_a: No
   :answer_b: Yes
   :correct: b
   :feedback_a: Every else-block must have exactly one corresponding if-block.  If you want to chain if-else statements together, you must use the else if construct, described in the chained conditionals section.
   :feedback_b: This will cause an error because the second else-block is not attached to a corresponding if-block.

   Will the following code cause an error?

   .. code-block:: python

     x = -10
     if x < 0:
         print("The negative number ",  x, " is not valid here.")
     else:
         print(x, " is a positive number")
     else:
         print("This is always printed")

