..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-4-
   :start: 1

.. _variables:

Variables
---------

One of the most powerful features of a programming language is the ability to manipulate variables. A **variable** is a
name that refers to a value. Programmers create variables to hold values in memory, so that the values can be
manipulated by the program to produce the desired computations. In this section, you will learn how to create variables
and use them to write programs that do useful work.

Assignment Statement
^^^^^^^^^^^^^^^^^^^^

Assignment statements are used to create new variables. An **assignment statement** creates a
variable and assigns it a value. Here is a short example with three assignment statements:

.. sourcecode:: python

    message = "What's up, Doc?"
    n = 17
    sum = 2 + 3.5

This example creates three variables named ``message``, ``n``, and ``sum``. The first statement assigns the string value ``"What's
up, Doc?"`` to a new variable named ``message``. The second assigns the integer ``17`` to ``n``, and the third assigns the
floating-point number ``5.5`` to a variable called ``sum``. 

An assignment statement has a variable on the left-hand side of the equal sign, and a literal value (ex. ``17``) or
expression (ex. ``2 + 3.5``) on the right-hand side. The statement creates a variable and associates it with the value
on the right-hand side. 

Take a moment to step through the following codelens example to the three assignment statements in action:

.. codelens:: var_basic

    message = "What's up, Doc?"
    n = 17
    pi = 3.14 + 0.00159

The last assignment statement in the example is interesting because it shows how when the expression ``3.14 + 0.0015`` is used
on the right-hand side of an assignment, Python evaluates the expression to produce a value, and assigns the resulting
value to the variable ``pi``.

A common way to represent variables on paper is to write the name with an arrow pointing to the variable's value. This
kind of figure depicts a snapshot of the program's state at a particular instant in time. The **state** of a program
is the values of the program variables. This diagram shows the result of executing the assignment statements shown above.

.. image:: Figures/refdiagram1.png
   :alt: Reference Diagram

Referencing Variables
^^^^^^^^^^^^^^^^^^^^^

After a variable is assigned a value, its value can be used by statements later in the program. Take a look at this example:

.. codelens:: var_basic2

    a = 5
    b = a + 1
    c = b

Here's what happens:

1. The value 5 is assigned to ``a``.

2. The expression ``a + 1`` is evaluated, and the resulting value (``6``) is assigned to ``b``.

3. The expression ``b`` is evaluated, and its value (``6``) is assigned to ``c``.

The sequence of assignment statements in a program is important, because they are executed one at a time, and the outcome
of one assignment statement can affect the assignment statements that follow. 

.. note::

    With simple assignment statements like ``c = b`` it's easy to become confused about which variable is altered by the
    assignment statement. Remember: it's always the variable on the left-hand side that is changed, not the right-hand
    side.

Note that it is illegal to attempt to use a variable on the right-hand side of an assignment statement before it has
been given a value. The following program crashes on the very first line, because ``a`` has not yet been given a value,
so the interpreter is unable to compute the value ``a + 1`` to assign to ``b``:

.. activecode:: var_basic3

    b = a + 1  # Error; a not assigned yet
    c = b
    a = 5


Writing Programs with Variables
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Using variables, we can now write programs that perform calculations using a series of steps. For example, consider the following
program that computes the total cost for a purchase of three books from a bookstore:

.. sourcecode:: python

    book1_price = 5.25
    book2_price = 1.15
    book3_price = 2.25

    total_before_tax = book1_price + book2_price + book3_price
    tax_amt = total_before_tax * 0.08
    total_amt = total_before_tax + tax_amt

    print(total_amt)

Here is a step-by-step description of what the program does:

1. This program begins by creating three variables with the prices of three different books. 

2. Next, it adds together the prices of the three individual books, assigning the resulting sum to ``total_before_tax``. 

3. Then, it computes the amount of tax due (``tax_amt`` ) by multiplying the ``total_before_tax`` by the tax rate of 8%,
   expressed as a float (``0.08``). 

4. Finally, it adds the ``total_before_tax`` to the ``tax_amt`` to compute the ``total_amt`` due, and then
   displays the result.

Note that the only value displayed is the final number. None of the values of the intermediate computations
appear on the screen.

Without variables, we could have computed this number, but the entire program would have to be written
using a single print statement::

    print((5.25 + 1.15 + 2.25) + (5.25 + 1.15 + 2.25) * 0.08)

As you can see, using variables is essential to writing programs that are readable!

Let's modify the program to take quantity into account in the calculations. Suppose the customer buys 3 copies of book1,
2 copies of book2, and 4 copies of book3 (see below). In that case, the total_before_tax should be $15 (3 copies of
book1) + $2 (2 copies of book2) + $8 (4 copies of book3), or $25. Complete the program below by replacing the ??? with
the expression needed to correctly compute the total_before_tax using the variables provided. When you click Run to test
the program, the activecode interpreter will check your work and let you know if you got it correct. Also, experiment
with using the **Show CodeLens** button to let you step through the code and watch it execute.

If you get stuck and need help, watch the solution video that follows.

.. activecode:: var_qty

    book1_price = 5.00
    book2_price = 1.00
    book3_price = 2.00

    book1_quantity = 3
    book2_quantity = 2
    book3_quantity = 4

    total_before_tax = ???
    tax_amt = total_before_tax * 0.08
    total_amt = total_before_tax + tax_amt

    print(total_amt)

    ====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
            self.assertEqual(total_before_tax, 
                    book1_price * book1_quantity + book2_price * book2_quantity + book3_price * book3_quantity, 
                    "correct total_before_tax?"  )
            self.assertEqual(total_amt, (book1_price * book1_quantity + book2_price * book2_quantity + book3_price * book3_quantity) * 1.08, "correct total_amt?"  )
            self.assertNotIn("25", self.getEditorText(), "Do not precompute total_before_tax")

    myTests().main()

Now, watch this brief video that shows how I solved the problem. In the video, I also discuss how the
activecode interpreter tests the solution for correctness. It's important for you to understand how to interpret
the test results, so I encourage you to watch the video so you can understand the messages you see in future
problems like this.

.. youtube:: -5zWM2E0AUY
    :divid: book_qty_sol_video
    :height: 315
    :width: 560
    :align: left

Assignment vs. Equality
^^^^^^^^^^^^^^^^^^^^^^^

The **assignment token**, ``=``, should not be confused with *equality* (we will see later that equality uses the
``==`` token).  The assignment statement links a *name*, on the left hand
side of the operator, with a *value*, on the right hand side.  This is why you
will get an error if you enter::

    17 = n              # Illegal assignment

.. tip::

   When reading or writing code, say to yourself "n is assigned 17" or "n gets
   the value 17." Avoid saying "n equals 17".


Displaying Several Values on One Line
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In the following example, note how the program computes a value, and then displays the result, preceded by
a brief label. 

.. activecode:: ch02_9
    :nocanvas:

    diameter = 100
    radius = diameter / 2

    print('Radius is:')
    print(radius)

Sometimes, you want the print statement to put the value of a variable on the same line as the text that describes it.
To do this, edit the program above. Replace the two print statements with this single print command:

.. sourcecode:: python

    print('The radius of a circle with diameter', diameter, 'is:', radius)

You should see the following output::

   The radius of a circle with diameter 100 is: 50.0

You can use a single print command to display multiple pieces of information on one line, by separating them with
commas. Note how this example outputs a line composed of four distinct values:

* A literal string: 'The radius of a circle with diameter'
* The value of the variable ``diameter``
* A literal string: 'is:'
* The value of the variable ``radius``

Look carefully at the print command. Notice the parts that are quoted, and how the commas are positioned with respect to
the quotes. It's important to understand the reason why the punctuation symbols occur in the order that they do. You
might observe that the positioning of commas is different from English usage, where commas typically go inside quotes. 
You might take a moment to experiment with moving the commas and quotes around to see the different behavior that happens 
when you modify the sequence of symbols.

Notice how when multiple values are output in one command using commas, ``print`` puts a space between each value in the
output. Later you'll see how to have more control over the formatting of the output.

Now, take a moment to practice. Complete the print statement in the program below. It should output a message like this::

    She requested, "Please give me 5 chocolate candies."

However, instead of putting that exact message inside a single pair of quotes in your print() command, write a print
statement that displays the values of the ``quantity`` and ``flavor`` variables at the appropriate places in the
message, using the technique demonstrated above. Experiment with altering the values in the variables to see the message
change. For example, if quantity is 3 and flavor is "peppermint", your program should display this message::

    She requested, "Please give me 3 peppermint candies."

The activecode interpreter will check your solution.

Tip: Because the message has quotes embedded in it, you'll need to be extra careful about the quoting that you use for
your string values. You may want to review the information on string quoting in the :ref:`previous
section<values-and-types>` (see "More on String Quoting").

.. tabbed:: var_chocolate_tabs

    .. tab:: Question

        .. activecode:: var_chocolate

            quantity = 5
            flavor = "chocolate"

            print(???)

            ====

            from unittest.gui import TestCaseGui
            class myTests(TestCaseGui):
                def testOne(self):
                    self.assertEqual('She requested, "Please give me ' + str(quantity) + " " + flavor + ' candies."', self.getOutput().strip(), "Correct message?"  )
                    self.assertNotIn('She requested, "Please give me 5 chocolate candies."', self.getEditorText(), "Must use variables in print()")

            myTests().main()

    .. tab:: Answer

        Here's the print statement to use::

            print('She requested, "Please give me', quantity, flavor, 'candies."')

        Note that we used single quotes around the string. We could also have used
        triple single quotes, or triple double quotes, like this::

            print("""She requested, "Please give me""", quantity, flavor, """candies."""")



Variable Types
^^^^^^^^^^^^^^

When you place a value in a variable using an assignment statement, the value has a type. You can use the ``type``
function to view the type of the value referenced by a variable.

.. activecode:: ch02_10
    :nocanvas:

    message = "What's up, Doc?"
    n = 17
    pi = 3.14159

    print(type(message))
    print(type(n))
    print(type(pi))

Note that variables don't have a data type, as they do in some languages like Java. Instead, values have a type,
and the ``type`` function allows you to discover the type of a variable's value.

.. index:: modulus
   single: %
   remainder

Case Study: Time Conversion
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Let's do something useful with variables. I encourage you to start the Python shell and follow along as we develop
a short program. Hands-on practice ... it's the best way to learn, right? 

Let's say that you've been keeping track of how much time you are spending reading this book using a digital stopwatch
that keeps time using only seconds. You want to write a program that takes a total number of seconds (say, 125) reported
by your digial stopwatch and figures out that 125 seconds breaks down into 2 minutes and 5 seconds. How might you go
about that?

Suppose we use the interpreter to help us out. Start by putting the total number of seconds in a variable named ``tot_seconds``:

.. sourcecode:: python

    >>> tot_seconds = 125
    >>>

Next, can you figure out a calculation that you can type into the interpreter that would compute the number of minutes
represented by ``tot_seconds``? Note that we want an integer value (2), not a float. Think about it a moment, and
experiment. I'll wait. 😀

.. reveal:: tip
   :showtitle: Give me a tip
   :modal:
   :modalTitle: Here's a tip!

   You need to use one of the division operators (``/`` or ``//``). Try out both and see which one will do the job.

Converting seconds
""""""""""""""""""

To determine the number of minutes, you need the integer division operator. Try this out:

.. sourcecode:: python

    >>> tot_seconds = 125
    >>> tot_seconds // 60
    2
    >>> 

Note that it is important that, for correct results, we do not want the result of the division rounded up to the nearest integer. 
For example, we want 115 // 60 to yield 1, since 115 is 1 minute + 55 seconds. Does ``//`` do the right thing? Try it out 
and see...

.. sourcecode:: python

    >>> tot_seconds = 115
    >>> tot_seconds // 60
    1
    >>>

As we learned earlier, the integer division operator truncates the fractional result, and does not round. So, it's exactly what
we need here.

Now that we know how to determine the number of minutes, the next challenge is to figure out how many seconds
remain. For example, 125 seconds converts to 2 minutes, 5 seconds. If ``tot_seconds // 60`` yields 2, what calculation
is needed to determine that there are 5 seconds left over?

.. note:: 

    If you need a tip, click on the Tip tab. To see the solution, click on the Solution tab.

.. tabbed:: var_minutes_tabs

    .. tab:: Question        
        
        Here's a partial solution to the original problem that computes the number of minutes that will fit into
        ``tot_seconds``. It doesn't yet compute the number of remaining seconds; it shows ??? for that value. Modify
        this program so that, in addition to displaying the number of minutes, it displays the remaining number of
        seconds. 

        .. activecode:: ch02_17

            tot_seconds = 645
            minutes = tot_seconds // 60
            print(tot_seconds, 'seconds =', minutes, 'minutes, ??? seconds')

    .. tab:: Tip

        Define a new variable named ``seconds``, just before the print command. Design a calculation that will
        determine a value for seconds using a calculation involving ``tot_seconds`` and ``minutes``. Then,
        modify the print command to display the values of both the minutes and seconds variable.

    .. tab:: Solution

        Here's the solution.

        .. sourcecode:: python

                tot_seconds = 645
                minutes = tot_seconds // 60
                seconds = tot_seconds - (60 * minutes)
                print(tot_seconds, 'seconds =', minutes, 'minutes', seconds, 'seconds')        


Meet the modulus (``%``) operator
"""""""""""""""""""""""""""""""""

The **modulus operator**, sometimes also called the **remainder operator** or **integer remainder operator**, computes
the remainder of the division of two integers. It may have been a while since you worked with the concept of a 
remainder, so let's do a brief review of the concept. When you divide 14 by 3, the integer quotient is 4 ("3 goes into 14
**4** times"), and the remainder is 2 ("3 goes into 14 **4** times, with **2** left over"). If you're like me, you may
need to re-read that last sentence and think about it before going on.

In Python, the modulus operator is a percent sign (``%``). Take a moment to try out the following in the interpreter:

.. sourcecode:: python

    >>> 14 // 3
    4
    >>> 14 % 3
    2
    >>>

The modulus operator turns out to be surprisingly useful. For example, you can check whether one number is divisible by
another---if ``x % y`` is zero, then ``x`` is divisible by ``y``. Also, you can extract the right-most digit or digits
from a number.  For example, ``x % 10`` yields the right-most digit of ``x`` (in base 10). Similarly ``x % 100`` yields
the last two digits.

Finally, returning to our time example, the remainder operator is extremely useful for doing conversions, say from seconds,
to minutes and seconds. We can use the remainder operator to simplify the formula used in the sample solution for our
seconds conversion problem. Step through the code below to see it in action, and think carefully about how it works.

.. codelens:: ch02_19_codelens

    tot_seconds = 645
    minutes = tot_seconds // 60
    seconds = tot_seconds % 60
    print(minutes, seconds)

Use the modulus Operator
""""""""""""""""""""""""

Now, let's expand the program to convert a total number of seconds to hours, minutes, and seconds. 
For example, 7,684 seconds converts to 2 hours, 8 minutes 4 seconds. 

Using the modulus operator, complete the program below to compute the number of hours, minutes, and seconds
corresponding to the number of seconds in ``tot_seconds``. The activecode interpreter will check your work.

This problem will require some thought. I've given you an outline of the solution, but you will need to think carefully about
the calculations. I suggest that you take some time to work out your calculations on paper. Working calculations on paper
may seem old fashioned, but you might be surprised about how it helps your mind to think through the issues.

.. tabbed:: var_minutes2_tabs

    .. tab:: Question        
        
        Replace the ??? marks in the program below with the expressions needed to calculate the
        values for the variables. You may find it helpful to introduce an additional variable.

        .. activecode:: var_hms
            :nocanvas:

            tot_seconds = 7684
            hours = ???
            minutes =  ???
            seconds = ???
            print(tot_seconds, 'seconds =', hours, 'hours,', minutes, 'minutes and', seconds, 'seconds')

            ====

            from unittest.gui import TestCaseGui

            class myTests(TestCaseGui):

                def testOne(self):
                    self.assertEqual(hours, 2, "2 hours" )
                    self.assertEqual(minutes, 8, "8 minutes"  )
                    self.assertEqual(seconds, 4, "4 seconds" )
                    self.assertNotIn("2", self.getEditorText(), "Do not precompute hours")

            myTests().main()    

    .. tab:: Tip

        To compute hours from seconds, you'll need to first figure out how many seconds are in an hour.
        After computing hours, you may find it helpful to introduce another variable that holds the left over
        (remaining) seconds to help you compute the remaining minutes and seconds.

    .. tab:: Solution

        This solution introduces another variable, ``secs_remaining``, to simplify the calculations
        required to determine the minutes and seconds. This isn't the only way to solve the problem,
        but it's a good approach. Take a moment to study the code and see how it works.

        .. sourcecode:: python

            tot_seconds = 7684
            hours = tot_seconds // 3600          # 3600 seconds in an hour
            
            # Now, compute number of seconds remaining
            secs_remaining = tot_seconds % 3600  
            
            # Convert seconds remaining to minutes and seconds
            minutes = secs_remaining // 60
            seconds = secs_remaining  % 60
            
            # Display results
            print(tot_seconds, 'seconds contains', hours, 'hours,', minutes, 'minutes', seconds, 'seconds')

