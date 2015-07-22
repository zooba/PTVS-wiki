# Which Python interpreter should I install?

PTVS does not come with a Python interpreter – in order to run your code, you need one. So let's install one!

Fortunately there are several choices and they're all free:

**CPython** – this is the "native" and most commonly used interpreter.

Attributes:
- Most commonly used, available in 32 and 64 bit versions. 
- Latest language features 
- Maximum Python package compatibility 
- Best debugging experience in PTVS (eg debug on Linux/Mac, Python/C++ debugging) 
- Works with [IPython](http://ipython.org/) 
- Versions: 2.7 (frozen) and 3.x (latest) 

If you've already installed VS and PTVS, we recommend the [latest 32-bit CPython](http://go.microsoft.com/fwlink/?LinkID=299430) (installer) from [www.python.org](http://www.python.org/). Once CPython is installed, it will be auto-detected by PTVS. If you want more information about the differences between Python 2.x versions and 3.x versions, please visit [http://wiki.python.org/moin/Python2orPython3](http://wiki.python.org/moin/Python2orPython3).

**IronPython** – this is a .NET implementation of Python

Attributes:
- Best .NET (C#/F#/...) interop, available in 32 and 64 bit versions. 
- Versions: 2.7.5 (3.x features underway) 
- Some non-.NET packages can be used via bridges, and others have been ported  
- Standard Python debugging (no mixed .NET/Native debugging) 
- No IPython support 
- Decent mixed IronPython <-> C# debugging 

If you've already installed VS and PTVS, we recommend the [IronPython 2.7.5](http://ironpython.codeplex.com/downloads/get/970325). This will run an MSI from [http://ironpython.codeplex.com](http://ironpython.codeplex.com) which will install Python and will be auto-detected by PTVS.

**PyPy** – this is a high performance tracing JIT implementation of Python: [www.pypy.org](http://www.pypy.org/).

**Jython** – Like IronPython, this is an implementation of Python on the JVM: [www.jython.org](http://www.jython.org/).

Both PyPy and Jython can be used with PTVS (edit, IntelliSense, etc.) but various advanced debugging features may not work.

**Canopy and Anaconda** – both of these distros will also be automatically discovered and added to your list of Python Environments.


## Hey, I already have an interpreter on my machine, but PTVS doesn't seem to know about it!

Alright, let's fix that! Normally PTVS can locate an installed Interpreter by checking the registry, but if it's installed in a non-standard fashion, you can directly tell PTVS about it:

### 1. Open the Python Environments window (View -> Other Windows -> Python Environments) and click "+ Custom...":

![Add Python Environment](Images/AddPythonEnvironment.png)

### 2. Enter the name and path to your interpreter manually or by clicking "...":

![Add Python Environment](Images/AddPythonEnvironment2.png)

Here we've entered `D:\pypy-2.5.0-win32` as the **prefix path**.
**Path** is the path to the interpreter executable, commonly the prefix path followed by `python.exe`, while **Windows Path** is the path to the non-console executable, often `pythonw.exe`.
Clicking "Auto-detect" will attempt to fill in the remaining information based off the executable at **path**, and will look for `python.exe` under **prefix path** if not specified yet.
**Library Path** specifies the root of the standard library, but this value may be ignored if PTVS is able to request a more accurate path from the interpreter.
**Architecture** is normally detected and filled in for you, and **language version** can be selected from the drop down menu.

**Path Environment** Variable is the environment variable that the interpreter is going to look at to find search paths.
PTVS will change the value of the variable when starting Python so that it contains the project's search paths.
Typically this property should be set to `PYTHONPATH`, but some interpreters use a different value.

You can delete environments you have added by coming back to this Cofiguration page and clicking **Remove**.

### 3. When you have interpreters installed, you can manage them easily via the Python Environments Window

![Python Environments](Images/PythonEnvironments.png)

Here we see that there are several Interpreters installed, including IronPython.
We've made Python 3.4 the current default, and Python 2.7 needs to have its completion DB refreshed because of a newly installed package.

Interpreter databases are used to improve IntelliSense speed and reduce memory usage for the standard library and any libraries installed into site-packages. Analyzing all of the available source files can take anywhere from a minute to an hour or more, depending on what you have installed. However, once complete, you will get detailed IntelliSense and won't have to refresh the database again until you install more libraries.