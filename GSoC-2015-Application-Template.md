*Based on: https://github.com/sympy/sympy/wiki/GSoC-2015-Application-Template*

GSoC 2015 Application Template
==============================

Things to do
------------

* Join the [Spyder mailing list](https://groups.google.com/group/spyderlib) 
  and introduce yourself.  Not only do we get to know you, but you can use 
  the mailing list to get feedback on project ideas and get help as you
  start working with the code base.

* Write and submit a proposal to the Google Summer of Code website
  (http://www.google-melange.com). If you want to, you can draft your project
  proposal on our wiki (https://github.com/sympy/sympy/wiki/).  This is not
  required, but if you do, we will help you proofread it.  See the section
  below for how to name and link to your application so we can easily find it.
  You may take a look at the old applications to see how they did things,
  links to pages containing old applications can be found on the wiki main
  page.

* You will need to create an account on GitHub and send a patch.  See below.

* If you need help with anything, ask on the `SymPy list
  <http://groups.google.com/group/sympy>`_ or Gitter
  (https://gitter.im/sympy/sympy) (don't be afraid if you don't
  know git for example. We'll teach you everything that is needed, the only
  required thing from you is enthusiasm and willingness to learn new things).


Writing your proposal
---------------------

To be considered, a GSoC application must have a written proposal submitted to
http://www.google-melange.com/.

If you want, you can start a wiki page to work on your proposal at
https://github.com/sympy/sympy/wiki/.  If you add your proposal there, we will
help you edit it and provide feedback (though understand that we will not help
you write it).  You can add your application to our list of
[[GSoC 2015 Current Applications]].  To maintain a consistent naming
scheme, title your application: "GSoC 2015 Application <Your Name>: <Project
Name>".  Old applications can be found either through the links on the main
page of the wiki or by browsing through [[_pages]].

Note that your final application must be submitted at
http://www.google-melange.com/, so do not worry about the formatting of your
application on the wiki, as you will have to reformat it there.  You should
not be too concerned with the formatting in Melange either, as we understand
that the text editor there is not the best for making things look nice
formatting-wise.  We are more concerned with the content of your application,
and that it is readable.

You may be able to get equivalent formatting in Melange from the wiki by
copying the webpage contents or messing with the HTML source, but you
shouldn't worry about it too much.

You should include the following information in your proposal:

Title
^^^^^

Since this year we have to accept students under umbrella organizations, please start the title of your proposal with "SymPy - ", like "SymPy - Improving the Risch integration algorithm". Please use a succinct title that describes your proposal. Do not include the words "GSoC", "2015", or your name in the proposal title. 

You the person
^^^^^^^^^^^^^^

**Please put this information at the top of your proposal.**

* Your full name

* University / current enrollment

* Short bio / overview of your background

* How can we contact you (email, GitHub username, etc.)?  This information
  will help us associate all of your various usernames with you.

  - Email
  - GitHub username
  - Any other user name you want us to know about

Also, please use your full real name in your Melange profile, so that it
appears in the proposal list.

You the programmer
^^^^^^^^^^^^^^^^^^

In your project proposal let us know about your programming experience.  Don't
worry if you don't know SymPy or git.  Many of our students start fresh.
We will teach you what you need to know.

* What platform do you use to code?  What editor do you prefer and why?

* What is your experience programming?  Tell us about something you have
  created.

* What is your experience with Python?  What are your favorite features of
  Python that are lacking in most other common programming languages?  What,
  in your opinion, is the most advanced Python language feature or standard
  library functionality that you have used?

* What is your favorite feature of SymPy?  Demonstrate it here with a cool example.

* Have you ever used git or another version control system?


You and your project
^^^^^^^^^^^^^^^^^^^^

Answer the following questions in your proposal:

* What do you want to achieve?

* What excites you about this project?  Why did you choose it?

* What qualifications do you have to implement your idea?  For example, if you
  are implementing solvers for partial differential equations, what courses
  have you taken or books have you read on PDEs?  Why are you suited to work on
  this project?

* What have other people done on this idea?  Has it been implemented before?
  (hint: it probably has)  Are there any papers or blog posts about it?

* How much time do you plan to invest in the project before, during, and after
  the Summer of Code? (we expect full time 40h/week during GSoC, but better
  make this explicit) If you plan to take any vacations over the summer, let
  us know about it here.

* Please provide a schedule of how this time will be spent on sub-tasks
  of the project over the period of the summer. While this is only
  preliminary, we will use it to help monitor your progress throughout
  the program.  Also understand that during the project you will issue
  weekly progress reports against that plan on your blog.

* In planning your project, it is good to note where along the way you could
  formulate a pull request. These would be points where you can have a self
  contained and well documented and tested piece of functionality. Doing this
  at several points during the summer helps to keep branch merges reasonable
  and code reviews manageable. A big code dump at the end of the summer will
  likely be hard to review and merge before the project deadline.

* Please do not verbatim copy text from the ideas page, or from other people's
  discussions about your project, but rewrite it in your own words.  If you
  include any significant text or code from another source in your
  application, it must be accompanied with a proper citation.  All papers or
  references that you use or plan to use must also be cited.  Put all this in
  a "References" section at the bottom of your application.

You do not need to format your application as a question/answer format
for the above questions, but we expect to see all of the above questions
answered in your application somewhere.

Patch requirement
-----------------

In addition to the written proposal, we require every GSoC applicant to write a
patch and get it pushed into our current master. To do this:

* Set up your platform to develop with SymPy (install git, clone
  https://github.com/sympy/sympy.git, execute tests). The page on our
  [[Development workflow]] will walk you through setting up git and lays out
  our preferred way of development.

* Create an account at GitHub and fork SymPy (https://github.com/sympy/sympy).

* Find something in SymPy that doesn't work or needs improvement and send us a
  git patch fixing it. If you need inspiration, feel free to fix any issue
  from our `easy to fix issues list
  <http://code.google.com/p/sympy/issues/list?q=label:EasyToFix>`_. Aside from
  the issues, search for ``FIXME`` or ``TODO`` in the code. You can grep from
  the command line with ``git grep "TODO"`` . You could also search for
  NotImplementedErrors and XFAILs).  You could also play with SymPy and find
  something that needs fixing or that could be implemented, and do it.

* Your patch must be code-related, not documentation. If your project will use
  a language other than Python (e.g., JavaScript), you should submit patches
  that use that language as well, so that we know that you know you are
  proficient in that language. **However, for the patch requirement to be
  fulfilled, you must have at least one patch in SymPy itself.**

* Report success on the SymPy list

* Publish your patch for peer review by creating a pull request on GitHub.
  You must submit a patch that is successfully reviewed and pushed in to be
  accepted. We do not consider applications without patches. This shows us that
  you know Python and that you are able to interact with the community.
  Furthermore, your patch must go through a GitHub pull request (as opposed to
  a patch file on an issue, for example), as this is not only the easiest way
  for us to review your code, but is also what we expect from a student working
  on a GSoC project.

* **In your application, please provide a brief summary of your contributions to
  SymPy so far, including unmerged work. At least one link to a merged pull
  request proving that you satisfied the patch requirement.**

* Note that because we may be slow to review the pull requests, you do not
  have to have your request merged by the application deadline (though you
  should try to do it if you can!).  But you do need to at least have one
  submitted by then.  We will give priority to reviewing requests that are
  needed to satisfy patch requirements.  It is up to you to respond to our
  feedback in a timely enough manner so that your patch gets merged before the
  acceptance deadline.

..  Ignore this.  These are words to be ignored by Emacs's Ispell spellchecker
..  LocalWords:  GSoC GitHub IRC FIXME TODO NotImplementedErrors XFAILs PDEs
..  LocalWords:  Freenode
