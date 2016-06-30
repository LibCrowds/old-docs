# LibCrowds Development Documentation

The following document aims to provide a few guidelines for future development
and maintenance. This document is probably best consulted after becoming
familiar with the main [PyBossa Documentation](http://docs.pybossa.com/en/latest/).


## Developing a new project

The suggested workflow for developing a new project is:

- Create a new GitHub repository.
    - The convention is to name these *project-{project-category}.*
- Clone this repository and add the following files:
    - **project.json:** A JSON file containing project metadata.
    - **template.html:** The task presenter via which contributions will be made.
    - **long_description.md:** A Markdown file containing a long description for the project.
    - **results.html:** A page for checking the results for the project.
    - **tutorial.html:** A tutorial for the project.
    - **README.md:** A document containing a detailed workflow for the project
    - **thumbnail.png:** A thumbnail image for the project.
- The project.json file should contain the following keys:
    - **name:** The name of the project.
    - **short_name:** An identifier used for filenames and URLs.
    - **description**: A short description for the project.
    - **webhook**: A webhook used to trigger results analysis, always enter https://analyse.libcrowds.com.
    - **category_id**: The ID for the project's category (see https://www.libcrowds.com/api/category).
    - **splash**: A splash image for the project's portal page.
    - **splash_attribution**: Any attribution required for the splash image.
    - **tutorial_video**: A link to an embeddable tutorial video (e.g. from Flickr).
- Add an analyser for the category to [libcrowds-analyst](https://github.com/LibCrowds/libcrowds-analyst).


## Updating the server

Before updating the server, tests for all plugins should be run against the latest
PyBossa version in your development environment.

To update PyBossa run:

```
git pull origin master
pip install -U pip
pip install -U -r requirements.txt
alembic upgrade head
```

Sometimes changes are made that will also require
[pybossa.js](https://github.com/PyBossa/pybossa.js) to be updated, so the LibCrowds theme
should also be updated on the server by running:

```
git submodule foreach git pull origin master
```

To update any plugins just remove the previous version from the pybossa plugins
directory, then follow the installation instructions for that plugin.

To update libcrowds-analyst run:

```
git pull origin master
pip install -U pip
pip install -U -r requirements.txt
```

Any changes will take effect after you next restart the server.
