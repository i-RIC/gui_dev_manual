Setting up a development environment of iRIC GUI
=================================================

Installing tools and libraries
------------------------------

You can setup development environment of iRIC GUI only with free softwares.

Please refer to the following site, to build and install the libraries and tools
that you need for developing iRIC GUI:

https://github.com/i-RIC/iricdev

iRIC GUI can be built on Windows or Linux, but Linux build is currently experimental.
Please setup development environment on Windows.


Building iRIC GUI
------------------

The source code of iRIC GUI is available in the following site:

https://github.com/i-RIC/prepost-gui

Please clone the git repository, and checkout master branch to get the currently stable
version of iRIC GUI.

To build iRIC GUI, please follow the procedure below:

1. Launch "Qt 5.5 64-bit for Desktop (MSVC 2013)" in "Qt" folder from start menu
2. Run the following command:

.. code-block:: bat

   "C:\Program Files (x86)\Microsoft Visual Studio 12.0\vc\vcvarsall.bat" x86_amd64

3. cd to top folder of the git repository, that contain file ``src.pro``
4. copy ``paths_std.pri`` to ``paths.pri``, and modify this file so that the paths of the
   libraries are right.

5. Run the following command:

.. code-block:: bat

   qmake -recursively -tp vc

6. Launch Visual Studio 2013 with the following command:

.. code-block:: bat

   "C:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE\WDExpress.exe" /useenv

7. Open src.sln from Visual Studio 2013, that exists in the top folder of the git repository.
8. Build iRIC GUI by selecting the menu Build --> Build solution

You can both Debug version binaries or Release version binaries, by switching the Combo Box
in the tool bar.

Debugging iRIC GUI
-------------------

You can debug iRIC GUI by the following procedure, after building iRIC GUI in debug mode:

1. Select "iRIC" in the solution explorer
2. From the right-clicking menu, select "Set it as startup project"
3. Start debugging iRIC by selecting the menu Debug --> Start debugging

Please note that when you want to debug iRIC GUI, add PATH to ``libdlls\debug`` folder,
so that iRIC.exe can find the DLLs that it depends on.

The Dlls that are build by the projects within iRIC GUI source are all copied to
this directory automatically.
Please copy all the other DLLs that iRIC needs to this folder.

