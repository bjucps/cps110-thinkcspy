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

.. question:: lists_ex_1
   :number: 1

   .. tabbed:: q1

        .. tab:: Question

           Draw a reference diagram for ``a`` and ``b`` before and after the third line of
           the following python code is executed:

           .. sourcecode:: python

               a = [1, 2, 3]
               b = a[:]
               b[0] = 5

        .. tab:: Answer

            Your diagram should show two variables referring to two different lists.  ``a`` refers to the original list with 1,2, and 3.
            ``b`` refers to a list with 5,2, and 3 since the zero-eth element was replaced with 5.


.. question:: lists_ex_2

    .. tabbed:: tab_lists_ex_2

        .. tab:: Question

            .. actex:: ac_lists_ex_2

                Create a list called ``myList`` with the following six items: 76, 92.3, "hello", True, 4, 76. 
                Begin with the empty list shown below, and add 6 statements to add each item, one per item. The first three statements should
                use the append method to append the item to the list, and the last three statements should use concatenation.
                ~~~~

                myList = []

                # Your code here

                ====
                from unittest.gui import TestCaseGui

                class myTests(TestCaseGui):

                    def testOne(self):
                        self.assertEqual(myList,[76, 92.3, 'hello', True, 4, 76],"myList should contain the specified items")
                        self.assertIn(".append(", self.getEditorText(), 'append method must be used')

                myTests().main()                

        .. tab:: Answer

            .. activecode:: ac_lists_ex_2_answer
                :optional:

                myList = []
                myList.append(76)
                myList.append(92.3)
                myList.append("hello")
                myList = myList + [True]
                myList = myList + [4]
                myList = myList + [76]
                print(myList)



.. question:: lists_ex_3

   .. tabbed:: q3

        .. tab:: Question

           .. actex:: ex_9_3

              Starting with the list of the previous exercise, write Python statements to do the following:
   
              a. Append "apple" and 76 to the list.
              #. Insert the value "cat" at position 3.
              #. Insert the value 99 at the start of the list.
              #. Find the index of "hello".
              #. Count the number of 76s in the list.
              #. Remove the first occurrence of 76 from the list.
              #. Remove True from the list using ``pop`` and ``index``.
              ~~~~
              myList = [76, 92.3, 'hello', True, 4, 76]

              # Your code here

        .. tab:: Answer

           .. activecode:: ex_9_3_answer
              :optional:

              myList = [76, 92.3, 'hello', True, 4, 76]

              myList.append("apple")         # a
              myList.append(76)              # a
              myList.insert(3, "cat")        # b
              myList.insert(0, 99)           # c

              print(myList.index("hello"))   # d
              print(myList.count(76))        # e
              myList.remove(76)              # f
              myList.pop(myList.index(True)) # g

              print (myList)


.. question:: lists_ex_4

   .. tabbed:: q4

        .. tab:: Question

            .. actex:: ex_9_4

                Create a list named ``randlist`` containing 100 random integers between 0 and 1000 (use iteration, append, and the random module). 
                ~~~~

                ====
                from unittest.gui import TestCaseGui

                class myTests(TestCaseGui):

                    def testOne(self):
                        self.assertEqual(len(randlist),100,"randlist should contain 100 numbers")

                myTests().main()

        .. tab:: Answer

            .. activecode:: ac_ex_9_4
                :optional:

                import random

                randlist = []
                for i in range(100):
                    randlist.append(random.randint(0, 1000))

.. question:: lists_ex_4b

   .. tabbed:: q4b

        .. tab:: Question

            .. actex:: ex_9_4b

                Write a function called ``average`` that will take a list of numbers as a parameter and return the average of the numbers.
                ~~~~
                def average(numlist):
                    # Complete the function definition

                ====
                from unittest.gui import TestCaseGui

                class myTests(TestCaseGui):

                    def testOne(self):
                        self.assertEqual(int(average([1, 3, 5, 7])),4,"average([1, 3, 5, 7]) should be 4")

                myTests().main()

        .. tab:: Tip

            Review :ref:`accumulator_lists`.

        .. tab:: Answer

            .. activecode:: ac_ex_9_4b
                :optional:

                def average(numlist):

                    total = 0
                    for num in numlist:
                        total = total + num

                    return total / len(numlist)   


.. question:: lists_ex_5

   .. tabbed:: q5

        .. tab:: Question

           .. actex:: ex_9_5

                Write a Python function that will take a nonempty list of integers whose values are in the range [0..1000] and return the smallest value.  (Note: there is a builtin function named ``min`` but pretend you cannot use it.)
                ~~~~

                def min(lst):
                    # Complete the function definition

                ====
                from unittest.gui import TestCaseGui

                class myTests(TestCaseGui):

                    def testOne(self):
                        self.assertEqual(min([31, 3, 5, 7])),31,"min([31, 3, 5, 7]) should be 3")

                myTests().main()

        .. tab:: Tip

            Review :ref:`accumulator_lists`.

        .. tab:: Answer

            .. activecode:: lst_q5_answer
                :optional:

                def min(lst):
                    min = 0
                    for e in lst:
                        if e < min:
                            min = e
                    return min

                print(min([5, 100, 13, 2, 19]))


.. question:: lists_ex_5b

   .. tabbed:: q5b

        .. tab:: Question

           .. actex:: ex_9_5b

                Write a Python function named join_star that will take a nonempty list of strings and return a string 
                containing all of the nonempty strings in the list, with an asterisk between each. The list should
                contain an asterisk at the beginning and at the end.

                For example::

                    join_star(["the","","cat","ate","","my","hat"])

                should return the value::

                    "*the*cat*ate*my*hat*"


                ~~~~

                def join_star(lst):
                    # Complete the function definition

                ====
                from unittest.gui import TestCaseGui

                class myTests(TestCaseGui):

                    def testOne(self):
                        self.assertEqual(join_star(["a","","b","c"]),"*a*b*c*", 'join_star(["a","","b","c"]) should be "*a*b*c*"')

                myTests().main()

        .. tab:: Tip

            Review :ref:`accumulator_lists`.

        .. tab:: Answer

            .. activecode:: lst_q5b_answer
                :optional:

                def join_star(lst):
                    result = "*"
                    for item in lst:
                        if item != '':
                            result += item + '*'

                    return result

                print(join_star(['the', '', 'cat', 'ate', '', 'my', 'hat']))

.. question:: lists_ex_6

   .. actex:: ex_7_11
      :practice: T
      :autograde: unittest

      Write a function ``sum_of_squares(xs)`` that computes the sum
      of the squares of the numbers in the list ``xs``.  For example,
      ``sum_of_squares([2, 3, 4])`` should return 4+9+16 which is 29:
      ~~~~   
      def sum_of_squares(xs):
          # your code here

      ====
      from unittest.gui import TestCaseGui

      class myTests(TestCaseGui):

          def testOne(self):
              self.assertEqual(sum_of_squares([2,3,4]),29,"Tested sum_of_squares on input [2,3,4]")
              self.assertEqual(sum_of_squares([0,1,-1]),2,"Tested sum_of_squares on input [0,1,-1]")
              self.assertEqual(sum_of_squares([5,12,14]),365,"Tested sum_of_squares on input [5,12,14]")

      myTests().main()

.. question:: lists_ex_7

   .. tabbed:: q7

        .. tab:: Question

           .. actex:: ex_9_6
              :practice: T
              :autograde: unittest

              Write a function to count how many odd numbers are in a list.
              ~~~~
              def countOdd(lst):
                  # your code here

              ====
              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(countOdd([1,3,5,7,9]),5,"Tested countOdd on input [1,3,5,7,9]")
                      self.assertEqual(countOdd([1,2,3,4,5]),3,"Tested countOdd on input [-1,-2,-3,-4,-5]")
                      self.assertEqual(countOdd([2,4,6,8,10]),0,"Tested countOdd on input [2,4,6,8,10]")
                      self.assertEqual(countOdd([0,-1,12,-33]),2,"Tested countOdd on input [0,-1,12,-33]")

              myTests().main()



        .. tab:: Answer

            .. activecode:: lst_q7_answer
                :optional:

                import random

                def countOdd(lst):
                    odd = 0
                    for e in lst:
                        if e % 2 != 0:
                            odd = odd + 1
                    return odd

                # make a random list to test the function
                lst = []
                for i in range(100):
                    lst.append(random.randint(0, 1000))

                print(countOdd(lst))


.. question:: lists_ex_8

   .. actex:: ex_9_7
      :practice: T
      :autograde: unittest

      Sum up all the even numbers in a list.
      ~~~~
      def sumEven(lst):
          # your code here

      ====
      from unittest.gui import TestCaseGui

      class myTests(TestCaseGui):

          def testOne(self):
              self.assertEqual(sumEven([1,3,5,7,9]),0,"Tested sumEven on input [1,3,5,7,9]")
              self.assertEqual(sumEven([-1,-2,-3,-4,-5]),-6,"Tested sumEven on input [-1,-2,-3,-4,-5]")
              self.assertEqual(sumEven([2,4,6,7,9]),12,"Tested sumEven on input [2,4,6,7,9]")
              self.assertEqual(sumEven([0,1,12,33]),12,"Tested sumEven on input [0,1,12,33]")

      myTests().main()

.. question:: lists_ex_9

   .. tabbed:: q9

        .. tab:: Question

           .. actex:: ex_9_8
              :practice: T
              :autograde: unittest

              Sum up all the negative numbers in a list.
              ~~~~
              def sumNegatives(lst):
                  # your code here

              ====
              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(sumNegatives([-1,-2,-3,-4,-5]),-15,"Tested sumNegatives on input [-1,-2,-3,-4,-5]")
                      self.assertEqual(sumNegatives([1,-3,5,-7,9]),-10,"Tested sumNegatives on input [1,-3,5,-7,9]")
                      self.assertEqual(sumNegatives([-2,-4,6,-7,9]),-13,"Tested sumNegatives on input [-2,-4,6,-7,9]")
                      self.assertEqual(sumNegatives([0,1,2,3,4]),0,"Tested sumNegatives on input [0,1,2,3,4]")

              myTests().main()



        .. tab:: Answer

            .. activecode:: lst_q9_answer
                :optional:

                import random

                def sumNegative(lst):
                    sum = 0
                    for e in lst:
                        if e < 0:
                            sum = sum + e
                    return sum

                lst = []
                for i in range(100):
                    lst.append(random.randrange(-1000, 1000))

                print(sumNegative(lst))


.. question:: lists_ex_10


   .. actex:: ex_9_9

      Count how many words in a list have length 5.
      ~~~~
      def countWords(lst):
          # your code here

.. question:: lists_ex_11

   .. tabbed:: q11

        .. tab:: Question

           Sum all the elements in a list up to but not including the first even number.

           .. actex:: ex_9_10
              :practice: T
              :autograde: unittest

              def sumUntilEven(lst):
                  # your code here

              ====
              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(sumUntilEven([1,2,3,4,5]),1,"Tested sumUntilEven on input [1,2,3,4.5]")
                      self.assertEqual(sumUntilEven([1,3,5,7,9]),25,"Tested sumUntilEven on input [1,3,5,7,9]")
                      self.assertEqual(sumUntilEven([2,4,6,7,9]),0,"Tested sumUntilEven on input [2,4,6,7,9]")

              myTests().main()


        .. tab:: Answer

            .. activecode:: lst_q11_answer
                :optional:

                import random

                def sum(lst):
                    sum = 0
                    index = 0
                    while index < len(lst) and lst[index] % 2 != 0:
                        sum = sum + lst[index]
                        index = index + 1
                    return sum

                lst = []
                for i in range(100):
                    lst.append(random.randint(0,1000))

                print(sum(lst))

.. question:: lists_ex_12

   .. actex:: ex_9_11

      Count how many words occur in a list up to and including the first occurrence of the word "sam".
      ~~~~
      def count(lst):
          # your code here



.. question:: lists_ex_13

   .. tabbed:: q13

        .. tab:: Question

           .. actex:: ex_9_12

              Although Python provides us with many list methods, it is good practice and very instructive to think about how they are implemented.  Implement a Python function that works like the following:
   
              a. count
              #. in
              #. reverse
              #. index
              #. insert
              ~~~~ 

        .. tab:: Answer

            .. activecode:: lst_q13_answer
                :optional:

                def count(obj, lst):
                    count = 0
                    for e in lst:
                        if e == obj:
                            count = count + 1
                    return count

                def is_in(obj, lst):  # cannot be called in() because in is a reserved keyword
                    for e in lst:
                        if e == obj:
                            return True
                    return False

                def reverse(lst):
                    reversed = []
                    for i in range(len(lst)-1, -1, -1): # step through the original list backwards
                        reversed.append(lst[i])
                    return reversed

                def index(obj, lst):
                    for i in range(len(lst)):
                        if lst[i] == obj:
                            return i
                    return -1

                def insert(obj, index, lst):
                    newlst = []
                    for i in range(len(lst)):
                        if i == index:
                            newlst.append(obj)
                        newlst.append(lst[i])
                    return newlst

                lst = [0, 1, 1, 2, 2, 3, 4, 5, 6, 7, 8, 9]
                print(count(1, lst))
                print(is_in(4, lst))
                print(reverse(lst))
                print(index(2, lst))
                print(insert('cat', 4, lst))


.. question:: lists_ex_14

   .. actex:: ex_9_13
      :practice: T
      :autograde: unittest

      Write a function ``replace(s, old, new)`` that replaces all occurences of
      ``old`` with ``new`` in a string ``s``::
   
         test(replace('Mississippi', 'i', 'I'), 'MIssIssIppI')
   
         s = 'I love spom!  Spom is my favorite food.  Spom, spom, spom, yum!'
         test(replace(s, 'om', 'am'),
                'I love spam!  Spam is my favorite food.  Spam, spam, spam, yum!')
   
         test(replace(s, 'o', 'a'),
                'I lave spam!  Spam is my favarite faad.  Spam, spam, spam, yum!')
   
      *Hint*: use the ``split`` and ``join`` methods.
      ~~~~
      def replace(s, old, new):
          # your code here

      ====
      from unittest.gui import TestCaseGui

      class myTests(TestCaseGui):

          def testOne(self):
              self.assertEqual(replace('Mississippi','i','I'),'MIssIssIppI',"Tested replace on input 'Mississippi','i','I'")
              self.assertEqual(replace('Bookkeeper','e','A'),'BookkAApAr',"Tested failed on input 'Bookkeeper','e','A'")
              self.assertEqual(replace('Deeded','e','q'),'Dqqdqd',"Tested failed on input 'Deeded','e','q'")

      myTests().main()


