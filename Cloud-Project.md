Microsoft Azure Cloud Service Projects
======================================

Microsoft Azure Cloud Services can be written in Python, and Python Tools for Visual Studio includes templates to help you get started.

This page is an overview of the support available in PTVS. Visit the [Python Developer Center](http://go.microsoft.com/fwlink/?linkid=254360) for more in-depth coverage of writing Python services on Azure.

What is a Cloud Service?
------------------------

Cloud Service is a model of an application that consists of multiple *roles*.
Each role performs a conceptually separate task, but may be replicated in order to provide scaling.
A cloud project may have any number of roles, and deploying the project will instantiate as many virtual machines as required.

Visit the [Cloud Service documentation](http://go.microsoft.com/fwlink/?LinkId=306052) for more details.

Roles
-----

Microsoft Azure Cloud Service supports two different kinds of roles: *web* and *worker*.

Web roles are intended for hosting front-end web applications.
For Python, any web framework that supports WSGI can be used to write this application.
See our [Python Web Projects](Web-Project) page for information about writing a web application using PTVS.

Worker roles are intended for long-running processes that do not interact directly with users.
They will typically make use of the [data](http://go.microsoft.com/fwlink/?LinkId=401571) and [app service](http://go.microsoft.com/fwlink/?LinkId=401572) libraries, which may be installed with `pip install`&nbsp;[`azure`](http://pypi.python.org/pypi/azure).


Create
======

To start creating your project, select the Azure Cloud Service template from the New Project dialog.
If you have not installed the Azure SDK Tools for Visual Studio, you will be prompted to install them now.

In the next dialog, you may select one or more roles to include.
Cloud projects may combine roles written in different languages, so you can easily write each part of your application in the most suitable language.
To add new roles to the project after completing this dialog, you can right click "Roles" in Solution Explorer and select one of the items under "Add".

**Important:**
After adding a new role to your Cloud project, you may be presented with some more configuration instructions.
If you are using Microsoft Azure Tools 2.4 or later, these instructions may not apply, and if you add multiple roles at the same time, you may not see all of the instructions.
The instructions and troubleshooting tips are available in the readme.mht file in each new role.


<div style="float: right">
<div style="margin: 1em"><img src="Images/AzureCloudProject.png" alt="Azure Cloud Project template" /></div>
<div style="float: right"><a href="Images/AzureCloudProjectWizard.png"><img src="Images/AzureCloudProjectWizard.png" width="400px" alt="Azure Cloud Project wizard" /></a></div>
</div>

In your role projects, you will see a `bin` directory containing one or two PowerShell scripts.
These are used to configure the remote machine, including installing Python, any [WebPI references](#webpi-references) or [requirements.txt](#requirementstxt) file in your project, and setting up IIS if necessary.
These files may be freely edited to customize your deployment, though most common options can be managed in other ways (see [Configure](#configure) below).
We do not suggest removing these files, as a legacy configuration script will be used instead if they are not available.
These items can be found as "Web Role Support Files" or "Worker Role Support Files" under Add New Item, if you need to add them to an existing project.

![Worker Role Support Files](Images/WorkerRoleSupportFiles.png)

Configure
=========
While the code above and the included PowerShell scripts may be edited freely, it is possible to set most configuration options through your Python project.

To specify the version of Python your worker should run with, make it the active environment for your project.
(Ensure that you have a WebPI reference or startup task to install this version on the instance - see the documentation in `ConfigureCloudService.ps1` for more details.)

If your version of Python cannot be detected using the CPython registry keys after it has been installed, you can add the `DeployedPythonInterpreterPath` property to your Python project by editing the .pyproj file.
This path will take precedence over the active environment.

To install packages using pip, update the `requirements.txt` file in the root directory of your project.

To set `PYTHONPATH` (or equivalent) before running the worker, add the necessary Search Paths to your project.
Other environment variables can be set by modifying `LaunchWorker.ps1` (worker role) or the automatically-generated `web.config` file (web role).

To specify the script to run in a worker role, or to specify your main handler script in a web role, make it the startup file in your project.
Alternatively, you can modify `LaunchWorker.ps1` (worker role) or set the full importable name of your WSGI app in Project Properties\Web\WSGI Handler (web role).

To specify command-line arguments for a worker role, add them to the Command Line Arguments property under Project Properties\Debug.

Test
====

While writing your roles, you can test your Cloud project locally using the Cloud Service Emulator.
The emulator is included with the Azure SDK Tools and is a limited version of the environment used when your Cloud Service is published to Azure.
To start the emulator, ensure your Cloud project is the startup project and press F5 or Ctrl+F5.

Note that, due to limitations in the emulator, it is not possible to debug your Python code.
We recommend you debug roles by running them independently of the emulator, and then use the emulator for integration testing before publishing.


Deploy
======

A project can be deployed to a Microsoft Azure Cloud Service by selecting the Cloud project, then selecting Publish from the Build menu.
You can also right-click the cloud project and select Publish.
(Note that the Publish menu on any individual project will not publish the entire cloud service, and may not be able to update the selected project in an existing cloud service.)

Publishing occurs in two phases.
The first is packaging, which runs on your development machine and produces a single package containing all the roles for your cloud service.
This package is deployed to Microsoft Azure, which will initialize one or more virtual machines for each role and deploy the source.

As each virtual machine activates, it will execute the `ConfigureCloudService.ps1` script and install any dependencies.
This script by default installs a recent version of Python from [nuget](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) and any packages specified in a `requirements.txt` file.
You can freely modify the `ConfigureCloudService.ps1` script in your project, or add alternate startup tasks to your cloud definition.

Finally, worker roles will execute `LaunchWorker.ps1`, which will start running your Python script, while web roles will initialize IIS and begin handling web requests.
You can freely modify the `LaunchWorker.ps1` script to change initial behavior, or add command-line arguments and environment variables to your cloud definition.

![Publish a Cloud Project](Images/PublishCloudProject.png)

Dependencies
------------

For Cloud Service, the `ConfigureCloudService.ps1` script uses pip to install a set of Python dependencies.
These should be specified in a file named `requirements.txt` (customizable by modifying `ConfigureCloudService.ps1`).
The file is executed with `pip -r requirements.txt` as part of initialization.

Note that Cloud Service instances do not include C compilers, so all libraries with C extensions must provide precompiled binaries.
pip and its dependencies, as well as the packages in `requirements.txt`, will be downloaded automatically and may count as chargeable bandwidth usage.
See [Virtual Environments](Python-Environments#managing-required-packages) for more information on managing `requirements.txt` files, including how to avoid compiler issues on the server and bandwidth charges.

Troubleshooting
---------------

If your web or worker role does not behave correctly after deployment, check the following:

* Your Python project includes a bin\ folder with (at least):
 * `ConfigureCloudService.ps1`
 * `LaunchWorker.ps1` (for worker roles)
 * `ps.cmd`

* Your Python project includes a `requirements.txt` file listing all dependencies
 * optionally, a collection of wheel files

* Enable Remote Desktop on your Cloud Service and investigate the log files.

* Logs for `ConfigureCloudService.ps1` and `LaunchWorker.ps1` are stored in the following path on the remote machine:
 * `C:\Resources\Directory\%RoleId%.DiagnosticStore\LogFiles`

* Currently, the `LaunchWorker.ps1.log` file is the only way to view output or errors displayed by your Python worker role.

If you are still having trouble, start a discussion at [our discussion forum](http://go.microsoft.com/fwlink/?LinkId=293415) for further help.


