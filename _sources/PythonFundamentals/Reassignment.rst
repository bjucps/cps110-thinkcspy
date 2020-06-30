..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-10-
   :start: 1

Reassignment
------------

We use variables in a program to "remember" things, like the current score at
the football game.  But variables are *variable*. This means they can change
over time, just like the scoreboard at a football game.  You can assign a value
to a variable, and later assign a different value to the same variable.

.. note::

    This is different from math. In math, if you give `x` the value 3, it
    cannot change to refer to a different value half-way through your
    calculations!

To see this, read and then run the following program.
You'll notice we change the value of `day` three times, and on the third
assignment we even give it a value that is of a different type.


.. codelens:: ch02_11
    :showoutput:

    day = "Thursday"
    day = "Friday"
    day = 21
    print(day)

A great deal of programming is about having the computer remember things.  For example, we might want to keep
track of the number of missed calls on your phone.  Each time another call is missed, we will arrange to update
or change the variable so that it will always reflect the correct value.

As we have mentioned previously, it is legal to make more than one assignment to the
same variable. A new assignment makes an existing variable refer to a new value
(and stop referring to the old value).

.. activecode:: ch07_reassign1

    bruce = 5
    print(bruce)
    bruce = 7
    print(bruce)


The first time ``bruce`` is
printed, its value is 5, and the second time, its value is 7.  The assignment statement changes
the value (the object) that ``bruce`` refers to.

Here is what **reassignment** looks like in a reference diagram:

.. image:: Figures/reassign1.png
   :alt: reassignment

It is important to note that in mathematics, a statement of equality is always true.  If ``a is equal to b``
now, then ``a will always equal to b``. In Python, an assignment statement can make
two variables refer to the same object and therefore have the same value.  They appear to be equal.  However, because of the possibility of reassignment,
they don't have to stay that way:

.. activecode:: ch07_reassign2

    a = 5
    b = a    # after executing this line, a and b are now equal
    print(a, b)
    a = 3    # after executing this line, a and b are no longer equal
    print(a, b)

Line 4 changes the value of ``a`` but does not change the value of
``b``, so they are no longer equal. We will have much more to say about equality in a later chapter.

Updating Variables
^^^^^^^^^^^^^^^^^^

One of the most common forms of reassignment is an **update** where the new
value of the variable depends on the old.  For example,

.. sourcecode:: python

    x = x + 1

This means get the current value of x, add one, and then update x with the new
value.  The new value of x is the old value of x plus 1.  Although this assignment statement may
look a bit strange, remember that executing assignment is a two-step process.  First, evaluate the
right-hand side expression.  Second, let the variable name on the left-hand side refer to this new
resulting object.  The fact that ``x`` appears on both sides does not matter.  The semantics of the assignment
statement makes sure that there is no confusion as to the result.  The visualizer makes this very clear.

.. showeval:: se_updatevar1
   :trace_mode: true

   x = 6
   x = x + 1
   ~~~~
   x = {{x}}{{6}} + 1
   x = {{6 + 1}}{{7}}


.. activecode:: ch07_update1

    x = 6        # initialize x
    print(x)
    x = x + 1    # update x
    print(x)


If you try to update a variable that doesn't exist, you get an error because
Python evaluates the expression on the right side of the assignment operator
before it assigns the resulting value to the name on the left.
Before you can update a variable, you have to **initialize** it, usually with a
simple assignment.  In the above example, ``x`` was initialized to 6.

Updating a variable by adding 1 is called an **increment**; subtracting 1 is
called a **decrement**.  Sometimes programmers also talk about **bumping**
a variable, which means the same as incrementing it by 1. Incrementing and
decrementing are such common operations that Python provides a shortcut. Instead of
writing::

    x = x + 1

you can write the following, which does the same thing::

    x += 1

Similarly instead of writing::

    x = x - 3

you can write::

    x -= 3

Similar shortcuts are available for multiplication and division::

    x *= 3  # Multiplies x by 3 
    y /= 2  # Divides ``y`` by 2


**Check your understanding**

.. mchoice:: test_question2_3_2
   :practice: T
   :answer_a: Nothing is printed. A runtime error occurs.
   :answer_b: Thursday
   :answer_c: 32.5
   :answer_d: 19
   :correct: d
   :feedback_a: It is legal to change the type of data that a variable holds in Python.
   :feedback_b: This is the first value assigned to the variable day, but the next statements reassign that variable to new values.
   :feedback_c: This is the second value assigned to the variable day, but the next statement reassigns that variable to a new value.
   :feedback_d: The variable day will contain the last value assigned to it when it is printed.

   What is printed when the following statements execute?

   .. code-block:: python

     day = "Thursday"
     day = 32.5
     day = 19
     print(day)

.. mchoice:: test_question2_9_1
   :practice: T
   :answer_a: x is 15 and y is 15
   :answer_b: x is 22 and y is 22
   :answer_c: x is 15 and y is 22
   :answer_d: x is 22 and y is 15
   :correct: d
   :feedback_a: Look at the last assignment statement which gives x a different value.
   :feedback_b: No, x and y are two separate variables.  Just because x changes in the last assignment statement, it does not change the value that was copied into y in the second statement.
   :feedback_c: Look at the last assignment statement, which reassigns x, and not y.
   :feedback_d: Yes, x has the value 22 and y the value 15.


   After the following statements, what are the values of x and y?

   .. code-block:: python

     x = 15
     y = x
     x = 22

.. mchoice:: test_question2_10_1
   :practice: T
   :answer_a: 12
   :answer_b: -1
   :answer_c: 11
   :answer_d: Nothing.  An error occurs because x can never be equal to x - 1.
   :correct: c
   :feedback_a: The value of x changes in the second statement.
   :feedback_b: In the second statement, substitute the current value of x before subtracting 1.
   :feedback_c: Yes, this statement sets the value of x equal to the current value minus 1.
   :feedback_d: Remember that variables in Python are different from variables in math in that they (temporarily) hold values, but can be reassigned.


   What is printed when the following statements execute?

   .. code-block:: python

     x = 12
     x = x - 1
     print(x)

.. mchoice:: test_question2_10_2
   :practice: T
   :answer_a: 12
   :answer_b: 9
   :answer_c: 15
   :answer_d: Nothing.  An error occurs because x cannot be used that many times in assignment statements.
   :correct: c
   :feedback_a: The value of x changes in the second statement.
   :feedback_b: Each statement changes the value of x, so 9 is not the final result.
   :feedback_c: Yes, starting with 12, subtract 3, than add 5, and finally add 1.
   :feedback_d: Remember that variables in Python are different from variables in math in that they (temporarily) hold values, but can be reassigned.


   What is printed when the following statements execute?

   .. code-block:: python

     x = 12
     x = x - 3
     x = x + 5
     x = x + 1
     print(x)

.. parsonsprob:: question2_10_3

   Construct the code that will result in the value 134 being printed.
   -----
   mybankbalance = 100
   mybankbalance = mybankbalance + 34
   print(mybankbalance)

.. mchoice:: test_question2_10_4
   :practice: T
   :answer_a: 12
   :answer_b: 3
   :answer_c: 36
   :answer_d: Nothing.  An error occurs because this is not a legal program.
   :correct: c
   :feedback_a: The value of x changes in the second statement.
   :feedback_b: No, ``x *= 3`` is different from ``x = 3``.
   :feedback_c: Yes, this is a shortcut for writing ``x = x * 3``.
   :feedback_d: No, this is legal code. Review the information above.

   What is printed when the following statements execute?

   .. code-block:: python

     x = 12
     x *= 3
     print(x)   