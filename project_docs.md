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

The code for the LibCrowds projects can be found via the
[LibCrowds GitHub organisation page](https://github.com/LibCrowds). There are
various ways to create a new project, such as via the web interface, the API
or the command line, all of which are described further in the
[PyBossa documentation](http://docs.pybossa.com/en/latest/user/overview.html).

A third way is to import the project directly from GitHub, using the following
method:

1.
2.
3.
4.
5.



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
