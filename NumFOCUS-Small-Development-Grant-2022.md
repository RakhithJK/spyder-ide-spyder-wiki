# Improving the Spyder IDE installation and usage experience

## **Summary**

Improve the installation experience for the [Spyder IDE](https://github.com/spyder-ide/spyder#readme) Windows users, by enabling the current standalone installers available to be auto-updatable and providing a way to install custom packages that are not bundled with the installers in a simpler way.

## **Description**

The current standalone Spyder installers available for Windows and MacOS provide an easy way to install Spyder with a base subset of the PyData stack (Cython, Numpy, Matplotlib, Pandas, Scipy and Sympy packages). These installers were developed during most of 2020 as a response to the serious difficulties we observed our users had when updating from Spyder 3 to 4, and have been provided since our 4.2.0 version, released in November of that year. Our Windows installer, in particular, has been very well received by our community because for the last bug fix releases of each minor version in the Spyder 5 cycle (i.e. 5.0.5, 5.1.5, and 5.2.2), it has had, on average, more than 80.000 monthly downloads [1]. That is a little bit more than the amount of downloads registered on PyPI (more than 70.000 [2]) and less than with conda’s defaults and conda-forge channels (more than 97.000 [3]). However, those numbers include all operating systems, so we can confidently say that our Windows installer has become the most popular installation method in a bit more than a year. This goes very well with our medium-term goal for this project, which is to encourage more and more users to switch to it since it is self-contained and much harder to break than an installation with package managers such as pip or conda.

Nevertheless, due to the way the installer is designed, it doesn’t support a simple and straightforward mechanism to update it. Instead, users need to first uninstall the previous version because not doing it could end up in errors when trying to install a new one. Furthermore, the way the Windows installer handles custom packages is prone to error and a fragile process, because users need to create an external Python environment and install the packages they want in it, which also needs to have the specific version of Spyder-kernels supported by the Spyder version they installed. For more information regarding this process, please go to [https://docs.spyder-ide.org/current/faq.html#using-packages-installer](https://docs.spyder-ide.org/current/faq.html#using-packages-installer). There you’ll see the video we created to help users with this, which already has around 28.000 views and 1000 new views per week. That clearly shows that there is a strong need in our community to understand how to do that for their own work. Unfortunately, the process involves a complex series of commands in the terminal, so it is quite possible that many users do not manage to successfully complete it.

With all this in mind, it is clear that improving the way Spyder’s standalone installer is updated and manages custom packages could greatly impact users’ experience and help decrease the entry and steep learning curve for people just starting their journey to use the PyData stack and the Spyder IDE. This will also make those tasks easier for already Spyder users as well. Moreover, by implementing these improvements, we hope to decrease issues related to installation problems and then have more time to focus on creating a more stable and robust IDE, and developing new and more interesting features. 

With this proposal we aim to fund one developer that will be supervised and working with one of our core developers (Daniel Allthviz-Moré), for 6 months full-time in order to give our Windows installer a much needed push forward.

Notes:

[1] Spyder installers downloads stats from Github releases: [https://tooomm.github.io/github-release-stats/?username=spyder-ide&repository=spyder](https://tooomm.github.io/github-release-stats/?username=spyder-ide&repository=spyder) 

[2] Spyder download stats from PyPI: [https://pepy.tech/project/spyder?versions=5.2.2&versions=5.1.5&versions=5.0.5](https://pepy.tech/project/spyder?versions=5.2.2&versions=5.1.5&versions=5.0.5&versions=4.2.5) 

[3] Spyder download stats with conda: [https://gist.github.com/dalthviz/a664ff9b76ed7f1aa13cfa60f7be85b6](https://gist.github.com/dalthviz/a664ff9b76ed7f1aa13cfa60f7be85b6)

## **Benefit to Project/Community**

The implementation of this project will have a positive impact because the Spyder community will gain access to the following features:

1. A much easier way for users to keep Spyder up to date on Windows without the fear that doing it will cause major issues or breakage. By providing a totally automatic and hassle-free update process to our installer, users won’t have to interrupt their work and start a days long search around the web for a solution or help. Unfortunately, that is what usually happens for newbies at the moment with Anaconda or pip.
2. A simple, graphical way to create an external, custom Python environment, install and manage any package requested by users and the right version of Spyder-kernels on it, and connect it automatically to the Spyder’s Windows installer. This will reduce the need for advanced knowledge about environments or extra installations done manually (e.g. Anaconda or Miniconda to be able to connect to the base environment or create a new one with conda afterwards).

A major benefit to the Spyder project itself will be that a new developer could work on it full-time for 6 months. This funding would give us the opportunity to train them and would give the new developer an opportunity to build up the necessary experience to start a career in open source and work with the project in the future.

## **References**

* Spyder IDE on Github: \
[https://github.com/spyder-ide/spyder](https://github.com/spyder-ide/spyder)
* Current documentation regarding usage of custom packages with standalone Spyder installations: \
[https://docs.spyder-ide.org/current/faq.html#using-packages-installer](https://docs.spyder-ide.org/current/faq.html#using-packages-installer)
* Spyder installers downloads stats from Github releases: [https://tooomm.github.io/github-release-stats/?username=spyder-ide&repository=spyder](https://tooomm.github.io/github-release-stats/?username=spyder-ide&repository=spyder) 
* Spyder downloads stats from PyPI: \
[https://pepy.tech/project/spyder?versions=5.2.2&versions=5.1.5&versions=5.0.5](https://pepy.tech/project/spyder?versions=5.2.2&versions=5.1.5&versions=5.0.5&versions=4.2.5) 
* Spyder download stats with conda: [https://gist.github.com/dalthviz/a664ff9b76ed7f1aa13cfa60f7be85b6](https://gist.github.com/dalthviz/a664ff9b76ed7f1aa13cfa60f7be85b6)
* Recent related issue: [https://github.com/spyder-ide/spyder/issues/17424](https://github.com/spyder-ide/spyder/issues/17424) 

## **Timeline of Deliverables**

* Month 1: Technical and social onboarding on the Spyder development workflow, Anaconda, and PyQt. Start to contribute to the maintenance of the Spyder 5 components related to installers and custom interpreter preference and how those things are currently working.
* Month 2: Update the scripts to build Windows installers in order to provide a patch update mechanism for them.
* Month 3: Help prepare a new Spyder 5 release, ensure all infrastructure for the installers to be built supporting patch updates, and start the creation of a Spyder plugin to manage custom packages through the creation of environments and the interaction with the preferences system used in Spyder.
* Month 4: Continue the implementation of the custom packages management plugin and do an initial implementation of the user interface.
* Month 5: Finish the implementation of this plugin, add automatic tests for it and do an internal release to ask for beta testers interested in helping us to improve this functionality.
* Month 6: Do a bug fix release if needed and include the new plugin by default with the Windows installers.

## **Project proposal Team**

* Spyder core developer and main reviewer: Daniel Althviz (@dalthviz)
* Selected applicant to work on the project: Juan Sebastian Bautista (@jsbautista)
* Spyder volunteer contributors interested in the project
