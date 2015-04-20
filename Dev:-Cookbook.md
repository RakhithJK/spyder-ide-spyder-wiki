A series of Python/Spyder common recipes to take into account when coding

# Python

## Make operations that depend on the Operating System (OS)

```python
import os
import sys

if os.name == 'nt':
    pass

if sys.platform.startswith('linux'):
    pass

if sys.platform == 'darwin':
    pass
```