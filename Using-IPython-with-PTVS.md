<h1>Using the IPython REPL with PTVS</h1>

<p>PTVS has a number of REPL modes to choose from:</p>
<p>&nbsp;</p>
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
<p>Note that there&rsquo;s also the &ldquo;Debug REPL&rdquo;, which is the standard REPL, but is aware of the current debugging context.</p>
<p>In this tutorial we&rsquo;ll cover IPython/matplotlib/etc.</p>
<h2>Installing IPython</h2>
<p>We highly recommend installing IPython, matplotlib and their dependencies from a distro and not via PyPi. For this tutorial, we&rsquo;ll use the package from UCI&rsquo;s Python Extensions page:</p>
<p><a href="http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack">http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack</a></p>
<h4>Configuring IPython in PTVS</h4>
<p>1. First let&rsquo;s make sure IPython/matplotlib have been installed on your system &amp; work properly.&nbsp;
<span style="font-size:10pt">Go to your Python installation directory and start IPython in Pylab mode (<strong>ipython --pylab</strong>), and enter the following:</span></p>
<p><strong>x = linspace(0, 5, 10) <br>
y = x ** 2 <br>
plot(x, y, 'r')</strong></p>
<p>Assuming everything is configured properly, you should see something like this:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716134"><img title="clip_image002_thumb[4]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716135" border="0" alt="clip_image002_thumb[4]" width="635" height="757" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<p>2. Now let&rsquo;s make sure PTVS can find all the right bits (IPython, matplotlib, etc):</p>
<p>- Bring up the Python Interpreters window by typing Ctrl-K-` (backtick). Here we see that Python 2.7 64-bit has been selected (<strong>Make Default</strong>):</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716136"><img title="clip_image004_thumb[2]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716137" border="0" alt="clip_image004_thumb[2]" width="624" height="138" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<p>- Click the <strong>View in File Explorer</strong> link and make sure you can see IPython &amp; matplotlib in your Lib\site-packages directory:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716138"><img title="clip_image005_thumb[1]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716139" border="0" alt="clip_image005_thumb[1]" width="628" height="321" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<p>3. On the Interpreters Windows, click the <strong>Interactive Options</strong> and set
<strong>Interactive Mode</strong> to IPython:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716140"><img title="clip_image007_thumb[1]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716141" border="0" alt="clip_image007_thumb[1]" width="630" height="364" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<p>4. On the Interpreters Window, click the <strong>Interactive Window </strong>link to bring up the REPL window (or Alt-I). Now click the blue curved arrow (top left) to RESET the REPL from the previous mode (eg Standard to IPython mode):</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716142"><img title="clip_image008_thumb[1]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716143" border="0" alt="clip_image008_thumb[1]" width="634" height="303" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<p>5.&nbsp; Now we&rsquo;re in IPython mode with Pylab. Let&rsquo;s try to plot something. Enter this in the REPL:</p>
<p><strong>x = linspace(0, 5, 10) <br>
y = x ** 2 <br>
plot(x, y, 'r')</strong></p>
<p>you should see a graph like this <em>inline</em>:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716144"><img title="clip_image009_thumb[3]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716145" border="0" alt="clip_image009_thumb[3]" width="640" height="554" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<p>If you hit enter again, you&rsquo;ll see that the image becomes a thumbnail:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716146"><img title="clip_image010_thumb[2]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716147" border="0" alt="clip_image010_thumb[2]" width="641" height="392" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<p>However you can place the mouse pointer on the image and resize it if necessary:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716148"><img title="clip_image011_thumb[2]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716149" border="0" alt="clip_image011_thumb[2]" width="643" height="467" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<h2>Entering, pasting and sending code to the REPL</h2>
<p>Instead of typing in the REPL, you can select text in the Editor and use <strong>
CTRL-E-E</strong> to send it to IPython. Try pasting this code into the Editor, then to the REPL via
<strong>CTRL-A</strong>, <strong>CTRL-E-E</strong>:</p>
<p><strong>from mpl_toolkits.mplot3d import Axes3D<br>
</strong><strong style="font-size:10pt">import matplotlib.pyplot as plt<br>
</strong><strong style="font-size:10pt">import numpy as np<br>
</strong><strong>fig = plt.figure() <br>
</strong><strong>ax = fig.add_subplot(111, projection='3d') <br>
</strong><strong>for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):&nbsp;<br>
</strong><strong>&nbsp;&nbsp;&nbsp;&nbsp;xs = np.arange(20)&nbsp;<br>
</strong><strong>&nbsp;&nbsp;&nbsp; ys = np.random.rand(20) </strong></p>
<p><strong>&nbsp;&nbsp;&nbsp; # You can provide either a single color or an array. To demonstrate this,
<br>
</strong><strong>&nbsp;&nbsp;&nbsp; # the first bar of each set will be colored cyan.
</strong></p>
<p><strong>&nbsp;&nbsp;&nbsp; cs = [c] * len(xs) <br>
</strong><strong>&nbsp;&nbsp;&nbsp; cs[0] = 'c' <br>
</strong><strong>&nbsp;&nbsp;&nbsp; ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)
<br>
</strong><strong></strong></p>
<p><strong>ax.set_xlabel('X') <br>
</strong><strong>ax.set_ylabel('Y') <br>
</strong><strong>ax.set_zlabel('Z') <br>
</strong><strong>plt.show()</strong></p>
<p>&nbsp;</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716150"><img title="clip_image013_thumb[1]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716151" border="0" alt="clip_image013_thumb[1]" width="633" height="402" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<p>When sending code to the Interactive window&nbsp; (by using Ctrt-E-E), the commands are sent to IPython as one unit to avoid giving you intermediate &ldquo;partial&rdquo; graphs:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716152"><img title="clip_image015_thumb[2]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716153" border="0" alt="clip_image015_thumb[2]" width="635" height="464" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<p>So far all the images have been inline in the REPL window.&nbsp; If you run the code from the Editor (CTRL-F5, or right click on the file name &amp; choose Run w/o Debugging), you&rsquo;ll get a standalone matplotlib window:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716154"><img title="clip_image017_thumb[2]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716155" border="0" alt="clip_image017_thumb[2]" width="635" height="467" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<h2>Shell commands, magics, etc.</h2>
<p>IPython has a number of useful features such as escaping to the system shell, variable substitution, capturing output, etc. Please refer to the IPython reference guide for further information:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716156"><img title="clip_image019_thumb[1]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716157" border="0" alt="clip_image019_thumb[1]" width="637" height="431" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<h2>IPython notebook mode</h2>
<p>You can also use IPython in &ldquo;notebook&rdquo; mode where you can use any browser on any OS as the canvas. The backend IPython engine can be local on your machine, or remote. Windows Azure has support for running IPython on a Windows or Linux VM.</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716158"><img title="clip_image021_thumb[2]" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=716159" border="0" alt="clip_image021_thumb[2]" width="640" height="592" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px"></a></p>
<p>Please see the following for details:</p>
<p>Video: <a href="http://www.youtube.com/watch?v=ljrSOkMs7DQ">http://www.youtube.com/watch?v=ljrSOkMs7DQ</a></p>
<p>Docs: <a href="http://www.windowsazure.com/en-us/develop/python/tutorials/ipython-notebook/">
http://www.windowsazure.com/en-us/develop/python/tutorials/ipython-notebook/</a></p>
<p>&nbsp;</p>
<h2>Limitations</h2>
<p>Note that IronPython does not support IPython, despite the fact that you can select it&nbsp; on the Interactive Options form.&nbsp; You can upvote the feature request or implement it if you&rsquo;d like!
<a href="https://pytools.codeplex.com/workitem/1632">https://pytools.codeplex.com/workitem/1632</a>).</p>
