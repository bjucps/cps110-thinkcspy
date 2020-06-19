..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-5-
   :start: 1

Iterating over lines in a file
------------------------------

We will now use this file as input in a program that will do some data processing. In the program, we will
examine each line of the file and print it with some additional text. Because ``readlines()`` returns a list of
lines of text, we can use the *for* loop to iterate through each line of the file.

As the *for* loop iterates through each line of the file the loop variable will contain the current line of the
file as a string of characters. The general pattern for processing each line of a text file is as follows:

::

        lines = myFile.readlines()
        for line in lines:
            statement1
            statement2
            ...

Recall that our olympics file looks like this:


.. datafile:: olympics2.txt

    Name,Sex,Age,Team,Event,Medal
    A Dijiang,M,24,China,Basketball,NA
    A Lamusi,M,23,China,Judo,NA
    Gunnar Nielsen Aaby,M,24,Denmark,Football,NA
    Edgar Lindenau Aabye,M,34,Denmark/Sweden,Tug-Of-War,Gold
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Timo Antero Aaltonen,M,31,Finland,Athletics,NA
    Win Valdemar Aaltonen,M,54,Finland,Art Competitions,NA

To process all of our olypmics data, we will use a *for* loop to iterate over the lines of the file. Using
the ``split`` method, we can break each line into a list containing all the fields of interest about the
athlete. We can then take the values corresponding to name, team and event to
construct a simple sentence.

.. activecode:: ac9_5_1
    :nocodelens:
    :available_files: olympics2.txt

    olypmicsfile = open("olypmics2.txt", "r")

    for aline in olypmicsfile.readlines():
        values = aline.split(",")
        print(values[0], "is from", values[3], "and is on the roster for", values[4])

    olypmicsfile.close()

If you look closely at the output when you run this example, you'll see that the first line of output contains
information from the first line of the file::

    Name is from Team and is on the roster for Event

You could cause the program to ignore that line if you use the ``readline`` method once after you open the file, and
before the for loop begins. Try adding the following line just after line 1 in the program above, and then run the
program again to see the result::

    olypmicsfile.readline()

To make the code a little simpler, and to allow for more efficient processing, Python provides a built-in way to
iterate through the contents of a file one line at a time, without first reading them all into a list. Here is what
it looks like:

.. activecode:: ac9_5_2
    :nocodelens:
    :available_files: olympics2.txt

    olypmicsfile = open("olypmics2.txt", "r")

    for aline in olypmicsfile:
        values = aline.split(",")
        print(values[0], "is from", values[3], "and is on the roster for", values[4])

    olypmicsfile.close()

Notice how this version is nearly identical to the one above. The only difference is that, instead of
explicitly invoking the readlines() method, we treat the file variable itself as a sequence, like a list
or a string, by writing its name after the ``in`` in the ``for`` loop::

    for aline in olypmicsfile:

The end result is the same. However, this version makes better use of memory, because instead of reading all of
the lines in the file into a list in memory and then iterating through the list, this version reads just one
line into memory at a time. For most text files, you wouldn't notice a difference, but for really large text files
this technique can be noticeably more efficient.




**Check your Understanding**

.. tabbed:: tabbed_9_5_3

   .. tab:: Question

      1. Write code to find out how many lines are in the file ``emotion_words3.txt`` as shown below. Save this value to the variable ``num_lines``. Do not use the len method.

      .. activecode:: ac9_5_3
         :available_files: emotion_words3.txt
         :language: python
         :nocodelens:
         :autograde: unittest
         :practice: T


         =====

         from unittest.gui import TestCaseGui

         class myTests(TestCaseGui):
 
            def testOne(self):
                self.assertEqual(num_lines, 7, "Testing that num_lines was assigned to the correct value.")
                self.assertNotIn('len', self.getEditorText(), "Testing you didn't use len (Don't worry about actual and expected values).")

         myTests().main()

   .. tab:: Tip

      Open the file, and write a loop that counts how many lines are in the file. The accumulator pattern will help.

   .. tab:: Solution

      Here's the solution::

         thefile = open("emotion_words3.txt", "r")

         num_lines = 0
         for aline in thefile:
            num_lines += 1

         thefile.close()


.. datafile:: emotion_words3.txt
   :fromfile: emotion_words.txt
