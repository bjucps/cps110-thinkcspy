.. qnum::
   :prefix: func-doc
   :start: 1

.. index:: 
   docstrings
   
Documenting Functions
=====================

Let's start this section off with a question. You're reading a section of a Python program and you encounter this
line. Quick: what does it do?

.. sourcecode:: python

    transmogrify(alex, 8, True)

Suppose that alex is a turtle (you can see that from the lines just above this one). And you know that ``transmogrify``
is some function you've spotted elsewhere in the code. But what does this particular line do?

To answer that question, you need the definition of the transmogrify function. You locate it and discover
that it has the following definition:

.. sourcecode:: python

    def transmogrify(t, s, a):
        for _ in range(s):
            t.right(360 // s)
            if a == True:
                t.forward(10)
            else:
                t.backward(10)

Hmmm... that's not very helpful. Wouldn't it be nice if the programmer had used decent parameter names, and maybe a more
meaningful method name? Maybe that would have helped us figure out what the mysterious line did. Suppose it looked this way:

.. sourcecode:: python

    def drawPoly(aTurtle, sides, goForward):
        for _ in range(sides):
            aTurtle.right(360 // sides)
            if goForward == True:
                aTurtle.forward(50)
            else:
                aTurtle.backward(50)

That's better! Now, if we look at this line::

    drawPoly(alex, 8, True)

we can make a guess about what will happen. The turtle will draw a polygon with 8 sides, traveling forward. 

Choosing good names for functions and parameters is extremely important to help the reader understand what the function does.
But good names are not enough. When we look at the call to ``drawPoly``, if we're not familiar with the drawPoly function,
we don't want to have to read through the definition of ``drawPoly`` to figure out what it does. We want a brief summary,
so we can read the summary and quickly understand the function without spending what may be considerable mental effort
to read the code inside the function, follow the logic, and deduce what will happen for this particular call to the function
that we're considering. We need **function documentation**.

Function Comment Format
-----------------------

Quick quiz: how should the following function be documented?

.. sourcecode:: python

    def sum(x, y):
        return x + y

Consider the following options::

    Option 1
    --------

    # Returns the sum of x and y
    def sum(x, y):
        return x + y

    Option 2
    --------

    def sum(x, y):
        """Returns the sum of x and y"""

        return x + y

Although either option will work, the Python Way is Option 2. As we learned earlier in this chapter, by convention,
Python programmers use a triple-quoted **docstring** as the first line of their function to describe what the function does.
There are benefits to preferring this approach. In addition to making you look like you know what you're doing (always a
good thing), Python editing tools like Visual Studio Code will consume docstrings and use them to provide helpful
hover tips to programmers who write or inspect lines of code that call the function.

Writing Effective Function Comments
-----------------------------------

Function comments are important because they summarize what the function does. An effective comment 

Multi-Line Function Comments
----------------------------

A function docstring should always include a brief description of what the function does. For simple functions,
a brief description may be sufficient. But what if we need to include detailed information about the parameters and return values? 
In that case, we can make the docstring extend over multiple lines. Here's an example of what a multiline docstring might
look like for our drawPoly function:

.. sourcecode:: python

    def drawPoly(aTurtle, sides, goForward):
        """Draws a polygon.

        This function uses `aTurtle` to draw a polygon with a specified 
        number of `sides`. The turtle moves either forwards to draw the figure
        if `goForward` is True, otherwise backwards.

        Parameters:
            aTurtle (Turtle) - the turtle to draw the figure
            sides (int) - the number of sides for the polygon
            goForward (bool) - if True, turtle moves forwards to draw

        Returns:
            no value

        """

        for _ in range(sides):
            ... rest of code omitted ...

Notice the sections of this multiline comment:

1. It begins with a brief, one-line description of the function::

        Draws a polygon.

2. Next, it includes an extended description::

        This function uses `aTurtle` to draw a polygon with a specified 
        number of `sides`. The turtle moves either forwards to draw the figure
        if `goForward` is True, otherwise backwards.

3. Following the extended description comes a list of parameters. For each
   parameter, the name, type, and description are specified.

4. The comment concludes with a description of the return value.

There is no single standard for the format of multiline docstrings. However, different
projects and organizations have developed useful standards. 
`This stackabuse post <https://stackabuse.com/python-docstrings/>`_ presents some helpful examples.
Pick one that you like and use it for your own projects!

How do Comments Help?
---------------------

Remember the issue we considered at the beginning of this section? We were looking at this line of
code and trying to determine what it does::

    transmogrify(alex, 8, True)

Now, imagine the level of difficulty involved in answering that question in these three scenarios:

1. **Scenario one: The transmogrify function has no comment at all.** 

   We'll almost certainly have to read the body of the transmogrify function, think about the arguments
   being passed to it by this particular line, and reason about what the function does.

2. **Scenario two: The transmogrify function has a single brief docstring comment: """Draws a polygon"""** 

   This is better than Scenario one (especially because the function is so poorly named), and in other situations, the
   brief comment may be all we need, but here we'll almost certainly have to look at the body of the function to figure
   out what the arguments are used for.

3. **Scenario three: The transmogrify function has a detailed multi-line docstring comment** 

   In this case, we probably won't need to look at the body of the function at all. Everything we need to know
   about what the parameters mean is discussed in the docstring. 

Good function comments **help the programmer to understand lines of code that call the function**.


To Comment or Not to Comment
----------------------------

Since the presence of comments in a program never makes any difference to the Python interpreter, many programmers
struggle with the question of when and how much to comment. As we end this section, let me offer some guidance on this
important question.

Professional programmers understand the importance of comments. In a well-engineered program, I would expect to see
that most functions include at least a brief one-line docstring summarizing their behavior. 

Not all functions need a multi-line docstring comment. Writing these comments takes time and effort, and
they come with a cost: when the function is changed (parameters renamed, behavior changed, etc.), they must be updated
to reflect the changes. Most functions are adequately commented by a well-written one-line docstring. You would
go to the trouble of writing a detailed docstring if the function is complicated, especially if you intend to reuse it
in more than one program.

What about comments *inside* functions? Some software companies require that every line of code be commented.
However, that often leads to such silliness as this::

    count += 1   # increments count

These comments have a cost, because anytime you change the line of code, you must also update the comment to reflect
the change, or else risk a misleading comment that is no longer accurate, and just serves to confuse the next
programmer who reads the code.

Most software professionals would agree that occasional comments inside functions are helpful to describe sections of
code, or individual lines that are particularly tricky. Whenever possible, it's better to write code that is
straightforward and does not need a comment than to write complicated code that is hard to understand and then comment
it.


**Check your understanding**

.. mchoice:: funcdoc-1
   :practice: T
   :answer_a: boo1
   :answer_b: boo2
   :answer_c: boo3
   :correct: c
   :feedback_a: This works, but Python editors won't use the comment to give hints as you type calls to this function
   :feedback_b: This is illegal syntax. The docstring must be indented to the same level as the first line of code in the function.
   :feedback_c: Correct! The triple-quoted docstring is the preferred way to write function comments in Python.

   Which of the following functions is commented correctly?

   .. sourcecode:: python

        # Prints 'Boo'
        def boo1():
            print("Boo!")

        def boo2():
        """ Prints 'Boo' """
            print("Boo!")

        def boo3():
            """ Prints 'Boo' """
            print("Boo!")


