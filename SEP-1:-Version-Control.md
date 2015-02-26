| key            | value                                                 |
|----------------|-------------------------------------------------------|
| Status         | Active                                                |
| Author         | Gonzalo Peña-Castellanos (@goanpeca)                  |
| Created        | February, 2015                                        |
| Updated        | February, 2015                                        |
| Discussion     | [Issue 816](https://github.com/spyder-ide/spyder/issues/816) / [Guitter](https://gitter.im/spyder-ide/)      |
| Implementation | link to the PR                                        |

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

