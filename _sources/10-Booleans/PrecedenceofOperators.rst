..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: select-3-
   :start: 1

Precedence of Operators
-----------------------

We have now added a number of additional operators to those we learned in the previous chapters.  It is important to understand how these operators relate to the others with respect to operator precedence.  Python will always evaluate the arithmetic operators first (** is highest, then multiplication/division, then addition/subtraction).  Next comes the relational operators.  Finally, the logical operators are done last.  This means that the expression ``x*5 >= 10 and y-6 <= 20`` will be evaluated so as to first perform the arithmetic and then check the relationships.  The ``and`` will be done last.  Although many programmers might place parenthesis around the two relational expressions, it is not necessary.

The following table summarizes the precedence discussed so far from highest to lowest.  
See :ref:`operator-summary` for *all* the operators introduced in this book.

=======   ==============  ===============
Level     Category        Operators
=======   ==============  ===============
7(high)   exponent        \**
6         multiplication  \*,/,//,%
5         addition        +,-
4         relational      ==,!=,<=,>=,>,<
3         logical         not
2         logical         and
1(low)    logical         or
=======   ==============  ===============

To understand how to apply this precedence chart to boolean operators, consider the following print statement::

   print(a < 3 or not c == 8 and b == 2)

To figure out how Python will process a complicated expression like this, it helps to fully parenthesize it, following
the order specified by the precedence chart. So, you would begin by putting parenthesis around the individual relational
comparisons, all of which have a higher precedence than any of the boolean operators::

   print((a < 3) or not (c == 8) and (b == 2))

Next, tackle the boolean operators.  ``not`` has the highest precedence::

   print((a < 3) or (not (c == 8)) and (b == 2))

... followed by ``and``::

   print((a < 3) or ((not (c == 8)) and (b == 2)))

This fully-parenthesized print statement is equivalent to the original. 

Now, you can work  your way through the parenthesis and evaluate each part as you go. Click **Next Step** repeatedly
to see how Python will do this, step by step, given the values of the variables as follows::

   a = 3
   b = 2
   c = 10

.. showeval:: se_boolprec
   :trace_mode: true

   print(a < 3 or not c == 8 and b == 2)
   ~~~~
   print({{a < 3}}{{False}} or not c == 8 and b == 2)
   print(False or not {{c == 8}}{{False}} and b == 2)
   print(False or not False and {{b == 2}}{{True}})
   print(False or {{not False}}{{True}} and True)
   print(False or {{True and True}}{{True}})
   print({{False or True}}{{True}})




**Check your understanding**

.. mchoice:: test_question6_3_1
   :practice: T
   :answer_a: ((5*3) &gt; 10) and ((4+6) == 11)
   :answer_b: (5*(3 &gt; 10)) and (4 + (6 == 11))
   :answer_c: ((((5*3) &gt; 10) and 4)+6) == 11
   :answer_d: ((5*3) &gt; (10 and (4+6))) == 11
   :correct: a
   :feedback_a: Yes, * and + have higher precedence, followed by &gt; and ==, and then the keyword &quot;and&quot;
   :feedback_b: Arithmetic operators (*, +) have higher precedence than comparison operators (&gt;, ==)
   :feedback_c: This grouping assumes Python simply evaluates from left to right, which is incorrect.  It follows the precedence listed in the table in this section.
   :feedback_d: This grouping assumes that &quot;and&quot; has a higher precedence than ==, which is not true. 

   Which of the following properly expresses the precedence of operators (using parentheses) in the following expression: 5*3 > 10 and 4+6==11

Here is an animation for the above expression:

.. showeval:: se_tq631
   :trace_mode: true

   5 * 3 > 10 and 4 + 6 == 11
   ~~~~
   {{5 * 3}}{{15}} > 10 and 4 + 6 == 11
   {{15 > 10}}{{True}} and 4 + 6 == 11
   True and {{4 + 6}}{{10}} == 11
   True and {{10 == 11}}{{False}}
   {{True and False}}{{False}}


.. mchoice:: test_question6_3_2
   :practice: T

   Consider the following::
   
      x = 3
      y = 8
      count = 2
      
      print(x < 5 or y > 10 and not count == 0)

   Which of the following fully-parenthesized statements is equivalent to the print statement above?

   - print(x < (5 or y) > 10 and (not count) == 0)

     - Incorrect. ``or`` has lower precedence than ``<``.

   - print(((x < 5) or (y > 10)) and (not count == 0))

     - Incorrect. ``or`` has lower precedence than ``and``.

   - print((x < 5) or ((y > 10) and (not (count == 0))))

     + Correct!

.. mchoice:: test_question6_3_3
   :practice: T

   Consider the following::
   
      x = 3
      y = 8
      count = 2
      
      print(x > 5 or y < 10 and not count == 0)

   Give the output of this code fragment.

   - True

     + Correct!

   - False

     - Incorrect. 

Here is an animation for the above expression:

.. showeval:: se_tq632
   :trace_mode: true

   x > 5 or y < 10 and not count == 0
   ~~~~
   {{x > 5}}{{False}} or y < 10 and not count == 0
   False or {{y < 10}}{{True}} and not count == 0
   False or True and not {{count == 0}}{{False}}
   False or True and {{not False}}{{True}}
   False or {{True and True}}{{True}}
   {{False or True}}{{True}}
