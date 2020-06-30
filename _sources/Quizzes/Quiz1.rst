.. qnum::
   :prefix: quiz-1
   :start: 1

Quiz 1
======

Part 1
------

.. actex:: ac_quiz1-1
    :autograde: unittest

    #. (10 points) Ask the user to enter an integer. Store it as an int in a variable named ``num``. 

    #. (5 points) Next, compute the value 3 + num and store in a variable named ``sum``. 
    
    #. (5 points) Next, divide the value in num by 2 (using integer division) and store in a variable named ``quotient``.

    #. (10 points) Finally, display a line containing the sum and the quotient, formatted as follows:
    
       *sum*, *quotient*

       For example, if the sum was 10 and the quotient was 5, display:

       10, 5
    
    ~~~~


    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(type(num), int, "Test 1: num is an int (10 points)")
            self.assertEqual(sum, 3 + num, "Test 2: sum = 3 + num (5 points)")
            self.assertEqual(type(quotient), int, "Test 3: quotient is an int (2 points)")
            self.assertEqual(quotient, num // 2, "Test 4: quotient = num // 2 (3 points)")
            self.assertEqual(self.getOutput().strip().replace(' ', ''), f"{sum},{quotient}", "Test 5: Correct values output (5 points)")
            self.assertEqual(self.getOutput().strip(), f"{sum}, {quotient}", "Test 6: Correct output format (5 points)")

    myTests().main()


Part 2
------

.. actex:: ac_quiz1-2
    :autograde: unittest

    (10 points) Write a loop that iterates over a list of three words: "green", "red", "blue". Put an if statement inside the
    loop that checks the length of each word, and if it is longer than 3 characters, display "word is one of my favorite
    words" substituting the user's entry in place of *word*. The correct output should be::
    
        green is one of my favorite words
        blue is one of my favorite words
    
    ~~~~


    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(self.getOutput().strip(), "green is one of my favorite words\nblue is one of my favorite words", "Test 1: Correct output (10 points)")
            self.assertIn("for", self.getEditorText(), "Test 2: Uses for loop")

    myTests().main()

Solution::

    for color in ["green", "red", "blue"]:
        if len(color) > 3:
            print(f"{color} is one of my favorite words")

.. note::

    5 points if there are misspellings or formatting issues
    0 points if a for loop was not used, or if "red" is displayed


Part 3
------

.. actex:: ac_quiz1-3
    :autograde: unittest

    (10 points) Write a loop that adds up the numbers from 1 to 100 that are evenly divisible by 10. Put the final sum in a variable named ``sum``. 
    
    ~~~~


    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertTrue(sum in [450, 550], "Test 1: Upper bound >= 99 (5 points)")
            self.assertEqual(sum, 550, "Test 2: Correct output (5 points)")
            self.assertIn("for", self.getEditorText(), "Test 2: Uses for loop")

    myTests().main()

Solution::

    sum = 0
    for i in range(0, 101, 10):
        sum += i
            

Part 4
------

.. actex:: ac_quiz1-4
    :autograde: unittest

    (Bonus 5 points) Write a loop that adds up the numbers from 1 to 100 that are evenly divisible by 4, but are not evenly
    divisible by 3. Put the final sum in a variable named ``sum``. 
    
    ~~~~


    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(sum, 768, "Test 1: Correct output (5 points)")
            self.assertIn("for", self.getEditorText(), "Test 2: Uses for loop")

    myTests().main()

Solution::

    sum = 0
    for i in range(0, 100, 4):
        if i % 3 != 0:
            sum += i
