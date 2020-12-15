..  Copyright (C)  Stephen Schaub.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Introduction to Refactoring
===========================

Consider the program below:

.. sourcecode:: python

    choice = int(input('Enter 1 for banana, 2 for apple, 3 for pear:'))
    
    if choice == 1:
        print('--------------------------')
        print('You chose banana.')
        print('--------------------------')
    
    elif choice == 2:
        print('--------------------------')
        print('You chose apple.')
        print('--------------------------')

    elif choice == 3:
        print('--------------------------')
        print('You chose pear.')
        print('--------------------------')

There is a fair amount of code duplication here. We can reduce the code duplication by reorganizing the code
a little. Take a look at this revised version:

.. sourcecode:: python

    choice = int(input('Enter 1 for banana, 2 for apple, 3 for pear:'))
    
    print('--------------------------')

    if choice == 1:
        print('You chose banana.')

    elif choice == 2:
        print('You chose apple.')

    elif choice == 3:
        print('You chose pear.')

    print('--------------------------')

Notice how the print statements that display the dashed lines have been moved around a little.
Compare the revised version to the original, and note two things:

1. The revised version behaves the same as the original.
2. The revised version has 4 fewer lines of code.

The modification that we did to this program did not change any behavior. When a programmer changes some code
in a way that does not alter its behavior, we say that the code has been **refactored**. I will have more to say about
refactoring in a later section in this book.

Generally, we refactor code in order to improve its organization in some way. Here is another way we could
reorganize this program:

.. activecode:: act_fruit_choice

    # Get user's choice

    choice = int(input('Enter 1 for banana, 2 for apple, 3 for pear:'))
    
    # Determine fruit based on user's choice

    fruit = ''
    if choice == 1:
        fruit = 'banana.'
    elif choice == 2:
        fruit = 'apple'
    elif choice == 3:
        fruit = 'pear'

    # Display result

    print('--------------------------')
    print(f'You chose {fruit}.')
    print('--------------------------')

In this version, the program has a clear 3-point outline: get input, process input, display result.
When possible, it's often a good idea to separate the processing of input from the output of the
results, because the resulting code tends to be easier to follow and contain less duplication.
