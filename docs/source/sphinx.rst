How to build the documentation
==================================

Getting started:
https://www.sphinx-doc.org/en/master/tutorial/getting-started.html

The idea behind Sphinx is to write documents in the rst format and build the docs into the html format.
After changes just push to the repository and the documents will be updated.
The repository can be found here: https://github.com/visualisationlab/visualisationlab

Initialize the virtual environment (.venv or another name)
::
    python -m venv .venv
    $ source .venv/bin/activate
    (.venv) $ python -m pip install sphinx
    (.venv) $ python -m pip install sphinx_rtd_theme

to build the documents:
::
    sphinx-build -b html docs/source/ docs/build/html/John W. Romein

Or:
::
    make html

When changing the documentation structure (adding or removing files) the make clean command should be used to remove the old build files.

::
    make clean

To view the built documents open the index.html file in the build/html folder.

RST cheatsheet:
https://bashtage.github.io/sphinx-material/rst-cheatsheet/rst-cheatsheet.html
