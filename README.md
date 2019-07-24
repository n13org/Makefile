# Makefile

Makefile How-Tos and Tutorials. Simple examples and even some detailed workflows. Also this project covers some wrapper for common build and release tools in the DevOps environment.

The project is maintained by [n13.org](https://n13.org) - Open Source by [KargWare](http://kargware.com).

The command ```make``` calls targets from a [Makefile](https://en.wikipedia.org/wiki/Make_(software)). The Makefile should be placed on root-level, or can be refered by the parameter ```make -f```. The first target in the Makefile is the default target and will be executed, when make is called without target.

## Sections
|Topic (examples)|Description|
|----------------|-----------|
|[Hello Make](./HelloMake)|Examples to use make with a Makefile|
|[Print Versions](./PrintVersions)|Print version numbers of command line tools (cli)|
  
|Topic|Description|
|-----|-----------|
|[AppCenter](./AppCenter)|Microsoft [AppCenter](https://appcenter.ms)|

## Summary - Recap

### Links
* [MakeFile Tutorial](http://makefiletutorial.com/)
* [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/)

### Tools
* [JQ - JSON Query](https://stedolan.github.io/jq/)
* [Node.js](https://nodejs.org/en/)
* [NPM](https://www.npmjs.com/)

### Additional for Windows Systems without Linux subsystem
* [Gnu CoreUtils for Win32](http://gnuwin32.sourceforge.net/packages/coreutils.htm)  
* [Make for Windows](http://gnuwin32.sourceforge.net/packages/make.htm) 
1. Download and install Binaries
2. Add Path to the Gnu-Binaries to PATH (e.g. C:\Program Files (x86)\GnuWin32\bin)
