# Using Jupyter Notebooks

The files in the /notebooks folder are all interactive files called Jupyter Notebooks. You can read more about them and their uses [here](https://jupyter.org/).

## Installing dependencies

Some of the Notebooks have a requirement on other Python libraries being installed. It is recommended to use a virtual environment when installing Python dependencies. See [working-with-virtual-environments](working-with-virtual-environments.md) for more information.

1. Change into the "/notebooks" directory
2. If this is your first time using the notebooks, make a new virtual environment by running `python -m venv .venv`. Note: if you have difficulties with this command, check that you are using Python 3.3 or newer. See [working-with-virtual-environments](working-with-virtual-environments.md) for more information.
3. Activate this new virtual environment by running `source .venv/bin/activate`
4. Install the dependencies for the notebooks by running `pip install -r requirements.txt`
5. Running Python code within this virtual environment will use the dependencies locked within the virtual environment rather than whatever is at the system level.
6. To leave the virtual environment type `deactivate`.

## How to run a notebook

There are several ways that you can run and use the notebooks. This guide discusses two of them: running in a browser and running inside VSCode. If you have another preferred way of doing this, please add it to the list.

### In the browser

1. Change into the "/notebooks" directory.
2. Activate the virtual environment by running `source .venv/bin/activate`.
3. Start the Jupyter Notebook server by running `jupyter notebook`.
4. You should now see a browser open with a file listing of the current directory. If you don't see this then open your browser and visit [http://localhost:8888/tree](http://localhost:8888/tree).
5. Click on a notebook file to open it.
6. You can make and save changes to the notebook file and run them to execute code blocks. See the [Jupyter docs](https://jupyter-notebook.readthedocs.io/en/stable/) for more information on what's possible.
7. Hit Ctrl-C in the terminal to shutdown the Jupyter server.

### In VSCode

**IMPORTANT**: it is far easier to use the Notebooks inside of VSCode if you open VSCode in the "/notebooks" folder, rather than this top level one. This is so that VSCode will use the Jupyter Notebook specific virtual environment by default. If you discover a way to remove this friction, please let me know!

1. Ensure that you have followed the [Installing dependencies](#installing-dependencies) above.
2. Change into the "/notebooks" directory.
3. Run VSCode using the `code .` command (if you are on OSX you may have to install that command line tool first).
4. VSCode should automatically pick up the virtual environment and use it as the source of its Python and dependency root folder.
5. Jupyter Notebooks in VSCode have pretty much the same user interface as the browser version, so see the [Jupyter docs](https://jupyter-notebook.readthedocs.io/en/stable/) for more information on what's possible.
