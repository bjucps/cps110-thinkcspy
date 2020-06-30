..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

.. qnum::
   :prefix: func-14-
   :start: 1

Exercises
=========
#.

    .. tabbed:: q1

        .. tab:: Question

           .. actex:: ac11_14_1

              Write a function named ``num_test`` that takes a number as input. If the number is greater than 10, the function should return "Greater than 10." If the number is less than 10, the function should return "Less than 10." If the number is equal to 10, the function should return "Equal to 10."
              ~~~~
              

              ====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                def testOne(self):
                    self.assertEqual(num_test(5), "Less than 10.", "Testing the num_test function on input 5.")
                    self.assertEqual(num_test(0), "Less than 10.", "Testing the num_test function on input 0.")
                    self.assertEqual(num_test(12.99), "Greater than 10.", "Testing the num_test function on input 12.99.")
                    self.assertEqual(num_test(10.00), "Equal to 10.", "Testing the num_test function on input 10.00.")



              myTests().main()

#.

    .. tabbed:: q2

        .. tab:: Question

           .. actex:: ac11_14_2

              Write a function that will return the number of digits in an integer.
              ~~~~
              def numDigits(n):
                  # your code here

              ====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                def testOne(self):
                    self.assertEqual(numDigits(2),1,"Tested numDigits on input of 2")
                    self.assertEqual(numDigits(55),2,"Tested numDigits on input of 55")
                    self.assertEqual(numDigits(1352),4,"Tested numDigits on input of 1352")
                    self.assertEqual(numDigits(444),3,"Tested numDigits on input of 444")



              myTests().main()

        .. tab:: Tip

            Consider converting the integer to a string and using the ``len`` function to find out
            how many digits it contains.


        .. tab:: Answer

            .. activecode:: answer11_14_2

                def numDigits(n):
                    n_str = str(n)
                    return len(n_str)


                print(numDigits(50))
                print(numDigits(20000))
                print(numDigits(1))

#.

    .. tabbed:: q13

        .. tab:: Question

            .. actex:: ac11_14_13
                :nocodelens:

                Write a function ``findHypot``.  The function will be given the length of two sides of a right-angled triangle and it should return the length of the hypotenuse. (Hint:  ``x ** 0.5`` will return the square root, or use ``sqrt`` from the math module)
                ~~~~

                def findHypot(a,b):
                    # your code here

                ====

                from unittest.gui import TestCaseGui

                class myTests(TestCaseGui):
                    def testOne(self):
                        self.assertEqual(findHypot(12.0,5.0),13.0,"Tested findHypot on inputs of 12.0 and 5.0")
                        self.assertEqual(findHypot(14.0,48.0),50.0,"Tested findHypot on inputs of 14.0 and 48.0")
                        self.assertEqual(findHypot(21.0,72.0),75.0,"Tested findHypot on inputs of 21.0 and 72.0")
                        self.assertAlmostEqual(findHypot(1,1.73205),1.999999,2,"Tested findHypot on inputs of 1 and 1.73205")

                myTests().main()

#.
   .. tabbed:: q14

        .. tab:: Question

           .. actex:: ac11_14_14
               :nocodelens:

               Write a function called ``is_even(n)`` that takes an integer as an argument and returns ``True`` if the argument is an **even number** and ``False`` if it is **odd**.
               ~~~~
               def is_even(n):
                   #your code here

               ====

               from unittest.gui import TestCaseGui

               class myTests(TestCaseGui):
                    def testOne(self):
                        self.assertEqual(is_even(10),True,"Tested is_even on input of 10")
                        self.assertEqual(is_even(5),False,"Tested is_even on input of 5")
                        self.assertEqual(is_even(1),False,"Tested is_even on input of 1")
                        self.assertEqual(is_even(0),True,"Tested is_even on input of 0")

               myTests().main()

#.
   .. tabbed:: q15

        .. tab:: Question

           .. actex:: ac11_14_15
               :nocodelens:

               Now write the function ``is_odd(n)`` that returns ``True`` when ``n`` is odd and ``False`` otherwise.
               ~~~~

               def is_odd(n):
                   # your code here


               ====
               from unittest.gui import TestCaseGui

               class myTests(TestCaseGui):
                   def testOne(self):
                       self.assertEqual(is_odd(10),False,"Tested is_odd on input of 10")
                       self.assertEqual(is_odd(5),True,"Tested is_odd on input of 5")
                       self.assertEqual(is_odd(1),True,"Tested is_odd on input of 1")
                       self.assertEqual(is_odd(0),False,"Tested is_odd on input of 0")

               myTests().main()



#.
   .. tabbed:: q16

        .. tab:: Question

           .. actex:: ac11_14_16

               Write a function ``is_rightangled`` which, given the length of three sides of a triangle, will determine whether the triangle is right-angled. Assume that the third argument to the function is always the longest side. It will return ``True`` if the triangle is right-angled, or ``False`` otherwise.

               Hint: floating point arithmetic is not always exactly accurate,
               so it is not safe to test floating point numbers for equality.
               If a good programmer wants to know whether
               ``x`` is equal or close enough to ``y``, they would probably code it up as
   
               .. sourcecode:: python
   
                   if  abs(x - y) < 0.001:      # if x is approximately equal to y
                       ...

               ~~~~
               def is_rightangled(a, b, c):
                   # your code here


               ====
               from unittest.gui import TestCaseGui

               class myTests(TestCaseGui):
                   def testOne(self):
                       self.assertEqual(is_rightangled(1.5,2.0,2.5),True,"Tested is_rightangled on inputs of 1.5, 2.0 and 2.5")
                       self.assertEqual(is_rightangled(4.0,8.0,16.0),False,"Tested is_rightangled on inputs of 4.0, 8.0 and 16.0")
                       self.assertEqual(is_rightangled(4.1,8.2,9.1678787077),True,"Tested is_rightangled on inputs of 4.1, 8.2 and 9.1678787077")
                       self.assertEqual(is_rightangled(4.1,8.2,9.16787),True,"Tested is_rightangled on inputs of 4.1, 8.2, and 9.16787")
                       self.assertEqual(is_rightangled(4.1,8.2,9.168),False,"Tested is_rightangled on inputs of 4.1, 8.2 and 9.168")
                       self.assertEqual(is_rightangled(0.5,0.4,0.64031),True,"Tested is_rightangled on inputs of 0.5, 0.4 and 0.64031")

               myTests().main()
