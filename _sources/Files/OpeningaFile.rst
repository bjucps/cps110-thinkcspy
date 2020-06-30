..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-3-
   :start: 1

Opening a File
~~~~~~~~~~~~~~

As an example, suppose we have a text file called ``school_prompt3.txt``. The contents of the file are shown at the bottom of the page.

To open this file, we would call the ``open`` function. The variable,
``fileref``, now holds a reference to the file object returned by
``open``. When we are finished with the file, we can close it by using
the ``close`` method. After the file is closed any further attempts to
use ``fileref`` will result in an error.

.. activecode:: ac9_2_1
    :available_files: school_prompt3.txt
    :nocodelens:

    fileref = open("school_prompt3.txt", "r")
    ## other code here that refers to variable fileref
    fileref.close()

.. note::

    A common mistake is to get confused about whether you are providing a variable name or a string literal as an input to the open function. In the code above, "school_prompt3.txt" is a string literal that should correspond to the name of a file on your computer. If you put something without quotes, like ``open(x, "r")``, it will be treated as a variable name. In this example, x should be a variable that's already been bound to a string value like "school_prompt3.txt".

.. datafile:: school_prompt3.txt
   :fromfile: school_prompt.txt