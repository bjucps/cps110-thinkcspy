..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-4-
   :start: 1

.. index:: accumulator pattern

The Accumulator Pattern
-----------------------

In this section we will compute the square of a number. But we will do it using an algorithm that relies on addition instead
of multiplication.

If you want to multiply two numbers together, the most basic approach is to think of it as repeating the process of
adding one number to itself.  The number of repetitions is where the second number comes into play.  For example, if we
wanted to multiply three and five, we could think about it as adding three to itself five times.  Three plus three is six, plus three is nine, plus three is 12, and finally plus three is 15.  Generalizing this, if we want to implement
the idea of squaring a number, call it `n`, we would add `n` to itself `n` times.

Do this by hand first and try to isolate exactly what steps you take.  You'll
find you need to keep some "running total" of the sum so far, either on a piece
of paper, or in your head.  Remembering things from one step to the next is
precisely why we have variables in a program.  This means that we will need some variable
to remember the "running total".  It should be initialized with a value of zero.  Then, we need to **update** the "running total" the correct number of times.  For each repetition, we'll want
to update the running total by adding the number to it.

In words we could say it this way.  To square the value of `n`, we will repeat the process of updating a running total `n` times.  To update the running total, we take the old value of the "running total" and add `n`.  That sum becomes the new
value of the "running total".

Here is the program in activecode.  


.. activecode:: sq_accum1

    toSquare = 4
    runningtotal = 0
    for counter in range(toSquare):
        runningtotal = runningtotal + toSquare

    print("The result of", toSquare, "squared is", runningtotal)


In the program above, notice that the variable ``runningtotal`` starts out with a value of 0.  Next, the iteration is performed ``toSquare`` times.  
Inside the for loop, the update occurs. ``runningtotal`` is reassigned a new value which is the old value plus the value of ``toSquare``.

This pattern of iterating the updating of a variable is commonly
referred to as the **accumulator pattern**.  We refer to the variable as the **accumulator** because it gradually accumulates the result.
This pattern will come up over and over again.  Remember that the key
to making it work successfully is to be sure to initialize the variable before you start the iteration.
Once inside the iteration, it is required that you update the accumulator.

.. note::

    What would happen if we put the assignment ``runningTotal = 0`` inside
    the for statement?  Not sure? Try it and find out.

Click on **Show CodeLens** above and step through the program to watch the "running total" accumulate the result.


The General Accumulator Pattern
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: python

    initialize the accumulator variable
    repeat:
        modify the accumulator variable

    # when the loop terminates the accumulator has the correct value


**Check your understanding**

.. mchoice:: test_question5_4_1
   :practice: T
   :answer_a: The square function will return x instead of x * x
   :answer_b: The square function will cause an error
   :answer_c: The square function will work as expected and return x * x
   :answer_d: The square function will return 0 instead of x * x
   :correct: a
   :feedback_a: The variable runningtotal will be reset to 0 each time through the loop.   However because this assignment happens as the first instruction, the next instruction in the loop will set it back to x.   When the loop finishes, it will have the value x, which is what is returned.
   :feedback_b: Assignment statements are perfectly legal inside loops and will not cause an error.
   :feedback_c: By putting the statement that sets runningtotal to 0 inside the loop, that statement gets executed every time through the loop, instead of once before the loop begins.  The result is that runningtotal is 'cleared' (reset to 0) each time through the loop.
   :feedback_d: The line runningtotal = 0 is the first line in the for loop, but immediately after this line, the line runningtotal = runningtotal + x will execute, giving runningtotal a non-zero value  (assuming x is non-zero).

   Consider the following code:

   .. code-block:: python

        toSquare = 10
        for counter in range(toSquare):
            runningtotal = 0
            runningtotal = runningtotal + toSquare

   What happens in this example when the initialization of runningtotal (the line runningtotal = 0) occurs inside the for loop as the first
   instruction in the loop?


.. parsonsprob:: question5_4_1p

   Rearrange the code statements so that the program will add up the first n odd numbers where n is provided by the user.
   -----
   n = int(input('How many odd numbers would
   you like to add together?'))
   thesum = 0
   oddnumber = 1
   =====
   for counter in range(n):
   =====
      thesum = thesum + oddnumber
      oddnumber = oddnumber + 2
   =====
   print(thesum)

The Accumulator Pattern with Strings
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The accumulator pattern can be used with strings as well as numbers. Take a look at the following example, which creates
a line of asterisks. Use the **Show CodeLens** feature to watch the line built by the loop.

.. activecode:: ch04_accum3

    symbol = '*'
    line = ''
    for counter in range(30):
        line = line + symbol

    print(line)

Each time through the loop, another asterisk is concatenated to the ``line``, so the ``line`` variable gradually accumulates the
asterisks. 


.. admonition:: Modify the program ...

   Experiment with changing the program. 
   
   1. Make it create a line of 50 dashes.
   2. Make it create a line that begins with '<' and ends with '>'

