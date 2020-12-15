..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

.. qnum::
   :prefix: func-14-
   :start: 1

Exercises
=========



#.

   .. tabbed:: q6

        .. tab:: Question

           .. actex:: ac11_14_6

              Although Python provides us with many list methods, it is good practice and very instructive to think about how they are implemented.  Implement a Python function that works like the following:
   
              a. count
              #. in
              #. reverse
              #. index
              #. insert
              ~~~~ 

        .. tab:: Answer

            .. activecode:: answer11_14_6
                :optional:

                def count(obj, lst):
                    count = 0
                    for e in lst:
                        if e == obj:
                            count = count + 1
                    return count

                def is_in(obj, lst):  # cannot be called in() because in is a reserved keyword
                    for e in lst:
                        if e == obj:
                            return True
                    return False

                def reverse(lst):
                    reversed = []
                    for i in range(len(lst)-1, -1, -1): # step through the original list backwards
                        reversed.append(lst[i])
                    return reversed

                def index(obj, lst):
                    for i in range(len(lst)):
                        if lst[i] == obj:
                            return i
                    return -1

                def insert(obj, index, lst):
                    newlst = []
                    for i in range(len(lst)):
                        if i == index:
                            newlst.append(obj)
                        newlst.append(lst[i])
                    return newlst

                lst = [0, 1, 1, 2, 2, 3, 4, 5, 6, 7, 8, 9]
                print(count(1, lst))
                print(is_in(4, lst))
                print(reverse(lst))
                print(index(2, lst))
                print(insert('cat', 4, lst))

