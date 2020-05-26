..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-3-
   :start: 1

.. index:: for loop, iteration, body, compound statement
   loop; for

The ``for`` Loop
================

.. youtube:: Q8WR16PuUtc
    :divid: whileloop
    :height: 315
    :width: 560
    :align: left

In Python, the **for** statement allows us to write programs that execute a group of statements repeatedly. As a simple
example, let's say we have some friends, and we'd like to send them each an email inviting them to our party.  We don't
quite know how to send email yet, so for the moment we'll just print a message for each friend.

.. activecode:: ch03_4
    :nocanvas:

    print("To my friends:")

    for name in ["Joe", "Amy", "Brad"]:
        print("Hi", name)
        print("Please come to my party on Saturday!")

    print("All done!")

Take a look at the output produced when you press the ``run`` button.  There are two lines printed for each friend.  Here's how it works:

* **name** in this ``for`` statement is called the **loop variable**.

* The list of names in the square brackets is called a Python **list**.
  Lists are very useful.  We will have much more to say about them later.

* Lines 4 and 5 compose the **loop body**.  The loop body is composed of the lines 
  that execute repeatedly in the loop. The loop body is always indented (more on indentation below),
  and the statements in the loop body are executed one time for each name in the
  list. 
  
* On each *iteration* or *pass* of the loop, a check is done to see if
  there are still more items to be processed.  If there are none left (this is
  called the **terminating condition** of the loop), the loop has finished.
  Program execution continues at the next statement after the loop body.

* If there are items still to be processed, the loop variable is updated to
  refer to the next item in the list.  This means, in this case, that the loop
  body is executed here 3 times, and each time ``name`` will refer to a different
  friend.

* At the end of each execution of the body of the loop, Python returns
  to top of the ``for`` statement, to see if there are more items to be handled.

To see how all of this works, try using the **Show CodeLens** button to step through the
program. 

Compound Statements and Indentation
-----------------------------------

The ``for`` loop is our first example of a **compound statement**. A compound statement is a statement that contains
a **block** of statements nested "inside" it. Python uses indentation to control which statements are part
of the compound statement, and which statements are not. 

Within the compound statement, all lines the body must be indented the same number
of spaces to avoid an error. 

To explore the role of indentation in Python, consider the following two programs:

.. sourcecode:: python

    for name in ["Joe", "Amy", "Brad"]:
        print("Hi", name)
        print("Please come to my party on Saturday!")

.. sourcecode:: python

    for name in ["Joe", "Amy", "Brad"]:
        print("Hi", name)
    print("Please come to my party on Saturday!")

The behavior of these two programs is significantly different. To see what I mean, try editing the code in the
activecode editor above and executing both of these versions. 

In the first version, both print statements are part of the single compound statement that makes up the
for loop. We would say that the overall program consists of one logical statement: the for loop (a compound
statement), which contains two nested print statements.

In the second version, the overall program consists of two logical statements: the for loop (containing a
single nested print statement), and the final print statement. To help make this organization clearer,
stylistically, it's a good idea to follow a compound statement with a blank line, like this:

.. sourcecode:: python

    for name in ["Joe", "Amy", "Brad"]:
        print("Hi", name)

    print("Please come to my party on Saturday!")

Blank lines don't change the meaning of the program, but they can help make the organization clearer.

Indentation is important in Python, because it defines the logical structure of the program. Changing the
indentation of individual statements can change the meaning of the program, so watch your indentation!
