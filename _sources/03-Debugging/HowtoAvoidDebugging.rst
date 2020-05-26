..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: debug-2-
   :start: 1

How to Avoid Debugging
----------------------

Perhaps the most important lesson in debugging is that it is **largely avoidable** -- if you work carefully.

1.  **Understand the Problem**  You must have a firm grasp on **what** you are trying to accomplish but not 
    necessarily **how** to do it. You do not need to understand the entire problem. But you must understand 
    at least a portion of it and what the program should do in a specific circumstance -- what output should 
    be produced for some given input. This will allow you to test your progress. You can then identify if a 
    solution is correct or whether there remains work to do or bugs to fix. This is probably the single 
    biggest piece of advice for programmers at every level. This is the step where you should create some
    test cases to make sure you understand the problem. If you can't determine what the expected output should
    be for a given set of test input, you either don't understand the problem well enough, or perhaps the
    problem specification is incomplete or vague and needs to be clarified. 

2.  **Start Small**  It is tempting to sit down and crank out an entire program at once.  But, when the program 
    -- inevitably -- does not work, you have a myriad of options for things that might be wrong.  Where to start? 
    Where to look first?  How to figure out what went wrong?  I'll get to that in the next section.  So, start 
    with something really small.  Maybe just two lines and then make sure that runs.  Hitting the run button 
    is quick and easy. It gives you immediate feedback about whether what you have just done works or not.  
    Another immediate benefit of having something small working is that you have something to turn in.  Turning 
    in a small, incomplete program, is almost always better than nothing.

3.  **Keep Improving It**  Once you have a small part of your program working, the next step is to figure out 
    something small to add to it -- how can you move closer to a correct solution. As you add to your program,
    you gain greater insight into the underlying problem you are trying to solve.

    If you keep adding small pieces of the program one at a time, it is much easier to figure out what went
    wrong. (This of course means you must be able to recognize if there is an error. And that is done through
    testing.)

    As long as you always test each new bit of code, it is most likely that any error is in the new code you 
    have just added. Less new code means its easier to figure out where the problem is.

This notion of **Get something working and keep improving it** is a mantra that you can repeat throughout your 
career as a programmer.  It's a great way to avoid the frustrations mentioned above.  Think of it this way.  
Every time you have a little success, your brain releases a tiny bit of chemical that makes you happy.  So, you 
can keep yourself happy and make programming more enjoyable by creating lots of small victories for yourself.

.. note::
   The technique of start small and keep improving is the basis of **Agile** software development. This
   practice is used widely in the industry. 


Ok, let's look at an example.  Let's solve the problem posed in question 3 at the end of the Python Fundamentals chapter. 
For reference, here's the problem:

   Many people keep time using a 24 hour clock (1 is 1 am, 11 is 11 am, 12 is 12 pm, 13 is 1 pm, 23 is 11 pm, 0 is midnight).
   If it is currently 13 (1 pm) and you set your alarm to go off in 12 hours, it will be 1 (1 am).
   Write a Python program to solve the general version of the above problem.
   Ask the user for the time now (in hours), and then ask for the number of hours to wait for the alarm.
   Your program should output what the time will be on the clock when the alarm goes off.

For example, if ``current_time`` is 8 and ``wait_time`` is 5, ``final_time`` should be 13 (1 pm). To help clarify
your understanding, let's write up a couple of test cases::

   Test Case 1
   -----------
   Inputs:
     * current_time: 8
     * wait_time: 5
   Expected output: 13

Now, you try your hand at a second test case:

.. tabbed:: avoid_debug_tc

    .. tab:: Question

      What is the expected output for the test case below?

      :: 

         Test Case 2
         -----------
         Inputs:
         * current_time: 17
         * wait_time: 9
         Expected output: ?

    .. tab:: Answer

      17 (5 pm) + 9 hours = 2 (2 am)

      Expected output: 2


So, where to start?  The problem requires two pieces of input from the user, so let's start there, write two input statements,
and then write print commands to display the values of the variables, to make sure we got the correct data into the variables.

.. activecode:: db_ex3_1

   current_time = input("what is the current time (in hours)?")
   wait_time = input("How many hours do you want to wait")

   print('current time:', current_time)
   print('wait time:', wait_time)


So far so good.  Now let's take the next step.  We need to figure out what the time will be after waiting ``wait_time`` number of hours.  A reasonable solution is to simply add ``wait_time`` to ``current_time`` and print out the result.  So lets try that.

.. activecode:: db_ex3_2

   current_time = input("What is the current time (in hours 0 - 23)?")
   wait_time = input("How many hours do you want to wait?")

   print('current time:', current_time)
   print('wait time:', wait_time)

   final_time = current_time + wait_time
   print('final time:', final_time)

Hmm, when you run this example you see that something unexpected has happened. You would not realize this was an error unless you first knew what the program was supposed to do.

.. mchoice:: db_q_ex3_1
   :practice: T
   :answer_a: Python is stupid and does not know how to add properly.
   :answer_b: There is nothing wrong here.
   :answer_c: Python is doing string concatenation, not integer addition.
   :correct: c
   :feedback_a: No, Python is probabaly not broken.
   :feedback_b: No, try adding the two numbers together yourself, you will definitely get a different result.
   :feedback_c: Yes!  Remember that input returns a string.  Now we will need to convert the string to an integer

   Which of the following best describes what is wrong with the  previous example?

This error was probably pretty simple to spot, because we printed out the value of ``final_time`` and it is easy to see that the numbers were just concatenated together rather than added.  

So what do we do about the problem? By now you should know exactly what to do: convert the input to ``int``.


.. activecode:: db_ex3_3

   current_time = int(input("What is the current time (in hours 0 - 23)?"))
   wait_time = int(input("How many hours do you want to wait?"))

   print('current time:', current_time)
   print('wait time:', wait_time)

   final_time = current_time + wait_time
   print('final time:', final_time)


.. index:: boundary conditions, testing, debugging

Now, that's a lot better, and for the first test case (``current_time`` = 8 and ``wait_time`` = 5) the program produces 13 - a correct result. 
But if you try the second test case (``current_time`` = 5 and ``wait_time`` = 9), the program produces 26 - not correct.

This illustrates an important aspect of **testing**: it is important to create test cases with a variety of inputs.  It is especially important to test your code on **boundary conditions**.  For this particular problem, you should test your program with ``current_time`` of 0, 23, and some values in between.  You should test your ``wait_time`` for 0, and some larger values.  What about negative numbers?  Negative numbers don't make sense, and since we don't really have the tools to deal with telling the user when something is wrong we will not worry about that just yet.  

So we need to account for those numbers that are bigger than 23. Here's a slightly streamlined version of the above
program in which the print statements that display the current time and wait time have been removed, since we know that
the input statements are doing what we want. Can you figure out how to force the final_time to always end up in the
range 0..23? See if you can adjust the program to work properly for both of the test cases. 

.. tabbed:: avoid_debug_1

    .. tab:: Question

        Complete the statement below to compute the correct result for both test cases. After you think you've
        solved it correctly, check it by running it for both of the test cases above.

        .. activecode:: avoid_debug_1_src

            current_time = int(input("What is the current time (in hours 0 - 23)?"))
            wait_time = int(input("How many hours do you want to wait?"))

            final_time = ???

            print("The time after waiting is: ", final_time)

            ====

            from unittest.gui import TestCaseGui
            class myTests(TestCaseGui):
               def testOne(self):
                  self.assertEqual(final_time, (current_time + wait_time) % 24, "correct final_time?" )

            myTests().main()    

    .. tab:: Tip

        Hint: Think in terms of computing the remainder of a division. The modulus operator will be very useful here!

    .. tab:: Answer

        Here's the line to compute final_time::

            final_time = (current_time + wait_time) % 24


Of course even in this simple progression, there are other ways you could have gone astray.  We'll look at some of those and how you track them down in the next section.

