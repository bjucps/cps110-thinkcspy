..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Exercises
---------

.. question:: q_coinflip

    .. tabbed:: tab_coinflip

        .. tab:: Question

            .. actex:: ac_coinflip
                :autograde: unittest
                :practice: T

                The following program simulates a number of coin flips by generating random numbers.
                Enhance the program so that it counts the number of times that the coin came up
                'heads' and the number of times that the coin came up 'tails'. Store the number of
                times the coin was 'heads' in the variable **head_count**, and the number of times
                the coin was 'tails' in **tail_count**. 
        
                ~~~~

                import random

                for i in range(10):
                    num = random.randrange(0, 2) # Generate a number that is either 0 or 1
                    if num == 0:
                        print("Heads ...")
                    else:
                        print("Tails ...")

                print(head_count, 'heads total')
                print(tail_count, 'tails total')
                ====

                from unittest.gui import TestCaseGui

                class myTests(TestCaseGui):

                    def testOne(self):
                        self.assertIn(str(self.getOutput().split('\n').count('Heads ...')) + ' heads total', self.getOutput(), "Correct heads count?")
                        self.assertIn(str(self.getOutput().split('\n').count('Tails ...')) + ' tails total', self.getOutput(), "Correct tails count?")

                myTests().main()

        .. tab:: Tip

            Review :ref:`accumulator`.
           
        .. tab:: Answer

            This solution uses the accumulator pattern.

            .. activecode:: ac_coinflip_ans
                :optional:

                import random

                head_count = 0
                tail_count = 0
                for i in range(10):
                    num = random.randrange(0, 2) # Generate a number that is either 0 or 1
                    if num == 0:
                        head_count = head_count + 1
                        print("Heads ...")
                    else:
                        tail_count = tail_count + 1
                        print("Tails ...")

                print(head_count, 'heads total')
                print(tail_count, 'tails total')

                 
.. question:: q_score2grade

    .. tabbed:: tab_score2grade

        .. tab:: Question

            .. actex:: ac7_14_1
                :autograde: unittest
                :practice: T

                Write a program that code that converts numeric scores to letter grades. The letter grades should be computed according to the table below.
        
                .. table::
        
                  =======   =====
                  Score     Grade
                  =======   =====
                  >= 90     A
                  [80-90)   B
                  [70-80)   C
                  [60-70)   D
                  < 60      F
                  =======   =====
        
                The square and round brackets denote closed and open intervals.
                A closed interval includes the number, and open interval excludes it. So 79.99999 gets grade C, but 80 gets grade B.
                ~~~~

                for score in [58, 69, 85, 73, 90]:
                    grade = ''

                    # Write code here to assign grade the appropriate letter based on the value of score

                    print(score, '-', grade)

                ====

                from unittest.gui import TestCaseGui

                class myTests(TestCaseGui):

                    def testOne(self):
                        self.assertIn('58 - F', self.getOutput(), "58 - F")
                        self.assertIn('69 - D', self.getOutput(), "69 - D")
                        self.assertIn('85 - B', self.getOutput(), "85 - B")
                        self.assertIn('73 - C', self.getOutput(), "73 - C")
                        self.assertIn('90 - A', self.getOutput(), "90 - A")

                myTests().main()
           
        .. tab:: Answer

            .. activecode:: ans7_14_1
                :optional:
            
                for score in [58, 69, 85, 73, 90]:
                    grade = ''
               
                    if score < 60:
                        grade = "F"
                    elif score < 70:
                        grade = "D"
                    elif score < 80:
                        grade = "C"
                    elif score < 90:
                        grade = "B"
                    else:
                        grade = "A"
                        
                    print(score, '-', grade)
                 
