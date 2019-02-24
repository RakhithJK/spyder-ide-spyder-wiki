### Option 1:
Call `turtle.done()` with `turtle.bye()` and use the `Inline` or `Automatic` backend for the IPython Console (`Preferences` > `IPython Console` > `Graphics` > `Graphics Backend`). As an example:
```python
import turtle

wn=turtle.Screen()
wn.bgcolor("lightgreen")
tess = turtle.Turtle() # Create tess and set some attributes
tess.color("hotpink")
tess.pensize(5)
alex = turtle.Turtle() # Create alex

tess.forward(80) # Make tess draw equilateral triangle
tess.left(120)
tess.forward(80)
tess.left(120)
tess.forward(80)
tess.left(120) # Complete the triangle

alex = turtle.forward(100)

turtle.done()
turtle.bye()   
```

The call of `turtle.bye()` will raise a `Terminator` error but the IPython kernel will not die. To prevent the output of the exception you can use a `try/except`, like this:

```python
...
turtle.done()
try:
    turtle.bye()   
except turtle.Terminator:
    pass
```

The reason for this is to clean some elements used by `Turtle` after running.

**Important note**: The `try/except` block is only needed if the Spyder version is less than **3.3.3**.

### Option 2:

Instead of using the IPython Console you can use an external system terminal. Go to `Run` > `Configuration per file...` > Select `Execute in an external system terminal` over the `Console` section.
