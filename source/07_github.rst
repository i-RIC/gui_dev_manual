Working with github repository
===============================

This page describes how you should use github repository.

Registering bugs or enhancement proposal
-------------------------------------------

Github has function to manage bugs and enhancement proposals, as "issues".

Please visit the page below:

https://github.com/i-RIC/prepost-gui/issues

* Press "New issue" button, to go to the page to register new issue.

* Input the title and comment

* If it is a bug, add "bug" label by clicking on "Labels". 
  If it is an enhancement proposal, add "enhancement" label as well.

* Press "Submit new issue" to register the issue.

Fixing bugs
-----------

When you fix a bug in iRIC GUI, please follow the procedure below:

* Make a new account to github.

* Create your own github repository, by forking. You can do this by going to
  iRIC GUI prepost-gui repository, and clicking on "Fork" button.

* Clone the original iRIC repository to your local environment. It will
  be registered as a remote "origin".

* Add the repository you've forked as a remote site, with name like "mine".

* "Checkout ``origin/master`` branch.

* Create a new branch, with a name like ``issue-123``. The number corresponds
  to the ID of the issue that you are going to fix.

* Fix the code, build, and test.

* When you think that you've finished, push the branch to **your** github
  repository, with command like below:

.. code-block:: bat

   git push mine issue-123

* Create a new pull request, with the following procedure:

  * Go to https://github.com/i-RIC/prepost-gui/pulls

  * Press "New pull request" button
  * Press "compare across forks" button.
  * Select base: master in the left combobox. This will be the default.
  * Select **your** repository in the combobox in the right side. The default is "i-RIC/prepost-gui",
    so select "youraccount/prepost-gui".
  * Select the branch you've created (``issue-123`` in this case), in the most right combobox.
  * You'll have "Create pull request" button, so press it.
  * You'll see "Open a pull request" page. Change the title to "Closes i-RIC/prepost-gui#123",
    for example. If named in this way, When the pull request is accepted and merged, the 
    corresponding issue is automatically closed.

