*Based on: https://github.com/sympy/sympy/wiki/GSoC-2015-Organization-Application*

This is based on the
[Google Summer of Code 2014 application](GSoC-2014-Organization-Application)
for SymPy to be an organization.

NOTE: Do not use any markup in this document. We have to copy-paste the text
to the application. All URLs should be in plain text.

If you want to add a comment or a TODO, use an html comment (`<!-- like this -->`) so
that it doesn't accidentally end up in the final application.

**If you chose "veteran" in the checkbox, please summarize your involvement in
  Google Summer of Code and the successes and challenges of your
  participation. Please also list your pass/fail rate for each year.**

The SymPy project participated in 2007 under the umbrellas of the Python
Software Foundation, Portland State University, and the Space Telescope
Science Institute.  We had five students in total.  All five projects were
successful. All the projects details can be found here:

[[https://github.com/sympy/sympy/wiki/GSoC-2007-Report]]

In 2008, we participated under the umbrella of the Python Software Foundation
and we got one student, who was successful. All details are here:

[[https://github.com/sympy/sympy/wiki/GSoC-2008-Report]]

In 2009, we participated under the umbrella of the Python Software Foundation
and Portland State University, for a total of five students. All but one were
successful.  Details are here:

[[https://github.com/sympy/sympy/wiki/GSoC-2009-Report]]

In 2010, we participated under the umbrella of the Python Software Foundation
and Portland State University.  There were five students, all of whom were
successful in their projects.  The details are here:

[[https://github.com/sympy/sympy/wiki/GSoC-2010-Report]]

In 2011, we participated as an official mentoring organization for the first
time. We mentored nine students, all of whom were successful in their
projects. The details are here:

[[https://github.com/sympy/sympy/wiki/GSoC-2011-Report]]

In 2012, we participated as an official mentoring organization for the second
time. We mentored six students, all of whom were successful in their
projects. The details are here:

[[https://github.com/sympy/sympy/wiki/GSoC-2012-Report]]

In 2013, we participated as an official mentoring organization for the third
time. We mentored seven students, all of whom were successful in their
projects. The details are here:

[[https://github.com/sympy/sympy/wiki/gsoc-2013-report]]

In 2014, we participated as an official mentoring organization for the fourth
time. We mentored ten students, all of whom were successful in their
projects. The details are here:

[[https://github.com/sympy/sympy/wiki/gsoc-2014-report]]

A total of 47 out of 48 GSoC projects (44 out of 45 students) were successful,
and they incredibly boosted SymPy's development. Some of the students who did
this program have continued developing for SymPy after the program ended,
again helping to boost the program.  Not only are these students sticking
around and writing code, but many have come back as mentors, both for the
Google Summer of Code and Google Code-in programs. For example, the current
SymPy project leader (Aaron Meurer) participated in 2009 and 2010.  In 2011,
Ondřej Čertík, the founder and leader of the project, asked him to step up and
be the leader of the project. Aaron would have never have heard of the project
and would not be doing any work at all for open source were it not for the
Google Summer of Code program.  Last year, five of the ten mentors were
previous GSoC students.

For almost all of the projects, it is almost certain that they would have
never been coded if it were not for the Google Summer of Code program, because
they were implemented by students who otherwise either would not have known
about SymPy or else wouldn't be able to dedicate their summer to working on it
without the stipend.  Many projects require the full summer of full time work
to bring to a usable state, making them difficult for the existing community
to implement.  SymPy is also special in that many projects that have been
implemented require advanced knowledge in math and related fields well beyond
the scope of traditional computer science and Python programming.  In many
cases the rest of the community would not have been able to implement the
project at all.

**Why is your organization applying to participate in Google Summer of Code
  2015? What do you hope to gain by participating?**

From previous experiences, we've found that GSoC is an effective way to get
students involved in the project, by coding on a specific task with a finite
timeline.

It will be beneficial for the project and the students, who will get the
chance to write code for an open source project (and get paid for it).

Our participation from the past four years as an official mentoring
organization has been very successful, totaling 32 projects with a 100% pass
rate.  A full reports are available at
[[https://github.com/sympy/sympy/wiki/gsoc-2011-report]],
[[https://github.com/sympy/sympy/wiki/gsoc-2012-report]],
[[https://github.com/sympy/sympy/wiki/gsoc-2013-report]], and
[[https://github.com/sympy/sympy/wiki/gsoc-2014-report]]. We received boosts to
many parts of our code base as a result.

Almost all of these projects would have never happened without GSoC, as our
active community members would not have the time to do this work.  Or, as is
more often the case, they would not have the background knowledge to do the
projects.  Due to the highly technical nature of SymPy, many projects require
an advanced knowledge in some mathematical area to complete. GSoC gives us the
opportunity to find people capable of completing such projects.

At the time of this writing, half of the core developers with push access to
the main development repo originated as GSoC students (14 out of 30),
including the lead developer.  Without this program, it is unlikely that any
of them would have ever joined the project.

**How many potential mentors do you have for this year's program? What
criteria did you use to select them?**

<!-- Make sure to update this number before submitting -->

We currently have 12 mentors signed up (see the bottom of our ideas page,
[[https://github.com/sympy/sympy/wiki/gsoc-2015-ideas]]). They have been
chosen from members of the community who have shown themselves to be committed
to the development of SymPy.  This means that they will be familiar both with
the code base and with git, so they will be able to help the students
effectively with these.  Also, we put lots of effort in choosing mentors who
are familiar with the concepts that the student will be implementing.  In
SymPy, these are often mathematically complicated, so it is useful to have a
mentor who understands them well.  And of course, if someone whom we feel
meets the above qualifications wants to mentor a particular student, we will
let him/her, because that person is the most likely to be the best person to
stick with that student and help him or her to complete his project.

We require all our mentors to be active contributors with push access to the
repo. Those are people that have already proven to be part of the SymPy
community and proven that they can be trusted. This is an obvious pool of
people to choose from. In the past, we had mentors from outside this pool, for
example a university professor familiar with the field of the
project. However, such mentors tend to be poorer, because they are not active
in the community.  We would only choose such mentors to be secondary mentors,
with the primary mentor as an active contributor.

In 2011, we made a big push for students to be active in the community, so
that instead of just talking with their mentors directly, they ask questions
on the public mailing list or Gitter chat, where even if the mentor is the
only one to answer, everyone will see and have a chance to comment.  We found
that this led to a huge increase in involvement after the program. Five of the
nine students from 2011 are still active in the community a year later, and
three are still active today. In contrast, only one of the five students from
2010 was active a year later.

Therefore, one of the key roles of the mentors will be to push the students to
participate openly as much as possible.  Thus, though it will still be the
mentors' responsibilities to ensure that their students are not slipping
behind, and to make sure that their code gets reviewed, the whole community
will serve to "mentor" the students in that they will follow their work and
participate in design discussions. In the past, we have even had members of
the user community be active in certain projects that were exciting new
developments, leading to things like pull requests against students' code.

**What is your plan for dealing with disappearing students?**

To begin with, we structure our application to try to pick students who will
not disappear.  We require all students to have submitted at least one patch
that passes review and is pushed into the code base in order to be considered.
This will show that they are dedicated, because they must be willing to learn
the code base enough to try fixing part of it, and be willing to stick around
for the review process.  It will also help prevent us from accepting students
who are unable to complete the project by ensuring that they are competent
enough to learn the basics of git and work within our preferred workflow.  The
patch submission process requires that the student communicate with the
community in the review process, especially since first patches tend to
require work before they can go in.  This will also help us to determine the
student's level of communication.  As was mentioned before, we have found a
strong correlation between level of open communication with the community and
success and permanence of a student.

We require each student to start a blog, if they don't already have one, and
to blog once a week about their progress.  We will additionally require that
the mentors and the students meet at least once a week, by whatever method is
best for the two of them (email, the mailing list, Gitter, etc., though we
encourage those methods that are public to the community).  However, we will
also try to get the students to stay in touch with the entire community
through the mailing list.

We will also require that students push their work to an online git repository
at GitHub, so that the mentor, as well as everyone in the project, can monitor
their progress and to see the things that they are doing, as well as to help
them fix mistakes early.   Not only should they push their work to a branch,
but every time they have work completed, they should make a pull request with
that work, so that the mentor and the community can start reviewing it, and so
that it can be pushed in as soon as it is ready, so that it doesn't grow
stale.

These two things (the blog and pushing often) will allow us to notice when
students have disappeared sooner, so that we can take action and hopefully
remedy the situation so that the student does not fail. If a student
disappears or does not work up to his or her potential, the mentor and the
SymPy organization admins will try to sit down with the student in a Google
hangout conversation or via some other medium to try to see what is holding
him or her back and how he or she can be brought back on track.  If necessary,
we may need to adjust the goals as originally stated in the student's
application, because it is better for a student to do a reduced amount of work
than to do nothing at all.  If the student stops being responsive, we will
require him/her to report daily on what work he or she did, and also setup a concrete plan that the student must complete otherwise he or she will be failed. 
We have done these things in the past, and it has helped students who
would otherwise have failed to complete enough work that we can satisfactorily
pass them.

If that doesn't help, then before failing him or her, we will raise the issue
among all the mentors.  In the past it was discussed with the Python Software
Foundation, who was the umbrella organization.  As a standalone organization,
we will try to discuss this (privately) with similar organizations, like the
Python Software Foundation, to get an outside opinion.  If there are any
doubts, we will also use the main GSoC list for mentors.  This is so that we
can make sure that the student was not treated/failed unfairly.

If nothing works, and it becomes clear that trying to get the student to work
is a waste of our mentors' time and Google's money, we will fail the student
in his midterm or final evaluation.  But this will be a last resort, because
it will be to everyone's benefit if the student can be brought back on track.
We believe that it should not come as an honest surprise to the student if he
or she is ultimately failed.

From the students that SymPy had so far, one project had to be ended at
midterm, and we followed the above procedure in that case. Other projects
started to decline after the midterm, but we were able to turn them around
before the final.

**What is your plan for dealing with disappearing mentors?**

Traditionally, SymPy has had a lot of willing backup mentors. We are in
frequent contact with all our mentors and we have collaborated with each other
for several years, so we do not expect that such thing would happen.  However,
we will assign a backup mentor for each student just in case.

Many of our mentors have mentored with us in the past, so we have an idea of
how reliable they are. We will be more cautious with new mentors, being sure
to always pair them with a more seasoned mentor.

Furthermore, we encourage students to interact with the whole community, and
ask the whole community for help (i.e., on the Gitter chat room or on the
mailing list) if they have a problem, rather than asking just one person.
This will help them to become better members of the community and will also
make it easier for the whole community to monitor their progress, as well as
increase the chance of the students to stick around after the GSoC is over.
It will also make it easier as an org admin to notice if a student or mentor
has disappeared, because we will see that there has been no communication from
them. Hopefully, in the unlikely case that a mentor disappears or even if he
or she has to become less available for a little while, it will not be a huge
issue for this reason.  Additionally, in the past, exceptional GSoC students
have helped each other out, though obviously we will not rely on this
happening.

We will also make sure to not request or assign too many slots. For example,
if we have ten mentors, then we should not request ten slots, because that
will stretch us too thin, an there will be no backup people if a mentor
disappears. It would be better to only request five slots in that case.

If, given the above, there is still some problem, both of the admins, Aaron
Meurer (the current project leader) and Ondřej Čertík (the former project
leader) are ready to step up and become a mentor or co-mentor for any project
if needed.  This has happened in the past, and we were able to mentor the
student to success (we also will not allow these people to mentor any more).

As shown by the past years of our experience with GSoC, this model seems to
work very well for us.

**What steps will you take to encourage students to interact with your
  project's community before and during the program?**

We require all applicants to submit a patch to the project that gets reviewed
and pushed in (see
[[https://github.com/sympy/sympy/wiki/GSoC-2015-Application-Template]] for a
full list of our requirements).  We do not require that this be a particularly
complicated patch.  In fact, we will reference to them the easy to fix issues
in our tracker:

[[https://github.com/sympy/sympy/issues?q=is%3Aopen+is%3Aissue+label%3A%22Easy+to+Fix%22]]

This is so that we can make sure that they can submit a patch and use git (if
they can't we teach them at this stage) and also so that we have some
experience with how they interact over email and other communication media.
We will communicate with them very frequently before they are accepted, and
try to get them involved in our community.  If we find that a student cannot
do these fundamental things, then he or she will not be accepted to the
program, even if their work and application are otherwise high quality.

In recent years, the patch requirement has become more of a bare minimum than
a requirement. The increasing popularity of Google Summer of Code and our
limited number of mentors generally makes the program competitive, so that the
best students, who we end up accepting, typically go beyond these base
requirements.

During the program, they need to blog once a week about their progress and are
encouraged to become active members of our community.  The mentors will also
have a meeting with the students regularly (once a week) to monitor their
progress.  We will leave this up to the mentor and the student to schedule,
because they may have problematic schedules to synchronize, not to mention
that they are often in distant timezones, but we will encourage them to do any
meeting publicly, such as on our logged public chat room on Gitter, so that it is
public to the entire community.  If it is more accessible to the mentor and
student to meet in over some other medium (e.g., over phone or in person), we
will ask them to provide minutes of the meeting somehow (for example, on the
student's blog). Public meetings are highly preferred, however, as it makes it
easier for the org admins to notice if a student or mentor has disappeared.

In general, we will try to teach the students that it is better to do things
publicly.  For example, we will encourage them to ask questions on our mailing
list or Gitter chat rather than over a private email or private chat.
Even if the mentor is the only person who responds to the question, the whole
community will be involved.  This will teach the student good habits about
interaction in open source.  In the past, we have found that it is those
students who have these good habits who tend to stick around. As noted in a
previous question, in 2011 we made a big push to do this better, and it
resulted in a huge increase in the number of students who stuck around after
the program.

**What will you do to encourage your accepted students to stick with the
  project after Google Summer of Code concludes?**

This year we plan to require each student to spend at least 10% or more of
their time in reviewing other people's pull requests (PRs) (most of these will
invariably be from other GSoC students, since they tend to be the most active
contributors during the summer time). That way, they will become more
integrated in our community and hopefully more likely to stay after the GSoC
is over. Historically, students that were active in our PR queue were more
likely to stay afterwords.

Making sure that the accepted students stick around has been the most
important thing for us (besides their actually finishing their projects),
because that is the only way to grow our community. We do not view GSoC as a
two month program, but rather as a great opportunity to get more people
involved with the project on the long term.

We have found that the most effective way to get students hooked in is to
directly encourage them to post and discuss issues on our public mailing list
and to publicly help other people (not just other GSoC students but anybody
who needs help).

After the program is over, the students already have their blogs, which are
synchronized with [[http://planet.sympy.org/]], and usually if they blogged
interesting things, they already built a nice community around their blogs,
and so they continue blogging about what they do (for example, on that site
right now, many of the recent blog posts are by prior GSoC students who have
stuck around and continued to work with the community).

It all depends how they like our community and how they communicate with
others, so we will try hard to make them feel comfortable so that they will
stick around.  This is how we treat all contributors to our project, not just
GSoC students, because we have found that it's the best way to get people to
contribute again.

We do encourage all students to stick around and become regular members of the
community.  Sometimes they do, and become valuable contributors and sometimes
they even participate in Google Summer of Code again in future years, either
as a students again or as mentors.  Other times, they move on to do their own
things, though often they will still sometimes submit bug reports or patches.
We will try to accept students who are likely to become regular contributors
to the community after the program ends, because that will benefit SymPy the
most.  But we do realize that people can become interested in other things, so
we do not require this of students (if it were even possible to require such a
thing), but we do let them know that our expectation, as well as the
expectation of the GSoC program, is to "contribute to open source, while
getting paid, and stick around later and contribute more," as opposed to
"getting paid, while contributing to open source, and move on after the job is
finished."

**Are you an established or larger organization who would like to vouch for a
  new organization applying this year? If so, please list their name(s)
  here.** *NOTE: This question is optional*

We'd like to vouch for the PyDy project (http://pydy.org). The PyDy project
aims to build the tools needed to derive, simulate, and visualize multibody
dynamic systems (i.e. robots, musculoskeletal models, vehicles, machinery,
etc). SymPy currently hosts PyDy's core package, mechanics, which symbolically
derives the equations of motion of multibody systems. PyDy has and will
continue to have a symbiotic relationship with SymPy but the PyDy project is
growing to encompass aspects that do not necessarily fit inside SymPy's code
base, so they are starting up an independent project to house the new
software. PyDy was birthed from three previous SymPy related GSoC projects
and, we'd like to vouch for their ability to mentor students under the GSoC
program and maintain a quality project.

PyDy participated in GSoC last year under the umbrella of the PSF. Jason
Moore and Chris Dembia, their org admins, did an excellent job of mentoring their
students: two of SymPy students and one PSF student.

**Is there anything else we should know or you'd like to tell us that doesn't
  fit anywhere else on the application?** *NOTE: This question is optional*

<!-- Anything we should put here? -->

## BELOW IS LAST YEAR'S APPLICATION. PLEASE INTEGRATE IT INTO THIS YEAR'S QUESTIONS AND DELETE

# Links (This is not part of the application)

- [[GSoC-2015-Ideas]] -- Ideas for Google Summer of Code projects
- [[GSoC-2015-Application-Template]] -- The template for student applications
  for Google Summer of Code.
- [[GSoC-2015-Current-Applications]] -- A list of active proposals.
- [[GSoC-2014-Report]] -- Report for the GSoC 2014
- [[GSoC-Previous-Applications]] -- Some examples of successful Google Summer
  of Code applications from the past.

<!-- Ignore this: it's so Emacs's Ispell will ignore these words -->
<!--  LocalWords:  GSoC UTC CAS url popup certik IRC Googler Freenode PyDy
 -->
<!--  LocalWords:  PyDy's
 -->
