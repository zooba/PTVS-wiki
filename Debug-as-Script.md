<p><strong><em>New in PTVS 2.0</em></strong></p>
<p><strong>For a quick overview, please watch this video:&nbsp; <a href="http://www.youtube.com/watch?v=QADxwr0wjU4">
http://www.youtube.com/watch?v=QADxwr0wjU4</a>&nbsp;</strong></p>
<p><a href="http://www.youtube.com/watch?v=z8njMo59pTc"><img title="image" border="0" alt="image" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=635048" width="352" height="208" style="border-left-width:0px; border-right-width:0px; border-bottom-width:0px; float:none; padding-top:0px; padding-left:0px; margin-left:auto; display:block; padding-right:0px; border-top-width:0px; margin-right:auto"></a></p>
<p><strong>&nbsp;</strong></p>
<p>PTVS 2.0 includes support for debugging any Python script file, without a project, by simply opening it in VS, right clicking on it and choosing ‘Start with debugging’.</p>
<p>&nbsp;</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722891"><img title="Overview" border="0" alt="Overview" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722892" width="701" height="622" style="border-top:0px; border-right:0px; border-bottom:0px; border-left:0px; display:inline"></a>
</p>
<p>&nbsp;</p>
<p>In general, you take the following steps to debug a miscellaneous Python script file:</p>
<ul>
<li>Start VS (with PTVS 2.0 installed) </li><li>Choose ‘File/Open/File…’ </li><li>Select and open the Python script file of your choice </li><li>Set desired breakpoints within the Python script file </li><li>Right click within the document window and choose ‘Start with Debugging’ </li></ul>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722893"><img title="Open" border="0" alt="Open" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722894" width="700" height="622" style="border-top:0px; border-right:0px; border-bottom:0px; border-left:0px; display:inline"></a>
</p>
<p>. . .</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722895"><img title="StartWithDebugging" border="0" alt="StartWithDebugging" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722896" width="702" height="623" style="border-top:0px; border-right:0px; border-bottom:0px; border-left:0px; display:inline"></a>
</p>
<p>&nbsp;</p>
<p>Note that you may also invoke ‘Start with Debugging’ from an opened Python script file’s tab:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722897"><img title="StartWithDebuggingFromTab" border="0" alt="StartWithDebuggingFromTab" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722898" width="702" height="624" style="border-top:0px; border-right:0px; border-bottom:0px; border-left:0px; display:inline"></a>
</p>
<p>&nbsp;</p>
<p>The resulting debugging experience is the same as that for debugging a Python project’s startup file using F5. For example you can set breakpoints, break all, inspect state with the call stack, locals and watch windows, etc.</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722899"><img title="Overview" border="0" alt="Overview" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722900" width="701" height="623" style="border-top:0px; border-right:0px; border-bottom:0px; border-left:0px; display:inline"></a>
</p>
<p>&nbsp;</p>
<p>When debugging a Python script without a containing project open, the VS default interpreter version from Python Tools Options is used.</p>
<p>It is also possible to debug a Python script in the context of a PTVS project opened in VS. To do this, simply open the related project before following the steps above.</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722901"><img title="StartWithDebuggingInProject" border="0" alt="StartWithDebuggingInProject" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722902" width="701" height="623" style="border-top:0px; border-right:0px; border-bottom:0px; border-left:0px; display:inline"></a>
</p>
<p>The only real difference when debugging a script file which is within a currently open PTVS project is that, if the project has a non-default Python environment activated, it will be used. Otherwise, the VS default interpreter version will be used.</p>
<p>&nbsp;</p>
<p>There is one more way to Debug a Python script when a PTVS project is open. In the solution explorer you can right click on a PTVS project’s Python script file and chose ‘Start with Debugging’:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722903"><img title="StartWithDebuggingFromSolExp" border="0" alt="StartWithDebuggingFromSolExp" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722904" width="702" height="624" style="border-top:0px; border-right:0px; border-bottom:0px; border-left:0px; display:inline"></a>
</p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p>&nbsp;</p>
<p>It is worth noting that everywhere that you may invoke ‘Start with Debugging’,&nbsp; you may alternately invoke ‘Start without Debugging’:</p>
<p><a href="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722905"><img title="StartWithoutDebugging" border="0" alt="StartWithoutDebugging" src="http://download-codeplex.sec.s-msft.com/Download?ProjectName=pytools&DownloadId=722906" width="285" height="315" style="border-top:0px; border-right:0px; border-bottom:0px; border-left:0px; display:inline"></a>
</p>
<p>This has the effect of running the Python script using the VS default interpreter version, or an opened project’s active Python environment, only without debugging:).</p>
