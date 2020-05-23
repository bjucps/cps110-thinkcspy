..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: select-1-
   :start: 1

.. index:: True, False, boolean value


Boolean Values and Boolean Expressions
--------------------------------------

.. youtube:: LD-F4RODy-I
    :divid: booleanexpressions
    :height: 315
    :width: 560
    :align: left

The Python type for storing true and false values is called ``bool``, named
after the British mathematician, George Boole. George Boole created *Boolean
Algebra*, which is the basis of all modern computer arithmetic.

There are only two **boolean values**.  They are ``True`` and ``False``.  Capitalization
is important, since ``true`` and ``false`` are not boolean values (remember Python is case
sensitive).

.. activecode:: ch05_1

    print(True, "has type", type(True))
    print(False, "has type", type(False))
    print('"False" has type', type("False"))

.. note:: Boolean values are not strings!

    It is extremely important to realize that True and False are not strings.   They are not
    surrounded by quotes.  They are the only two values in the data type ``bool``.  Take a close look at the
    difference in the last two lines of output above.

A **boolean expression** is an expression that evaluates to a boolean value. We've already seen
boolean expressions using the comparison operators ``==``, ``!=``, ``<``, and so on,
in ``if`` statements. For example, in the following statement::

    if x < 5:

``x < 5`` is a boolean expression. You can use boolean expressions outside of ``if`` statements,
as in the following example:

.. activecode:: ch05_2

    print(5 == 5)
    print(5 == 6)

    x = (3 > 7)
    print('x is', x)

In the first statement, the two operands are equal, so the expression evaluates
to ``True``.  In the second statement, 5 is not equal to 6, so we get ``False``.

Next, the example evaluates the expression ``3 > 7``, assigns the resulting 
value to ``x``, and displays the result.

Flag Variables
^^^^^^^^^^^^^^

Boolean variables are useful as flags. A **flag** is a variable that has only two possible values during the
execution of the program. Here's a program we encountered in an earlier chapter, written before we had covered boolean variables. The
``valid_input`` variable is a flag, because it is assigned only two different values during the execution of the
program. In the original version, we used the values 0 and 1. In this version, we've rewritten it to use boolean values
to make the intent clearer.

.. activecode:: ch07_validation_flag
    :timelimit: 60000

    valid_input = False
    while valid_input == False:
        response = input('Do you like lima beans? Y)es or N)o: ')
        response = response.upper()
        if response == 'Y':
            valid_input = True
        elif response == 'N':
            valid_input = True
        else:
            print('Please enter Y for yes or N for no.')

    if response == 'Y':
        print('Great! They are very healthy.')
    else:
        print('Too bad. If cooked right, they are quite tasty.')


**Check your understanding**

.. mchoice:: test_question6_1_1
   :practice: T
   :multiple_answers:
   :answer_a: True
   :answer_b: 3 == 4
   :answer_c: 3 + 4
   :answer_d: 3 + 4 == 7
   :answer_e: &quot;False&quot;
   :correct: a,b,d
   :feedback_a: True and False are both Boolean literals.
   :feedback_b: The comparison between two numbers via == results in either True or False (in this case False),  both Boolean values.
   :feedback_c:  3 + 4 evaluates to 7, which is a number, not a Boolean value.
   :feedback_d: 3 + 4 evaluates to 7.  7 == 7 then evaluates to True, which is a Boolean value.
   :feedback_e: With the double quotes surrounding it, False is interpreted as a string, not a Boolean value.  If the quotes had not been included, False alone is in fact a Boolean value.

   Which of the following is a Boolean expression?  Select all that apply.
