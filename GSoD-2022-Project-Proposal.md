# Update user and developer documentation for Spyder 5

## About Spyder IDE

Spyder is an integrated development environment designed from the ground up for scientists, engineers and data analysts. It combines the best features of a full-fledged IDE, an interactive analysis tool, and a visualization suite. This allows researchers to transition from exploring their data to building reproducible, reusable algorithms, models, and complete scientific toolkits.  Characterized as the Python world’s counterpart to tools like Rstudio and MATLAB, Spyder is unique in being developed both by and for the global scientific community. In addition, it is written in Python, which is also its target development language, allowing easy extension development for specific research needs.

Spyder includes an advanced editor, debugger, profiler, analyzer, and other development tools. It combines this with key scientific functionality, including interactive IPython consoles, on-demand help, plot viewing and manipulation, import, browsing, editing and export of common scientific data types and more. Furthermore, it provides full and seamless integration with the scientific Python stack, including NumPy, SciPy, Pandas, Matplotlib, IPython, SymPy and Cython. In addition, these native capabilities can be further extended by numerous first-party plugins for unit testing, Jupyter notebooks support, terminal integration, profiling and more, as well as third party extensions ranging from new panes to complete overhauls for specific research needs. 

Since its inception in 2009, Spyder has grown from a simple IDE created by a single individual to an open-source ecosystem developed and used by hundreds of thousands of scientists all around the world to solve critical problems currently faced by the global community. We look forward to making Spyder more accessible and useful to users of all disciplines, regions and skill levels, and further its positive impact on the world at large.


## About the project

### Our project's problem

Spyder 5 introduced significant changes, including a new API that allows the interface to be extensible, along with UX and accessibility improvements reflected in the look and feel of the whole application. While most of the documentation is up to date, there are still some remaining pieces that need further work, including the most important piece of Spyder, the Editor pane. Also, the new API is lacking developer-focused online documentation, making it really challenging for current and future contributors to understand how to use and extend the API and how to integrate this into their existing projects.

Right now, we need to update both the user and developer documentation to support and provide the Spyder community with a reliable source for troubleshooting and to showcase all of the current IDE’s functionalities. In the end, ensuring this information is available to the whole community will not only benefit our end-users but also better support existing and new contributors.

### Our project's scope

This project includes:

- Update Spyder 5 documentation for the Editor pane by reviewing the existing documentation and adding missing content for the new features and up-to-date screenshots and gifs.
- Update Spyder developer online documentation adding the new public API functionality and detailed technical guides covering what is needed to create a new basic plugin and how to update existing ones. 

Work that is out of the scope for this project includes:

- How-to guides and FAQs
- Tutorials and workshops to present in conferences
- Live streams and social media engagement

We have two core developers that will be supporting the project, one of whom has vast experience in technical writing and is the main maintainer of Spyder’s documentation, and the other a core developer who contributed to and understands the complete new API surface. We haven’t yet identified specific technical writers for this project but would do so following acceptance by this program. We estimate to have all this work done in six months working with one technical writer full time.

### Measuring our project's success

Users on Stack Overflow are creating an average of 3 questions per month asking about using and configuring Spyder’s Editor. While users vary in their expertise, level and knowledge of the application, it seems there’s a general lack of awareness about the features of the editor, which results in relatively few conversations and bug reports. If we were able to update the editor’s multiple functionalities in the documentation, it is possible that the number of issues regarding additional configurations of the editor will increase. 

Also, we have at least three external plugins that haven’t been updated because of the lack of documentation on migrating to the new API to support the maintainers of such plugins. This results in high levels of frustration given the breaking changes that were made during 2021.

To measure the success of this documentation project, we will track three metrics. The first is the number of the editor features and configuration options documented; the second is the number of pages added to the online developer documentation; and the third is the amount of pull requests made regarding the new API in external Spyder IDE plugins. The last one will be to count the number of external plugins that were successfully migrated to the new API and work with the latest release of Spyder in a span of 6 months. 

We would consider the project as successful if after finalizing the new documentation:
- At least **8** major editor features/configuration options are documented; right now we only have **3** basic features described in the docs.
- Complete at least **3** additional pages of the online developer documentation.
- At least **2** external plugins are migrated in the six months following project completion.

### Timeline

The project overall will take approximately six months to complete. Once we have the technical writer in the team, we’ll spend the time as follows,

| Month | Action items |
| --- | --- |
| Month 1 | Orientation - setup of development environment and understanding of the current workflow for opening, reviewing and deploying the documentation |
| Month 2 & 3 | Update and publish the editor pane documentation |
| Month 4 & 5 | Update and publish new developer documentation |
| Month 6 | Project completion |

## Project budget

| Budget item | Amount | Running total |
| --- | --- | --- |
| Technical writer that will update, test and publish new documentation for users and developers | $10000 | $10000 |

## Additional information

### The state of Spyder 5 documentation

Spyder IDE's first public documentation was for the release of Spyder 3, and is still available on our official documentation site. Since then, we’ve worked with a lot of volunteer contributors and a couple of full time paid developers and technical writers on building the documentation site we currently have. 

The pillars of our documentation include a quickstart, FAQ, troubleshooting, workshops, in-depth descriptions of the majority of the panes and even some introductory videos to help new users get familiarized with Spyder. Our current documentation maintainer does a lot of the technical writing, reviews work and supervises the deployments. Thanks to our team’s work, we now have clear, concise and well-written documentation.

### How Spyder documentation is built

The docs are built using Sphinx and deployed with Github Actions to the docs.spyder-ide.org domain. The master branch contains the in-development docs for Spyder 5, while the 4.x branch is still maintained with Spyder 4 docs. We also have the frozen 3.x branch that retains the docs for the legacy Spyder 3.

### Current documentation

- Latest version: https://docs.spyder-ide.org/
- Spyder IDE website: https://www.spyder-ide.org/
- Github repository: https://github.com/spyder-ide/spyder-docs
