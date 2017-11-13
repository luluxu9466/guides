# Python setup
This is a short guide for inital python setup on a new computer, using Atom as an IDE.

Note that this is the first time I have used this setup, so it is far from guaranteed to have good performance and workflow.

This guide assumes you are running macOS (I am running 10.13.1 specifically), with no existing installs of python other than the system one.

## pyenv
Because different toolboxes will rely on either python2 or python3, it is a good idea to be able to switch between these two in an easy way. [`pyenv`](https://github.com/pyenv/pyenv) allows for this by managing different python installations, and setting them as the global default, or locally for specific projects.

1. Using the terminal, install the package manager `Homebrew`: `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
2. Install `pyenv`: `brew install pyenv`
3. Add `pyenv init` to your bash_profile: `echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bash_profile`
4. Restart the shell: `$ exec "$SHELL"`

## python
With `pyenv` we can now install as many different versions of python as we might need. Type `pyenv install -l` for a list of all available versions.

In the first instance, I would recommend having an install of each of python2 (which is needed for psychopy and nypype) and python3 (which is needed for newer toolboxes). I would also recommend a distribution package like anaconda, which will have many of the scientific modules pre-installed.

1. To install a given version: `pyenv install anaconda2-5.0.0`
2. To check which versions are installed: `pyenv versions`
3. To uninstall: `pyenv uninstall anaconda2-5.0.0`
4. To set the globally used version: `pyenv global anaconda2-5.0.0`

## IPython kernels
We now want to install kernels for each of your installed python versions so that we can run code interactively using Atom (below). This basically uses the same system as IPython/Jupyter notebooks that you may be familiar with.

For each version of python that you wish to install a kernel for:  
1. Switch to that version using `pyenv`
2. Run `python2 -m pip install ipykernel`
3. Run `python2 -m ipykernel install --user`
Replacing `python2` with `python3` if that is the version you want. 

## Atom
Let's use the [Atom](https://atom.io) text editor as an IDE, which is highly configurable. We can run code in the editor by installing a package called [Hydrogen](https://www.gitbook.com/book/nteract/hydrogen/details) pointing it to an installed kernel. This applies to any language that we have a kernel for, so this can be used for languages other than python!

1. [Install Atom](https://atom.io)
2. Go to the package manager, and install Hydrogen (or in the terminal: `apm install hydrogen`).

We may also want some other useful packages, for example:
- language-matlab
- language-r
- psychopy (this can only launch full scripts)
- hydrogen-launcher (which brings up a command line)
There are also autocomplete and formatting packages that help you follow [PEP8](https://www.python.org/dev/peps/pep-0008/) formatting if desired. These can all be installed as above or with the command `apm install`.

Atom allows you to use commands from different packages by pressing <kbd>⌘</kbd> <kbd>⇧</kbd> <kbd>P</kbd>. If you press this you can search for a command called 'Hydrogen: Update Kernel' which should now show the kernels for each version of python you have installed.

If you have a python script, you should now be able to run this using 'Hydrogen: Run' and selecting the version of python you wish to use for this script. Results will be displayed in-line, including plots.

You will also see the kernels status in the bottom left of the screen. You can click here to interupt or restart the kernel if necessary.

## Some useful shortcuts
- Run line/selection: <kbd>⌘</kbd> <kbd>⏎</kbd>
- Run line and move down: <kbd>⇧</kbd> <kbd>⏎</kbd>
- Run all: <kbd>⌃</kbd> <kbd>⌘</kbd> <kbd>⏎</kbd>
- Run cell: <kbd>⌥</kbd> <kbd>⌘</kbd> <kbd>⏎</kbd> 
