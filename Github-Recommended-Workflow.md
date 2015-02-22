# Users
If you want to use software that is hosted on GitHub and get updates when they
are released, but you don't think it's likely that you will ever want to fix
bugs or add new features yourself, then probably you are a User (you can upgrade
yourself to a Developer later if you need to).

Users will want to take the "official" version of the software, make a copy of
it on their own computer, and run the code from there. Using ``expyfun``
software as an example, this is done on the command line like this::

    $ git clone git://github.com/LABSN/expyfun.git
    $ cd expyfun
    $ python setup.py install

The :bash:`git clone` command will create a folder ``expyfun`` in the current
directory to store the source code, and the :bash:`python setup.py install`
command will install the necessary parts of ``expyfun`` in the special places
where python
looks when you do :python:`import expyfun` and call ``expyfun`` functions in
your own scripts. The only thing you really need to decide first is where on
your computer to store the source code. When you want to update ``expyfun`` to a
newer version of the source code, just go back to that folder in your terminal
and type::

    $ git pull
    $ python setup.py install

What is actually happening under the hood when you do these things? In addition
to making you a local copy of the source code, the initial :bash:`git clone`
command sets up a relationship between that folder on your computer and the
"origin" of the code. You can see this by typing::

    $ git remote -v
    origin	git://github.com/LABSN/expyfun.git (fetch)
    origin	git://github.com/LABSN/expyfun.git (push)

This tells you that :bash:`git` knows about two "remote" addresses of
``expyfun``: one to ``fetch`` new changes from (if the source code gets updated
by someone else), and one to ``push`` new changes to (if you make changes that
you want to share). In this case the two addresses both point to the "official"
version of the ``expyfun`` software, and because you're a User, you won't
actually be allowed to ``push`` any changes you make: the ``remote`` copy that
your computer calls ``origin`` is picky about who it allows to make changes
(i.e., only the Maintainers_ can).

The initial :bash:`git clone` command also automatically gives your local copy
of the code a "branch" name. You probably won't need to use this functionality,
but the short explanation is that :bash:`git` allows you to add, delete, and
change files within the  ``expyfun`` directory and then easily go back to where
you started from in case your changes didn't work. One way :bash:`git` enables
this is by having different "branches" of the same source code, and by default
it creates a branch called "master" when it first clones the remote repository
to your computer::

    $ git branch
    * master

The asterisk means that ``master`` is the currently active branch. Later, if you
update ``expyfun`` to a newer version using :bash:`git pull`, what :bash:`git`
is really doing is :bash:`git pull origin master`, i.e., pulling changes that
exist in the ``origin`` copy of ``expyfun`` into your local ``master`` branch.

# Developers

One of the most challenging concepts with :bash:`git` source code control
is the fact that its job is to seamlessly manage multiple different versions
of a code base. The idea is that :bash:`git` allows you to swap back and
forth between these different versions while working within the same directory
structure.

In other words, typically there is only one repository for a given project on
a developer's local machine. That repository can have multiple
`branches <http://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell>`_
within it.
When a developer switches between branches, they are effectively switching
between different copies of that repository. The :bash:`git` protocol thus
modifies or updates files in-place, and you can keep track of different versions
of the files by keeping track of branch names, instead of storing temporary
copies in other folders, or appending ``_newVersion`` to the filename.

In addition to each developer having a local git repository, they usually become
associated with some number of remote repositories on
`GitHub <https://github.com>`_. The developer's local repository can "know"
about any number of remote repositories, and users get to name those remote
repositories whatever they want. Here is a diagram of the connections between
the remote repositories on GitHub and the local computers of each of three
collaborators on the ``expyfun`` project:

.. _diagram:
.. image:: https://cdn.rawgit.com/LABSN/expyfun/master/doc/git_flow.svg

Developers (like ``rkmaddox`` in the diagram) typically first go to the
`official repo of the project <https://github.com/LABSN/expyfun>`_
and `fork <https://help.github.com/articles/fork-a-repo/>`_ the repository so
that their changes can be sandboxed. The convention is to then set up their
local copy of the codebase with their own fork as the remote ``origin``, and
connect to the official remote repo with the name ``upstream``. So after forking
`expyfun <https://github.com/LABSN/expyfun>`_ to his own GitHub account, user
``rkmaddox`` would run::

    $ git clone git@github.com:/rkmaddox/expyfun.git
    $ cd expyfun
    $ git remote add upstream git://github.com/LABSN/expyfun.git

Now this user has the standard ``origin``/``upstream`` configuration, as seen
below. Note the difference in the URIs between ``origin`` and ``upstream``::

    $ git remote -v
    origin	git@github.com:/rkmaddox/expyfun.git (fetch)
    origin	git@github.com:/rkmaddox/expyfun.git (push)
    upstream	git://github.com/LABSN/expyfun.git (fetch)
    upstream	git://github.com/LABSN/expyfun.git (push)
    $ git branch
    * master

URIs beginning with ``git://`` are read-only connections, so ``rkmaddox`` can
pull down new changes from ``upstream``, but won't be able to directly push his
local changes to upstream. Instead, he would have to push to his fork
(``origin``) first, and create a
`pull request <https://help.github.com/articles/using-pull-requests/>`_.
For example, to add some trivial file::

    $ git branch fix_branch
    $ git branch
      fix_branch
    * master
    $ git checkout fix_branch
    $ git branch
    * fix_branch
      master
    $ touch foo.txt
    $ git add foo.txt
    $ git commit -am 'FIX: Add missing foo file'
    $ git push origin fix_branch

This creates a new branch called ``fix_branch`` on the local machine, checks out
that branch, adds a file, commits the change to the branch, and then pushes the
branch to a new remote branch (also called ``fix_branch``) on the ``origin``
repo (i.e., their fork of the official repo). ``rkmaddox`` could then navigate
to `the website of the upstream repository <http://github.com/LABSN/expyfun/>`_
and they would find a nice **Pull Request** button available.

Maintainers_ would then typically comment on the pull request and ask for
some changes. For example, maybe the user forgot to also add the necessary
``bar`` file. The user could then do::

    $ git branch
    * fix_branch
      master
    $ touch bar.txt
    $ git add bar.txt
    $ git commit -am 'FIX: Add missing bar file'
    $ git push origin fix_branch

After this set of commands, the pull request (PR) is automatically
updated to reflect this new addition. The cycle of commenting on and
updating the continues until the Maintainers_ are satisfied with the
changes. They will then
`merge <https://help.github.com/articles/merging-a-pull-request/>`_ the pull
request to incorporate the proposed changes into the upstream GitHub repo.

Once their branch gets merged into the ``master`` branch of
the upstream repo, the developer can do the following to get
up to date on their local machine::

    $ git checkout master
    $ git fetch upstream
    $ git pull upstream/master
    $ git branch -d fix_branch
    $ git branch
    * master

This synchronizes their local ``master`` branch with the ``master`` branch of
the ``upstream`` remote repo, and deletes their local ``fix_branch`` (which is
no longer needed, since its changes have been merged into the upstream master).

# Maintainers

Maintainers start out with a similar set up as Developers_. However, they might
want to be able to push directly to the ``upstream`` repo as well as pushing to
their fork. Having a repo set up with :bash:`git://` access instead of
:bash:`git@github.com` or :bash:`https://` access will not allow pushing. So
starting from scratch, a maintainer ``Eric89GXL`` might fork the upstream repo
and then do::

    $ git clone git@github.com:/Eric89GXL/expyfun.git
    $ cd expyfun
    $ git remote add upstream git@github.com:/LABSN/expyfun.git
    $ git remote add ross git://github.com/rkmaddox/expyfun.git

Now the maintainer's local repository has push/pull access to their own personal
development fork and the upstream repo, and has read-only access to
``rkmaddox``'s fork::

    $ git remote -v
    origin	git@github.com:/Eric89GXL/expyfun.git (fetch)
    origin	git@github.com:/Eric89GXL/expyfun.git (push)
    ross	git://github.com/rkmaddox/expyfun.git (fetch)
    ross	git://github.com/rkmaddox/expyfun.git (push)
    upstream	git@github.com:/LABSN/expyfun.git (fetch)
    upstream	git@github.com:/LABSN/expyfun.git (push)

Let's say ``rkmaddox`` has opened a PR on Github, and the maintainer wants
to test out the code. This can be done this way::

    $ git fetch ross
    $ git checkout -b ross_branch ross/fix_branch

The first command allows the local repository to know about the changes (if
any) that have occurred on ``rkmaddox``'s fork of the project
(`<github.com/rkmaddox/expyfun.git>`_).
In this case, a new branch named ``fix_branch`` has been added.

The second command is more complex. :bash:`git checkout -b $NAME` is a command
that first creates a branch named :bash:`$NAME`, then checks it out. The
additional argument :bash:`ross/fix_branch` tells :bash:`git` to make the
branch track changes from the remote branch ``fix_branch`` in the remote
repository known as ``ross``, which you may recall points to
`<github.com/rkmaddox/expyfun.git>`_. The full command can thus be interpreted
in human-readable form as "create and check out a branch named
``ross_branch`` that tracks the changes in the branch
``fix_branch`` from the remote repo named ``ross``". The maintainer can
now inspect and test ``rkmaddox``'s code locally rather than just viewing the
changes on the GitHub pull request page.

Once the code is merged on GitHub, the maintainer can update their local copy
in a similar way as the developer did earlier::

    $ git checkout master
    $ git pull upstream/master
