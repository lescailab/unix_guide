Introduction to Shell
==========================

What is a shell?
-----------------

A shell is also often called CLI, i.e. command line interface. It is a program, where user can write commands.

The most popular Unix shell is Bash (the Bourne Again SHell — so-called because it’s derived from a shell written by Stephen Bourne)


Anatomy of a Shell Command
------------------------------

A shell command is usually composed of three parts, and typed after a *prompt*, i.e. usually a dollar *$* sign indicating the shell is waiting for an input.

.. code-block:: bash

    $ command [option(s)] [object]

Both options and object are not mandatory.
Options can either start with a single dash (*-*) or double dash (*--*), and they are used to change the behaviour of a command.

.. warning::

  In UNIX we always need to be careful about white/blank space: normally, they separate a *command* from its *options* or different options from each other. It is always good practice to **avoid using white spaces in folder and file names**, because if we don't tell the shell we want to consider the space as a normal character, it will interpret it as a separator in the command line

Examples:

The command **ls** is used to list the content of a folder

.. code-block:: bash

  $ ls
  file.txt  folder  script.sh

One could add the option *-F* which adds a flag to each element of the list, to indicate their type (i.e. file, folder, executable)

.. code-block:: bash

  $ ls -F
  file.txt  folder/  script.sh*

Often we also use the option *-l* to print several details:

.. code-block:: bash

  $ ls -l
  total 4
  -rw-r--r-- 1 flescai domain users   0 Feb 19 11:03 file.txt
  drwxr-xr-x 2 flescai domain users  10 Feb 19 11:03 folder
  -rwxr-xr-x 1 flescai domain users 122 Feb 19 11:03 script.sh

This provides a large amount of information, tab-separated, and in particular:

- nature and permissions, in the format: [directory][owner][group][all users]
- link count: number of hard links to that element in the file system (this is a little more complicated, and you can skip it for the moment)
- owner
- group
- file size
- date last modified
- file name

There are other 2 options that I find frequently useful:

- *-h* which gives a human readable file size
- *-t* which orders the elements in a folder by last modified

The options an also be combined together:

.. code-block:: bash

    $ ls -lth
    total 4.0K
    -rwxr-xr-x 1 flescai domain users 122 Feb 19 11:03 script.sh
    drwxr-xr-x 2 flescai domain users  10 Feb 19 11:03 folder
    -rw-r--r-- 1 flescai domain users   0 Feb 19 11:03 file.txt


Move across folders
--------------------

To visualise the folder location where we are currently executing our commands:

.. code-block:: bash

  $ pwd
  /home/AD/flescai/tests/bash

To go to (chdir) a specific folder

.. code-block:: bash

  $ cd /my/folder

To move up to the *parent* folder we use the symbol **..** (i.e. two dots)

.. code-block:: bash

  $ pwd
  /home/AD/flescai/tests/bash
  $ cd ..
  $ pwd
  /home/AD/flescai/tests

Another useful symbol is **~** (called *tilde*) which indicate a user's home folder

.. code-block:: bash

  $ cd ~
  $ pwd
  /home/AD/flescai
