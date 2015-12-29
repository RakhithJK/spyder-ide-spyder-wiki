# Description
A series of Python/Spyder common recipes to take into account when coding

# Python

## Operating system (OS) specific operations

```python
import os
import sys

# Operations for windows only
if os.name == 'nt':
    pass

# Operations for linux only
if sys.platform.startswith('linux'):
    pass

# Operations for Mac only
if sys.platform == 'darwin':
    pass

# Operations for unix (linux and mac)
if os.name != 'nt':
    pass

```

## Don't use `subprocess.Popen`

Instead, use `programs.run_shell_command` and `programs.run_program` to launch external programs.  These wrapper functions make sure that the correct flags are set for each platform. For example, `close_fds` is set on POSIX, while on Windows the creation of a separate CMD shell window is disabled (under certain circumstances, this window would quickly flash in the background when the external call was performed).  These wrappers also set `stdout`, `stdin` and `stderr` to `subprocess.PIPE` by default.  Have a look at the implementation in `programs.py` for further details.  There are also a few examples of calls scattered throughout the source code. 

All extra `kwargs` in both `run_shell_command()` and `run_program()` are passed through internally to `subprocess.Popen()`, so you can override any of the default behaviour.

### Example using `run_shell_command()`

```
from programs import run_shell_command

pipe = run_shell_command('ls -la')
output = pipe.stdout.read()
```

# Example using `run_program()`
```
from programs import run_program

proc = run_program('/usr/bin/python', ['-V'], cwd='/Users/caleb')
output, err = proc.communicate()
```