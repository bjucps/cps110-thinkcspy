..  Copyright (C)  Stephen Schaub.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Combining Loops and Conditionals
================================

Often it is necessary to combine loops and conditional structures to solve a problem.

For example, suppose you want to write a program that simulates flipping a coin 10 times. Here is one way you might
do it:

.. activecode:: ac_heads_tails

    import random

    for i in range(10):
        num = random.randrange(0, 2) # Generate a number that is either 0 or 1
        if num == 0:
            print('Flip', i+1, 'came up Heads ...')
        else:
            print('Flip', i+1, 'came up Tails ...')
                
In this example, the ``for`` loop executes 10 times, using the ``range`` function. Each time, the computer picks a
number in the range [0..1] using the ``randrange`` function, and then the ``if`` statement on lines 5-8
interprets the number as 'Heads' or 'Tails' and displays the result.
