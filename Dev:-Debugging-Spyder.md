# Spyder Debugging mode

`SPYDER_DEBUG` environment variable supports 3 levels of debug mode:
* `SPYDER_DEBUG=0` or `False`: debug mode is off
* `SPYDER_DEBUG=1` or `True`: debug level 1 is on (internal console is disconnected)
* `SPYDER_DEBUG=2`: debug level 2 is on (+ logging coms with external Python processes)
* `SPYDER_DEBUG=3`: debug level 3 is on (+ enabling -v option in external Python processes and debugging editor)

Example:
```bash
export SPYDER_DEBUG=3
```
Debug mode can be also activated using the bootstrap script:

```bash
./bootstrap.py --debug
```
## Adding debug prints

```python
from spyder.config.base import debug_print

debug_print("This will only printed in debug mode")
```