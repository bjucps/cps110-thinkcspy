.. qnum::
   :prefix: quiz-2
   :start: 1

Quiz 2
======

Part 1
------

.. actex:: ac_quiz2-1
    :autograde: unittest

    (25 points) Write a function named ``countVowels``. It should receive a string parameter, and return an int
    indicating the count of capital vowels it contains (A, E, I, O, or U). For example, 

    * countVowels('DOGGIE') == 3
    * countVowels('WAha') == 1
    * countVowels('doggie') == 0    
    
    ~~~~


    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(countVowels('DOGGIE'), 3, "Test 1: countVowels('DOGGIE') == 3 (15 points)")
            self.assertEqual(countVowels('aaeiou'), 6, "Test 2: countVowels('AAEIOU') == 6 (5 points)")
            self.assertEqual(countVowels('doggie'), 0, "Test 3: countVowels('doggie') == 0 (5 points)")

    myTests().main()

Solution::

    def countVowels(s):

        count = 0
        for l in s:
            if l in ['A', 'E', 'I', 'O', 'U']:
                count += 1

        return count

Part 2
------

.. actex:: ac_quiz2-2
    :autograde: unittest

    (25 points) Write a function named extractDigits that takes a parameter containing a string, extracts all of the
    digits, and returns the resulting integer. If there are no digits, return 0.

    For example,

    * extractDigits('ab12c3') == 123
    * extractDigits ('D') == 0
 
    
    ~~~~


    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(extractDigits('ab12c3'), 123, "Test 1: extractDigits('ab12c3') == 123 (15 points)")
            self.assertEqual(extractDigits('abc'), 0, "Test 1: extractDigits('ab12c3') == 0 (10 points)")

    myTests().main()


Solution::

    def extractDigits(s):

        result = '0'
        for d in s:
            if d >= '0' and d <= '9':
                result += d

        return int(result)
