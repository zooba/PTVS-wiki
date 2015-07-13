# Using the IPython REPL with PTVS

## PTVS has a number of REPL modes to choose from:
**REPL** | **Description** | **Editing** | **Debugging** | **Images**
Standard | Default REPL, talks to Python directly | Standard editing (multiline, etc). | Yes, via `$attach` | No
IPython | REPL talks to IPython backend | IPython commands, Pylab conveniences | No | Yes, inline in REPL
IPython w/o Pylab | REPL talks to IPython backend | Standard IPython | No | Yes, separate window
Debug REPL | Default REPL, talks to debugged Python process | Standard editing | Only debugging | No

In this document we'll cover IPython/matplotlib/etc.

## Installing IPython

We highly recommend installing IPython, matplotlib and their dependencies from a distro and not via PyPi. For this tutorial, we'll use the package from UCI's Python Extensions page:

[http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack)

### Configuring IPython in PTVS
#### 1. First let's make sure IPython/matplotlib have been installed on your system &amp; work properly.

Go to your Python installation directory and start IPython in Pylab mode (**ipython --pylab**), and enter the following:

```python
y = x ** 2
plot(x, y, 'r')
```

Assuming everything is configured properly, you should see something like this:

![IPython Configured](Images/IPython01Step.png)

#### 2. Now let's make sure PTVS can find all the right bits (IPython, matplotlib, etc):
Bring up the Python Environments window by typing Ctrl-K-` (backtick) and select your Python environment. Here we've selected Python 2.7 64-bit.

![2](Images/IPython2.png)

Look at the 'pip' panel and ensure you can see `IPython` and `matplotlib` listed.

![3](Images/IPython3.png)

#### 3. Switch back to 'Overview', click "Configure interactive options" and set **Interactive Mode** to IPython:

![4](Images/IPython4.png)

#### 4. In the Environments list, click the **Open interactive window** link to bring up the Interactive window. You may need to reset the window if you have just changed the interactive mode:

![5](Images/IPython5.png)

#### 5. Now we're in IPython mode with Pylab. Let's try to plot something. Enter this in the REPL:

```python
>>> x = linspace(0, 5, 10)
>>> y = x ** 2
>>> plot(x, y, 'r')
```

You should see a graph like this inline:

![6](Images/IPython6.png)

You can place the mouse pointer on the image and resize it if necessary:

![8](Images/IPython8.png)

## Entering, pasting and sending code to the REPL
Instead of typing in the REPL, you can select text in the Editor and use **Ctrl+E, E** to send it to the interactive window. The window will be selected based on your current project or your default environment.

Try pasting this code into the Editor, then send it to the interactive window using **Ctrl+A** (to select it all), then **Ctrl+E, E**:

```python
from mpl_toolkits.mplot3d import Axes3D
import matplotlib.pyplot as plt
import numpy as np
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
    xs = np.arange(20)
    ys = np.random.rand(20)
    # You can provide either a single color or an array. To demonstrate this,
    # the first bar of each set will be colored cyan.
    cs = [c] * len(xs) 
    cs[0] = 'c' 
    ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

ax.set_xlabel('X') 
ax.set_ylabel('Y') 
ax.set_zlabel('Z') 
plt.show()
```

![9](Images/IPython9.png)

When sending code to the Interactive window (by using Ctrl+E, E), the commands are sent to IPython as one unit to avoid giving you intermediate 'partial' graphs:

![10](Images/IPython10.png)

So far all the images have been inline in the REPL window. If you run the code from the Editor (CTRL-F5, or right click on the file name & choose Run without Debugging), you'll get a standalone matplotlib window:

![11](Images/IPython11.png)

## Shell commands, magics, etc.

IPython has a number of useful features such as escaping to the system shell, variable substitution, capturing output, etc. Please refer to the IPython reference guide for further information:

![12](Images/IPython12.png)

## IPython notebook mode

You can also use IPython in "notebook" mode where you can use any browser on any OS as the canvas. The backend IPython engine can be local on your machine, or remote. Windows Azure has support for running IPython on a Windows or Linux VM.

![13](Images/IPython13.png)

Please see the following for details:
Video: [http://www.youtube.com/watch?v=ljrSOkMs7DQ](http://www.youtube.com/watch?v=ljrSOkMs7DQ)

Docs: [http://www.windowsazure.com/en-us/develop/python/tutorials/ipython-notebook/](http://www.windowsazure.com/en-us/develop/python/tutorials/ipython-notebook/)

## Limitations
Note that IronPython does not support IPython, despite the fact that you can select it on the Interactive Options form. You can upvote the [feature request](https://github.com/Microsoft/PTVS/issues/84) or implement it if you'd like!
