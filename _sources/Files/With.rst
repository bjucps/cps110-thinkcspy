..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _with_page:

.. qnum::
   :prefix: files-12-
   :start: 1

Using ``with`` for Files
========================

Now that you have seen and practiced a bit with opening and closing files, there is another mechanism that Python 
provides for us that cleans up the often forgotten close. Forgetting to close a file does not necessarily cause a runtime 
error in the kinds of programs you typically write in an introductory programing course. However if you are writing a 
program that may run for days or weeks at a time that does a lot of file reading and writing you may run into trouble. 

Here is a program that uses a ``with`` statement to open a file:

.. activecode:: ac9_12_1
   :nocodelens:
   :available_files: mydata.txt
   
   with open('mydata.txt', 'r') as md:
       for line in md:
           print(line)
   # continue on with other code          

The first line of the `with` statement opens the file and assigns it to the variable ``md``. Then we can iterate over the file in any of the usual ways. When we are done we simply stop indenting, and Python automatically closes the file without our having to call the ``close`` method explicitly. 

Compare the code above to the version below, which explicitly calls ``.close()``.

.. activecode:: ac9_12_2
   :nocodelens:
   :available_files: mydata.txt
   
   md = open('mydata.txt', 'r')
   for line in md:
       print(line)
   md.close()
   # continue with other code



.. datafile:: mydata.txt

   1 2 3
   4 5 6
