Working with Files and Folders
===================================


Creating directories
-------------------------

The command to create a new directory is **mkdir**

.. code-block:: bash

  $ ls
  file.txt  folder  script.sh

  $ mkdir subfolder
  $ ls -F
  file.txt  folder/  script.sh*  subfolder/

A very useful option of this command is **-p**, which doesn't cause an error should the folder already exist. Additionally, if we are creating a subfolder, it will create parent directories as needed if they don't exist

.. code-block:: bash

  $ mkdir -p subfolder/sub_subfolder/lowelevel



Creating and editing a file
----------------------------

An empty file can be created using the command **touch**

.. code-block:: bash

  $ ls -l
  total 4
  -rw-r--r-- 1 flescai domain users   0 Feb 19 11:03 file.txt
  drwxr-xr-x 2 flescai domain users  10 Feb 19 11:03 folder
  -rwxr-xr-x 1 flescai domain users 122 Feb 19 11:03 script.sh
  drwxr-xr-x 3 flescai domain users  34 Feb 19 13:17 subfolder

  $ touch newfile.txt
  $ ls -l
  total 4
  -rw-r--r-- 1 flescai domain users   0 Feb 19 11:03 file.txt
  drwxr-xr-x 2 flescai domain users  10 Feb 19 11:03 folder
  -rw-r--r-- 1 flescai domain users   0 Feb 19 13:19 newfile.txt
  -rwxr-xr-x 1 flescai domain users 122 Feb 19 11:03 script.sh
  drwxr-xr-x 3 flescai domain users  34 Feb 19 13:17 subfolder


The file can then be edited using one of the many command line editors in shell, like **vi** or **vim** or **nano**, according to one's preferences.
A new file can also be created by editing it straight away, even if it doesn't exist yet: the command will create it first, and open for editing.

.. code-block:: bash

  $ vim textfile.txt

The use of *vi* or *vim* should be explained more extensively `elsewhere`_.

.. _elsewhere: https://www.howtoforge.com/vim-basics


Moving and copying files and folders
--------------------------------------

The basic command to move a file or a folder is **mv**.

For example, we can use it to move our new text file into the subfolder with this syntax

.. code-block:: bash

  $ ls -F
  file.txt  folder/  newfile.txt  script.sh*  subfolder/

  $ mv file.txt subfolder/.
  $ ls -F
  folder/  newfile.txt  script.sh*  subfolder/

The use of the final dot is not strictly necessary, it just makes the command more safe: the dot indicates the same folder, i.e. it is like writing *right here*.

There is not much difference in UNIX between *moving* a file or *renaming* a file: i.e. renaming is like moving one file into another with a different name.
Therefore, if I wanted to change the name of *newfile.txt* into something else, I would do the following


.. code-block:: bash

   $ mv newfile.txt oldfile.txt
   $ ls -F
   folder/  oldfile.txt  script.sh*  subfolder/

Copying is done using the command **cp** and an important option is **-r** which allows to copy files *recursively*, i.e. by copying also the content of folders and sufolders.

.. code-block:: bash

   $ ls *
   oldfile.txt  script.sh

   folder:

   subfolder:
   file.txt  sub_subfolder

We want to copy the directory named *subfolder* which contains a file and a sub-subfolder

.. code-block:: bash

  $ cp -r subfolder newfolder
  $ ls *
  oldfile.txt  script.sh

  folder:

  newfolder:
  file.txt  sub_subfolder

  subfolder:
  file.txt  sub_subfolder


Removing files and folder
---------------------------

The command to remove files is **rm** and by adding the option **-r** i.e. *recursively* we can also remove folders and their content.

.. code-block:: bash

  $ rm -r newfolder
  $ ls -F
  folder/  oldfile.txt  script.sh*  subfolder/

.. warning:: Deleting is permanent

   The Unix shell doesn’t have a trash bin that we can recover deleted files from: therefore once you have deleted a file with the command **rm** there is **no way to recover the file** and it is lost forever (unless a backup exists somewhere)


Peek at file content
-------------------------

A couple of useful commands allow us to inspect quickly at a file content, either at the beginning (**head**) or at the end (**tail**) of a file.

.. code-block:: bash

  $ head oldfile.txt
  first line
  second line
  third line
  fourth line
  fifth line
  sixth line
  seventh line
  eighth line
  ninth line
  tenth line

  $ tail oldfile.txt
  third line
  fourth line
  fifth line
  sixth line
  seventh line
  eighth line
  ninth line
  tenth line
  eleventh line
  twelfth line

By default the command will print the first or last 10 lines of the file. You can change this using the option **-n** and specifying the number of lines.
