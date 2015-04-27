## Contributing to PTVS

So, you want to contribute to PTVS?  The very first step you'll need to take is [building PTVS for the first time](http://pytools.codeplex.com/wikipage?title=Build%20Instructions%20for%20PTVS). There's instructions on what you'll need to install, how to build, how to run and debug from within Visual Studio, and even how to create the installer which we ship with major releases.

From there you'll need to decide what you want to work on.  You might have an immediate idea of a feature you'd like to work on.  But if not the issue tracker has hundreds of active [features](https://github.com/Microsoft/PTVS/issues) as well as a number of open issues which you could either work on directly or which might inspire you with your own ideas.  

In general when the core PTVS team is working on a feature for a future release we'll assign it to that release. Unassigned issues are generally things we're not actively working on.  But if you're not sure, feel free to ask. And if you're planning a particularly large feature you should probably ask before hand.  Either we might have failed to update the issue or we might think you have a completely crazy idea.  Either way, we don't want you to feel like you wasted a bunch of effort.  We currently have more outstanding features than issues so you might want to look at finding a small feature to get started rather than fixing bugs unless you have a particular itch.  

Once you have an idea for what you want to work on you'll need to figure out how to actually go about doing that.  If what you're working on is clearly Python related you'll find the appropriate code in the Python\Product directory.  If the code is more sharable, such as the project system and interactive window, you'll find that in Common\Product.

Assuming you're looking in Python\Product at this point you'll find a decent number of reasonably named projects.  If you don't immediately see what you're looking for you'll probably want to look in PythonTools where the core of PTVS lives.  Inside of PythonTools lives another PythonTools folder which is again nicely organized by major features.

Hopefully that will at least give you an idea of where to look around.  But if you're still feeling lost please post questions to our discussion forms.  We'll be happy to answer your questions!

Once you've developed some code and are ready to contribute it back there's just a few basic guidelines:
All code has to be reviewed by gatekeepers 
All code contributions must come with tests. (We will give you help and advice on integrating into our test infrastructure if you need it.) 
Bug fixes will generally have a short review prior to acceptance 
For **new** functionality, please contact us first so we can coordinate efforts (e.g.  to avoid duplication of work, roadmap fit, etc.) 
Licensing: Since the PTVS is under the Apache 2.0 license, all contributions will be made under that license as well. Please don’t submit anything with any other licensing statements. If you want to make a contribution that includes code that you received under a different license, please let us know and we can figure out what to do. Please be sure that you have the right to make your contribution, including clearance from your employer if applicable. 