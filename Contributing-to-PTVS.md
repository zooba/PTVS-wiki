## Contributing to PTVS

So, you want to contribute to PTVS?  The very first step you'll need to take is [building PTVS for the first time](Build-Instructions-for-PTVS). There's instructions on what you'll need to install, how to build, how to run and debug from within Visual Studio, and even how to create the installer which we ship with major releases.

From there you'll need to decide what you want to work on. You might have an immediate idea of a feature you'd like to work on, but if not the issue tracker has hundreds of active [features](https://github.com/Microsoft/PTVS/issues) as well as a number of open issues which you could either work on directly or might inspire your own ideas.

We use the [help wanted](https://github.com/Microsoft/PTVS/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22) tag when we spot a feature or issue that could be a good way for someone to get started contributing. No promises that it will be an easy fix, but we'll be able to help point you in the right direction.

In general when the core PTVS team is working on a feature for a future release we'll assign it to that release. Unassigned issues are things we're not actively working on and not planning to get to in the near future. But if you're not sure, feel free to ask. And if you're planning a particularly large feature you should probably ask beforehand. Either we might have failed to update the issue or we might think you have a completely crazy idea. Either way, we don't want you to feel like you wasted a bunch of effort. We currently have more outstanding features than issues so you might want to look at finding a small feature to get started rather than fixing bugs unless you have a particular itch. 

Once you have an idea for what you want to work on you'll need to figure out how to actually go about doing that. Asking for guidance on the appropriate issue or in our [gitter.im](https://gitter.im/Microsoft/PTVS) room is the best way. We're more than happy

Once you've developed some code and are ready to contribute it back there's just a few basic guidelines:
* All code has to be reviewed by gatekeepers (us)
* Nearly all code contributions will require a [CLA](https://cla.microsoft.com/)
* All code contributions must come with tests. (We will give you help and advice on integrating into our test infrastructure if you need it.) 
* Bug fixes will generally have a short review prior to acceptance 
* Pull requests should have an associated issue or feature request

Licensing: Since the PTVS is under the Apache 2.0 license, all contributions will be made under that license as well. Please don’t submit anything with any other licensing statements. If you want to make a contribution that includes code that you received under a different license, please let us know and we can figure out what to do. Please be sure that you have the right to make your contribution, including clearance from your employer if applicable.
