Special Characters
===================


Folder structure
------------------

Like in natural language, in UNIX we define as **path** the route to reach a specific element (a file, a folder).
The path can be *absolute* or *relative*.

If the path is *absolute* its origin is called the *root folder*, and it is indicated as **/** at the very beginning.

.. code-block:: bash

  $ pwd
  /home/AD/flescai/tests/bash


In the example above the folder *bash* can be reached starting from the *root* down the tree through the *home* folder, inside the home through the *AD* folder, and inside of it the *user* folder, and so on.
Note that each folder in a path is separated by a subsequent **/** character.

If the path is *relative*, its origin refers to the current folder where we are located with the terminal. It can be any sub-folder


.. code-block:: bash

  ./current/sub-folder/sub-sub-folder


Or it can be a sub-folder of the parent folder

.. code-block:: bash

  ../parent-sub-folder/file


Special Characters
-----------------------

There are many special characters in UNIX which serve different functions. Among the most common:

+-----------+--------------------------------------------------------------------------------------------------------------------------------+
| Character | Function                                                                                                                       |
+===========+================================================================================================================================+
|  #        | The character is used mostly in scripts to indicate a comment, i.e. a line that should not be executed                         |
+-----------+--------------------------------------------------------------------------------------------------------------------------------+
|  ''       | Strong quotes: disable all special characters between quotes, everything is considered a string                                |
+-----------+--------------------------------------------------------------------------------------------------------------------------------+
|  ""       | Weak quotes: disable all special characters except **$**, i.e. allowing variables to be transformed in strings                 |
+-----------+--------------------------------------------------------------------------------------------------------------------------------+
|  \`\`     | Backquotes: command substitution, i.e. text inside is interpreted as a prompt command                                          |
+-----------+--------------------------------------------------------------------------------------------------------------------------------+
|  >        | Redirect output (for example, to write the shell output into a file)                                                           |
+-----------+--------------------------------------------------------------------------------------------------------------------------------+
|  >>       | Append output. The difference with redirect, is that output is written at the end of a file without deleting previous content  |
+-----------+--------------------------------------------------------------------------------------------------------------------------------+
| <         | Redirect input.                                                                                                                |
+-----------+--------------------------------------------------------------------------------------------------------------------------------+
| $         | Used to indicate variables, by preceding the variable name.                                                                    |
+-----------+--------------------------------------------------------------------------------------------------------------------------------+
| \|        | Pipe: used to combine shell commands one after the other, while directing the output of the previous command into the next one |
+-----------+--------------------------------------------------------------------------------------------------------------------------------+
| \*        | The star is considered a wild card, i.e. indicating any possible caracter or file or folder                                    |
+-----------+--------------------------------------------------------------------------------------------------------------------------------+


Escape
----------

The character **\\** is used to *escape* (i.e. disable) special characters and instruct UNIX to consider them like strings.
It can be used in several useful cases, for example if we wanted to print quotes

.. code-block:: bash

  $ echo "this is a single quote \""


Or if we wanted to write several options of a command in a new line, without starting the execution until we completed the code

.. code-block:: bash

  $ ls \
  -l \
  -t
