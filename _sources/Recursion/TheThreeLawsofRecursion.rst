..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: rec-3-
   :start: 1

The Three Laws of Recursion
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Like the robots of Asimov, all recursive algorithms must obey three
important laws:

#. A recursive algorithm must have a **base case**. 

#. A recursive algorithm must have a **recursive case** in which it calls itself.

#. A recursive algorithm must converge toward the base
   case in its recursive case.


Let’s look at each one of these laws in more detail and see how it was
used in the ``listsum`` algorithm. First, a base case is the condition
that allows the algorithm to stop. Without it, the algorithm would
keep calling itself and never end. A base case is typically a
problem that is small enough to solve directly. In the ``listsum``
algorithm the base case is a list of length 1.

The second law is that the algorithm must call itself. This is the very
definition of recursion. Recursion is a confusing concept to many
beginning programmers. As a novice programmer, you have learned that
functions are good because you can take a large problem and break it up
into smaller problems. The smaller problems can be solved by writing a
function to solve each problem. When we talk about recursion it may seem
that we are talking ourselves in circles. We have a problem to solve
with a function, but that function solves the problem by calling itself!
But the logic is not circular at all; the logic of recursion is an
elegant expression of solving a problem by breaking it down into a
smaller and easier problems.

To obey the third law, the algorithm's recursive case must "move toward" the base case.
This means the parameter that is passed in the recursive call must have a value
that is "closer" to the value that triggers the base case. 
Usually, this means the data that
represents our problem gets smaller in some way. In the ``listsum``
algorithm our primary data structure is a list. Since the base case is a list of
length 1, a natural progression toward the base case is to shorten the
list. This is exactly what happens on line 5 of :ref:`listsum <lst_recsum>` when we call ``listsum`` with a shorter list.

If an algorithm fails to obey either the first or the third laws (or both), it will suffer from a problem called
**infinite recursion**. Like an infinite loop, an algorithm that does not include a base case, or whose recursive case
fails to converge towards the base case, will never end. However, in Python, infinitely recursive functions will fail
with a crash (caused by a ``RecursionError`` exception). The reason is because each recursive call stores information about the
recursive function's parameters and local variables in a small chunk of memory called an **activation record**, and the
region of memory dedicated to holding activation records is relatively small in Python. You can think of it as being
able to manage about 1,000 recursive invocations. So, in a Python recursive function with no base case, or where the
recursive calls don't converge to the base case, after about 1,000 invocations Python will terminate the function with
an exception.

Because of the limit Python places on the number of recursive invocations, even properly designed recursive functions
will fail to execute correctly in Python, if they need more than about 1,000 recursive calls to finish.
To see this in action, try the following example, which defines a function that adds up the numbers from 0 to *n*:

.. activecode:: ac_infrecur

   def sumup(n):
      if n == 0:
         return 0
      else:
         return n + sumup(n - 1)

   print(sumup(1000))
   print(sumup(10000))

In the ActiveCode interpreter used in this book, the first call succeeds, but the second call fails. If you try this
out in a real Python interpreter, the default recursion limit will cause the first call to fail.

Because of this practical limitation, even if you decide you love recursion and want to use it a lot in your programs,
it cannot be used to replace all for loops and while loops.

.. admonition:: Think about it

   Suppose line 5 in the example above were written as follows::

      return n + sumup(n + 1)

   This is a logic error. Which of the three laws of recursion would be violated? What would happen? Try it and see. Change line 5,
   and experiment with calling sumup with different parameter values to see what happens.

In the remainder of this chapter we will look at more examples of
recursion. In each case we will focus on designing a solution to a
problem by using the three laws of recursion.


**Check your understanding**

.. mchoice:: question_recsimp_2
   :practice: T
   :correct: d
   :answer_a: n == 0
   :answer_b: n == 1
   :answer_c: n &gt;= 0
   :answer_d: n &lt;= 1
   :feedback_a:  Although this would work there are better and slightly more efficient choices, since fact(1) and fact(0) are the same.
   :feedback_b: A good choice, but what happens if you call fact(0)?
   :feedback_c: This base case would be true for all numbers greater than zero, so fact of any positive number would be 1.
   :feedback_d: Good. This is the most efficient, and even keeps your program from crashing if you try to compute the factorial of a negative number.

   Suppose you are going to write a recusive function to calculate the factorial of a number.  fact(n) returns n * n-1 * n-2 * ... * 1, and the factorial of zero is defined to be 1.  What would be the most appropriate base case?

.. mchoice:: question_recsimp_3
   :practice: T
   :correct: a,c
   :answer_a: The first law (no base case)
   :answer_b: The second law (no recursive case)
   :answer_c: The third law (recursive case does not converge to base case)
   :answer_d: None are violated
   :feedback_a: Correct. There is no base case.
   :feedback_b: Incorrect. The function calls itself.
   :feedback_c: Correct, since there is no base case.
   :feedback_d: Incorrect.

   Consider the following recursive function. Which of the three laws is violated?

   ::

      def fact(n):
         return n * fact(n-1)

.. mchoice:: question_recsimp_4
   :practice: T
   :correct: c
   :answer_a: The first law (no base case)
   :answer_b: The second law (no recursive case)
   :answer_c: The third law (recursive case does not converge to base case)
   :answer_d: None are violated
   :feedback_a: Incorrect. There is a base case.
   :feedback_b: Incorrect. The function calls itself.
   :feedback_c: Correct; fact(n+1) does not decrease n.
   :feedback_d: Incorrect.

   Consider the following recursive function. Which of the three laws is violated?

   ::

      def fact(n):
         if n <= 1:
            return 0
         else:
            return n * fact(n+1)
