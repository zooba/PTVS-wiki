# Cookiecutter

## About Cookiecutter

Cookiecutter is a utility that creates projects/files from templates.

The Cookiecutter extension for Visual Studio provides a graphical user interface to discover templates, input template options and create projects/files.

To learn more about Cookiecutter, using templates, or creating your own templates, see the [official Cookiecutter documentation](https://cookiecutter.readthedocs.io/en/latest/).

## Prerequisites

### Visual Studio 15 Preview 5

The Cookiecutter extension is included with Visual Studio 15. You can select it from the Python workload.

### Python interpreter

Cookiecutter works with Python 2.7, 3.3, 3.4, 3.5.

The Visual Studio 15 installer includes 32-bit and 64-bit distributions of CPython 2.7, CPython 3.5, Anaconda 2.7 and Anaconda 3.5. You can select them under the Data Science or Python workloads.

You can also download the latest CPython distributions from [python.org](https://www.python.org/downloads/windows/). 

**Important**: Restart Visual Studio after installing all the prerequisites.

### Cookiecutter python package

To install the python package into your python distribution, run the following command.

Note: You may need to run it in an elevated command prompt, depending on the options you've selected when you installed your python distribution.

```
pip install cookiecutter
```

If python isn't in your PATH, try the Python launcher instead:
```
py -m pip install cookiecutter
```

**Important**: Restart Visual Studio after installing all the prerequisites.

### Git

Cookiecutter uses the copy of git.exe that is included by default with Visual Studio 15, so there is no need to install a standalone release of git. If for some reason it can't find the git that comes with VS, it will try to find one in the PATH.

**Important**: Restart Visual Studio after installing all the prerequisites.

## Using Cookiecutter extension

To open the Cookiecutter window, go to View -> Other Windows -> Cookiecutter.

### Discover templates

The home page displays a list of templates to choose from.

- **Installed**: These are templates that have been installed to your local machine. When an online template is used, its repository is automatically cloned to a subfolder of `~/.cookiecutters`. You can delete a selected installed template by pressing **Del**.

- **Recommended**: These are templates loaded from the recommended feed. The default feed is curated by Microsoft. See the Cookiecutter Options section below for more information on customizing the feed.

- **GitHub**: These are GitHub search results for the cookiecutter keyword. Results from GitHub come back paginated, if more results are available, a 'Load More' will appear at the end of the list. Click on it retrieve the next page of results.

- **Custom**: When a custom location is entered in the search box, it will appear in this section. You can either type in a full path to the GitHub repository, or the full path to a folder on your local disk.

Once you've selected the template you want to use, click on **Next**. This will clone the template's repository to your local machine, if necessary, then it will load the template.

### Cloning

Cookiecutter templates that are located in a git repository online must be cloned to your local machine before they can be loaded by Cookiecutter.

If you select a template from the **Recommended** or **GitHub** sections, or if you enter a custom URL into the search box and select that template, it will be cloned/installed on your local machine. If that template was installed in a previous session of Visual Studio, it will automatically delete the installed template, and clone the latest version.

If you select a template from the **Installed** section, or if you enter a custom folder path into the search box and select that template, it will load the template from your local machine (no cloning).

**Limitation**: Cookiecutter templates are cloned/installed under a single folder `~/.cookiecutters`. Each subfolder is named after the git repository name, which does **not** include the GitHub user name. This can cause conflicts if you attempt to clone/install 2 different templates with the same name (for example, you'll find a few templates named `cookiecutter-flask`). When that happens, the tool will prevent you from overwriting your existing template with a different template of the same name. To confirm, delete the installed template with `Del` and try installing again.

### Output Location

After the template is loaded successfully, the view will change to a form where the first input field is **Create To**. This allows you to specify where your want Cookiecutter to generate files.

If you specify a folder that isn't empty, a warning message will pop up when you click **Create**.

If you are familiar with the template's output and are okay with it potentially overwriting files in your output folder, you can dismiss the warning. If not, you should cancel and select an empty folder, and manually copy the created files to your non-empty output folder.

### Template Options

Each Cookiecutter template defines its own set of options, and specifies a default value for each one. The default value is displayed in both tooltip and text box watermark.

Sometimes the default value may be a code snippet. This happens when an option's default value is calculated dynamically (often based on another option value). If you are okay with using the dynamic value, you can leave the text box empty.

It is possible to define user default values for specific options by using a user configuration file. When the Cookiecutter extension detects a user configuration file, it will overwrite the template's default values with the user config's default values. See the [official Cookiecutter documentation on User Config](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) to learn how to create your personal configuration file.

### Create

Click **Create** to launch Cookiecutter with the specified output folder and options.  Click **Cancel** to go back to the home page to select a different template.

After the files are created successfully, you will be prompted to open the files in **Solution Explorer - Folder View**.

## Cookiecutter Options

To see the options, go to Tools -> Options -> Cookiecutter.

### Recommended Feed URL

This is the location of the recommended templates feed. It can be a URL or a path to a local file. Leave the URL empty to use the default Microsoft curated feed.

The contents of the feed is a simple list of template locations, separated by newlines.

To request changes to the official feed, make a pull request against [the source on GitHub](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt)

### Show Help

This controls the visibility of the help information bar at the top of the Cookiecutter tool window.

## Troubleshooting

### Error loading template

Some templates may be using invalid data types, such as boolean, in their `cookiecutter.json`. This should be reported to the template author. Click on the **Issues** link in the template information pane.
