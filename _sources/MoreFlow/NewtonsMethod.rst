..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-6-
   :start: 1

.. index:: Newton

Newton's Method
===============

Loops are often used in programs that compute numerical results by starting
with an approximate answer and iteratively improving it.

For example, one way of computing square roots is Newton's method.  Suppose
that you want to know the square root of ``n``. If you start with almost any
approximation, you can compute a better approximation with the following
formula:

.. sourcecode:: python

    better =  1/2 * (approx + n/approx)

Execute this algorithm a few times using your calculator.  Can you
see why each iteration brings your estimate a little closer?  One of the amazing
properties of this particular algorithm is how quickly it converges to an accurate
answer.

The following implementation of Newton's method uses a ``for`` loop to perform the
iterations.

.. activecode:: chp07_newtonsdef

    n = 100         # Compute square root of this number
    howmany = 10    # Number of iterations
    approx = 0.5 * n
    for i in range(howmany):
        betterapprox = 0.5 * (approx + n/approx)
        approx = betterapprox

    print('Square root of', n, 'is about', approx)

Step through the program using **Show CodeLens** to see how ``approx`` changes in each
iteration to converge towards the correct answer. This algorithm is a variation of the
accumulator pattern we've seen before, because ``approx`` "accumulates" the correct value
over several iterations.

.. admonition:: Modify the program ...

   This program produces the correct square root for ``n`` = 100.  However, were 10 iterations required to get the
   correct answer? Experiment with different values for the ``howmany``. Find the **smallest** value for ``howmany``
   that will produce the **correct** result. Then, repeat your experiment, this time with ``n`` = 4, and then again with
   ``n`` = 1. 

Revising with Indefinite Iteration
----------------------------------

Repeating more than the required number of times is a waste of computing resources. So definite iteration is not a good solution to this problem.

In general, Newton's algorithm will eventually reach a point where the new approximation is no better than the previous.  At that point, we could simply stop.
In other words, by repeatedly applying this formula until the better approximation gets close
enough to the previous one, we can write a function for computing the square root that uses the number of iterations necessary and no more.

Take a look at the implementation of Newton's algorithm below that uses a ``while`` loop to execute instead of a ``for``
loop. This loop, like the one above, executes a fixed number of iterations. However, because we've written it as a ``while``
loop, we can easily change the loop condition to make the loop repeat just long enough until the approximation is no longer changing. 

.. tabbed:: tab_chp07_newtonswhile

    .. tab:: Question

        Replace the loop condition ``num_iterations < 10`` with a different condition that stops the loop when the
        approximation is no longer changing. The activecode interpreter will check your work for correctness.

        .. activecode:: chp07_newtonswhile

            n = 10
            approx = 0.5 * n
            betterapprox = 0.5 * (approx + n/approx)
            num_iterations = 0
            while num_iterations < 10:
                approx = betterapprox
                betterapprox = 0.5 * (approx + n/approx)
                num_iterations += 1

            print('Square root of', n, 'is about', approx)
            print('It took', num_iterations, 'iterations to compute.')

            ====

            from unittest.gui import TestCaseGui
            class myTests(TestCaseGui):
                def testOne(self):
                    self.assertEqual(approx == betterapprox, True, "approx == betterapprox?"  )
                    self.assertNotIn('while num_iterations', self.getEditorText(), "loop condition must not use num_iterations")
            myTests().main()

    .. tab:: Tip

        We want the loop to stop when ``approx`` and ``betterapprox`` are equal.

    .. tab:: Solution

        We want the loop to continue until ``approx`` and ``betterapprox`` are equal. So one condition to use is:
        ``betterapprox != approx``. If you didn't come up with that, plug it in and try it out with different
        values for ``n``.
        

Comparing Floats
----------------

The solution presented above compares two floating point values using the inequality operator. In this case, we want the
loop to stop when there are no changes in the approximation, so using the inequality operator is an appropriate
technique for this program. However, *in general,* comparing floats for equality or inequality in any programming language
carries an element of risk. Since floating point numbers in computers are themselves an approximation of real numbers in
mathematics, the small rounding errors that creep into calculations using these values can result in situations where
two floating point values are nearly equal, but not quite, and comparing them with ``==`` or ``!=`` will yield
surprising and undesirable results. 

For example, look at the following program. What do you expect it to display? Run it and see what happens.

.. activecode:: ac_compare_floats

    a = .2
    b = .2
    if a + b == .4:
        print('Equal')
    else:
        print('Not Equal')

    a = .1
    b = .2
    if a + b == .3:
        print('Equal')
    else:
        print('Not Equal')

In a computer, the numbers .1, .2, .3, and .4 are all represented in base 2 as *approximations* of their
true values. In this program, the result of adding the approximations of .2 and .2 yielded a value that was
equivalent to the approximation of .4, but adding the approximations of .1 and .2 yielded a value that was slightly
different from the approximation of .3. 

Python provides the ``isclose`` function in the ``math`` module to help deal with this problem. It compares two floats and
returns ``True`` if they are "close enough" to be considered equal. You should use it anywhere
you would want to compare two floats with ``==``, like this::

    import math

    a = .1
    b = .2
    if math.isclose(a + b, .3):
        print('Equal')
    else:
        print('Not Equal')

For more details about ``isclose``, look it up in the Python Standard Library documentation.

For further reading on this fascinating subject, have a look at the section on `floating point in the Python documentation
<https://docs.python.org/3/tutorial/floatingpoint.html>`_, or better yet, take a computer science course in numerical analysis.

