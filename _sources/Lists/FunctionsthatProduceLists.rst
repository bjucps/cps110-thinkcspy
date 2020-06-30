..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: list-21-
   :start: 1

Functions that Produce Lists
----------------------------

Here is a function that creates and produces a list of random numbers:

.. activecode:: ch09_mod2

    import random

    def make_random_list(size):
        """ Return a list of random values in the range [0..9]. """
        new_list = []
        for value in range(size):
            value = random.randrange(10)
            new_list.append(value)
        return new_list
    
    print(make_random_list(5))

Whenever you need to write a function that creates and returns a list, the pattern is
usually::

    initialize a result variable to be an empty list
    loop
       create a new element 
       append it to result
    return the result

Compare the pattern to the code above, then try your hand at solving the problem below.


**Check Your Understanding**

.. tabbed:: make_list

    .. tab:: Question

        Write a function named ``multiples_of_n`` that returns a list of numbers
        from 0 to 100 that are multiples of ``n``, where ``n`` is the 
        parameter. See the assert below for an example of what the function
        should do.


        .. activecode:: ac_make_list
            :practice: T
            :autograde: unittest

            def multiples_of_n(n: int) -> list:
                """Returns a list of multiples of `n` in the range [0..100]"""

            
            result = multiples_of_n(25)
            print(result)
            assert result == [0, 25, 50, 75, 100]

            ====

            from unittest.gui import TestCaseGui
            class myTests(TestCaseGui):
                def testOne(self):
                    self.assertEqual(multiples_of_n(25), [0, 25, 50, 75, 100], "multiples_of_n(25) correct?"  )
                    self.assertEqual(multiples_of_n(15), [0, 15, 30, 45, 60, 75, 90], "multiples_of_n(15) correct?"  )

            myTests().main()

    .. tab:: Tip

        This one is pretty easy if you use the form of the range function that takes an increment. Example::

            for i in range(0, 10, 2):

    .. tab:: Solution

        Here's one solution:

        .. sourcecode:: python

            def multiples_of_n(n: int) -> list:
                result = []
                for i in range(0, 101, n):
                    result.append(i)
                return result

