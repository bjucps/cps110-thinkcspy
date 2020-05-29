..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-11-
   :start: 1

Print vs. return
================

Many beginning programmers find the distinction between ``print`` and ``return`` very confusing. In this section,
we'll explore that distinction and try to clear up some confusion.

The print statement is fairly easy to understand. It takes a python object and outputs a printed representation of it 
in the output window. You can think of the print statement as something that takes an object from the land of the 
program and makes it visible to the land of the human observer.

.. note::

   **Print is for people**. Remember that slogan. Printing has no effect on the ongoing execution of a program. It
   doesn't assign a value to a variable. It doesn't return a value from a function call.

The ``return`` statement is a little more difficult to understand. It does something with a value, but that something
is not as immediately obvious as what the ``print`` statement does.

Consider the following common mistake made by beginning Python programmers. As you step through this example, pay very
close attention to the return value in the variables listing. Then look at what is printed when the function is
over.

.. codelens:: clens11_4_2
    :python: py3

    def square(x):
        y = x * x
        print(y)   # Bad! Should return!

    toSquare = 10
    squareResult = square(toSquare)
    print("The result of {} squared is {}.".format(toSquare, squareResult))

The problem with this function is that it prints the value of the squared input, but does not return it 
to the place where the call was done. When a Python function does not have an explicit return statement,
it returns the the special value ``None``. 

Since line 6 assigns the result of this function to ``squareResult``, it receives the value ``None`` and the result
printed in line 7 is incorrect. In general, if you call a function in an assignment statement, as in line 6, the function should include a
return statement. **It is a mistake to call a function that does not return a value in an assignment statement.**

Prefer ``return`` to ``print``
------------------------------

So which is better for a function to do: print the value it computes, or return it? Here's a general piece of advice:

.. admonition:: When designing a function, prefer return to print.

    Most functions should return the value they compute, instead of printing it.

Why? A function that prints the value it computes can be used only to compute and print the value. That limits the
possibilities for using that function. When a function returns the value it computes, it can be used for more purposes.
Consider our square function above. If it returned its value instead of printing it, the code calling the function could
do more things with the result, such as:

#. Save it for later. 
    The returned value may be:
    
    * Assigned to a variable. For example, ``w = square(3)``
    * Put in a list. 
    * Written to a file.

#. Use it in a more complex expression. 
    For example, the calling code could use it in an assignment statement like this::

        w = square(square(3) + 7) - 5

#. Print it for human consumption. 
    For example, ``print(square(3))`` outputs 9 to the
    output area. Note that, unless the return value is first  saved as in possibility 1, it will be available
    only to the humans watching the output area, not to the program as it continues executing.

You will know you've really internalized the idea of functions when you are no longer confused about the difference 
between print and return. Keep working at it until it makes sense to you!

**Check your understanding**

.. mchoice:: question11_4_2
   :answer_a: The value None
   :answer_b: The value of x+y+z
   :answer_c: The string 'x+y+z'
   :correct: a
   :feedback_a: We have accidentally used print where we mean return.  Therefore, the function will return the value None by default.  This is a VERY COMMON mistake so watch out!  This mistake is also particularly difficult to find because when you run the function the output looks the same.  It is not until you try to assign its value to a variable that you can notice a difference.
   :feedback_b: Careful!  This is a very common mistake.  Here we have printed the value x+y+z but we have not returned it.  To return a value we MUST use the return keyword.
   :feedback_c: x+y+z calculates a number (assuming x+y+z are numbers) which represents the sum of the values x, y and z.
   :practice: T

   What will the following function return?

   .. code-block:: python

    def addEm(x, y, z):
        print(x+y+z)
