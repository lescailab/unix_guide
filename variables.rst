Working with Variables
=======================


Initialise a variable
---------------------

A variable is a temporary store for a piece of information. Most commonly we store strings (i.e. text) or numbers inside variables.

A file name is a string, and so is a file path. A counter (in a loop) is a number.

In bash a variable is initialised (i.e. created, by assigning some parts of memory) by using the variable name, and equal sign and either a value or an empty value.

.. code-block:: bash

  $ filename=''

.. note::
  Note how there is no whitespace between the variable name, the equal sign and its value.

One could also initialise a variable by assigning immediately a value

.. code-block:: bash

  $ filename="myfile.txt"


There is no rule about variable names, but normally a special chategory of variables is written with all capital letters

.. code-block:: bash

  $ RHOME="~/.R/lib"

These variables are called *environment variables* and they are valid system-wide, often conventionally used by different software applications.
A local variable can become an environment variable when it is *exported* with the command **export**

.. code-block:: bash

  $ RHOME="~/.R/lib"
  $ export RHOME

You can see all your environment variables using the command **env**.


Use a variable
--------------------

In order to *use* the value stored in a variable, we refer to it with the variable name preceded by the **$** sign. We can use the command **echo** to print something on standard output like in the following code:

.. code-block:: bash

  $ myname="Francesco"
  $ echo $myname
  Francesco

Sometimes when we combine a variable name with a string or other elements (for example when renaming a file or naming new files from a root string), we might want to *protect* the variable name with curly parenthesis, to make sure our shell understand which exact part of the string is the variable name, compared to the other characters we might use:

.. code-block:: bash

  $ institute="NIBSC"
  $ echo "${institute}MHRA"
  NIBSCMHRA

In the above example we have combined *NIBSC* with *MHRA* but we haven't used any separator, and we want to avoid the shell to interpret *NIBSCMHRA* as a variable name, thus returning nothing.

.. code-block:: bash

  $ echo "$NIBSCMHRA"

  $

.. note::

  When we export a variable to set it as environment variable we don't use the dollar sign in bash




Create or Modifying a variable with commands
---------------------------------------------

Most interestingly, we can create or fill in a variable with values from a bash command, using the backquotes special character which interprets what is in between as command to be executed.

.. code-block:: bash

  $ fileList=`ls`
  $ echo $fileList
  folder oldfile.txt script.sh subfolder

We can use this in many different ways, one is the loop explained in a following section.


Basic String Manipulation
---------------------------------

Two methods of manipulating strings can be very useful to change file names, when we stored the file name as a string into a variable. They are called **substring removal** and there are two different symbols to be used to remove the shortest match either from the front of a string (**#**) or from the back of the string (**%**).

Let's imagine we have a file name stored in a variable as follows

.. code-block:: bash

  $ filename="macro_analysis.txt"

We can use the above string removal symbols to change the string stored in the variable

.. code-block:: bash

  $ echo "${filename#macro_}"
  analysis.txt

  $ echo "${filename%.txt}"
  macro_analysis

We can use these methods to change the file names, if we combine the value stored in the variable with the commands we explained in the other sections

.. code-block:: bash

  $ touch macro_analysis.txt
  $ filename="macro_analysis.txt"
  $ mv $filename "${filename#macro_}"
  $ ls
  analysis.txt
