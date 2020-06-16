..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-4-
   :start: 1

Reading a File
==============

Once you have a file "object", the thing returned by the open function, Python provides three methods to read data
from that object. The ``read()`` method returns the entire contents of the file as a single string.
The ``readlines`` method returns the entire contents of
the entire file as a list of strings, where each item in the list is one line of the file. The ``readline``
method reads one line from the file and returns it as a string. The strings returned by ``readlines`` or
``readline`` will contain the newline character at the end.  :ref:`Table 2 <filemethods2a>` summarizes these
methods and the following session shows them in action.

.. _filemethods2a:

======================== =========================== =====================================
**Method Name**           **Use**                     **Explanation**
======================== =========================== =====================================
``read``                 ``filevar.read()``          Read and return the entire file as a
                                                      single string.
``readline``             ``filevar.readline()``      Read and return the next line of the file with
                                                      all text up to and including the
                                                      newline character.
``readlines``            ``filevar.readlines()``     Returns a list of strings, each
                                                      representing a single line of the file.                                                      
======================== =========================== =====================================


Here's an example showing the ``readline`` and ``read`` methods in action:

.. activecode:: ac_file_read
    :available_files: hello.txt
    :nocodelens:

    datafile = open("hello.txt", "r")
    line = datafile.readline()
    line = line[:-1]  # Remove trailing newline
    print(f'First line of file: **{line}**')
    line = datafile.readline()
    line = line[:-1]
    print(f'Next line of file: **{line}**')
    rest = datafile.read()
    print(f'Rest of file: **{rest}**')
    datafile.close()

Let's walk through this program carefully. 

1. This program begins by opening the file *hello.txt* (shown below). 

1. In lines 2-4, the program uses the ``readline`` method to read the first line from the file,
   and displays the information it read.
   
   The data returned from ``readline`` includes a trailing newline character (more about that in 
   a moment), which is removed by the slice operation on line 3. 

1. Next, the program reads the next line from the file using the same sequence of method calls it used
   to read the first line. The file reference variable, *datafile*, remembers the position in the file where it stopped
   reading after the first call to ``readline``. So, the second call to ``readline`` on line 5 resumes reading at the
   beginning of the second line, and returns the second line from the file.

1. Finally, the program uses the ``read`` method to read the rest of the data in the file, starting with the third line.

.. datafile:: hello.txt

   Hello.
   This is the second line.
   Here is another line.
   And another.

This example demonstrates how a file reference variable like *datafile* keeps track of not only which file it is reading
(hello.txt), but also where in the file it is reading.

The newline character
-------------------------

Text files are organized into lines of text. Each line is separated from the next by a special control character
called a **newline**, discussed earlier in this book when we introduced :ref:`escape-sequences`.

The ``read`` method includes the newline characters in the string. You can see the effect of those newline characters in
the output of the final print statement of the example above, where the newline characters force line breaks in the
lines of output.

The ``readline`` method also includes the terminating **newline** character at the end of the string it returns. To see
this, try commenting out or deleting line 3 in the example above. Then, run the program. You should see the following
output::

   First line of file: **Hello.
   **

When you use the readline method, you usually want to remove the terminating newline character from the line of data before
using the information. The slice operation is often used to do this.

**Check your Understanding**

.. tabbed:: tabbed_9_4_1

   .. tab:: Question

      1. Find the number of characters in the file ``school_prompt2.txt`` (shown below) and assign that value to the variable ``num_char``. 

      .. activecode:: ac9_4_1
         :language: python
         :nocodelens:
         :autograde: unittest
         :practice: T
         :available_files: school_prompt2.txt


         =====

         from unittest.gui import TestCaseGui

         class myTests(TestCaseGui):

            def testOne(self):
               self.assertEqual(num_char, 537, "Testing that num_char has the correct value.")

         myTests().main()

   .. tab:: Tip

      Write code to open the file ``school_prompt2.txt``, use the appropriate file reading method to read it into a single string variable, 
      and then get the length of the string.

   .. tab:: Solution

      .. sourcecode:: python

         f = open('school_prompt2.txt', 'r')
         data = f.read()
         num_char = len(data)

.. datafile:: school_prompt2.txt
   :fromfile: school_prompt.txt

.. tabbed:: tabbed_9_4_2

   .. tab:: Question

      2. Find the number of lines in the file, ``travel_plans2.txt`` (shown below), and assign it to the variable ``num_lines``.

      .. activecode:: ac9_4_2
         :available_files: travel_plans2.txt
         :language: python
         :nocodelens:
         :autograde: unittest
         :practice: T

         =====

         from unittest.gui import TestCaseGui

         class myTests(TestCaseGui):

            def testTwo(self):
               self.assertEqual(num_lines, 11, "Testing that num_lines is assigned to correct value.")

         myTests().main()

   .. tab:: Tip

      The ``readlines`` method should come in handy!

   .. tab:: Solution

      .. sourcecode:: python

         f = open('travel_plans2.txt', 'r')
         data = f.readlines()
         num_lines = len(data)

.. datafile:: travel_plans2.txt
   :fromfile: travel_plans.txt

.. tabbed:: tabbed_9_4_3

   .. tab:: Question

      3. Create a variable called ``third_line`` that contains the third line of ``emotion_words2.txt`` (shown below).
      Your solution must use the ``readline`` method.

      .. activecode:: ac9_4_3
         :available_files: emotion_words2.txt
         :language: python
         :nocodelens:
         :autograde: unittest
         :practice: T

         
         =====

         from unittest.gui import TestCaseGui
         class myTests(TestCaseGui):
            def testOne(self):
               self.assertEqual(third_line, 'Happy cheerful content elated joyous delighted lively glad\n', "Testing that third_line was created correctly.")
               self.assertIn('readline()', self.getEditorText(), "Testing that readline() is used")
         myTests().main()

   .. tab:: Tip

      You'll need to call ``readline()`` more than once to get the job done.

   .. tab:: Solution

      .. sourcecode:: python

         f = open('emotion_words2.txt', 'r')
         f.readline()  # Ignore first line
         f.readline()  # Ignore first line
         third_line = f.readline()


.. datafile:: emotion_words2.txt
   :fromfile: emotion_words.txt
