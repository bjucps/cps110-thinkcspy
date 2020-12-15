


Debugging Conditional Logic
===========================

When programs with if statements don't work correctly, tracking down the trouble can be tricky because often it's not
immediately clear which of the various possible branches the program actually took as it executed, especially if
you don't have print statements in each branch as in the example above.

To make the flow of the program clearer, try adding a ``print`` statement inside each ``if``, ``elif``, and ``else``
block in the program so that you can see which of the branches is taken as the program runs. That can help give you
the visibility into the program's execution that you need to determine why the program isn't producing the results
you expect. 

.. TODO: Enhance this section. Create an activity with a buggy version of the grader program
