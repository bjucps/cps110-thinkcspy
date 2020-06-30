..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-1-
   :start: 1

Introduction: Flow Control
==========================

So far, all of the programs we've seen have involved the computer executing the instructions in order from beginning
to end. We call this a **sequential** flow of control.

Often, programs need to be able to repeat some code over and over again.  Whether it is updating
the bank balances of millions of customers each night, or sending email messages to thousands of people programming
involves instructing the computer to do many repetitive actions. In computing, we refer to this repetitive execution as
**iteration** or **looping**. When a program has a loop, the flow of control proceeds sequentially through a group
of statements, and then jumps back to the top of the group and executes them again, over and over. This is a
departure from a simple sequential flow of control. 

In addition to looping, programs need to be able to make decisions about the input they are given and perform different
sets of statements depending on the outcome of the decisions. For example, if a customer's is attempting to withdraw
funds from an ATM but is requesting more money than is in the account, the program processing the withdrawal request
would need to execute a different set of statements than in the scenario where there are sufficient funds. We refer
to this as **conditional** flow of control.

In this chapter, we will explore a two important statements for altering the flow of control: the ``for`` statement
(for looping) and the ``if`` statement (for conditional execution).
