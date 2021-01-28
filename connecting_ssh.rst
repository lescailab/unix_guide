Connecting to a remote computer
==================================

Connecting to a remote computer using the **SSH** (i.e. secure shell) protocol is actually very simple.

The command has the following structure

.. code-block:: bash

  $ ssh [options] username@server

There are several options that one can use, perhaps the most useful one is **-X** which indicates that any graphical output from the server we connect to should be displayed on the local computer we are connecting from.

For example, if we wanted to connect to our NIBSC HPC cluster, and also forward graphical output we would write

.. code-block:: bash

  $ ssh -X user@hpc-head
