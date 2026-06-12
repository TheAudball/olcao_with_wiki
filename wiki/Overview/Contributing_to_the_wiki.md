## Contributing

#### Overview

Thank you for your interest in improving the quality of this wiki! To contribute to the wiki, please fork [repo/branch] and navigate to the wiki/ directory. The wiki/ directory is where a file tree describing the desired structure of the wiki lives. Every wiki page is a .md file using github-flavored markdown, and the directory that each page lives in is where it should exist in the overall structure and will be compile as such in the sidebar. 

Once you have made your edits, additions, and removals commit them and initiate a pull request. The current maintainer will review your changes and pull as normal. Upon acceptance, it will automatically run any compilation files and push to the wiki page of [repo]. See below sections for further information on the automation structure.

#### Conventions

There are a couple of conventions to follow when contributing to the wiki so that your contributions will be properly displayed when being compiled by certain automation scripts, primarily CompileSidebar.py.

**Conventions:**
* Any spaces in the file name can be replaced with \_. There is no method by which to explicity include an \_ in a file or directory name at the moment
* The topmost directories in wiki/* are treated as section headers. Their title level can be set in [options.py](#options.py).
* The side bar is compiled as a tiered list. Ordered or unordered. Each subdirectory will increase the indent of all pages inside it by one.
* A directory can still link to an associated page, just include a .md file with the same name as the directory ([\$directoryName].md) it is in  and the line item corresponding to that directory will link to that .md file.
* Automation scripts follow their own list of conventions found [here](#Adding your own automation scripts)
* Any files placed directly in the wiki/ directory will not be linked to in the sidebar. It is recommended you place files with unique purposes here, such as Home.md and \_Sidebar.md.

## Automation Scripts

#### Overview

The purpose of these scripts is to ease the burden of updating and maintaining the wiki. For pages that contain information that may change often, such as the sidebar, it is recommended you create an automation script that can do the repetitive task of updating everything for you. The primary example of this is seen in the CompileSidebar.py module: every time a page is added, removed, or renamed the sidebar needs to be changed. Thus, CompileSidebar.py and its auxillary tools MarkdownTools.py and DirectoryStructure.py will re-read the entire wiki/ directory and construct the \_Sidebar.md file for you, so you do not have to update it.

Currently Automated tasks: 
* Sidebar creation (CompileSidebar.py)
* Script Catalog (CompileCatalog.py)

#### options.py

options.py is a required file that is automatically added to every subdirectory after push. It contains a pythong dict with a few options, with the default values set in DirectoryStructure.py (this is also the script that adds the options.py file). If you want to add an option for your own compilation script, you should add it to the default dict in DirectoryStructure.py. That way it will propogate to every already existing options.py automatically. Additionally, please update the list of options on this page manually.

| Option    | Accepted values   | Description |
|:---------:|:-----------------:|:-----------:|
|dropdown   |boolean            |If true, this directory will be a dropdown menu in the sidebar. Otherwise it will be compiled as a normal tiered list|
|ordered    |boolean            |If true, then the sub items in this directory will be ordered according to the **order** list|
|order      |list of strings    |The list entries should be the directory or file name of a directory or file in the directory where the options.py is. '*' is a wildcard which will place every unlisted item in the directory at the location. Order is important, determines the order of the subitems under this in the sidebar. Only matters if **ordered** is set to True. If an item is listed in this order but neither a .md file or directory with the name is in the directory, the entry is skipped.|
|title_level|integer            |Sets the title level (number of #) of a directory in wiki/*. Not subdirectories below that will have a title level so it is unused in those cases|

#### Adding your own automation scripts

If you have a page that you wish to automate you need to do a few things:
1. Write a python script whose name follows the Compile*.py convention. The github action will always pass the following two arguments into every script which are defined in the .yml file: 
    * Repo Name
    * wiki directory root path
1. Place it in the scripts directory so the action can find it. This is also defined in the .yml file, and for UMKC-CPG/olcao is wiki_scripts/
1. If you need to create any other helper scripts that are not meant to be directly run, they should NOT follow the Compile*.py convention, and must also be placed in the wiki_scripts directory so that the compilation script can load it when run.

Once you have created the necessary files in the correct locations, you should be able to push to the repo and it will automatically run. If you wish, you may also update this page to reflect the current automation state.

