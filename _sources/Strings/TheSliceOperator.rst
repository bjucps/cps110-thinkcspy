..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: strings-7-
   :start: 1

.. index::
   single: [ : ]; string slice
   slice; string

The Slice Operator
==================

A substring of a string is called a **slice**. Selecting a slice is similar to
selecting a character:

.. activecode:: chp08_slice1
    
    singers = "Peter, Paul, and Mary"
    print(singers[0:5])
    print(singers[7:11])
    print(singers[17:21])
    

The `slice` operator ``[n:m]`` returns the part of the string from the n'th character
to the m'th character, including the first but excluding the last. In other words,  start with the character at index n and
go up to but do not include the character at index m.
This
behavior may seem counter-intuitive but if you recall the ``range`` function, it did not include its end
point either.

If you omit the first index (before the colon), the slice starts at the
beginning of the string. If you omit the second index, the slice goes to the
end of the string.

There is no Index Out Of Range exception for a slice.  
A slice is forgiving and shifts any offending index to something legal. 

.. activecode:: chp08_slice2
    
    fruit = "banana"
    print(fruit[:3])
    print(fruit[3:])
    print(fruit[3:-10])
    print(fruit[3:99])

What do you think ``fruit[:]`` means?

Parsing Data
------------

Suppose you have a variable containing a first and a last name::

   full_name = 'Joe Boggs'

If you know where the space is located in the string, you can use the slice operator to extract
the first and the last name, like this::

   first_name = full_name[:3]
   last_name = full_name[4:]

But what if you don't know where the space is located? That's where the find() method comes in
handy. You can use the find() method to locate the position of the space::

   >>> full_name = 'Joe Boggs'
   >>> full_name.find(' ')
   3

You can combine the find() method and the slice operator to help you parse, or extract,
information from strings. Take a look at this program that extracts the first name from
input containing a first and last name:

.. activecode:: chp08_slice3
    
    full_name = input('Enter a first and last name separated by a space:')
    space_loc = full_name.find(' ')
    first_name = full_name[:space_loc]
    print('Hello,', first_name)

On line 2, the ``find`` method locates the position of the space. Then, on line 3, the slice
operator is used to extract just the first name. Try using **Show in CodeLens** to step through this
example. 

**Check your understanding**

.. mchoice:: test_question8_5_1
   :practice: T
   :answer_a: python
   :answer_b: rocks
   :answer_c: hon r
   :answer_d: Error, you cannot have two numbers inside the [ ].
   :correct: c
   :feedback_a: That would be s[0:6].
   :feedback_b: That would be s[7:].
   :feedback_c: Yes, start with the character at index 3 and go up to but not include the character at index 8.
   :feedback_d: This is called slicing, not indexing.  It requires a start and an end.


   What is printed by the following statements?
   
   .. code-block:: python

      s = "python rocks"
      print(s[3:8])



.. mchoice:: test_question8_5_2
   :practice: T
   :answer_a: rockrockrock
   :answer_b: rock rock rock
   :answer_c: rocksrocksrocks
   :answer_d: Error, you cannot use repetition with slicing.
   :correct: a
   :feedback_a: Yes, rock starts at 7 and goes through 10.  Repeat it 3 times.
   :feedback_b: Repetition does not add a space.
   :feedback_c: Slicing will not include the character at index 11.  Just up to it (10 in this case).
   :feedback_d: The slice will happen first, then the repetition.  So it is ok.


   What is printed by the following statements?
   
   .. code-block:: python

      s = "python rocks"
      print(s[7:11] * 3)

.. tabbed:: tab_parsename

    .. tab:: Question

        .. activecode:: ac_parsename
            :autograde: unittest

            Complete the following function which, given a parameter containing a first and last name,
            returns the last name.
            ~~~~
            def get_lastname(full_name):

                # Complete the function

            ====
            from unittest.gui import TestCaseGui

            class myTests(TestCaseGui):

                def testOne(self):
                    self.assertEquals(get_lastname('Joe Boggs'), 'Boggs', "get_lastname('Joe Boggs') == 'Boggs'")
                    self.assertEquals(get_lastname('Helen Witherspoon'), 'Witherspoon', "get_lastname('Helen Witherspoon') == 'Witherspoon'")

            myTests().main()

    .. tab:: Tip

        Use the find() method to determine the location of the space. Then, use the slice operator to extract the part of the
        string that begins after the space and goes to the end.

    .. tab:: Answer

        .. activecode:: ac_parsename_sol
            :optional:

            def get_lastname(full_name):

                space_loc = full_name.find(' ')
                return full_name[space_loc + 1:]