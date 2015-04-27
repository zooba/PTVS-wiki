# Pyvot – A Python to/from Excel Connector

<p>&nbsp;(NOTE: pyvot is not actively maintained anymore and is serving more as a technology demo. please check out DataNitro and PyXLL instead - thanks)</p>
<p><a href="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299134"><img title="pyvot.screenshot" src="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299135" alt="pyvot.screenshot" style="float:none; padding-top:0px; padding-left:0px; margin-left:auto; display:block; padding-right:0px; margin-right:auto; border-width:0px" border="0" height="373" width="595"></a></p>
<p><span style="font-size:medium"><span style="color:#ffffff; background-color:#dd8484">Click this to view:</span>&nbsp;<a href="http://www.youtube.com/watch?v=Gu31s7kXPOg">http://www.youtube.com/watch?v=Gu31s7kXPOg</a></span></p>
<p><span style="font-size:x-large">&nbsp;</span><span style="font-size:x-large">Introduction</span></p>
<p>Pyvot connects familiar data-exploration and visualization tools in Excel with the powerful data analysis and transformation capabilities of Python, with an emphasis on tabular data. It provides a minimal and Pythonic interface to Excel, smoothing over the
 pain points in using the existing Excel object model as exposed via COM.</p>
<ul>
<li>Pyvot on PyPI: <a href="http://pypi.python.org/pypi/Pyvot">http://pypi.python.org/pypi/Pyvot</a>
</li><li>Pyvot documentation, including tutorial: <a href="http://packages.python.org/Pyvot/">
http://packages.python.org/Pyvot/</a> </li></ul>
<h1>Examples</h1>
<p>We’ll now present a quick tour of Pyvot’s key features and workflow. For a more thorough treatment, make sure to check out the full
<a href="http://packages.python.org/Pyvot/tutorial.html">Pyvot tutorial</a>.</p>
<h2>Python to Excel and back again</h2>
<p>Pyvot enables easy transit of data between Python and Excel.</p>
<p>For example, we can move a list of Python values to Excel, view and manipulate the data, and retrieve the new version. In a symmetric and equally common usage, we can grab and process Excel values in Python, and display the result to Excel.</p>
<blockquote>
<pre>&gt;&gt;&gt; xl.Workbook() # Create empty Excel workbook, stored as the 'active' workbook
&gt;&gt;&gt; a = range(1,10) 
&gt;&gt;&gt; a
[1, 2, 3, 4, 5, 6, 7, 8, 9]
&gt;&gt;&gt; xl.view(a) # show Python enumerable in Excel (active workbook)</pre>
</blockquote>
<p>The Python array is copied into Excel. By default, Pyvot picks an open range on the active worksheet.</p>
<p><a href="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299069"><img title="view" src="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299070" alt="view" style="padding-top:0px; padding-left:0px; margin:0px; display:inline; padding-right:0px; border-width:0px" border="0" height="244" width="213"></a>&nbsp;</p>
<p>Retrieving data from Excel requires an <span style="font-family:courier new">xl.Range</span> object, which represents the cells on which to operate. The
<span style="font-family:courier new">xl.view</span> function returns the range that it selected to store the data:</p>
<blockquote>
<pre>&gt;&gt;&gt; r = xl.view(range(1,10))
&gt;&gt;&gt; r
&lt;ColumnVector range object for $A$2:$A$1048576 (visible only)&gt;
&gt;&gt;&gt; r.get()
[1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0]
&gt;&gt;&gt; sum(r) # ranges are iterable
45.0</pre>
</blockquote>
<p>Note that view chose the entirety of column A (sans header) to store our list, but
<span style="font-family:courier new">Range.get </span>assumed we only wanted its useful data.</p>
<p>Now we can manipulate the Excel range, and fetch the new results back. For example, suppose we delete some rows using the Excel UI and change the values like so:</p>
<p><a href="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299071"><img title="view_post_delete" src="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299072" alt="view_post_delete" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px" border="0" height="180" width="167"></a></p>
<blockquote>
<pre>&gt;&gt;&gt; r.get() # get updated values
[1.0, 20.0, 8.0, 9.0]</pre>
</blockquote>
<p>The current selection is also available as a Range. This allows Excel to act as an interface for selecting interesting data:</p>
<blockquote>
<pre>&gt;&gt;&gt; xl.selected_range().get()
8.0</pre>
</blockquote>
<h2>Mapping Excel columns</h2>
<p>You can also run map operations on Excel data. This can be useful for writing Python functions to clean the data and return new computed columns.</p>
<p>For example, suppose we want to combine the city and state columns in a single column:</p>
<blockquote>
<pre>&gt;&gt;&gt; def Merge(city, state):
...     return city + ", " + state
...
&gt;&gt;&gt; wCities = xl.Workbook("cities.xlsx")
&gt;&gt;&gt; xl.map(Merge, wCities.get("City"), wCities.get("State"))
&lt;ColumnVector range object for $N$2:$N$51 (visible only)&gt;</pre>
</blockquote>
<p>Note that <strong>we retrieved Range objects for the table columns by name</strong>. Pyvot can obtain ranges for table columns, named ranges, and plain A1:B2-style references.</p>
<p><span style="font-family:courier new">xl.map</span> works just like the built-in map function, but inserts the results as a new column in Excel. It will infer a column name from the function name, and it will pick a column related to its arguments. Note
 below that “Merge” becomes a new column in the source table:</p>
<p><a href="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299073"><img title="alaska_map" src="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299074" alt="alaska_map" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px" border="0" height="199" width="382"></a></p>
<p>&nbsp;</p>
<h2>Table joins</h2>
<p>Pyvot supports join operations on Excel tables. <span style="font-family:courier new">
xl.join(rangeDest, rangeSrc)</span> takes in 2 Ranges. It infers the containing tables for each range. For each value in rangeDest, it will do the lookup in
<span style="font-family:courier new">rangeSrc</span> and merge the row into the table in
<span style="font-family:courier new">rangeDest</span>.</p>
<p>For example, suppose we want to city crime data from in “cities.xlsx” with population data from “population.xlsx”.</p>
<p>First we load (or connect to) the workbooks containing tables we want to join:</p>
<blockquote>
<pre>&gt;&gt;&gt; wCities = xl.Workbook(“cities.xlsx”)
&gt;&gt;&gt; wPop = xl.Workbook("Population.xlsx")</pre>
</blockquote>
<p>Then we compute a primary key column, if necessary. In this case, we’re joining on multiple columns (both city and state), so we’ll merge them into a single column for the join:</p>
<blockquote>
<pre>&gt;&gt;&gt; xl.map(Merge, wPop.get("City"), wPop.get("State"))
&lt;ColumnVector range object for $D$2:$D$51 (visible only)&gt;</pre>
</blockquote>
<p>The same operation is then applied on <span style="font-family:courier new">wCities</span>.</p>
<p>The two mapped columns act as keys for the join:</p>
<blockquote>
<pre>&gt;&gt;&gt; xl.join(wCities.get("Merge"), wPop.get("Merge"))</pre>
</blockquote>
<p><a href="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299075"><img title="alaska_join_city" src="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299076" alt="alaska_join_city" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px" border="0" height="164" width="400"></a></p>
<p>Destination table</p>
<p><a href="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299077"><img title="alaska_join_pop" src="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299078" alt="alaska_join_pop" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px" border="0" height="163" width="377"></a></p>
<p>Source table</p>
<p><a href="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299079"><img title="alaska_join_final" src="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299080" alt="alaska_join_final" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px" border="0" height="132" width="565"></a></p>
<p>Destination table after join</p>
<h1>Installation</h1>
<p>Pyvot requires <strong>CPython</strong> 2.6 or <a href="http://python.org/download/releases/2.7.2/">
2.7</a> with the <a href="http://sourceforge.net/projects/pywin32/">Python for Windows extensions (pywin32)</a> installed, and at the minimum, Office 2010.</p>
<p>If a clean Python session can import the win32com module, Pyvot is ready to be installed:</p>
<blockquote>
<pre>PS C:\&gt; python
Python 2.7 (r27:82525, Jul  4 2010, 09:01:59) [MSC v.1500 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
&gt;&gt;&gt; import win32com
&gt;&gt;&gt;</pre>
</blockquote>
<h3>Installing from PTVS</h3>
<p>Python Tools for Visual Studio now ships an <a href="http://pytools.codeplex.com/">
add-on for Pyvot integration</a>. This add-on includes a Pyvot project template as well as support for installing Pyvot into multiple interpreters.</p>
<p>First, install Pyvot into the desired interpreters from the Tools menu (keep in mind that Pyvot requires CPython):</p>
<p><a href="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299081"><img title="image" src="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299082" alt="image" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px" border="0" height="221" width="969"></a></p>
<p>Then, create a new Pyvot project:</p>
<p><a href="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299083"><img title="image" src="http://download.codeplex.com/Download?ProjectName=pytools&amp;DownloadId=299084" alt="image" style="padding-top:0px; padding-left:0px; display:inline; padding-right:0px; border-width:0px" border="0" height="300" width="550"></a></p>
<p>The new project will need to be configured to use an interpreter for which Pyvot has been installed.</p>
<p>&nbsp;</p>
<h3>Installing with <span style="font-family:courier new">setuptools</span></h3>
<p>If you have <a href="http://pypi.python.org/pypi/setuptools">setuptools</a> installed, you can install a source or binary distribution of Pyvot with
<strong>easy_install</strong>. <strong>easy_install</strong> is usually in <span style="font-family:courier new">
&lt;Python directory, ex. C:\Python27&gt;\Scripts</span></p>
<ul>
<li>
<p>To install the latest version from PyPI:</p>
<pre>easy_install Pyvot</pre>
</li><li>
<p>To install an already-downloaded source (.zip) or binary (.egg) distribution:</p>
<pre>easy_install path\to\file</pre>
</li></ul>
