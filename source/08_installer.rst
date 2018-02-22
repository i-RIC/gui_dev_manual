Releasing an installer
=======================

iRIC GUI is now released with the two ways below:

* Offline installer
* Online update

At first, a user has to install iRIC using the offline installer.

When they have installed, and new iRIC GUI and solvers are released,
they do not have to uninstall and install new one. They just can
get the newest version with online update, using "iRIC Maintainance tool".

In this page, the way to release an installer is described.

Preparing
-----------


Install Qt Installer Framework
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To build iRIC installer, you need Qt Installer Framework 2.0.

You can install it with the following procedure:

1. Launch "Qt Maintainance Tool" in "Qt" folder in menu.
2. Press "Next" button.
3. Select "Add or remove component" radio button, and press "Next" button.
4. Check on "Qt/Tools/Qt Installer Framework 2.0", and press "Next" button.
5. Wait until installing finishes.

Install Python 3
~~~~~~~~~~~~~~~~~

You need python 3, because the scripts to build installer are written in Python.
Install Python 3. Python 3 is available in the following URL:

https://www.python.org/

Install Subversion client
~~~~~~~~~~~~~~~~~~~~~~~~~~

You need subversion client to work on the repository.
We recommend that you install TortoiseSVN.

https://ja.osdn.net/projects/tortoisesvn/


Checkout iRIC installer repository
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iRIC installer repository is a subversion repository.
Please checkout the following URL:

https://i-ric.org/svn/iric/


Releasing iRIC developer version
---------------------------------

Update the files in dev_src folder
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The files that you want to put into installer are stored in dev_src/packages
folder. For example, files for iRIC GUI are stored in dev_src/packages/gui.prepost.

Put the new files into that folder.

**Important Note**: Please do not forget to update the definition.xml, to 
modify the version number and release date. It is important because iRIC
Maintainance tool use this information to recognize whether new version
is released or not.

Run script to build online update repository
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Run the two scripts below, in this order:

.. code-block:: bat

   python copy_release_and_version.py
   python build_update_repository.py

After running these scripts, the Files inside dev folder are updated.

Releasing the files
~~~~~~~~~~~~~~~~~~~~

Commit all the changes in dev_src and dev folders.
Leave appropriate log message to that commit.

Testing
~~~~~~~~

After releasing the development version repository, launch
"iRIC Maintainance tool" for "iRIC (develop)",  select
"Update components", and press "Next" button. If the release
was successful, you'll have a dialog that you have a new version,
and can update.

Update the iRIC GUI, and when it is finished, launch "iRIC (develop)",
and test if it works.


