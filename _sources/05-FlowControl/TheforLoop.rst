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

.. index:: for loop, iteration, body
   loop; for

The ``for`` Loop
----------------

.. youtube:: xGSfiZt5cdw
    :divid: forloopvid
    :height: 315
    :width: 560
    :align: left


In Python, the **for** statement allows us to write programs that implement iteration.   As a simple example, let's say we have some friends, and
we'd like to send them each an email inviting them to our party.  We don't quite know how to send email yet, so for the moment we'll just print a
message for each friend.

.. activecode:: ch03_4
    :nocanvas:
    :tour_1: "Overall Tour"; 1-2: Example04_Tour01_Line01; 2: Example04_Tour01_Line02; 1: Example04_Tour01_Line03;

    for name in ["Joe", "Amy", "Brad"]:
        print("Hi", name)
        print("Please come to my party on Saturday!")

    print("All done!")

Take a look at the output produced when you press the ``run`` button.  There are two lines printed for each friend.  Here's how it works:


* **name** in this ``for`` statement is called the **loop variable**.
* The list of names in the square brackets is called a Python **list**.
  Lists are very useful.  We will have much
  more to say about them later.
* Lines 2 and 3 compose the **loop body**.  The loop body is always
  indented, and all lines in the body must be indented the same number
  of spaces to avoid an error. The indentation determines exactly what statements are "in the
  loop".  The loop body is performed one time for each name in the list.
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
