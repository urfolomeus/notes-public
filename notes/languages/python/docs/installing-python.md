# Installing Python

This guide has instructions for installing Python on your computer. I currently only have notes for Linux as that's my main OS right now. I aim to add install notes for Windows soon as I need to be able to do that for client work.

This guide only shows one of many possible ways to install Python on your computer. You may prefer another way. Feel free to add it here as an alternative if you think others would benefit from the choice.

## Linux

**CAVEAT**: Be careful when dealing with Python on Linux machines. You can really screw up your install if you manage to muck with the system Python version/interpreter. I managed this once before but am not entirely clear on how I managed it. So far I have found the following to be good practice:

1. Use a version manager to ensure that you are able to work with different Python version without affecting the system Python install.
2. If your version manager allows it, pin a python version installed via the version manager as your "global" version, i.e. the one that will be used by default if you are not in a project (sub)folder that overrides it.
3. [optional] Install the majority of your Python libs locally to the project that uses them and use a virtual environment to keep these packages separate from the system or global packages. This has the advantage of ensuring that projects are encapsulated and not influenced by one another, whilst having the disadvantage that you will have some libs installed multiple times on your machine at the same version. FWIW virtualenvs seem to be the Pythonic way to handle dependencies.

### Ubuntu-based

My current distro of choice is [Pop!\_OS](https://pop.system76.com/). The following worked on that OS last time I installed Python.

I used to use [pyenv](https://github.com/pyenv/pyenv) to manage my Python versions, but more recently have moved to [asdf](https://asdf-vm.com/#/) so that I'm only using one version manager for all the languages/tools that I use.

- Install pre-requisite libs
  ```bash
  sudo apt update && sudo apt install --no-install-recommends make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
  ```
- Install the asdf Python plugin
  ```bash
  asdf plugin add python
  ```
- Install the desired version of Python
  ```bash
  asdf install python <version>
  ```
- Set your global python to be the desired version
  ```bash
  asdf global python <version>
  ```

**NOTE**: sometimes there will be packages that you will want to add globally so that they are available to applications such as your code editor. For example, having a global install of `black` and `flake8` enable your editor to easily find the binaries for formatting/linting. To install these globally use `pip` when you are not in a folder structure that contains a project-specific virtual environment.

```bash
// [OPTIONAL] make sure that we are using the latest version of pip
pip install --upgrade pip
pip install black flake8
```

**Further note**: if you are using asdf you will need to ensure that global package (installed as just mentioned above) have been added to the shims so that you can call them from the command line. You can do this by running:

```bash
asdf reshim python
// check that this has worked, the output should be `~/.asdf/shims/<black|flake8>`
which black
which flake8
```
