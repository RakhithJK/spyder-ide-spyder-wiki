| key            | value                                                 |
|----------------|-------------------------------------------------------|
| Status         | Active                                                |
| Author         | Full Name &lt;full.name@gmail.com&gt;                 |
| Created        | February, 2015                                        |
| Updated        | February, 2015                                        |
| Discussion     | link to the issue where the SEP is being discussed    |
| Implementation | link to the PR                                        |

# Conversation and Discussion
Over [Gitter](https://gitter.im/spyder-ide/)

# Description
The idea is to have a basic abstraction layer and support for different version control systems, namely Git and Mercurial. [Issue 816](https://github.com/spyder-ide/spyder/issues/816) started the discussion and will serve as basis for this PR.

The plan is to have a minimal set of features that would allow common vc commands to be used inside spyder by calling the external programs (using a QProcess)

# Current Status

# Proposal

## Existing abstraction layers

https://code.google.com/p/pysync/

https://github.com/alex/pyvcs

https://github.com/codeinn/vcs/

https://github.com/gitpython-developers/GitPython

