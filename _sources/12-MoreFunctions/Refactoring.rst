.. qnum::
   :prefix: func-whycreate
   :start: 1

.. index:: code duplication, refactor
   
Refactoring
===========

.. youtube:: ALHIlysBWUM
    :divid: vid_refactoring
    :height: 315
    :width: 560
    :align: left


Typically, programmers create functions for one of at least two reasons:

#. **Code reuse.** They have a section of code that needs to be executed at several different places in the program,
   and rather than copying and pasting that section, they create a function.

#. **Improved program organization.** Programs consist of logical sections of code. Programmers create functions
   to organize these sections of code into distinct units that can be separately analyzed and tested. 

To illustrate this, suppose we have the following program:

.. sourcecode:: python

    # draw a line with 40 *'s
    line = ''
    for _ in range(40):
        line += '*'
    print(line)

    # draw a line with 30 -'s
    line = ''
    for _ in range(30):
        line += '-'
    print(line)
    
You notice that the program contains two sections of code that are very similar, and decide to create a function to reduce the
duplication. You decide to call the function ``makeline``, and to determine the parameters it should receive, you notice that the 
only two differences between the sections of code are the number passed to the ``range`` function, which determines the length
of the line, and the symbol concatenated to ``line``, which determines the character that is repeated to compose the line.
So, you decide to define makeline with two parameters named ``symbol`` and ``length``, like this::

    def makeline(symbol, length):
        """Returns a string containing `symbol` repeated `length` times"""

Now, go ahead and fill out the definition of the function in the activecode editor below, using the lines of code above as a guide. 
When you run it to test it, the activecode editor will check your work and let you know if your function is working correctly.
After you get it working, compare your solution with mine.

.. note::
    By the way: there's a shorter way to created a line of dashes or asterisks, which is covered in the chapter on Strings.
    If you know it, feel free to use that technique in your solution to improve the code even further.

.. tabbed:: func-whycreate-tab

    .. tab:: Question

        Complete the definition of the makeline function.

        .. activecode:: func-whycreate-ac

            def makeline(symbol, length):
                """Returns a string containing `symbol` repeated `length` times"""


            # Now, use makeline to create the lines

            print(makeline('*', 40))
            print(makeline('-', 30))

            ====

            from unittest.gui import TestCaseGui

            class myTests(TestCaseGui):

                def testOne(self):
                    self.assertEqual(makeline('*', 40), '*' * 40, "makeline('*', 40) correct?"  )
                    self.assertEqual(makeline('-', 30), '-' * 40, "makeline('-', 30) correct?"  )
                    self.assertEqual(makeline('+', 20), '+' * 20, "makeline('+', 20) correct?"  )

            myTests().main()            


    .. tab:: Solution

        Here's my solution:

        .. sourcecode:: python

            def makeline(symbol, length):
                "Returns a string containing `symbol` repeated `length` times"

                line = ''
                for _ in range(length):
                    line += symbol

                return line

The modification that we did to this program did not change any behavior. When a programmer changes some code
in a way that does not alter its behavior, we say that the code has been refactored.

.. admonition:: Refactoring

    Refactoring is any reorganization of a program that does not alter its behavior.
    
Replacing sequences of duplicate code with a single function is one important example of refactoring. Other examples include
reorganizing code to improve its readability, or renaming functions or variables. 

We have significantly improved this program. One of the improvements involved reducing the amount of code duplication.
How did that help? It helped in two important ways:

#. The newer program has fewer lines of code, if you don't count blank lines. Smaller programs are generally easier
   to maintain than larger programs.

#. Programs with duplicate code tend to have more bugs than programs without duplicate code. 

Let's think about the second point for a moment. Why is that true? Well, imagine that you're writing the original program
above. You start by writing the lines that create the first line of asterisks. Suppose you don't get it quite right and
there's a bug or two in there, but you don't realize it because you're in a hurry and not following the recommended practice of 
testing code immediately after you write it that we presented earlier in this book. So you forge ahead since you've just
solved the first challenge of creating a line of asterisks (or so you think) and you tackle the second challenge of creating
a line of dashes. Now, how are you going to do that? Copy and paste, of course! So, you select the first bit of code,
copy and paste it, make a couple of changes to change the symbol and the length, and pat yourself on the back for using the
editor's clipboard functionality to save yourself a bunch of keystrokes.

Now, you run the program, and discover the bugs in your logic. So you set about fixing them in the first section of lines.
Then you have to make the same repair in the second section of lines. Not fun fixing the same bug in multiple places.

It gets worse than that. Suppose the bug isn't immediately obvious when you run the program. Maybe it prints one too few
or one too many symbols in each line. Something you're not going to spot. And further, the program is significantly more
complicated, and the lines are printed at various places under various conditions. You've copied and pasted this stupid
line printing code ALL OVER THE PLACE. So you release the program to the customer, who notices that the wrong number of
symbols are printed in a couple of spots. The customer is one of these picky types and wants you to fix it. So you fix it in
a place or two, but the bug is in so many places that you can't easily find them all. So over the next months the customer
keeps coming back to you with bug fix request after bug fix request. You get the idea.

This leads to an important rule to remember:

.. admonition:: Copy and Paste Rule

    Any time you copy and paste code, you are **copying and pasting the bugs** that likely exist in that code.

Imagine an alternate scenario. In this scenario, you're writing the original program, and as soon as you finish
writing the first section of code that prints the line of asterisks, you select those lines and hit copy. You start
to hit paste, but you remember the Copy and Paste Rule. And you remember the customer that hit you with all of
those bug fix requests on that other project where you ignored the rule. So in this scenario you decide not to hit paste, but instead you go to
the trouble of defining a function. You still mess up and the function contains bugs, but when you discover the bug,
you have just one place to go to fix the bug, because everywhere in the program where you needed to print a line of symbols,
you called the function instead of copying and pasting bugs. So fixing the bug in one place fixes it for all of the places in
the program that use that function to create a line of symbols. Nice job!

As we've seen, reducing code duplication is one important reason to create functions. But the second reason is even More Important!
Keep reading...

.. index:: abstraction, modularization

Abstraction
-----------

Think about the transformation that we did in the previous exercise. You took lines like this::

    line = ''
    for _ in range(40):
        line += '*'
    print(line)

and replaced them with this::

    print(makeline('-', 30))

In other words, you took a semi-complex section of code, hid the details away in a function named ``makeline``, and
replaced that section of code with a call to the function. Now, ask yourself the question: is the line

::

    print(makeline('-', 30))

easier to understand than the four lines of code that it replaced? In other words, would someone reading the main program
that now looks like this::

    print(makeline('*', 40))
    print(makeline('-', 30))

find it easier to understand what the program is doing than reading the original version, where all of the detail was
right there in the main program? 

I think the answer is "perhaps." The function name ``makeline`` implies that it creates a line, and someone unfamiliar
with the makeline function can probably guess the role of the two parameters. They can confirm their guess by looking up
the definition of makeline. If ``makeline`` has a well-written docstring, they can confirm their intuition with very
little effort, so a good docstring can make the answer to that question "definitely."

What we've done in this little exercise is to apply an idea called **abstraction**. Abstraction is one of the Big Ideas in computer science,
so I'm going to highlight its definition for you in a pretty box:

.. admonition:: Definition of Abstraction

    Abstraction means removing or hiding detail to aid comprehension.

When you created the **makeline** function, you were applying the tool of abstraction to help make your program clearer and easier to
read. How? By removing the details of creating a line of symbols from the main part of the program into a separate function,
the main part of the program becomes more streamlined, and generally easier to understand. Functions are one of the primary
tools programmers use to apply the principle of abstraction in their programs.

Abstraction is important because the human mind has a finite capacity for keeping track of details. Think about the
effort it took to understand the original program. Even in those few lines of code, there were a number of details to
keep track of. Larger programs have even more details. By organizing a large program into small, well-designed
functions, you make it easier for programmers to understand it, because they can *focus on one function at a time* and
deal with only the details contained within that function. They don't have to comprehend the program *as a whole*.
Related to the idea of abstraction is the idea of modularization. **Modularization** means dividing a program up into
separate units that can be individually reasoned about and tested.

The ability to create functions is what makes it intellectually possible for programmers to create the large, complex
software that powers our computers. Without functions, creating large programs would become an impossible task, because
the amount of detail that a programmer would have to keep track of would exceed the capacity of the human mind.
So the humble function plays a key role in making the modern world possible. That's an interesting thought!

When you create a function, keep in mind that people are going to need to understand lines of code that call that function.
Abstraction works well only if, when we look at a line like this::

    drawPoly(fred, 30, True)

we can figure out with little effort what that line does. If we have to dig through all of the detail inside the drawPoly
function to understand what this particular call is doing, then the abstraction has failed in its job of making the
code more understandable. So, that's why it is important to use good names for functions and their parameters, and to
write good docstrings. Good function names and good docstrings go a long way to bringing the power of abstraction to bear
on making your programs clear, understandable, and easy to debug and add features to. 

