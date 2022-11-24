# Spyder IDE - Google Season of Docs 2022: Case Study

Spyder is an integrated development environment (IDE) designed from the ground up for scientists, researchers, engineers and data analysts. It combines the best features of a full-fledged IDE, an interactive analysis tool, and a visualization suite. This allows users to transition from exploring their data to building reproducible, reusable algorithms, models, and complete scientific toolkits. Characterized as the Python world’s counterpart to tools like Rstudio and MATLAB, Spyder is uniquely developed by and for the global scientific community. In addition, it is written in Python, which is also its target development language, allowing easy extension development for specific users’ needs.

Spyder is formed by a versatile set of tools and features, such as an advanced editor, debugger, profiler, analyzer, among others. It combines this with key scientific functionalities like interactive IPython consoles, on-demand help, plot viewing and manipulation, import, browsing, editing and export of common scientific data types and more. Furthermore, it provides a seamless integration with the scientific Python stack, including popular packages such as NumPy, SciPy, Pandas, Matplotlib, IPython, SymPy and Cython. 

Though its versatility does not end there, these native capabilities can be further extended by numerous first-party plugins for unit testing, Jupyter notebooks support, terminal integration, profiling and more, as well as third-party extensions ranging from new panes to complete overhauls for specific research needs.

Since its inception in 2009, Spyder has grown from a simple IDE created by a single individual to an open-source ecosystem used by hundreds of thousands of scientists worldwide to solve critical problems currently faced by the global community. We look forward to making Spyder more accessible and useful to users of all disciplines, backgrounds, and skill levels and further its positive impact on the world at large.

## Problem statement

The project focused on updating the documentation for Spyder 5 released in April 2021. Normally, we update our documentation after enough features have been added. As an open-source project, we face many challenges in keeping our documentation and codebase up-to-date and aligned with each other.

We identified the following two problems,

- The editor pane documentation had not been updated in a while, and it didn’t showcase all its amazing features. This pane has a lot of non-obvious functionalities, so our main goal for this problem was to increase their discoverability.
- Some of the external plugins hadn’t been updated to the new API due to a lack of documentation and migration guides to Spyder 5. Having documentation for the new API would also increase the number of external plugins created by our community and their maintainability.

## Proposal abstract

Spyder 5 introduced significant changes, including a new API that allows the interface to be extensible, along with UX and accessibility improvements reflected in the look and feel of the whole application. While most of the documentation is up to date, some remaining pieces still need further work, including the most important piece of Spyder, the Editor pane. 

We need to update the user documentation to support and provide the Spyder community with a reliable source for troubleshooting and showcase all of the current IDE’s functionalities. In the end, ensuring this information is available to the whole community will benefit our end-users and better support existing and new contributors.

As part of Google Season of Docs 2022, the technical writer working on this project would:

- Update Spyder 5 documentation for the Editor pane by reviewing the existing documentation and adding missing content for the new features and up-to-date screenshots and gifs.
- Update Spyder developer online documentation adding the new public API functionality and detailed technical guides covering what is needed to create a new basic plugin and how to update existing ones.

The complete proposal is available [here](https://github.com/spyder-ide/spyder/wiki/GSoD-2022-Project-Proposal)

## Project Description

### Creating the proposal

This is the first year that Spyder IDE participated in the Google Season of Docs initiative, it helped identify opportunities to improve our existing documentation. In the end, we chose the biggest documentation debt we had to fully take advantage of the grant. Internally, we wrote the proposal, gave rounds of feedback and submitted it via the Google Season of Docs selection process. Also, we decided to add it as a page in the wiki at the Spyder IDE GitHub repository available publicly for all our community. 

### Budget

There were no unexpected expenses outside of the approved grant budget, and we didn’t have any other source of funding. Also, all the payments were made through [Open Collective](https://opencollective.com/spyder) on time without any issues.

### Participants

We didn’t have anyone in mind when writing the application, so we were eager to find a technical writer interested in the project. We received five applications via email, so we set up video interviews to find the best-fitted candidate. In the end, we hired one technical writer to work with us for the next six months. 

We are grateful for the flexibility to hire anyone without any restriction in any part of the world. As our project’s community engages with different people and timezones, we had no restrictions. This is something important to be mindful of while recruiting and also setting up different communication channels to move the project forward.
Given the open source nature of Spyder IDE, the technical writer’s first task was to set up the contribution environment and start creating pull requests (PRs) to receive public feedback and review. Our main channel of communication was the documentation repository, but we also set up an account for the technical writer in Slack. We also had weekly meetings to sync the work and track the priorities for each week.

The participants for this project were:

- Stephannie Jimenez Gacha (mentor, reviewer)
- Christopher Gerlach (project maintainer, reviewer)
- Carlos Cordoba (project maintainer, reviewer)
- Daniel Althviz (project maintainer, reviewer)
- Hanan Younes (technical writer)

### Timeline

The timeline of the project is shown above,

| Stage | Completed by |
| ----- | ------------ |
| **Onboarding** | |
| Project kickoff | May 24 |
| Set-up of development environments | June 8 |
| Introduction to Spyder IDE features via contributing guidelines, tutorials, workshops and other resources | June 21 |
| **Review project** | |
| Review project requirements | July 1 |
| Test and familiarize existing Editor documentation | July 1 |
| **Documentation development phase** | |
| Make outline for the new Editor documentation | July 3 |
| First PRs up for review | July 31 | 
| First PRs reviewed and merged | August 14 | 
| Documentation published and available in the Spyder IDE docs | August 14 |
| Subsequent PRs reviewed and merged | August - November |
| Documentation published and available in the Spyder IDE docs | August - November |
| **Finalization phase** | |
| Create and upload GIFs and screenshots | November 14 |
| Finish documentation development and PRs | November 15 |
| Technical writer working on blog post | November 10 |
| Working on Season of Docs case study | November |
| Case study submitted | November 30 |

We had to do adjustments to the deliverables and the scope of the project overall because of the amount of features that were included in the final editor pane documentation, further details in Analysis.

### Results

Working on this project, Hanan was able to:

- Familiarize themself with a complex project that involves more than one repository by following the existing contributing guidelines, tutorials, workshops and other resources.
- Helped flag pain points of the contributing guidelines - [PR #319](https://github.com/spyder-ide/spyder-docs/pull/319)
- Updated the Editor documentation introduction section - [PR #322](https://github.com/spyder-ide/spyder-docs/pull/322) - [Editor docs](https://docs.spyder-ide.org/current/panes/editor.html)
- Verified, organized and created new sections for the Editor pane documentation - [PR #331](https://github.com/spyder-ide/spyder-docs/pull/331) - [Editor docs](https://docs.spyder-ide.org/current/panes/editor.html)
- Created a whole new documentation page for the Outline pane - [PR #327](https://github.com/spyder-ide/spyder-docs/pull/327) - [Outline docs](https://docs.spyder-ide.org/current/panes/outline.html)
- Wrote a blog post about GSoD experience available [here](https://labs.quansight.org/blog/the-new-spyder-editor-documentation-under-the-spotlights)!

Originally we had planned to update the developer documentation as part of this grant, but we shifted our focus in favor of showcasing more features for the Editor pane and creating the Outline pane documentation page.

### Metrics

At the start of this project, we would consider the project as successful if after finalizing the new documentation:

- At least 8 major editor features/configuration options were documented; there were only 3 basic features described in the docs at the start of the grant.
- Complete at least 3 additional pages of the online developer documentation.
- At least 2 external plugins were migrated in the six months following project completion.

Six months later, the Editor documentation has 18 sections describing its key components, interface, editing features, code execution, code navigation, code analysis and completions, and keyboard shortcuts. With additional screenshots and gifs showcasing all its functionality completing the first metric. 

Given that we weren’t able to update the developer documentation we cannot take into account the last two metrics. Nevertheless, the contributing guidelines were updated, and the Outline page was created which summed up to the creation/update of 3 additional pages in the overall documentation of the project. 

Two of the chosen metrics correlate well with the outcomes of the project given that we were interested in extending our documentation. We hope we can continue growing our resources for our community every year at a steady pace because we still have a lot of features that need to be described.

### Analysis

We are really grateful for the opportunity of being part of Google Season of Docs 2022 and consider it beneficial and a needed improvement for Spyder IDE. The outcome of this project includes clear and fresh documentation that is available on the project website. All the editor pane documentation is a great improvement and will serve all our users.

For our organization, this grant was a success even if we didn’t get to make all the deliverables we had in mind. We were able to reduce the documentation debt that we had for more than a year, giving us room to move to other documentation projects in the future. 

Our technical writer was a perfect fit for our project, she gave us really useful feedback, and introduced new ideas and new perspectives about the current state of the contribution guidelines and the overall documentation. We hope that Hanan continues to work with open source projects because her role is really important for our ecosystem. Please give a read to her blog post with her experience available [here]([https://labs.quansight.org/blog/the-new-spyder-editor-documentation-under-the-spotlight](https://labs.quansight.org/blog/the-new-spyder-editor-documentation-under-the-spotlights))

We faced a couple of setbacks during the grant including,

- Underestimating the time of onboarding - Spyder is a huge project with a big codebase and hundreds of features. For our technical writer to be able to write about the principal component, she needed to not just install the IDE, but also play with some tutorials, workshops and other resources.
- Our technical writer took a couple of weeks off to handle urgent personal matters.
- Structural changes in the governance of the project made the grant work slower.
- Some of our reviewers work as volunteers in the project, meaning oftentimes there were a couple of weeks where the writer was waiting for a final review before being able to merge the work.

## Summary

Our experience in Google Season of Docs (GSoD) was generally positive and rewarding. We deeply appreciate Google for this opportunity, and we are beyond thankful for their genuine support for improving documentation in open source. Our technical writer succeeded in producing quality documentation deliverables, showing strong technical and communication skills, and developing a good understanding of the Spyder IDE promptly. 

As a result of this first participation in GSoD, the Spyder Editor documentation has been expanded and improved, which was the main objective of this project. We achieved great results with the Editor documentation and we aim to update our developer online documentation in the future.

### Lessons learned

1. Communication is key
1. Be flexible and adaptable to any unforeseen changes to your initial plan 
1. Expect the process to take a larger part of your time
1. Don’t be afraid of unexpected changes
1. Patience and resilience are key to making contributions
1. Documentation work is meaningful and goes hand to hand with software development

### Advice for other organizations who consider participating in GSoD

1. Review and recognize the needs of your documentation, and take full advantage of the unique skills of your technical writer.
1. Take into account applicants from all over the world, diversity helps a lot with the flow of ideas and we assure you that it will have a very positive impact on your project. Having a fresh set of eyes on your documentation is invaluable and can help identify awareness gaps and opportunities to improve user experience significantly.
1. Be flexible with deliverables and goals for the grant, sometimes the estimation of work is off but that doesn’t mean your end result is not sufficient.
