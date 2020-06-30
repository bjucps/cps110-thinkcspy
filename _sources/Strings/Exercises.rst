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

#.

    .. tabbed:: q1

        .. tab:: Question

            What is the result of each of the following:

            a. 'Python'[1]
            #. "Strings are sequences of characters."[5]
            #. len("wonderful")
            #. 'Mystery'[:4]
            #. 'p' in 'Pineapple'
            #. 'apple' in 'Pineapple'
            #. 'pear' not in 'Pineapple'
            #. 'apple' > 'pineapple'
            #. 'pineapple' < 'Peach'

        .. tab:: Answer

            a. 'Python'[1] = 'y'
            #. 'Strings are sequences of characters.'[5] = 'g'
            #. len('wonderful') = 9
            #. 'Mystery'[:4] = 'Myst'
            #. 'p' in 'Pineapple' = True
            #. 'apple' in 'Pineapple' = True
            #. 'pear' not in 'Pineapple' = True
            #. 'apple' > 'pineapple' = False
            #. 'pineapple' < 'Peach' = False

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_dc2457710a924d9283b12f42a31d2b27


#. 

    .. tabbed:: q2

        .. tab:: Question 

            .. actex:: ac_q2

            In Robert McCloskey's
            book *Make Way for Ducklings*, the names of the ducklings are Jack, Kack, Lack,
            Mack, Nack, Ouack, Pack, and Quack.  This loop tries to output these names in order.
            
            .. sourcecode:: python
            
                    prefixes = "JKLMNOPQ"
                    suffix = "ack"
            
                for p in prefixes:
                    print(p + suffix)
            
            
            Of course, that's not quite right because Ouack and Quack are misspelled.
            Can you fix it?
            ~~~~ 

#.

    .. tabbed:: q3

        .. tab:: Question 

           .. actex:: ac11_14_3
      
              Write a function that reverses its string argument.
              ~~~~
              def reverse(astring):
                  # your code here

              ====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(reverse("happy"),"yppah","Tested reverse on input of 'happy'")
                      self.assertEqual(reverse("Python"),"nohtyP","Tested reverse on input of 'Python'")
                      self.assertEqual(reverse(""),"","Tested reverse on input of ''")




              myTests().main()

#.

    .. tabbed:: q4

        .. tab:: Question

           .. actex:: ac11_14_4
              :nocodelens:

              Write a function that mirrors its string argument, 
              generating a string containing the original string and the string backwards.
              ~~~~

              def mirror(mystr):
                  # your code here

              ====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(mirror("good"),"gooddoog","Tested mirror on input of 'good'")
                      self.assertEqual(mirror("Python"),"PythonnohtyP","Tested mirror on input of 'Python'")
                      self.assertEqual(mirror(""),"","Tested mirror on input of ''")
                      self.assertEqual(mirror("a"),"aa","Tested mirror on input of 'a'")


              myTests().main()



        .. tab:: Answer

            .. activecode:: answer11_14_4
                :nocodelens:

                def reverse(mystr):
                    reversed = ''
                    for char in mystr:
                        reversed = char + reversed
                    return reversed

                def mirror(mystr):
                    return mystr + reverse(mystr)

                assert mirror('good') == 'gooddoog'
                assert mirror('Python') == 'PythonnohtyP'
                assert mirror('') == ''
                assert mirror('a') == 'aa'

#.

    .. tabbed:: q5

        .. tab:: Question 

           .. actex:: ac11_14_5
              :nocodelens:

              Write a function that removes all occurrences of a given letter from a string.
              ~~~~
              def remove_letter(theLetter, theString):
                  # your code here

              ====


              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(remove_letter("a","apple"),"pple","Tested remove_letter on inputs of 'a' and 'apple'")
                      self.assertEqual(remove_letter("a","banana"),"bnn","Tested remove_letter on inputs of 'a' and 'banana'")
                      self.assertEqual(remove_letter("z","banana"),"banana","Tested remove_letter on inputs of 'z' and 'banana'")



              myTests().main()



