How to implement iRIC GUI functions
====================================

This page describes how you should implement basic iRIC GUI functions.

Implementing Project File I/O
------------------------------

When you want to save some new data into a project, and it can be expressed as text,
you should think of saving that into project file, i. e. XML file.

Implement I/O for Project File (project.xml), by overriding the following functions:

* ProjectDataItem::doLoadFromProjectMainFile(const QDomNode& node)
* ProjectDataItem::doSaveToProjectMainFile(QXmlStreamWriter& writer)

Please refer to ``misc\xmlsupport.h``. It has convenient functions to load/save bool,
integer, and double attributes from/to project file.


Implementing CGNS File I/O
---------------------------

When you want to give some new data to solver, you should think of saving that
data into CGNS file.

When you decide that the data should be saved into CGNS file, implement I/O for
CGNS file, by overriding the following functions:

* ProjectDataItem::loadFromCgnsFile(const int fn)
* ProjectDataItem::saveToCgnsFile(const int fn)

When you conclude that the data is not suitable to be saved into CGNS File,
implement I/O for External File. Please refer to Geographic data I/O implementation for example.
Geographic data I/O functions are implemented in iRIClib, and used from both GUI and solvers.

Implementing External File I/O
--------------------------------

When you want to save some new data into a project, and it is not suitable to save that
data as text data, you should think of saving that into a separate file inside
the project folder (just like background images or grid creating condition).

* Set value to ProjectDataItem::m_filename, and that will be used for the separate file.
* Set value to ProjectDataItem::m_subFolder for the ancient node classes if needed.
* Implement I/O for external File, by overriding the following functions:

  * ProjectDataItem::loadExternalData(const QString& filename)
  * ProjectDataItem::saveExternalData(const QString& filename)


Implementing some data modification feature
--------------------------------------------

Some of iRIC GUI functions are made undo-able. This is implemented in the following way:

* Data modification action is implemented as a subclass of QUndoCommand.
* When user do the modification, the following code will be executed:

iRICUndoStack::instance()->push(new SomeUndoCommand());

But in some cases, it is hard to make some action undo-able. In that case, execute the
following code after that action is executed:

.. code-block:: cpp

   iRICUndoStack::instance()->clear();

