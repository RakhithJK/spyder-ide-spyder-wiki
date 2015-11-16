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