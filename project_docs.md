# LibCrowds Project Documentation

The following document describes how to create and manage LibCrowds projects.
The focus here is on details specific to the LibCrowds platform, more general
information can be found within the
[PyBossa Docs](http://docs.pybossa.com/en/latest/build_with_pybossa.html).


## Project ownership

Each project is assigned an owner who will be responsible for creating and
maintaining that project. Project owners have access to a dashboard, accessible
via the **Open project** menu option, or the project portal page. The
dashboard provides access to various settings and additional pages for the
project, including:

- **Analysis:** A link to the results analysis application (see below).
- **Results:** View the current results, which can be useful for spot checking.
- **Statistics:** View contribution statistics.


## Creating a new project

The easiest way to create LibCrowds projects is probably to use
[pybossa-github-builder](https://github.com/alexandermendes/pybossa-github-builder),
which is a plugin that automates much of the setup process. The steps to create
a new project using this plugin are as follows:

1. **Sign in** to LibCrowds.
2. Visit [http://www.libcrowds.com/github/new_project](http://www.libcrowds.com/github/new_project).
3. Fill in the form and click **Create**. The GitHub URL for your project can be found on the
[LibCrowds GitHub organisation page](https://github.com/LibCrowds)
(e.g. [https://github.com/LibCrowds/project-convert-a-card](https://github.com/LibCrowds/project-convert-a-card)).
6. From the **Project Dashboard**, click **Import Tasks** and choose the relevant importer (e.g. Flickr).
7. From the **Project Dashboard**, click **Publish**.

Note that there are various ways to create new projects, all of which are described in the
[PyBossa documentation](http://docs.pybossa.com/en/latest/user/overview.html).


## Analysing results

A seperate application has been create to handle the analysis of results. The
analysis process is automated, as far as possible, according to the rules
defined for each category of project (which happens during the development
stage).

Human intervention is only required for any results that cannot be analysed
automatically (e.g. those that contributed to the task all gave different answers).
A template is available for each category of project that aims to make the process
of checking answers as straightforward as possible.

The **Analysis** menu option, available via the project dashboard, provides a
link to this application. Next to the same link, a notification will appear when
there are results that need to be checked. A password is required to access the
application, which can be requested from a LibCrowds administrator.


## Project completion

Once a project has been completed and all results analysed a CSV containing the
final results can be download from the
[LibCrowds Data page](https://www.libcrowds.com/data). The way in which this
spreadsheet will be used depends on the workflow established for your particular
project. For example, it might be checked and edited before being sent off to
metadata services for the creation of catalogue records.
