..  Copyright (C) Stephen Schaub.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: test-1-
   :start: 1

Introduction: Unit Testing
==========================

Testing plays an important role in the development of software. 


.. note::
    A note to instructors: this chapter is deliberately structured so that you can introduce testing early in the course if you want to. You will need to cover chapter 8, on Conditionals, before starting this chapter, because that chapter covers Booleans. The subchapters on testing types and testing conditionals can be covered right after that. The subchapter on testing functions can be delayed until after you have covered function definition.


**Check your understanding**

.. mchoice:: question19_1_1
   :answer_a: A runtime error will occur
   :answer_b: A message is printed out saying that the test failed.
   :answer_c: x will get the value that y currently has
   :answer_d: Nothing will happen
   :answer_e: A message is printed out saying that the test passed.
   :correct: a
   :feedback_a: The expression ``x==y`` evaluates to ``False``, so a runtime error will occur
   :feedback_b: If the assertion fails, a runtime error will occur
   :feedback_c: ``x==y`` is a Boolean expression, not an assignment statement
   :feedback_d: The expression ``x==y`` evaluates to ``False``
   :feedback_e: When an assertion test passes, no message is printed. In this case, the assertion test fails.
   :practice: T

   When ``assert x==y`` is executed and x and y have different values, what will happen?


.. mchoice:: question19_1_1b
   :answer_a: A runtime error will occur
   :answer_b: A message is printed out saying that the test failed.
   :answer_c: x will get the value that y currently has
   :answer_d: Nothing will happen
   :answer_e: A message is printed out saying that the test passed.
   :correct: d
   :feedback_a: The expression ``x==y`` evaluates to ``True``
   :feedback_b: The expression ``x==y`` evaluates to ``True``
   :feedback_c: ``x==y`` is a Boolean expression, not an assignment statement
   :feedback_d: The expression ``x==y`` evaluates to ``True``
   :feedback_e: When an assertion test passes, no message is printed.
   :practice: T

   When ``assert x==y`` is executed and x and y have the same values, what will happen?



.. mchoice:: question19_1_2
   :answer_a: True
   :answer_b: False
   :correct: b
   :feedback_a: You might not notice the error, if the code just produces a wrong output rather generating an error. And it may be difficult to figure out the original cause of an error when you do get one.
   :feedback_b: Test cases let you test some pieces of code as you write them, rather than waiting for problems to show themselves later.
   :practice: T

   Test cases are a waste of time, because the python interpreter will give an error
   message when the program runs incorrectly, and that's all you need for debugging.

