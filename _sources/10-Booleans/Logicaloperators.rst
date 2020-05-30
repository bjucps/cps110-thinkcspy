..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: select-2-
   :start: 1

.. index::logical operator
   operator; logical
   single: and 
   single: or
   single: not


Logical operators
-----------------

There are three **logical operators**: ``and``, ``or``, and ``not``. The
All three operators take boolean operands and produce boolean values. 
The semantics (meaning) of these operators is similar to their meaning in English:

* ``x and y`` is True if both ``x`` and ``y`` are True. Otherwise, ``and`` produces False.
* ``x or y`` yields True if either ``x`` or ``y`` is True. Only if both operands are False
  does ``or`` yield False.
* ``not x`` yields False if ``x`` is True, and vice versa.

Try out the following example:

.. activecode:: logop_ex1

   x = True
   y = False
   print(x or y)
   print(x and y)
   print(not x)

Although you can use boolean operators with simple boolean literals or variables as in the above
example, they are often combined with the comparison operators, like this:

.. activecode:: chp05_3

    x = 5
    print(x > 0 and x < 10)

    n = 25
    print(n % 2 == 0 or n % 3 == 0)


For example, ``x > 0 and x < 10`` is True only if ``x`` is greater than 0 *and*
at the same time, x is less than 10.  In other words, this expression is True if 
x is between 0 and 10, not including the endpoints.


.. admonition:: Common Mistake!

   There is a very common mistake that occurs when programmers try to write boolean expressions.  For example, what if
   we have a variable ``number`` and we want to check to see if its value is 5 or 6.  In words we might say: "number
   equal to 5 or 6".  However, if we translate this into Python, ``number == 5 or 6``, it will not yield correct
   results. The ``or`` operator must have a complete equality check on both sides.  The correct way to write this is 
   ``number == 5 or number == 6``. Remember that both operands of ``or`` must be booleans in order to yield proper results.


**Check your understanding**

.. mchoice:: test_question6_2_1
   :practice: T
   :answer_a: x &gt; 0 and &lt; 5
   :answer_b: x &gt; 0 or x &lt; 5
   :answer_c: x &gt; 0 and x &lt; 5
   :correct: c
   :feedback_a: Each comparison must be between exactly two values.  In this case the right-hand expression &lt; 5 lacks a value on its left.
   :feedback_b: Although this is legal Python syntax, the expression is incorrect.  It will evaluate to true for all numbers that are either greater than 0 or less than 5.  Because all numbers are either greater than 0 or less than 5, this expression will always be True.
   :feedback_c: Yes, with an and keyword both expressions must be true so the number must be greater than 0 an less than 5 for this expression to be true. Although most other programming languages do not allow this mathematical syntax, in Python, you could also write 0 &lt; x &lt; 5.

   What is a correct Python expression for checking to see if a number stored in a variable x is between 0 and 5?



