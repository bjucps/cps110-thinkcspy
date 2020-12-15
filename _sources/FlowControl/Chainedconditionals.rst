..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: select-7-
   :start: 1

.. index::
   single: chained conditional
   single: conditional; chained

Chained conditionals
====================

A basic ``if`` statement tests a single condition and determines which of two alternative actions to take
based on the outcome. But sometimes a program needs to choose from more than two alternative actions.
The program presented in the previous section is a good example. It displayed one of three possible outputs,
based on the relationship of x and y.

The program in the previous section used a nested if statement to get the job done. However, when exactly one
of multiple alternative actions should be taken, Python provides the ``elif`` ("else if") keyword to simplify the 
code required. Take a look at the following alternative version of the program presented in the previous section. 
This one uses an ``if-elif-else`` sequence to do the job.

.. activecode:: sel4

    x = 10
    y = 10

    if x < y:
        print("x is less than y")
    elif x > y:
        print("x is greater than y")
    else:
        print("x and y must be equal")

Take a moment to compare these two versions of the program  to the version from the previous section, shown below:

.. sourcecode:: python

    Nested Conditionals                                 Chained Conditionals
    ---------------------------------------             -----------------------------------
    if x < y:                                           if x < y:
        print("x is less than y")                           print("x is less than y")
    else:                                               elif x > y:
        if x > y:                                           print("x is greater than y")
            print("x is greater than y")                else:
        else:                                               print("x and y must be equal")
            print("x and y must be equal")              

You can see the advantage that ``elif`` version provides: reduced nesting with ``elif`` helps make
the intent clearer, by indenting all three alternative statements to the same indentation level, as
a visual cue that there are exactly three alternatives. When nested ``if``'s are used, the indentation
tends to obscure the logic.

An ``if`` statement that makes use of ``elif`` is sometimes referred to as a **chained conditional**. 
Here is a flow chart that shows how Python executes an ``if-elif-else`` statement. 

.. image:: Figures/flowchart_chained_conditional.png

As this diagram illustrates, the if statement checks to see if ``x < y`` is True. If so,
it executes line 5, but if not, it checks the condition ``x > y``. If that is true, it executes
line 7, but if not, it executes line 9.

.. admonition:: Try It Out

    Try experimenting with the program above by changing the numbers on lines 1 and 2 and executing the
    program several times. Also, use the **Show in CodeLens** button to watch the flow of control.

Here is the general form of an ``if`` statement containing ``elif`` sections:

.. sourcecode:: python

    if CONDITION_1:
        STATEMENTS_1        # executed if CONDITION_1 evaluates to True
    elif CONDITION_2:
        STATEMENTS_2        # executed if CONDITION_2 evaluates to True
    elif CONDITION_3:
        STATEMENTS_3        # executed if CONDITION_3 evaluates to True
    ... more elifs are possible here ...
    else:                   # optional else
        STATEMENTS_n        # executed if none of the conditions is True

There is no limit of the number of ``elif`` statements, but only a
single (and optional) final ``else`` statement is allowed and it must be the last
branch in the statement. 

Each condition is checked in order. If the first is false, the next is checked,
and so on. If one of them is true, the corresponding statement(s) execute, and the
rest of the conditions and else statement are ignored, and execution proceeds
with the next statement following the ``if-elif-else`` block. 

Detecting Invalid Input
-----------------------

Consider a program that asks a user to enter a number to choose from one of
several options:

.. activecode:: fruit

    choice = int(input('Enter 1 for banana, 2 for apple, 3 for pear:'))
    
    if choice == 1:
        print('You chose banana.')
    
    if choice == 2:
        print('You chose apple.')

    if choice == 3:
        print('You chose pear.')

Try running the program above a couple of times. Enter some valid selections, then try
running it with a number like 4 that is not a valid selection. What happens?

.. tabbed:: tab_validate_choice

    .. tab:: Question

        Enhance the program above so that, if the user enters a number that is not one of the
        three valid choices, the program reports 'Invalid selection.' Make sure you test your solution by entering 
        valid choices and numbers like 4 that are not valid. Then, compare your answer with mine.

    .. tab:: Tip

        Try rewriting the sequence of three ``if`` statements using a single ``if`` statement that uses
        ``elif`` blocks.

    .. tab:: Answer

        This program needs to choose between 4 alternative statements, so it should be written
        using a single ``if`` statement with multiple ``elif`` blocks, like this:

        .. activecode:: ac_validate_choice_ans
            :optional:

            choice = int(input('Enter 1 for banana, 2 for apple, 3 for pear:'))
            
            if choice == 1:
                print('You chose banana.')
            
            elif choice == 2:
                print('You chose apple.')

            elif choice == 3:
                print('You chose pear.')

            else: 
                print('Invalid selection.')

When a program needs to report an invalid selection, you'll almost always need to use an ``if-elif-else`` construct.

Overlapping Conditions
----------------------

Sometimes more than one condition may be true in an ``if-elif-else`` statement. If more than one
condition is true, only the first true branch executes. This is an important feature of the
``if-elif-else`` construct, and it allows you to solve certain problems that would otherwise require
boolean logic.

For example, consider the problem of `Goldilocks and the Three Bears <https://en.wikipedia.org/wiki/Goldilocks_and_the_Three_Bears>`_. 
Goldilocks samples a bit of porridge from papa bear's bowl ("too hot!"), mama bear's bowl ("too cold!") and baby bear's bowl
("just right!"). Here is a program that lets the user enter a temperature of porridge in degrees
fahrenheit, and determines whether the porridge is too hot (over 120 degrees), too cold (under 80 degrees), or just right (80-120
degrees):

.. activecode:: ac_3bears

    degrees = int(input('Enter temperature of porridge:'))
    
    if degrees >= 120:
        print('Too hot.')
    
    elif degrees < 80:
        print('Too cold.')

    else: 
        print('Just right!')

Take a moment to run this example and see how it works.

Now, let's enhance this program for a more discerning Goldilocks, who rates the porridge into one of
four temperature categories: Scalding (150 degrees or higher), Too Hot (120 to 150 degrees, not
including 150), Just Right (80 to 120 degrees, not including 120), and Too Cold (below 80 degrees).

Here's a revised version that does that:

.. activecode:: ac_3bearsb

    degrees = int(input('Enter temperature of porridge:'))
    
    if degrees >= 150:
        print('Scalding.')
    
    elif degrees >= 120:
        print('Too hot.')

    elif degrees >= 80:
        print('Just right.')

    else: 
        print('Too cold.')

Try this version out, and use **Show in CodeLens** to see how it works.

Notice that the conditions in this program overlap. For example, the conditions ``degrees >= 120`` and 
``degrees >= 80`` are both True when degrees is ``125``. 

This program works correctly because of the order in which the conditions are listed. Since
the conditions are tested in the order they are listed, when ``degrees`` is ``125``, the computer
evaluates the condition ``degrees >= 120`` and finds it True, and it does not evaluate the condition
``degrees >= 80``. What would happen if the order were switched, and the condition ``degrees >= 80`` and
its statement 'Too Hot' came before ``degrees >= 120``? Try it out and run a few tests.

You can take advantage of chained conditionals to solve problems where the program needs to determine an appropriate
action to take based on a value that falls into one of several ranges.

**Check your understanding**

.. parsonsprob:: par_cc_dgold
    :adaptive:

    Solve the "discerning Goldilocks" problem (see problem description in the
    section above) using the blocks provided. Note that the conditions provided
    are different than the ones used in the solution above.
    -----
    if degrees < 80:
        print('Too cold.')
    elif degrees < 120:
        print('Just right.')
    elif degrees < 150:
        print('Too hot.')
    else: 
        print('Scalding.')

.. tabbed:: tab_bloodp

    .. tab:: Question

        .. activecode:: ac_bloodp
            :autograde: unittest

            A blood pressure reading consists of two numbers: `systolic` and `diastolic`. According to
            cdc.gov, a systolic value less than 120 is considered normal. A systolic value in the range
            120-139 is considered prehypertension, and a systolic value 140 or higher is considered
            hypertension, and a significant factor in a risk for heart attack. 

            The following program loops over a list of diastolic values. For each diastolic
            value, it should determine whether the diastolic value is 'Normal', 'Prehypertension', or
            'Hypertension'. Complete the program by replacing the blanks with the conditions necessary
            to determine the condition that is correct for the value.
            ~~~~
            for diastolic in [95, 142, 120]:

                if ______________________:
                    condition = 'Normal'
                _________________________:
                    condition = 'Prehypertension'
                _________________________:
                    condition = 'Hypertension'

                print(diastolic, '-', condition)

            ====
            from unittest.gui import TestCaseGui

            class myTests(TestCaseGui):

                def testOne(self):
                    self.assertIn('95 - Normal', self.getOutput(), "95 - Normal")
                    self.assertIn('142 - Hypertension', self.getOutput(), "142 - Hypertension")
                    self.assertIn('120 - Prehypertension', self.getOutput(), "120 - Prehypertension")

            myTests().main()


    .. tab:: Answer

        .. activecode:: ac_bloodp_sol
            :optional:

            for diastolic in [95, 142, 120]:

                if diastolic < 120:
                    condition = 'Normal'
                elif diastolic < 140:
                    condition = 'Prehypertension'
                else:
                    condition = 'Hypertension'

                print(diastolic, '-', condition)
