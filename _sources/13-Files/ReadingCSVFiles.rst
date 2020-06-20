..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-13-
   :start: 1

Reading in data from a CSV File
================================

We are able to read in CSV files the same way we have with other text files. Because of the standardized structure of the data, there is a common pattern for processing it. To practice this,
we will be using data about olympic events.

Typically, CSV files will have a header as the first line, which contains column names. Then,
each following row in the file will contain data that corresponds to the appropriate columns. Here's an example file
that contains data about olympic events:

.. datafile:: olympics.txt

    Name,Sex,Age,Team,Event,Medal
    A Dijiang,M,24,China,Basketball,NA
    A Lamusi,M,23,China,Judo,NA
    Gunnar Nielsen Aaby,M,24,Denmark,Football,NA
    Edgar Lindenau Aabye,M,34,Denmark/Sweden,Tug-Of-War,Gold
    Per Knut Aaland,M,33,United States,Cross Country Skiing,NA
    John Aalberg,M,33,United States,Cross Country Skiing,NA
    Antti Sami Aalto,M,26,Finland,Ice Hockey,NA
    Jorma Ilmari Aalto,M,22,Finland,Cross Country Skiing,NA
    Jyri Tapani Aalto,M,31,Finland,Badminton,NA
    Arvo Ossian Aaltonen,M,22,Finland,Swimming,NA
    Arvo Ossian Aaltonen,M,22,Finland,Swimming,NA
    Arvo Ossian Aaltonen,M,30,Finland,Swimming,Bronze
    Arvo Ossian Aaltonen,M,30,Finland,Swimming,Bronze
    Arvo Ossian Aaltonen,M,34,Finland,Swimming,NA
    Juhamatti Tapio Aaltonen,M,28,Finland,Ice Hockey,Bronze
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,Bronze
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,Gold
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,Gold
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Timo Antero Aaltonen,M,31,Finland,Athletics,NA
    Win Valdemar Aaltonen,M,54,Finland,Art Competitions,NA


All file methods that we have mentioned - ``read``, ``readline``, and ``readlines``, and simply iterating over the file object itself - will work on CSV files. In our examples, we will iterate over the lines. Because the values on each line are separated with commas, we can use the ``.split()`` method to parse each line into a collection of separate value.

.. activecode:: ac9_13_1
    :nocodelens:

    with open("olympics.txt", 'r') as infile:
        lines = infile.readlines()

    header = lines[0]
    field_names = header.strip().split(',')
    print(field_names)
    for row in lines[1:]:
        vals = row.strip().split(',')
        if vals[5] != "NA":
            print(f"{vals[0]}: {vals[4]}; {vals[5]}")

In the above code, we open the file, olympics.txt, which contains data on some olympians (see below for the contents). 

We split the first row to get the field names. We split other rows to get values. Note that we specify to split on commas by passing that as a parameter. Also note that we first pass the row through the .strip() method to get rid of the trailing ``\n``.

Once we have parsed the lines into their separate values, we can use those values in the program. For example, in the code above, we select only those rows where the olympian won a medal, and we print out only three of the fields, in a different format.

Note that the trick of splitting the text for each row based on the presence of commas only works because commas are not used in any of the field values. Suppose that some of our events were more specific, and used commas. For example, "Swimming, 100M Freestyle". How will a program processing a .csv file know when a comma is separating columns, and when it is just part of the text string giving a value within a column?

The CSV format is actually a little more general than we have described and has a couple of solutions for that problem. One alternative format uses a different column separator, such as | or a tab (\t).  Sometimes, when a tab is used, the format is called tsv, for tab-separated values). If you get a file using a different separator, you can just call the ``.split('|')`` or ``.split('\\t')``.

The csv Module
--------------

The other advanced CSV format uses commas to separate but encloses all values in double quotes.

For example, the data file might look like:

.. datafile:: olympics4.txt

    "Name","Sex","Age","Team","Event","Medal"
    "Dijiang, A","M","24","China","Basketball","NA"
    "Aabye, Edgar Lindenau","M","34","Denmark/Sweden","Tug-Of-War","Gold"
    "Aaftink, Christine Jacoba","F","21","Netherlands","Speed Skating, 1500M","NA"


If you are reading a CSV file that has enclosed all values in double quotes, it's actually a pretty tricky programming
problem to split the text for one row into a list of values. You won't want to try to do it directly. Instead, you
should use python's built-in csv module. For more information, see the `chapter on CSV files <https://automatetheboringstuff.com/2e/chapter16/>`_
in Al Sweigart's excellent *Automate the Boring Stuff with Python*.
