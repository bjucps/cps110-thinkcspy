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

Now that you know how to read data from a file, let's put that knowledge to use and write a program that will do some 
meaningful data processing. Here is a data file containing a list of some cities in Washington State:


.. datafile:: wa_cities.txt

    Cities in Washington
    South Creek
    Roslyn
    Sprague  
    Gig Harbor
    Lake Cassidy
    Tenino
    Jamestown   
    Three Lakes
    Curlew Lake
    Chain Lake    
    Pateros
    Rosburg
    Parkland

Let's write a program that will determine the city with the longest name. To get started, here is a program
that reads the wa_cities.txt file and displays each line, one at a time:

.. activecode:: ac9_5_1
    :nocodelens:
    :available_files: wa_cities.txt

    infile = open("wa_cities.txt", "r")

    lines = infile.readlines()
    for aline in lines:
        aline = aline.strip()
        print(f'**City: {aline}**')

    infile.close()

In this program, after opening the file, line 3 uses the ``readlines`` method to read all of the lines from
the file into a list. Then, lines 4-6 iterate over the list, displaying each line. Notice the line::

    aline = aline.strip()

The ``strip()`` method removes leading and trailing whitespace. It is another way to remove the trailing newline from
each line, along with any excess space that may be present. Try commenting out or deleting this line to see the
effect that it has.

To make the code a little simpler, and to allow for more efficient processing, Python provides a built-in way to
iterate through the contents of a file one line at a time, without first reading them all into a list. Here is what
it looks like:

.. activecode:: ac9_5_2
    :nocodelens:
    :available_files: wa_cities.txt

    infile = open("wa_cities.txt", "r")
    infile.readline()  # Read first line and throw it away

    for aline in infile:
        aline = aline.strip()
        print(aline)

    infile.close()

Notice how this version does not invoke the ``readlines`` method. Instead, it treats the file variable itself as a
sequence, like a list or a string, by writing its name after the ``in`` in the ``for`` loop::

    for aline in infile:

The end result is the same. However, this version makes better use of memory, because instead of reading all of
the lines in the file into a list in memory and then iterating through the list, this version reads just one
line into memory at a time. For most text files, you wouldn't notice a difference, but for really large text files
this technique can be noticeably more efficient.

Now that we have a basic structure in place for reading the file a line at a time, let's enhance the program so that it
finds the city with the longest name, using the accumulator pattern. Here's an attempt that is close, but not quite right:

.. activecode:: ac9_5_1a
    :nocodelens:
    :available_files: wa_cities.txt

    infile = open("wa_cities.txt", "r")

    longest_name = ''
    for aline in infile:
        aline = aline.strip()
        if len(aline) > len(longest_name):
            longest_name = aline
        print(aline)

    infile.close()
    print('The city with the longest name is:', longest_name)


The program gives an incorrect result because the first line of the file is not a city, but is longer than any
of the city names::

    Cities in Washington

Many data files have descriptive information on the first line that should be ignored by programs that read them.
You could cause the program to ignore the first line if you use the ``readline`` method once after you open the file, 
before starting to iterate over the lines. Try adding the following line just after line 1 in the program above, and then run the
program again to see the result::

    infile.readline()

That's better. After that change, Lake Cassidy is now correctly determined to be the city with the longest namee.


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
