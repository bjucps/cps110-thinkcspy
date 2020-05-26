..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-8-
   :start: 1

.. index:: table, escape sequence, tab, newline,
           cursor

Escape Sequences
================

Consider the following program::

    print("Dear Jane,")
    print("What's for lunch?")
    print("John")

This program displays three lines of output. We created that output using three
print statements, but we could have used a single print statement using a triple-quoted
string, like this::

    print("""Dear Jane
    What's for lunch?
    John""")

There's also another approach we could have used. Take a look at this program:

.. activecode:: ac_newline
    :nocodelens:

    print("Dear Jane,\nWhat's for lunch?\nJohn")

This program uses the two-character sequence ``\n`` to cause a line break after the comma and the question mark in the string.
To understand how it works, it helps to know a bit about how ``print`` displays its output. As ``print`` emits the
characters in a string onto the screen, an invisible marker called the **cursor** keeps track of where the next
character will go. After a ``print`` function is executed, the cursor normally goes to the beginning of the next line.
But you can force the cursor to move to the beginning of the next line early by inserting a special control character
into a string called a **newline** character. 

A newline is an invisible character that you can't type on your keyboard (pressing the ``Enter`` key doesn't insert a
newline character; it moves the cursor to the next line in your editor). Since you can't type a newline character into
the Python string, Python allows you to embed the sequence of characters ``\n`` into the string which it interprets as a
single newline character. The sequence ``\n`` is an example of an **escape sequence**.

.. admonition:: Escape sequence

    An escape sequence is a sequence of characters beginning with a backslash (``\``) that is used to embed a special
    control character or other symbol in a string.

Two common escape sequences are the newline sequence (``\n``) and the tab sequence (``\t``). 
You've seen how the newline sequence forces a line break. In a moment,
you'll see what the tab is used for. But first, some observations:

#. An escape sequence is a sequence of two or more characters that causes Python to
   insert a *single* control character into the string. So, the string ``"\n"`` has length 1, 
   not 2. To prove it, try typing the following into the Python shell::

      >>> len('\n')
      1
      >>>

#. If you need to put a true backslash into a string, you must double the backslash. The
   following statement::

      print("Here is a real backslash: \\")

   outputs the message::

      Here is a real backslash: \

#. You can use an escape sequence to include the same type of quote in a single quoted string
   as the quote that delimits the string::

      print("He said, \"Run!\"")

   outputs::

      He said, "Run!"

   Although this case doesn't come up often in Python because you can delimit strings with either single or double quotes,
   and you can use triple-quoted strings to include both types of quotes, it is occasionally useful, so I'm mentioning
   it here.

I've been focusing on print statements in these examples, but you can also use escape sequences to embed control sequences in
strings in regular assignment statements. For example::

    two_lines = 'line 1\nline 2'      # Creates a string containing two "lines" of data

.. admonition:: Multiple Lines: Which Technique is Best?

    Now you know three ways to output multiple lines of information: individual print statements;
    multi-line strings, and the ``\n`` escape sequence. Which is best?

    Generally, you should prefer individual print statements or multi-line strings, which lead to more readable code.
    One place where the ``\n`` escape sequence comes in handy is when you want an *extra* blank line at the end of a
    print statement::

        # The following output is double-spaced
        print("These two lines are separated by a blank line.\n")
        print("Here is the second line.")

Tabular Data
------------

One of the things loops are good for is generating tabular data.  Before
computers were readily available, people had to calculate logarithms, sines and
cosines, and other mathematical functions by hand. To make that easier,
mathematics books contained long tables listing the values of these functions.
Creating the tables was slow and boring, and they tended to be full of errors.

When computers appeared on the scene, one of the initial reactions was, *"This is
great! We can use the computers to generate the tables, so there will be no
errors."* That turned out to be true (mostly) but shortsighted. Soon thereafter,
computers and calculators were so pervasive that the tables became obsolete.

Well, almost. For some operations, computers use tables of values to get an
approximate answer and then perform computations to improve the approximation.
In some cases, there have been errors in the underlying tables, most famously
in the table the Intel Pentium processor chip used to perform floating-point division.

Although a power of 2 table is not as useful as it once was, it still makes a good
example of iteration. The following program outputs a sequence of values in the
left column and 2 raised to the power of that value in the right column:

.. activecode:: ch07_table0
    :nocodelens:

    print("n    2**n")     #table column headings
    print("---  -----")

    for x in range(13):        # generate values for columns
        print(x, 2 ** x)

There's one problem with this example. The numbers in the table don't line up into columns
neatly. Try fixing the problem by changing the print statement to this::

    print(str(x) + '    ' + str(2 ** x))

What do you think? That's improved, but when ``n`` increases to 10, there's an unsightly
shift in the data.

One way to fix the problem is to use an escape sequence called a tab. Take a look at this version:

.. activecode:: ch07_table1
    :nocodelens:

    print("n", '\t', "2**n")     
    print("---", '\t', "-----")

    for x in range(13):        
        print(x, '\t', 2 ** x)

The string ``'\t'`` represents a **tab character**. When the print statement encounters a tab character in a string, the
tab character causes the cursor to shift to the right until it reaches one of the invisible *tab stops* that occur every 8
positions on a line. Tabs are useful for making columns of text line up, as in the output of this program.
Because of the tab characters between the columns, the position of the second column does not depend on the number of
digits in the first column.

Try experimenting with the program above by changing the ``'\t'`` to ``'\t\t'`` and observing the result. 

Also, try changing the first two lines to read as follows::

    print("n\t2**n")     
    print("---\t-----")

Does that make any difference in the output (it shouldn't)? Does it make any difference in the readability of the code? (Better? Worse?)
Which version of the program do you prefer?


**Check your understanding**

.. mchoice:: test_question7_7_1
  :practice: T
  :answer_a: A tab will line up items in a second column, regardless of how many characters were in the first column, while spaces will not.
  :answer_b: There is no difference
  :answer_c: A tab is wider than a sequence of spaces
  :answer_d: You must use tabs for creating tables.  You cannot use spaces.
  :correct: a
  :feedback_a: Assuming the size of the first column is less than the size of the tab width.
  :feedback_b: Tabs and spaces will sometimes make output appear visually different.
  :feedback_c: A tab has a pre-defined width that is equal to a given number of spaces.
  :feedback_d: You may use spaces to create tables.  The columns might look jagged, or they might not, depending on the width of the items in each column.

  What is the difference between a tab (``'\t'``) and a sequence of spaces?

