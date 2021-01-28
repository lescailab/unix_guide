Creating a Loop
==================

Loop are meant to perform the same actions multiple times. For example, changing the name of many different files.

.. note::

  When a command is not finished (for example when we are still editing a loop), the prompt changes from **$** to **>**


The FOR loop
--------------

One of the most basic loops is the so called "for loop", because it begins with the instruction **for**. It is a loop based on the iteration over something, and it means *execute the following for a certain number of iterations*.

It is composed of the following essential blocks:

- **for** instruction followed by an expression (or a list) indicating the number of iterations
- **do** command, indicating where the series of commands to be executed for n iteration begins
- the list of instructions/commands to be executed in a loop
- **done** command, indicating where the loop ends



Using the for loop to change file extension
----------------------------------------------

 We can look at a concrete case, which might happen frequently: we want to change the name of many files, maybe change their extension.
 A typical example is the index of a bam file called **alignment.bam** , which some software create as *alignment.bam.bai* and some other software instead create as *alignment.bai*.
 We have created the index with one application, but now we want to use it with another which needs the other kind of file name.

 Let's start by creating some dummy files, purely for the exercise:

 .. code-block:: bash

    $ touch file1.bam.bai file2.bam.bai file3.bam.bai file4.bam.bai
    $ ls *.bai
    file1.bam.bai  file2.bam.bai  file3.bam.bai  file4.bam.bai

We now want to use the string removal trick, to remove *bam.bai* and attach *.bai* effectively removing *bam.* from the name. The command we know would be

.. code-block:: bash

  $ filename="file1.bam.bai"
  $ echo "${filename%bam.bai}bai"
  file1.bai

However, we want to do this for all files, and we will use the command **mv** to rename them

.. warning::

  Before performing potentially *dangerous* loops, i.e. changing the name of many files, it is always good to run the loop using the command **echo** instead of the command **mv** to make sure we print what should happen at screen before making it happen

We can therefore prepare the loop as follows:

.. code-block:: bash

  $ for file in `ls *.bai`
  > do
  > mv $file "${file%bam.bai}bai"
  > done

  $ ls
  file1.bai  file2.bai  file3.bai  file4.bai
