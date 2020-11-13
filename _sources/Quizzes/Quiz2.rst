.. qnum::
   :prefix: quiz-2
   :start: 1

Code Quiz 2
===========

Part 1
------

.. actex:: ac_quiz2-1
    :autograde: unittest
    :timelimit: 1000

    (35 points) Write a function named ``countVowels``. It should receive a string parameter, and return an int
    indicating the count of capital vowels it contains (A, E, I, O, or U). For example, 

    * countVowels('DOGGIE') == 3
    * countVowels('WAha') == 1
    * countVowels('doggie') == 0    
    
    ~~~~


    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(countVowels('FOGGIE'), 3, "Test 1: countVowels('DOGGIE') == 3")
            self.assertEqual(countVowels('AAEIOU'), 6, "Test 2: countVowels('AAEIOU') == 6")
            self.assertEqual(countVowels('doggie'), 0, "Test 3: countVowels('doggie') == 0")

    myTests().main()


Part 2
------

.. actex:: ac_quiz2-2
    :autograde: unittest
    :timelimit: 1000

    (15 points) Write a function named extractDigits that takes a parameter containing a string, extracts all of the
    digits, and returns the resulting integer. If there are no digits, return 0.

    For example,

    * extractDigits('ab12c3') == 123
    * extractDigits ('D') == 0
 
    
    ~~~~


    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(extractDigits('ab42c3'), 423, "Test 1: extractDigits('ab12c3') == 123 (10 points)")
            self.assertEqual(extractDigits('abc'), 0, "Test 2: extractDigits('abc') == 0 (5 points)")

    myTests().main()


