# LibCrowds Project Documentation

The following document describes how to create and manage LibCrowds projects.
The focus here is on details specific to the LibCrowds platform, more general
information can be found within the
[PyBossa Docs](http://docs.pybossa.com/en/latest/build_with_pybossa.html).


## Project ownership

Each project is assigned an owner who will be responsible for its creation and
maintenance. Project owners have access to a dashboard, accessible
via the [Open Project](https://www.libcrowds.com/account/alexmendes/projects)
menu, which provides access to various settings and additional information
regarding the project, including:

- **Analysis:** A link to the results analysis application (see below).
- **Results:** To view the current results (useful for spot checking).
- **Statistics:** Contribution statistics for the project.


## Workflow

For specific details of the workflow established for your project, please see
the documentation available for each type of project on the
[LibCrowds GitHub page](https://github.com/LibCrowds?utf8=%E2%9C%93&query=project)
(e.g. [project-convert-a-card](https://github.com/LibCrowds/project-convert-a-card)).

Following is a general outline for all project types.


#### 1. Creating a new project

The easiest way to create a LibCrowds project is probably to use
[pybossa-github-builder](https://github.com/alexandermendes/pybossa-github-builder),
which is a plugin that automates much of the setup process. It also provides a way
to import templates for the new results and tutorial pages, via the web interface. 
The basic steps to create a new project using this plugin are as follows:

1. Visit the [Create Project from GitHub](http://www.libcrowds.com/github/new_project) page.
2. Search for a GitHub repository.
3. Configure the import and create a new project.
4. Import some tasks.
5. Set the task redundancy.
6. Publish.

Note that there are various other ways to create new projects, all of which are
described in the [PyBossa documentation](http://docs.pybossa.com/en/latest/user/overview.html).


#### 2. Analysing results

A separate application has been created to handle the analysis of results. The
analysis process is automated, as far as possible, according to the rules
defined for each category of project. Human intervention is only required for
any results that cannot be analysed automatically (e.g. different answers were
given for the task). A template is available for each category of project that
aims to make the process of checking these answers as straightforward as possible.

The **Analysis** menu option, available via the project dashboard, provides a
link to this application. A notification will appear next to this link showing
when there are results that need to be checked. A password is required to access the
application, which can be requested from a LibCrowds administrator.

Results can also be viewed via the **Results** menu option, also available via
the project dashboard. While nothing can be modified here, this view can be useful
for spot checking.


#### 3. Project completion

Once a project has been completed and all results analysed a CSV containing the
final results can be download from the
[LibCrowds Data page](https://www.libcrowds.com/data). The way in which this
spreadsheet will be used depends on the workflow established for your particular
project. For example, it might be checked and edited before being sent off to
metadata services for the creation of catalogue records.
