..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Exercises
---------

#.

    .. tabbed:: q1

        .. tab:: Question

            .. actex:: ac7_14_1

               Write code that asks the user to enter a numeric score (0-100). In response, it should print out the score and corresponding letter grade, according to the table below.
        
               .. table::
        
                  =======   =====
                  Score     Grade
                  =======   =====
                  >= 90     A
                  [80-90)   B
                  [70-80)   C
                  [60-70)   D
                  < 60      F
                  =======   =====
        
               The square and round brackets denote closed and open intervals.
               A closed interval includes the number, and open interval excludes it. So 79.99999 gets grade C , but 80 gets grade B.
               ~~~~
           
        .. tab:: Answer

            .. activecode:: ans7_14_1
            
               sc = input("Enter a score from 0 to 100 (decimal points are allowed)")
               fl_sc = float(sc)
               
               if fl_sc < 60:
                   gr = "F"
               elif fl_sc < 70:
                   gr = "D"
               elif fl_sc < 80:
                   gr = "C"
               elif fl_sc < 90:
                   gr = "B"
               else:
                   gr = "A"
               
               print("Score", fl_sc, "gets a grade of", gr)
                 
