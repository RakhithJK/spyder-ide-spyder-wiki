*Based on: https://github.com/sympy/sympy/wiki/GSoC-2015-Ideas/*

# GSoC 2015 Project Ideas

This is the list of ideas for students wishing to apply for Google Summer of Code 2015. For more information on how to apply, see [[GSoC 2015 Application Template]].

This is for inspiration, you can apply with something completely different if you like. The best project for you is one you are interested in, and are knowledgeable about.  That way, you will be the most successful in your project and have the most fun doing it, while we will be the most confident in your commitment and your ability to complete it.

If you do want to suggest your own idea, please discuss it with us first, so we can determine if it is already been implemented, if it is enough work to constitute a Summer's worth of coding, if it is not too much work, and if it is within the scope of our project.

Even if you want to do an idea listed here, you should still contact us on our mailing list and discuss it with us.  Also take a look at our [[application template|gsoc-2015-application-template]].

**Please always ask on our [mailing list](http://groups.google.com/group/spyderlib) about these ideas to get the latest information about what is implemented and what exactly has to be done.**

The list is organized as follows:

 1. "High Priority" - projects that are considered important in our roadmap.
 2. "Detailed Projects: Mathematics" - well developed ideas of interest for us, however they
 do not block the release of the next major version of SymPy. These require deep understanding
 of the mathematics in question.
 3. "Detailed Projects: Physics" - well developed ideas of interest for us, however they
 do not block the release of the next major version of SymPy. A number of well developed modules dealing with classical and quantum physics are being developed as part of SymPy.
 4. "Detailed Projects: Computer Science, GUIs, Graphics, Infrastructure" - well developed ideas of interest for us, however they
 do not block the release of the next major version of SymPy. These projects do not necessitate deep understanding of math. Nonetheless they are just as challenging.
 5. "Ideas" - list in a "brainstorming" style that has _many_ nice project
 ideas. Each "Detailed Projects" entry was born in this list. Read it carefully
 as the most interesting projects may come from there.

The order of ideas in this list has no bearing to the chances of an idea to be
accepted. All of them are equally good and your chances depend on the quality
of your application. As already said, you can very well submit your own idea
not listed here.


## Table of Contents
- [High Priority](#high-priority)
  - [Assumptions](#assumptions)
- [Detailed Projects: Mathematics](#detailed-projects-mathematics)
  - [Solvers](#solvers)
  - [Group theory](#group-theory)
  - [Risch algorithm for symbolic integration](#risch-algorithm-for-symbolic-integration)
  - [Ordinary Differential Equations](#ordinary-differential-equations)
  - [Series expansions](#series-expansions)
  - [Cylindrical algebraic decomposition](#cylindrical-algebraic-decomposition)
  - [Polynomials module](#polynomials-module)
    - [Efficient Groebner bases and their applications](#efficient-groebner-bases-and-their-applications)
    - [Multivariate polynomials and factorization](#multivariate-polynomials-and-factorization)
    - [Univariate polynomials over algebraic domains](#univariate-polynomials-over-algebraic-domains)
  - [Concrete module: Implement Karr algorithm, a decision procedure for symbolic summation](#concrete-module-implement-karr-algorithm-a-decision-procedure-for-symbolic-summation)
  - [Linear Algebra: Tensor core](#linear-algebra-tensor-core)
  - [Step-by-step Expression Visualization](#step-by-step-expression-visualization)
    - [A Strategy for step-by-step](#a-strategy-for-step-by-step)
- [Detailed subprojects in Physics](#detailed-subprojects-in-physics)
  - [Symbolic quantum mechanics (sympy.physics.quantum)](#symbolic-quantum-mechanics-sympyphysicsquantum)
    - [Abstract Dirac notation](#abstract-dirac-notation)
    - [Implement All Known Analytical Solutions to Quantum Mechanical Systems](#implement-all-known-analytical-solutions-to-quantum-mechanical-systems)
    - [Position and momentum basis functions](#position-and-momentum-basis-functions)
    - [Symbolic quantum computing](#symbolic-quantum-computing)
    - [Second quantization capabilities](#second-quantization-capabilities)
  - [Symbolic vector calculus and classical mechanics in SymPy (sympy.physics.vector and sympy.physics.mechanics)](#symbolic-vector-calculus-and-classical-mechanics-in-sympy-sympyphysicsvector-and-sympyphysicsmechanics)
- [Projects for vector package](#projects-for-vector-package)
- [Detailed subprojects in CSymPy](#detailed-subprojects-in-csympy)
  - [Port SymPy's new Assumptions to C++](#port-sympys-new-assumptions-to-c)
  - [Implement Fast Series Expansion](#implement-fast-series-expansion)
  - [Improve Python wrappers](#improve-python-wrappers)
- [Detailed subprojects in Computer Science, Infrastructure, GUIs and Graphics](#detailed-subprojects-in-computer-science-infrastructure-guis-and-graphics)
  - [Code Generation](#code-generation)
  - [SymPy subprojects related to GUIs and user interaction](#sympy-subprojects-related-to-guis-and-user-interaction)
    - [SymPy Live and SymPy Gamma (on Google App Engine)](#sympy-live-and-sympy-gamma-on-google-app-engine)
  - [Parsing](#parsing)
  - [Improve the plotting module](#improve-the-plotting-module)
  - [Benchmarks](#benchmarks)
- [Other Related Projets](#other-related-projets)
- [Ideas](#ideas)
- [Non-Ideas](#non-ideas)
- [Potential Mentors](#potential-mentors)

## High Priority

### Assumptions

Possible mentors: Aaron Meurer, Ondřej Čertík.

The project is to completely remove our old assumptions system, replacing it
with the new one.

The difference between the two systems is outlined in the first two sections of [this blog post](http://matthewrocklin.com/blog/work/2013/02/05/Assuming/).  A list of detailed issues can be found at [this issue](https://code.google.com/p/sympy/issues/detail?id=3631).

This project is challenging.  It requires deep understanding of the core of SymPy, basic logical inference, excellent code organization, and attention to performance.  It is also very important and of high value to the SymPy community.

You should take a look at the work started at
https://github.com/sympy/sympy/pull/2508.

Numerous related tasks are mentioned in the "Ideas" section.

## Detailed Projects: Mathematics

### Solvers

SymPy already has a pretty powerful `solve` function. But it has a lot of major
issues
1. It doesn't have a consistent output for various types of solutions
   It needs to return a lot of types of solutions consistently:
   * single solution : ` x == 1`
   * Multiple solutions: `x**2 == 1`
   * No Solution: `x**2 + 1 == 0; x is real`
   * Interval of solution: `floor(x) == 0`
   * Infinitely many solutions: `sin(x) == 0`
   * Multivariate functions with point solutions `x**2 + y**2 == 0`
   * Multivariate functions with non point solution `x**2 + y**2 == 1`
   * System of equations `x + y == 1` and `x - y == 0`
   * Relational `x > 0`
   * And the most important case "We don't Know"


2. The input API is also a mess, there are a lot of parameter. Many of them
   are not needed and they makes it hard for the user and the developers to
   work on solvers.

3. There are cases like finding the maxima and minima of function using
   critical points where it is important to know if it has returned all the
   solutions. `solve` does not guarantee this.

During the summer of 2014 Harsh Gupta worked to improve solvers as part of his
GSoC project. Instead of making changes in the current `solve` function a new
submodule named `solveset` was written.

* `solveset` has a cleaner input and output interface: `solveset` returns a set
  object and a set object take care of all the types of the output. For cases
  where is doesn't "know" all the solutions a `NotImplementedError` is raised.
  For input only takes the equation and the variables for which the equations
  has to be solved.

* `solveset` can return infinitely many solutions. For example solving for
  `sin(x) = 0` returns {2⋅n⋅π | n ∊ ℤ} ∪ {2⋅n⋅π + π | n ∊ ℤ} Whereas `solve`
  only returns [0, π]

* There is a clear code level and interface level separation between solvers
  for equations in complex domain and equations in real domain. For example
  solving `exp(x) = 1` when x is complex returns the set of all solutions that
  is {2⋅n⋅ⅈ⋅π | n ∊ ℤ} . Whereas if x is a real symbol then only {0} is
  returned.

* `solveset` returns a solution only when it can guarantee that it is returning
  all the solutions.

There had been a lot of discussion during and before the project and you should know why we did what we did. Here are some links:

* [Discussion on the mailing list](https://groups.google.com/forum/#!searchin/sympy/solvers/sympy/Oyz8SkR2fRk/RMpooqwu3oMJ)
* [Action Plan on solvers](https://github.com/sympy/sympy/pull/2948)
* [Harsh Gupta's proposal for GSoC 2014](https://github.com/sympy/sympy/wiki/GSoC-2014-Application-Harsh-Gupta:-Solvers)
* [Harsh's blog for GSoC](http://hargup.github.io/categories/sympy.html)
* [solveset pull request](https://github.com/sympy/sympy/pull/7523)

Here's a brief list of things that needs to be done:
* Solveset only solves a single equations for a single variable. It should be
  capable to solving a system of equations and for more than one variable.
* Implement more equation solvers for univariate algebraic equations. For example equations solvable by LambertW function
* Build the set infrastructure: This includes implementing complex sets and
  functions to handle multidimentional ImageSet etc., This part must go hand in
  hand with the improvements in the solvers as set module can be a universe in
  itself. Also there can be fundamental limits on the things you can do.

This project is difficult because it requires a good deal of thought in the
application period. You should have a clear plan of most of what you plan to
do in your application: waiting until the Summer to do the designing will not
work.

[#8725](https://github.com/sympy/sympy/issues/8725) and [#8711](https://github.com/sympy/sympy/issues/8711)
can be good entry points.


### Group theory

Implement a module to work with groups.  You should take a look at the GAP
library, as this is the canonical group theory computation system right now.
Some things to think about:

- How do you represent a group?
- How do you represent the elements of a group?
- Can we support both finite and infinite groups?
- Can we support defining groups by generators?

Algorithms to think about implementing:

- Computation of subgroups of various types (e.g., normal subgroups).
- Computation of Galois groups for a given polynomial.

Also take a look at the Permutation class already implemented in SymPy.

Some work is already done on discrete groups. Nonetheless there is still much
that can be done both for discrete groups and for Lie groups.

### Risch algorithm for symbolic integration

  * The project is to continue where Aaron Meurer left off in his 2010 GSoC
    project, implementing the algorithm from Manuel Bronstein's book,
    _Symbolic Integration I:  Transcendental Functions_.  If you want to do
    this project, be sure to ask on the mailing list or our IRC channel to get
    the status of the current project.

  * **Status** The algorithm has already been partially implemented, but there
    is plenty of work remaining to do.  Contact Aaron Meurer for more
    information. There was also work done in 2013, which hasn't been
    completely merged yet. A good place to start would be to look at finishing
    this work: https://github.com/sympy/sympy/pulls/cheatiiit. See https://groups.google.com/forum/#!msg/sympy/bYHtVOmKEFs/UZoyDX81eP4J for some more details on this project (nothing has changed since that email thread). 

  * **Idea** The Risch algorithm is a complete algorithm to integrate any
    elementary function.  Given an elementary function, it will either produce
    an antiderivative, or prove that none exists.  The algorithm described in
    Bronstein's book deals with transcendental functions (functions that do
    not have algebraic functions, so ``log(x)`` is transcendental, but
    ``sqrt(x)`` and ``sqrt(log(x))`` are not).

  * **Prerequisites** You should have at least a semester's worth of knowledge
    in abstract algebra.  Knowing more, especially about differential algebra,
    will be beneficial, as you will be starting from the middle of a
    project. Take a look at the first chapter of Bronstein's book (you should
    be able to read it for free via Google Books) and see how much of that you
    already know.  If you are unsure, discuss this with Aaron Meurer (asmeurer).


### Ordinary Differential Equations

Currently, SymPy only supports many basic
types of differential equations, but there are plenty of methods that are
not implemented. Maybe support for using Lie groups to help solve ODEs.  See
[the ODE docs](http://docs.sympy.org/0.7.1/modules/solvers/ode.html) and the
[current source](https://github.com/sympy/sympy/blob/master/sympy/solvers/ode.py)
for information on what methods are currently implemented.  Also, there is
no support currently for solving systems of ODEs.  You also might want to
look at
[Manuel Bronstein's sumit](http://www-sop.inria.fr/cafe/Manuel.Bronstein/sumit/index.html).

  * Separation ansatz:
      * "A simple method to find out when an ordinary differential equation is separable" by José ́Ángel Cid

  * "Solving Differential Equations in Terms of Bessel Functions" by Ruben Debeerst.
      * Webpage: http://www.mathematik.uni-kassel.de/~debeerst/master/
      * Master Thesis: http://www.mathematik.uni-kassel.de/~debeerst/master/master.pdf
      * Corresponding ISSAC 08 paper: http://www.mathematik.uni-kassel.de/~debeerst/master/paper_issac2008.pdf

  * Lie groups and symmetry related:
      * An implementation of these methods was done for first order ODEs during gsoc13. But we can do the same tricks for second order ODEs too.
      * "Computer Algebra Solving of First Order ODEs Using Symmetry Methods" by
        E.S. Cheb-Terrab, L.G.S. Duarte and L.A.C.P. da Mota.
        There is a short (15 pages) and an updated (24 pages) version of this paper.
      * "Computer Algebra Solving of Second Order ODEs Using Symmetry Methods" by
        E.S. Cheb-Terrab, L.G.S. Duarte, L.A.C.P. da Mota
      * "Integrating factors for second order ODEs" by E.S. Cheb-Terrab and A.D. Roche
      * "Symmetries and First Order ODE Patterns" by E.S. Cheb-Terrab and A.D. Roche
      * "Abel ODEs: Equivalence and Integrable Classes" by E.S. Cheb-Terrab and A.D. Roche
        Note: Original version (12 pages): July 1999. Revised version (31 pages): January 2000
      * "First order ODEs, Symmetries and Linear Transformations" by E.S. Cheb-Terrab and T. Kolokolnikov
      * "Non-Liouvillian solutions for second order linear ODEs" by L. Chan, E.S. Cheb-Terrab
      * And probably some more by these authors ...


### Series expansions

This includes numerous smaller subprojects.

  * improve series expansions
    * [relevant issues](http://code.google.com/p/sympy/issues/list?q=label:Series)
  * formal power series
  * improve limits - make sure all basic limits work
    * limit of series
  * asymptotic series
  * Better support for Order term arithmetic (for example, expression of the
    order term of the series around a point that is not 0, like O((x - a)**3)).
  * All other problems, which are described in wiki page about [series](UD-series) and
    [current situation](UD-series-situation)

  * Some references:
    * "Formal Power Series" by Dominik Gruntz and Wolfram Koepf
    * "A New Algorithm Computing for Asymptotic Series" by Dominik Gruntz
    * "Computing limits of Sequences" by Manuel Kauers
    * "Symbolic Asymptotics: Functions of Two Variables, Implicit Functions"
      by Bruno Savly and John Shackell
    * "Symbolic Asymptotics: Multiseries of Inverse Functions" by Bruno Savly
      and John Shackell

### Cylindrical algebraic decomposition

* Implement the Cylindrical algebraic decomposition algorithm
* Use CAD to do quantifier elimination
* Provide an interface for solving systems of polynomial inequalities

* Some references:
  * Cylindrical Algebraic Decomposition
    [[http://mathworld.wolfram.com/CylindricalAlgebraicDecomposition.html]]
  * "Algorithms in Real Algebraic Geometry"
    [[http://perso.univ-rennes1.fr/marie-francoise.roy/bpr-ed2-posted1.html]]
    (useful background resource, but contains much more information)
  * "Cylindrical Algebraic Decomposition I: The Basic Algorithm" by Dennis
    S. Arnon, George E. Collins, Scot McCallum
  * "Computing Cylindrical Algebraic Decomposition via Triangular
    Decomposition" by Marc Moreno Maza, Changbo Chen, Bican Xia, Lu Yang
  * "Simple CAD Construction and its Applications" by Christopher W. Brown
  * "Improved Projection for Cylindrical Algebraic Decomposition" by Christopher W. Brown
  * "Symbolic Computation for Inequalities" by Manuel Kauers
    [[http://www.sfb013.uni-linz.ac.at/uploads/media/SymCompIneq.pdf]]
  * "How To Use Cylindrical Algebraic Decomposition" by Manuel Kauers


### Polynomials module

#### Efficient Groebner bases and their applications

* **Status**:  Groebner bases computation is one of the most important tools
    in computer algebra, which can be used for computing multivariate
    polynomial LCM and GCD, solving systems of polynomial equations, symbolic
    integration, simplification of rational expressions, etc. Currently there
    is an efficient version of Buchberger algorithm implemented and of the
    F5B algorithm, along with naive multivariate polynomial arithmetic
    in monomial form.
    There is also the FGLM algorithm converting reduced Groebner bases of
    zero-dimensional ideals from one ordering to another.
* **Idea**:  Improve efficiency of Groebner basis algorithm by using better
    selection strategy (e.g. sugar method) and implement Faugere F4
    algorithm and analyze which approach is better in what contexts.
    Implement the generic Groebner walk converting between Groebner basis
    of finite-dimensional ideals; there are efficient algorithms for it,
    by Tran (2000) and Fukuda et al. (2005).
    Apply Groebner bases in integration of rational and transcendental functions
    and simplification of rational expressions modulo a polynomial ideal
    (e.g. trigonometric functions).  **Note: There was a project last year
    relating to Groebner bases.  Please take a look a the source and discuss
    things with us to see what remains to be done.**  **Second Note: Some
    Groebner bases algorithms, in particular F4, require strong linear
    algebra.  Thus, if you want to do that, you may have to first improve our
    matrices (see the ideas relating to this above).**
* **Rating**: (very hard)

#### Multivariate polynomials and factorization

* **Status**:  Factorization of multivariate polynomials is an important tool
    in algebra systems, very useful by its own, also used in symbolic
    integration algorithms, simplification of expressions, partial fractions,
    etc. Currently multivariate factorization algorithm is based on
    Kronecker's method, which is impractical for real life problems. Undergo
    there is implementation of Wang's algorithm, the most widely used method
    for the task.
* **Idea**:  Start with implementing efficient multivariate polynomial
    arithmetic and GCD algorithm. You do this by improving existing code,
    which is based on recursive dense representation or implement new methods
    based on your research in the field. There are many interesting methods,
    like Yan's geobuckets or heap based algorithms (Monagan & Pearce). Having
    this, implement efficient GCD algorithm over integers, which is not a
    heuristic, e.g. Zippel's SPMOD, Musser's EZ-GCD, Wang's EEZ-GCD. Help with
    implementing Wang's EEZ factorization algorithm or implement your favorite
    method, e.g. Gao's partial differential equations approach. You can go
    further and extend all this to polynomials with coefficients in algebraic
    domains or implement efficient multivariate factorization over finite
    fields.  **Note: Some work on this may already be done.  Take a look at
    sympy/polys/factortools.py in the SymPy source code.**
* **Rating**: (quite hard)

#### Univariate polynomials over algebraic domains

* **Status**:  Currently SymPy features efficient univariate polynomial
    arithmetic, GCD and factorization over Galois fields and integers
    (rationals). This is, however, insufficient in solving real life problems,
    and has limited use for symbolic integration and simplification
    algorithms.
* **Idea**:  Choose a univariate polynomial representation in which elements
    of algebraic domains will be efficiently encoded. By algebraic domains we
    mean algebraic numbers and algebraic function fields. Having a good
    representation, implement efficient arithmetic and GCD algorithm. You
    should refer to work due to Monagan, Pearce, van Hoeij et. al. Having
    this, implement your favorite algorithm for factorization over discussed
    domains. This will require algorithms for computing minimal polynomials
    (this can be done by using LLL or Groebner bases). You can also go ahead
    and do all this in multivariate case.
* **Rating**: (quite hard)

### Concrete module: Implement Karr algorithm, a decision procedure for symbolic summation

* **Status**:  SymPy currently features Gosper algorithm and some heuristics
    for computing sums of expressions. Special preference is for summations of
    hypergeometric type. It would be very convenient to support more classes
    of expressions, like (generalized) harmonic numbers etc. There is already
    an complete algorithm rational expression summation.
* **Idea**:  Algorithm due to Karr is the most powerful tool in the field of
    symbolic summation, which you will implement in SymPy. There are strong
    similarities between this method and Risch algorithm for the integration
    problem. You will start with implementing the indefinite case and later
    can extend it to support definite summation (see work due to Schneider and
    Kauers). Possibly you will also need to work on solving difference
    equations.
* **Rating**: (very hard)

* Some references:
  * "A=B" by Marko Petkovsek, Herbert S. Wilf, Doron Zeilberger
  * "Symbolic Summation with Radical Expressions" by Manuel Kauers and Carsten
    Schneider
  * "An Implementation of Karr's Summation Algorithm in Mathematica" by
    Carsten Schneider
  * Manuel Kauers, webpage: [[http://www.risc.jku.at/home/mkauers]]
  * Carsten Schneider, webpage: [[http://www.risc.jku.at/people/cschneid]]
  * "Algorithmen für mehrfache Summen", by Torsten Sprenger


### Linear Algebra: Tensor core

* **Status**: SymPy has a number of disconnected projects related to
 Tensor/Linear algebra. These include Matrices, Sparse Matrices, Matrix
 Expressions, Indexed (for code generation), Geometric Algebra, Differential
 Geometry, Tensor Canonicalization, and various projects in Physics.

* **Idea**: Build a Tensor core that can serve as a base to connect these projects and others. This core should be able to seamlessly support a broad range of applications ranging from very abstract (vector spaces, geometry, multi-linear operators) to very numerical (explicit matrices, NumPy integration, code generation). This project should include both a general Tensor Expression class and a general refactoring of the existing code-base. See [[Linear-Algebra-Vision]]. This project requires experience both in abstract linear algebra and in good code organization.

### Step-by-step Expression Visualization

Many times, people ask how they can tell what some functions are doing.  For
example, they want to know step by step how something like `diff(x*sin(x**2),
x)` or `integrate(x*sin(x**2), x)` works.  For the former, the best you can do
is to follow the code; for the latter, the algorithm doesn't work at all like
you would do it by hand, so there's really no way.

The idea is to implement a way to do this.  It would be along the lines of
WolframAlpha, where if you do certain operations (including the above two),
there is a button "Show steps," which shows everything step by step.

Some questions:
* What would be a good interface for this?  For the most part, it would
probably mean reimplementing the basic "by hand" algorithms, so that you can
determine exactly what steps are used. Check out the "rewrite rules and
strategies" submodule in SymPy.

* What should the output look like, so that it is both readable and usable
(e.g., maybe some kind of annotated objects representing operations that you
can literally apply to an expression to do those things)?

* For those operations where what SymPy does is pretty close to what you'd do
by hand (e.g., differentiation), what is a good way to avoid code duplication
and make things extensible?


Note, not all of these questions are unanswered.  For instance,
`sympy.integrals.manualintegrate` already implements some of these
ideas. It's probably a good idea to discuss this with us (as always) if you
are interested, as we will probably have some ideas ourselves on how to
answer these questions.

#### A Strategy for step-by-step

The logic behind many SymPy operations is separated into several small methods.  For example objects like `sin` or `exp` have `_eval_derivative` methods that are called as SymPy evaluates the derivative of a complex expression like `sin(exp(x))`.  By capturing the inputs and outputs of all of these small methods we can collect a great quantity of information about the steps that SymPy takes.  We can see that `exp._eval_derivative` took in `exp(x)` and returned `exp(x)` and that `sin._eval_derivative` took in `sin(exp(x))` and returned `cos(exp(x))*exp(x)`.  These input-output pairs for each method are probably sufficient to illustrate how SymPy solves problems in many domains.

This approach of capturing the inputs of many internal functions is similar to logging systems traditionally used to analyze large codebases.  We should investigate how they work and if they cause any problems with normal operation.

Once this source of information is available we can then think about interesting ways to visualize and to interact with it.  A good solution will not irrevocably tie the data stream to a particular visualization technique.

This approach is straightforward intellectually but may require the student to interact with a lot of the codebase.  Approaches like `_eval_derivative` are ubiquitous throughout SymPy but often have small variations in different modules.

## Detailed subprojects in Physics

### Symbolic quantum mechanics (sympy.physics.quantum)

Please contact the SymPy list (or Brian E. Granger, Ondřej Čertík) for
questions about the physics related topics.

#### Abstract Dirac notation

* **Status**: In sympy.physics.quantum we have code for symbolic Dirac notation. There is a lot there, but much more could be done on this.
* **Idea**: Continue to improve this code by adding any number of
    features. The sky is the limit on this one. You could basically pick
    anything from quantum mechanics and implement it (a physical system,
    scattering theory, perturbation theory, etc.).  A student interested in
    working on this should minimally have already taken an upper division
    (undergrad) quantum course and have a solid understanding of quantum
    mechanics. You would need to dig into the code and figure out what the next steps are.

#### Implement All Known Analytical Solutions to Quantum Mechanical Systems

* **Status**: Currently, we have Hydrogen Schroedinger/Dirac energies and
    nonrelativistic wave functions implemented in
    [sympy.physics.hydrogen](https://github.com/sympy/sympy/blob/master/sympy/physics/hydrogen.py)
    and 1-dimensional infinite square well wave functions in
    [sympy.physics.quantum.piab](https://github.com/sympy/sympy/blob/master/sympy/physics/quantum/piab.py). **Before this can be done, we have to finish implementing basic position/momentum bases in SymPy (see [pull 573](https://github.com/sympy/sympy/pull/573)). There is still a ton of work left to do on that, so this project may be premature.**
* **Idea**: Implement all known analytical formulas for energies and
    wave functions for all QM systems that can be solved analytically (there
    are not too many, see http://en.wikipedia.org/wiki/List_of_quantum-mechanical_systems_with_analytical_solutions). In particular, 1d: finite/infinite well, oscillator,
    Coulombic field, 1d radial equation: Coulombic field, oscillator,
    finite/infinite well, Dirac wave functions, 2d: Coulombic field,
    oscillator, finite/infinite well, 3D: finite/infinite well. Then there are
    systems in cylindrical coordinates and other things. There will be a
    submodule in the quantum, that would contain as much analytical knowledge
    about these systems as possible, and one would retrieve the knowledge
    using physical parameters (e.g. (Z, n) for Hydrogen states, (n1, n2, n3)
    for 3D oscillator, and so on). When this is done, more things can be added
    --- there are many systems, whose energies can be obtained with a simple
    numerical procedure (like zeros of Bessel functions), and systems whose
    solution is given as a series.  The devil is in little details, and there
    is high value in having all these systems implemented and tested to ensure
    correctness. Usage of this is for testing numerical codes, that they
    can reproduce analytical results, as well as when playing with and
    learning about QM. This project should be quite easy in terms of
    Python/SymPy programming, but it requires knowledge about QM.

#### Position and momentum basis functions

* **Status**:  The position and momentum basis functions in quantum mechanics
    are somewhat pathological because the basis functions are not square
    integrable. In spite of this, these representations are immensely useful
    and are introduced to students early on.  We would like to be able to
    handle position and momentum wave functions on arbitrary domains in 1D, 2D
    and 3D. **NOTE: This was the topic of a GSoC project in 2012,
    and this description has not been updated to reflect the work that
    has been done and what could still be implemented.** There is a pull open
    from this work [here](https://github.com/sympy/sympy/pull/573). Anyone
    interested in this topic should consult the list.
* **Idea**:  Implement full machinery for position and momentum wave functions,
    including modified Hilbert spaces, various coordinate systems, Dirac delta
    functions, basis transformations in 1D, 2D and 3D. This should use the
    base layer of quantum states and operators in sympy.physics.quantum.  The
    test suite/code should include classic examples from quantum mechanics,
    such as particle in box, H atom, simple harmonic oscillator, scattering,
    etc. There are some real subtle issues in this work in how operators,
    states and general quantum expressions are represented in the position and
    momentum bases.
* **Rating**: (moderate-hard)

#### Symbolic quantum computing

* **Status**:  Quantum computing refers to the usage of quantum states,
operators, time-evolution and measurement to perform non-trivial
computations. SymPy already has a quite sophisticated symbolic quantum
computing library and work continues on this.
* **Idea**:  Quantum error correction, Solovay-Kitaev
algorithm, gate+circuit simplification using genetic algorithms, etc.
* **Rating**: (hard)

#### Second quantization capabilities

* **Status**: SymPy currently a solid module for second quantization
    implemented, but it needs to be updated to take advantage of the new stuff
    in sympy.physics.quantum. Interesting, but challenging work.
* **Idea**:  Work on sympy.physics.secondquant in the following areas:
    1. Refactor to use the new assumptions system.
    2. Refactor to use the stuff in sympy.physics.quantum.
    3. Implement Wick's theorem for Bosons, including the macroscopic
       population of the ground states.
    4. Density matrices.
    5. Time evolution.
    6. Various approximations, such as perturbation theory, Hartree-Fock,
       time-dependent Hartree-Fock, Hartree-Fock-Bogoliubov, etc.
    7. Implement new functions for simplifying products of second quantized
       operators in different ways (such as moving an annihilation operator
       R).
* **Rating**: (hard)

### Symbolic vector calculus and classical mechanics in SymPy (sympy.physics.vector and sympy.physics.mechanics)

* See https://github.com/pydy/pydy/wiki/GSoC-2015-Ideas

## Projects for vector package

The original roadmap for [the vector package](https://github.com/sympy/sympy/tree/master/sympy/vector) dealt with the ideas expressed in the following projects. Any other ideas are welcome.
A pull request for the documentation is [here](https://github.com/sympy/sympy/pull/7860).

### Implementation of multiple types of coordinate systems

* **Status**: sympy.vector currently deals only with Cartesian(rectangular) coordinate systems. The basic architecture for coordinate systems and vectors, as well as their interaction is ready.
* **Idea**: The idea is to have a proper class system for coordinate systems, with a class like `CoordinateSystem` abstracting the common architectural elements for all types of systems. This class would have subclasses like `CartesianCoordinateSystem`, `SphericalCoordinateSystem`, etc. that implement the relevant functionality. We would probably need to modify the `Vector` class structure too, to allow for different vector behaviours in different systems - for example, vectors in spherical systems add differently than vectors in rectangular coordinate systems.
* **Difficulty**: medium

### Implementation of vector integration

* **Status**: sympy.vector supports vector derivatives, but not proper functionality for vector integration - over lines, surfaces etc..
* **Idea**: The idea is to build proper helper functions and class structure to support vector integration over lines, surfaces and volumes. For help, Prasoon's [PR](https://github.com/sympy/sympy/pull/2208) with his work in GSoC 2013 can be taken as a starting point.
* **Difficulty**: medium

## Detailed subprojects in CSymPy

[CSymPy](https://github.com/certik/csympy) is a standalone fast C++ symbolic manipulation library. Optional thin Python wrappers allow easy usage from Python and integration with SymPy.

Please contact the SymPy list (or Ondřej Čertík) for
questions about the CSymPy related topics. You can also ask on CSymPy's gitter: https://gitter.im/sympy/csympy and propose something that is not listed below.

### Port SymPy's new Assumptions to C++

* **Status**: Assumptions are not currently implemented in CSymPy.
* **Idea**: Assumptions are used in Computer Algebra Systems for queries and automatic simplification. SymPy has a [new assumptions](http://docs.sympy.org/dev/modules/assumptions/index.html) module. Port this module to C++ so that assumptions can be used within CSymPy. Fast SAT solvers like [pycosat](https://github.com/ContinuumIO/pycosat) can be used in the implementation.
* **Difficulty**: medium

### Implement Fast Series Expansion

* **Status**: There are currently a few functions implemented in [functions.h](https://github.com/certik/csympy/blob/master/src/functions.h). They can differentiate themselves, but series expansion is not implemented yet.
* **Idea**: Implement fast series expansion by following the similar design in SymPy. Add the `.taylor_term()` method that efficiently returns the n-th Taylor term. Then implement general machinery that uses this to return a series expansion
* **Difficulty**: medium

### Port SymPy's fast sparse polynomials to C++

* **Status**: Very preliminary implementation is in `rings.cpp` and `monomials.cpp`.
* **Idea**: The polynomials should support more operations and allow seamless conversion to and from CSymPy's symbolic expression. The sparse polys in SymPy use a tuple of ints `(5, 2, 3)` to represent the monomial `x^5 y^2 z^3`. Then you have a dictionary (hashtable) where you simply store the coefficients, so `3x^5y^2z^3+x` becomes `{(5, 2, 3): 3, (1, 0, 0):1}` and that's your sparse representation.
The exponents however can be packed into one integer, e.g. if each requires 8 bits, then you need total of 24 bits and you can use up to 64bit integers (or perhaps 128bit using the __int128 type in C++). So you pack them into one integer, that's called Kronecker substitution, and then you use just that integer as the key in the hashtable, so everything becomes much faster. Also, multiplying two monomials then just becomes adding the ints of exponents, etc. Of course, if the exponents are too large to be packed, then the code needs to notice this and raise an exception, the user then needs to use the tuple representation (std::vector<int> in C++, though std::array is faster, as std::vector is allocating on heap, so Piranha implements its own fast small vector that uses static allocation).
The integer arithmetic, the coefficients of the monomials, must be very fast. SymPy uses either Python ints (slow) or gmpy (fast). In C++, we also use GMP, but even faster is to use machine integers for small integers and then switch to GMP for large integers. This trick can and should be used for all CSymPy integers, it should speed things up considerably.
The hashtable should be tailored for this purpose, so [Piranha](https://github.com/bluescarni/piranha/) stores the values directly in the array (if there is only one value in a bucket), only if there is more values in a bucket, it uses a linked list I think. Also, there is a trick to use a 1:1 hash function, Piranha uses that.
finally, we also need polynomials with rational coefficients and probably rational exponents as well, etc.
* **Difficulty**: medium


### Improve Python wrappers

* **Status**: Currently the basic Python wrappers provide seamless integration with SymPy.
* **Idea**: Make `CSymPy` work with `Sage`. This requires implementing the `_sage_` methods as well as converting from `Sage`. This would be tested in a similar way as in SymPy, see e.g. the [sympy/external/tests/test_sage.py](https://github.com/sympy/sympy/blob/master/sympy/external/tests/test_sage.py) and [.travis.yml](https://github.com/sympy/sympy/blob/master/.travis.yml#L101) as well as [bin/test_travis.sh](https://github.com/sympy/sympy/blob/master/bin/test_travis.sh#L16) for this. This project is not particularly difficult, but one needs to carefully check all corner cases and make sure that `CSymPy` works out of the box in both SymPy and Sage (for example making sure that we can use the plotting facilities in SymPy with CSymPy). As part of it would be to create an SPKG package for Sage and get it into the optional packages section of Sage. Part of the project would also be improving the documentation of the Python wrappers in form of docstrings. The general idea is that after this project is implemented, we can use SymPy for all the functionality (like plots, conversions etc.), and CSymPy only implements very fast symbolic manipulation.
* **Difficulty**: easy/medium

## Detailed subprojects in Computer Science, Infrastructure, GUIs and Graphics

### Code Generation

Code generation needs to support more backends, e.g. numba, python, javascript, etc. We also need better support for vectorizing (ufuncifying) sequences of expressions that use a common cse() call. 

### SymPy subprojects related to GUIs and user interaction

#### SymPy Live and SymPy Gamma (on Google App Engine)

WolframAlpha recently released a big update.  You can now pay them and get a
bunch of features.  They also do things like save your search history.

Right now, our competition to WolframAlpha is SymPy Live
(http://live.sympy.org/), but this works a little differently.  SymPy Live is
an exact duplicate of the console version of SymPy, running on the App Engine,
but WolframAlpha tries to be smart about what the user wants.  A while back,
Ondřej whipped up a thing called SymPy Gamma (http://sympygamma.com/), which
is a little closer to WolframAlpha.

The GSoC project would be to improve one or both of these projects.  SymPy Gamma
could be improved a lot, by making it more intelligent about what output it
produces for different inputs, making it parse expressions that aren't given
in exact SymPy syntax (e.g. natural language queries like Wolfram|Alpha allows),
making it produce plots, perhaps replacing the notebook with an IPython notebook.
SymPy Live could use a lot of the same features.  Furthermore, SymPy Live has bugs
with pickling, which could be fixed or eliminated by converting Live to use dill
instead of pickle and/or by improving the pickling support in SymPy itself.

Many of these things should be implemented in SymPy and simply called from the
web applications, for example, improved parsing for SymPy Gamma.
Look at Mathics (http://www.mathics.org/) for inspiration.

### Parsing

* **Status**:  Currently SymPy has the ability to generate Python, C, and Fortran code from SymPy expressions.

* **Idea**:  It would be very interesting to go the other way. Can we parse
    Python, C, and Fortran code and produce SymPy expressions? This would
    allow SymPy to easily read in, alter, and write out computational
    code. This project would enable many other projects in the future. As a
    first step take a look at the current
    [code generation and autowrap functionality](http://docs.sympy.org/0.7.1/modules/utilities/). Ideally
    this project would create a general framework for parsers and then use
    this system to implement parsers for a few of the languages listed above.
    See the other parsing ideas on this page, as well as [[Parsing]].


### Improve the plotting module

A very approximate difficulty guesstimate is given.

  * medium-hard: Manipulate parameters in graphs (needs some kind of GUI
    (matplotlib provides widgets)) (IPython's notebook?)
  * medium: Animations (in matplotlib and IPython's notebook)
  * easy-medium: Write/fix/extend/port backends: matplotlib, Google Chart API
    link, pyglet, asciart, d3.js
  * easy: The old pyglet module does not work with the new module. Simplify
    the old module and write a backend for it.
  * medium-hard: Write an openGL backend for matplotlib (that should be
    discussed with the matplotlib team) (you may start with our pyglet module)
  * hard: Implement an intelligent routine that decides on the sampling rate
    so that sharp edges are better plotted (it is done for 2D however it would
    be nice to have it for 3D). An "asymptote detector" would be
    nice.
  * easy /medium: Implement a intelligent routine that automatically determines
    the regions of interest for plotting.
  * easy: Plot:
      * objects from the geometry module
      * 2D and 3D linear operators (the effect of a matrix on a plane/3D
        space)
      * the effect of complex maps
      * vector fields
      * contours
  * easy / medium: Implement a backend for Mayavi for 3D plotting.
  * Fix related things/bugs in SymPy
  * Implement high level features, so that it works akin to Mathematica
    (http://reference.wolfram.com/mathematica/ref/Plot.html)
  * Improve textplot so that it can support all kinds of plots using
    ASCII/Unicode characters right in the terminal (with no dependencies).

### Benchmarks

Speed is important for SymPy. One issue is that it's difficult to tell what is
too slow, and, more importantly, if a given change makes things faster or
slower.

SymPy needs more benchmarks. It also needs an automated system to run them
(similar to PyPy, you should look at what they are using). That way, when
someone adds some code that slows things down in an unexpected
way, we will know about it.

## Other Related Projets

Their is 2 ideas in the
[Theano GSoC
ideas list](https://github.com/nouiz/Theano/wiki/Gsoc2015) that are of interest to SymPy user's. 1) Lower Theano
overhead (significant for scalars) and 2) generate dynamic
libraries. They are interesting to SymPy user's via the SymPy -> Theano bridge that allow to compile a SymPy graph for faster execution. If you are interested in them, contact them.

## Ideas

* Linear algebra
  * Rewrite the Matrices module to be more like the polys module, i.e., allow
    Matrix to use the polys ground types, and separate the internal data
    (sparse vs. dense) from the Matrix interface.  The goal is to make the
    matrices in SymPy much faster and more modular than they are now.
  * Refactor the matrices module to have a cleaner orthogonal organization
* improve the integration algorithm
  * integration of functions on domains of maximum extent, etc.
  * Interesting idea: "SYMBOLIC COMPUTATION OF INTEGRALS BY RECURRENCE" by
    MICHAEL P. BARNETT
* definite integration & integration on complex plane using residues.  Note
  that we already have a strong algorithm that uses Meijer G-Functions
  implemented.  So we need to first determine if such an algorithm would be
  worthwhile, or if it would be better to extend the current algorithm.  Note
  that there are many integrals that are easy to compute using residues that
  cannot be computed by the current engine.  Other possibilities:  the ability
  to closed path integrals in the complex plane, which is not possible with
  the Meijer G algorithm.
* Groebner bases and their applications in geometry, simplification and
  integration
  * improve Buchberger's algorithm and implement Faugere F4 (compare their
    speed) _Note: This has already been implemented by a previous GSoC
    student.  Please check with us to see the current state of Groebner bases
    in SymPy_
* improve polynomial algorithms (gcd, factorization) by allowing coefficients
  in algebraic extensions of the ground domain
* implement efficient multivariate polynomials (arithmetic, gcd,
  factorization)
  * Implement a sparse representation for polynomials (see the dummy files in
    sympy/polys/ starting with "sparse" in the SymPy source code for a start
    to this project).
  * Figure out which representations to use where (sparse vs. dense).
  * implement efficient arithmetic (e.g. using geobuckets (Yan) or heaps
    (Monagan & Pearce))
* improve SymPy's pattern matching abilities (efficiency and generality)
  * implement similarity measure between expression trees
  * expression complexity measures (e.g. Kolmogorov's complexity)
  * implement expressions signatures and heuristic equivalence testing
  * implement semantic matching (e.g. expression: cos(x), pattern: sin(a*x) +
    b)
    * e.g by using power series for this purpose (improve series speed)
  * Expand the capabilities of Wild() and match() to support regular
    expression-like quantifiers.
* improve simplification and term rewriting algorithms
  * add (improve) verbatim and semi-verbatim modes (more control on expression
    rewriting)
  * implement more expression rewrite functions (to an exact form that user
    specifies).  This may involve rewriting the rewrite framework to be more
    expressive.  For example, should cos(x).rewrite(sin) return sqrt(1 -
    sin(x)**2) or sin(pi/2 - x)?
  * maybe put transformation rules in an external database (e.g. prolog), what
    about speed?
  * improve context (e.g. input) depended simplification steps in different
    algorithms
      * e.g. the integrator needs different sets of rules to return "better"
        output for different input
      * but there are more: recurrences, summations, solvers, polynomials with
        arbitrary coefficients
  * what about information carried by expressions?
      * what is simpler: chebyshevt(1, x) or x ?
      * what is simpler: chebyshevt(1000, x) or (...) ?
  * improve trigonometric simplification. See for example the paper by fu et. al.
* implement symbolic (formal) logic and set theory
  * implement predicate (e.g. first-order), modal, temporal, description
    logic
  * implement multivalued logic; fuzzy and uncertain logic and variables
  * implement rewriting, minimization, normalization (e.g. Skolem) of
    expressions
  * implement set theory, cardinal numbers, relations etc.
  * This task is heavily tied to the assumptions system.
* implement symbolic global optimization (value, argument) with/without
  constraints, use assumptions
* continue work on objects with indices (tensors)
  * include the index simplification algorithms used in
    [xAct](http://www.xact.es/) and [cadabra](http://cadabra.phi-sci.com/).
* generalized functions -- Dirac delta, P(1/x), etc... Convolution, Fourier
  and Laplace transforms
  * Fourier and Laplace transforms are implemented but we can not do many
    cases involving distributions _Is this enough alone for a project though? -Aaron_
* vector calculus, differential fields, maybe Lie algebras & groups
* parametric integrals asymptotic expansion (integral series)
* Integral equations.  See for example the work started at
  http://code.google.com/p/sympy/issues/detail?id=2344.  This could be part of
  a project on ODEs, for example.
* partial differential equations. Currently, SymPy can't solve any PDEs,
  though a few tools related to separation of variables are implemented. The
  PDE module should be structured similarly to the ODE module (see the source
  code of sympy/solvers/ode.py).
* improve SymPy's Common Subexpression Elimination (CSE) abilities.
  * Poly factorization http://cseweb.ucsd.edu/~kastner/papers/tcad06-poly_factorization_cse.pdf
* Singular analysis and test continuous.
  * find singularities of the function and classify them.
  * test the function whether it is continuous at some point or not. And in the interval.
    Note: Please discuss this idea with us if you are interested, as as it currently presented,
    it is somewhat vague.
* Control theory. systems for Maple and Mathematica might provide insight
  here. http://www.mcs.anl.gov/~wozniak/papers/wozniak_mmath.pdf might be useful.
* Diophantine Equations: SymPy does have substantial support for solving these, never the less
  there is more work possible to improve the solver.

## Non-Ideas

Every year, people ask about implementing various things that we have already
decided do not belong in SymPy.  Among these are:

- Graph theory. The [NetworkX](http://networkx.github.com/) package already
  does a great job of graph theory in Python. If you are interested in working
  in graph theory, you should contact them.
- Numerical solvers. SymPy is a symbolic library, so the code should focus on
  solving things symbolically. There are already many libraries for solving
  problems numerically ([NumPy](http://www.numpy.org/),
  [SciPy](http://www.scipy.org/), ...).

## Potential Mentors

If you are willing to mentor, please add yourself here.  In parentheses, put
your link-id from http://www.google-melange.com.

* Aaron Meurer (asmeurer)
* Mateusz Paprocki (mattpap)
* Jim Crist (jcrist) - code generation, physics.vector, physics.mechanics, PyDy
* Ondřej Čertík (certik)
* Tim Lahey (tjlahey)
* Thilina Rathnayake (thilinarmtb) - CSymPy, Diophantine equations
* Harsh Gupta (hargup) - solvers
* David Li (lidavidm96) - SymPy Live, SymPy Gamma, manualintegrate & related work
* Sean Vig (flacjacket)
* Jason Moore (moorepants) - physics.vector, physics.mechanics, PyDy
* Gilbert Gede (gilbertgede) - physics.vector, physics.mechanics, PyDy
* Sachin Joglekar (srjoglekar246) - sympy.vector, physics.vector

<!--  LocalWords:  GSoC GUIs iOS Andriod sqrt sumit José Debeerst Cheb Terrab
 -->
<!--  LocalWords:  Duarte da Mota Kolokolnikov Onur Kiymaz Seref Karr Dominik
 -->
<!--  LocalWords:  Mirasyedioglu Gruntz Koepf Kauers Savly Shackell Arnon Xia
 -->
<!--  LocalWords:  McCallum Maza Changbo Bican GCD Buchberger FGLM Faugere et
 -->
<!--  LocalWords:  Fukuda al Yan's geobuckets Monagan Pearce Zippel's SPMOD
 -->
<!--  LocalWords:  Musser's EZ EEZ Gao's Hoeij LLL Gosper Marko Petkovsek für
 -->
<!--  LocalWords:  Wilf Doron Zeilberger Carsten Karr's Algorithmen mehrfache
 -->
<!--  LocalWords:  Summen Torsten Sprenger Granger Schroedinger Coulombic cse
 -->
<!--  LocalWords:  Solovay Kitaev Bosons Hartree Fock Bogoliubov KanesMethod
 -->
<!--  LocalWords:  LagrangesMethod pyglet PyOpenGL vtk mayavi mprint mlatex
 -->
<!--  LocalWords:  NDSovle InterpolatingFunction Mathics autowrap matplotlib
 -->
<!--  LocalWords:  asciart js openGL textplot Buchberger's gcd Yan prolog fu
 -->
<!--  LocalWords:  Kolmogorov's chebyshevt Skolem xAct cadabra asmeurer Vig
 -->
<!--  LocalWords:  Krastanov certik seanv wdjoyner Mateusz Paprocki mattpap
 -->
<!--  LocalWords:  Lukas hazelnusse moorepants Gede gilbertgede
 -->