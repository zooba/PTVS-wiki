# Using the IPython REPL with PTVS

## PTVS has a number of REPL modes to choose from:

<table border="1" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td width="117" valign="top">
<p><strong>REPL</strong></p>
</td>
<td width="124" valign="top">
<p><strong>Description</strong></p>
</td>
<td width="292" valign="top">
<p><strong>Editing / Debugging</strong></p>
</td>
<td width="90" valign="top">
<p><strong>Images</strong></p>
</td>
</tr>
<tr>
<td width="117" valign="top">
<p><strong>Standard</strong></p>
</td>
<td width="124" valign="top">
<p>Default REPL, talks to Python directly</p>
</td>
<td width="292" valign="top">
<p>Edit: Standard Editing (arrows, multiline, etc).</p>
<p>Debug: No</p>
</td>
<td width="90" valign="top">
<p>No</p>
</td>
</tr>
<tr>
<td width="117" valign="top">
<p><strong>IPython with Pylab</strong></p>
</td>
<td width="124" valign="top">
<p>REPL talks to IPython backend</p>
</td>
<td width="292" valign="top">
<p>Edit: Standard &#43; IPython commands &#43; Pylab conveniences<br>
Debug: No</p>
</td>
<td width="90" valign="top">
<p>Yes, inline in REPL</p>
</td>
</tr>
<tr>
<td width="117" valign="top">
<p><strong>IPython w/o Pylab</strong></p>
</td>
<td width="124" valign="top">
<p>REPL talks to IPython backend</p>
</td>
<td width="292" valign="top">
<p>Edit: Standard &#43; IPython</p>
<p>Debug: No</p>
</td>
<td width="90" valign="top">
<p>Yes, separate window</p>
</td>
</tr>
</tbody>
</table>


Note that there's also the "Debug REPL", which is the standard REPL, but is aware of the current debugging context.

In this tutorial we'll cover IPython/matplotlib/etc.

## Installing IPython

We highly recommend installing IPython, matplotlib and their dependencies from a distro and not via PyPi. For this tutorial, we'll use the package from UCI's Python Extensions page:

[http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack"](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack)

### Configuring IPython in PTVS
#### 1. First let's make sure IPython/matplotlib have been installed on your system &amp; work properly.

Go to your Python installation directory and start IPython in Pylab mode (**ipython --pylab**), and enter the following:

	y = x ** 2
	plot(x, y, 'r')

Assuming everything is configured properly, you should see something like this:

![1](Images/IPython1.png)

#### 2. Now let's make sure PTVS can find all the right bits (IPython, matplotlib, etc):
* bring up the Python Interpreters window by typing Ctrl-K-` (backtick). Here we see that Python 2.7 64-bit has been selected (<strong>Make Default</strong>):

![2](Images/IPython2.png)

* Click the <strong>View in File Explorer</strong> link and make sure you can see IPython & matplotlib in your Lib\site-packages directory:</p>

![3](Images/IPython3.png)

#### 3. On the Interpreters Windows, click the <strong>Interactive Options</strong> and set **Interactive Mode** to IPython:

![4](Images/IPython4.png)

#### 4. On the Interpreters Window, click the **Interactive Window** link to bring up the REPL window (or Alt-I). Now click the blue curved arrow (top left) to RESET the REPL from the previous mode (eg Standard to IPython mode):

![5](Images/IPython5.png)

#### 5.&nbsp; Now we're in IPython mode with Pylab. Let's try to plot something. Enter this in the REPL:

	x = linspace(0, 5, 10)
	y = x ** 2
	plot(x, y, 'r')

You should see a graph like this <em>inline</em>:

![6](Images/IPython6.png)

If you hit enter again, you'll see that the image becomes a thumbnail:

![7](Images/IPython7.png)

However you can place the mouse pointer on the image and resize it if necessary:

![8](Images/IPython8.png)

## Entering, pasting and sending code to the REP
Instead of typing in the REPL, you can select text in the Editor and use **CTRL-E-E** to send it to IPython. Try pasting this code into the Editor, then to the REPL via
**CTRL-A**, **CTRL-E-E**:

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
	plt.show()</strong>

![9](Images/IPython9.png)

When sending code to the Interactive window (by using Ctrt-E-E), the commands are sent to IPython as one unit to avoid giving you intermediate 'partial' graphs:

![10](Images/IPython10.png)

So far all the images have been inline in the REPL window. If you run the code from the Editor (CTRL-F5, or right click on the file name & choose Run w/o Debugging), you'll get a standalone matplotlib window:

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
Note that IronPython does not support IPython, despite the fact that you can select it on the Interactive Options form. You can upvote the feature request or implement it if you'd like!
([https://pytools.codeplex.com/workitem/1632](https://pytools.codeplex.com/workitem/1632)).</p>
