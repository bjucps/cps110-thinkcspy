.. qnum::
   :prefix: python-practice
   :start: 1

Python Practice
===============

On this page are a set of practice problems to go along with the python lectures.  The total set of problems counts as one quiz grade and each problem is worth one point.

Holiday
-------

.. actex:: hr_holiday
    :autograde: unittest

    It is possible to name the days 0 through 6 where day 0 is Sunday and day 6 is Saturday. If you go on a wonderful holiday leaving on day number 3 (a Wednesday) and you return home after 10 nights you would return home on a Saturday (day 6). Write a general version of the program which asks for the starting day number, and the length of your stay, and it will tell you the number of day of the week you will return on.

    Read two numbers from standard input and print the return day.

    **Sample Input 0**
    
        2

        3
    
    **Sample Output 0**

        5
    
    **Explanation 0**

    If the user leaves on day Tuesday and is on vacation 3 days, the user will return on day 5 (Friday).

    **Sample Input 1**

        5

        3

    **Sample Output 1**

        1
    
    **Explanation 1**

    If the user leaves on day Friday and is gone for 3 days, the user will return on Monday (day 1).
    ~~~~
    leaveDay = # get input 1
    daysGone = # get input 2
    returnDay = # calculate return day
    print(returnDay)
    ====
    from unittest.gui import TestCaseGui
    from re import sub
    class myTests(TestCaseGui):
        def testOne(self):
            code = self.getEditorText()
            sub("input\([^\)]*\)", "2", code, 1)
            sub("input\([^\)]*\)", "3", code, 1)
            value = exec(code)
            self.assertEqual(value, "5", "day 2 + 3 days is day 5")
        def testTwo(self):
            code = self.getEditorText()
            sub("input\([^\)]*\)", "5", code, 1)
            sub("input\([^\)]*\)", "3", code, 1)
            value = exec(code)
            self.assertEqual(value, "1", "day 5 + 3 days is day 1")
        def testThree(self):
            code = self.getEditorText()
            sub("input\([^\)]*\)", "5", code, 1)
            sub("input\([^\)]*\)", "20", code, 1)
            value = exec(code)
            self.assertEqual(value, "4", "day 5 + 20 days is day 4")
    myTests().main()


