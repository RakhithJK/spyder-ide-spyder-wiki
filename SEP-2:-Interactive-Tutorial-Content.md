| key            | value                                                 |
|----------------|-------------------------------------------------------|
| Status         | Active                                                |
| Author         | Gonzalo Peña-Castellanos ([@goanpeca](https://github.com/goanpeca))                  |
| Created        | February 24, 2015                                     |
| Updated        | March 04, 2015                                     |
| Discussion     | link to the issue where the SEP is being discussed    |
| Implementation | link to the PR                                        |

# Description

# Suggested Content

## scipy lectures notes
We could try to include a scientific python course in the interactive course like the one developed by the europython community that could be found here:

[GitHub page](https://github.com/scipy-lectures/scipy-lecture-notes)

[live preview](http://scipy-lectures.github.io/)

The course cover all the basics from numpy, scipy and matplotlib to more advanced topics like scikits image and learn, sympy and numpy optimization.
The content is great and cover most of the topics necessary for a beginner scientist that wants to start using python for its everyday content.

The content are written in rst, so we coud either fork the content and adapt it, or find a way to automatically sync to the upstream repo.

## python from matlab/R conversion

Several user of Spyder comes from a background of using MATLAB or R.
This connection is recognized by the Spyder team, as one of the possible disposition is an explicit reference to MATLAB. 

In my experience one of the things that prevent the adoption of python for scientific environment is the cost of conversion. Having an explicit tutorial to ease the transition could help the transition.

There are several conversion tutorial online, as:
[The scipy page for matlab -> numpy](http://wiki.scipy.org/NumPy_for_Matlab_Users)

[Mathesaurus page about matlab -> numpy](http://mathesaurus.sourceforge.net/matlab-numpy.html)

[hyperpolyglot for matlab, r and python](http://hyperpolyglot.org/numerical-analysis)

[a tutorial for matlab -> numpy](http://bastibe.de/2013-01-20-a-python-primer-for-matlab-users.html)

[pdf cheatsheet for matlab -> numpy](http://web.stanford.edu/class/physics91si/2014/handouts/matlab-python-xref.pdf)

Of course all these material are available online, but having it in the everyday IDE would probably reduce the opportunity cost of finding a solution to the problem.

## cheat sheet for cvs and simulation management
In the last few years the concept of reproducibility in computational science has become a major issue.
Aside from the statistical and methodological steps required in every fields, the computational side has several tools that can help with the process, nominally control version system and simulation management systems.

An example of the first is git, that is currently used as the CVS for spyder, while for the second systems like [sumatra](https://pythonhosted.org/Sumatra/) could be used.
These tools can help the user to deal with most of the long term problems that scientist are faced, but require the scientist to learn new tools external of its workflow.

This is not a problem, but a simple interactive help to remind the user of the most common command and issues with these instruments could simplify the everyday work.

## TODO

#Implementation Details
The impletation should be easy enough.
The interactive tutorials are simply rst files, so write them is simple.

To expand the interactive tutorial menu the reference line in the code are the following:

[Including the line in the menu](https://github.com/EnricoGiampieri/spyder/blob/master/spyderlib/spyder.py#L943)

[loading the rst file in the viewer](https://github.com/EnricoGiampieri/spyder/blob/master/spyderlib/plugins/inspector.py#L776)