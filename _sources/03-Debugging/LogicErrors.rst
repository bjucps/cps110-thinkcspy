..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: intro-9-
   :start: 1

.. index:: semantic error, logic error, error; semantic, error; logic


Logic Errors
------------

The third type of error is the **logic error** (also known as a **semantic error**). If there is a logic error in your
program, it will run successfully in the sense that the program will not crash with an error message.  However, your
program will not produce the desired result. It will produce incorrect results.

The following program is one we've seen before. It has a logic error. Execute it to remind yourself of what it does:

.. activecode:: logicerr_sum

    num1 = input('Enter a number:')
    num2 = input('Enter another number:')
    sum = num1 + num2

    print('The sum of', num1, 'and', num2, 'is', sum)

This program runs and produces a result. However, the result is not what the programmer intended. It contains
a logic error. The error is that the program performs concatenation instead of addition, because the programmer
failed to write the code necessary to convert the inputs to integers.

With logic errors, the problem is that the program you wrote is not the program you intended to write. The meaning of the
program (its semantics) is wrong. The computer is faithfully carrying out the instructions you wrote, and its results
are correct, given the instructions that you provided. However, because your instructions have a flaw in their design,
the program does not behave as desired.

Identifying logic errors can be tricky because no error message appears to make it obvious that the results are
incorrect. The only way you can detect logic errors is if you *know in advance* what the program should do for a given set
of input. Then, you run the program with that input data and compare the output of the program with what you expect. If
there is a discrepancy between the actual output and the expected output, you can conclude that there is either 1) a
logic error or 2) an error in your expected results.

Therefore, detecting logic errors requires that you create test cases. A **test case** is a set of input values for the
program, together with the output that you expect the program should produce when it is run with those particular
inputs. Here is an example of a test case for the program above::

   Test Case
   ---------
   Input: 2, 3
   Expected Output: 5

If you give this test case to someone and ask them to test the program, they can type in the inputs, observe the output,
check it against the expected output, and determine whether a logic error exists based on whether the actual output
matches the expected output or not. The tester doesn't even have to know what the program is supposed to do. For this reason,
software companies often have separate quality assurance departments whose responsibility is to check that the programs written
by the programmers perform as expected. The testers don't have to be programmers; they just have to be able to operate the
program and compare its results with the test cases they're given.

In this case, the program is so simple that we don't need to write down a test case at all; we can compute the expected output
in our heads with very little effort. More complicated programs require effort to create the test case (since you shouldn't use
the program to compute the expected output; you have to do it with a calculator or by hand), but the effort pays off when 
the test case helps you to identify a logic error that you didn't know existed.

Logic errors are the most dangerous of the three types of errors, because in some cases they are not noticed by either
the programmers or the users who use the program. Syntax errors cannot go undetected (the program won't run at all if
they exist), and runtime errors are usually also obvious and typically detected by developers before a program is
released for use (although, as you've seen, it is possible for a runtime error to occur for some inputs and not for
others, so these can sometimes remain undetected for a while). However, programs often go for years with undetected
logic errors; no one realizes that the program has been producing incorrect results. They just assume that because the
results seem reasonable, they are correct. Sometimes, these errors are relatively harmless. But if they involve
financial transactions or medical equipment, the results can be harmful or even deadly. For this reason, creating test
cases is an important part of the work that programmers perform in order to help them produce programs that work
correctly.

**Check your understanding**

.. mchoice:: question1_8_1
   :practice: T
   :answer_a: Attempting to divide by 0.
   :answer_b: Forgetting a colon at the end of a statement where one is required.
   :answer_c: Forgetting to divide by 100 when printing a percentage amount.
   :correct: c
   :feedback_a: Dividing by zero produces an error at runtime. This would be considered a run-time error.
   :feedback_b: This would be considered a syntax error.
   :feedback_c: This will produce the wrong answer because the programmer implemented the solution incorrectly. This is a logic error.

   Which of the following is a logic error?

.. mchoice:: question1_8_2
   :practice: T
   :answer_a: Syntax error.
   :answer_b: Runtime error.
   :answer_c: Logic error.
   :correct: c
   :feedback_a: Syntax errors provide a line number and are usually easy to fix.
   :feedback_b: Runtime errors provide a line number and are usually not too hard to fix.
   :feedback_c: Logic errors can exist without your knowledge, and never provide a line number to help you locate the problem.


   Which of the following errors is the most difficult to diagnose?

