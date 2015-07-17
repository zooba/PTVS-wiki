Browsing your Code
==================

Visual Studio provides a number of ways to navigate around your projects, regardless of the language used to develop them. This page provides an overview of navigating around Python projects in Visual Studio, though most of the features are available in all languages.

Solution Explorer
-----------------

The Solution Explorer window shows the files included in your project (see [Projects](Projects) for an overview of project files). You can double-click any of these files to open them in the associated editor, and files can be moved, copied, renamed, or deleted. Because Python projects are required to match the file structure on disk, most changes made through Solution Explorer will also update the file system.

Solution Explorer also includes the [Python Environments](Python Environments), [Search Paths](Projects#search-paths), and [References](Projects#references) nodes.

By default, Solution Explorer is visible and docked to one side of the main Visual Studio window. To show the window again, you can click on View -> Solution Explorer. Depending on your settings, the keyboard shortcut may be Ctrl+Alt+L, or Ctrl+W followed by S.

![Solution Explorer](Images/SolutionExplorer.png)

### Show All Files

When using Solution Explorer to view project files you have the option to view files only in the project, or all files that are on disk. This behavior is controlled by the "Show All Files" button on the Solution Explorer toolbar. When enabled, "Show All Files" will display all the files on disk, regardless of whether they are included in the project or not. Disabling "Show All Files" will show only those files and folders included in the project.

Files that are not part of the project may not be scanned for IntelliSense and may not be packaged or deployed to a remote server. Folders and files not currently included in the project will appear as a dotted outline, and can be added to the project by right clicking and selecting "Include in Project". Including or excluding a folder will also include or exclude all of its children. This does not make any changes to files on disk.

<div style="float: left; padding: 1em">
<img src="Images/ShowAllFilesDisabled.png" title="Show All Files disabled" alt="Show All Files disabled" />
<p style="text-align: center"><strong>Disabled</strong></p>
</div>
<div style="float: left; padding: 1em;">
<img src="Images/ShowAllFilesEnabled.png" title="Show All Files enabled" alt="Show All Files enabled" />
<p style="text-align: center"><strong>Enabled</strong></p>
</div>


Class View
----------

![Class View](Images/ClassView.png)

The Class View window shows a flat view of the modules in your project, and lets you expand them to view classes. Selecting a class will list its members in the lower part of the window, and double clicking on any item will take you to its definition in code.

To show the Class View window, click View -> Class View. Depending on your settings, the keyboard shortcut may be Ctrl+Shift+C, or Ctrl+W followed by C.

Object Browser
--------------

![Object Browser](Images/ObjectBrowser.png)

The Object Browser is similar to the Class View, but also displays information about the selected item in a panel in the lower-right. It has a less compact layout and is better suited to being placed in the main part of the window, rather than docked to one side.

To show the Object Browser window, click View -> Object Browser. Depending on your settings, the keyboard shortcut may be Ctrl+Alt+J, or Ctrl+W followed by J.

Navigate To
-----------

![Navigate To](Images/NavigateTo.png)

Navigate To provides a quick way to search for any element in your project. Using the same fuzzy search as [IntelliSense](Editor-Features#intellisense), you can find modules, classes, functions, and module- or class-scoped variables. Type a few letters matching the name of the item you want, use the arrow keys to select the right one, and press Enter to display it in the editor.

To access Navigate To, click Edit -> Navigate To. The keyboard shortcut is typically Ctrl+, (comma).


Bookmarks
---------

![Bookmarks](Images/Bookmarks.png)

Bookmarks allow you to add markers on particular lines of code so you can easily return to them. Under the Edit -> Bookmarks menu are commands for adding, removing, and navigating between bookmarks. There is also a Bookmark Window that lists all of the bookmarks in all open projects, allowing you to double-click on the one you want to view. Bookmarks can be renamed through this window.

To show the Bookmark Window, click View -> Bookmark Window. Depending on your settings, the keyboard shortcut may be Ctrl+K followed by Ctrl+W, or Ctrl+W followed by B. Check the Edit -> Bookmarks menu for the shortcuts to add, remove, and navigate between bookmarks.
