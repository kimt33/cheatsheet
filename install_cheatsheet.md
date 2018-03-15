
Installation Cheatsheet
=============================

General Tips
--------------
* Try not to use too many different package managers. They tend to not play well with each other.
  * Use one or two package managers.

* If you are going to be juggling different versions of python, use virtual environments.
  * Virtual environments are available in conda.
  
* Try not to give `sudo` to package managers.
  * Use `sudo` for one package manager (usually the package manager for your OS).
  * Use reputable package managers.
  * This also applies when you are building/compiling things.
  
* Try to install locally.
  * Unless you are a system manager (which hopefully means that you know what you're doing), you
    have no need to install things system wide.
  * It is much easier to find and fix problems if you stay local. Worse case, we make a new user.
  * It is **very much harder** to find and fix problems if your system is screwed up. Worse case, we
    reinstall the OS (this is the "easy" fix).
  * This also applies when you are building/compiling things.
  
* Try not to use environment variables, such as `PYTHONPATH`, especially in your bashrc.
  * This causes some problems if you use more than one version of python.
  * Use the `setup.py`.
  * Use virtual environments.
  * Use the `.local` directory.

Local Installation
----------------------
* Local installation often means that you are installing to your `.local` in your home directory.

* `.local/bin` contains your installed executables.

* `.local/lib` contains your installed codes. These can be compiled (especially if code requires
  compilation).

* `.local/share` contains your code-specific data.

* `.local/lib/python_version/site-packages/` contains your installed python packages.

* To delete a package, you just need to go through these directories (especially the `.local/lib`)
  and delete the files that correspond to this package.

  * Use your package manager to delete packages.

Pip
----
* Install package (`package`) from PyPI repository
```bash
pip install --user package
```

* Install package in a specific directory (`path`) with `setup.py`
```bash
pip install path
```
  * Note that just `path` was used and not `path/setup.py`.

* Installing a package through pip results in **copying** the provided package to your
  `.local/lib/python_version/site-packages/` directory.
  
* If the package you are installing is in development (e.g. git repository), then use
```bash
pip install path -e
```

  * You can technically use `pip install path`, but this would require you to reinstall your package
    everytime your code is changed.
  
* Each pip is specific to a version of python.

  * If you have more than one version of python, you will need to have more than one pip.
  * Your system package manager may not handle different versions of pip very nicely.
  * Use virtual environment (conda) if you have more than one version of python.

Conda
------

Installation

* Try to install miniconda (rather than anaconda).

  * Miniconda contains the minimum necessary for normal python packages (by default). If you plan on
    installing packages and having multiple environments, miniconda will be easier to manage.
  * Anaconda contains a lot of the python packages (by default). If you never plan on updating
    anything and just want to have a stable python without ever having to worry about installation,
    anaconda is *usually* alright.

* Do not let conda write to your bashrc.

  * This will overwrite your default python to that of conda.
  * Try not to use package manager to install conda. Download the installation script from the 
    website.

Environments

* Each environment is a (hopefully) an isolated platform from which you can develop your code.

  * Paths are set up such that priority is given to the packages installed in your environment 

* Activate root conda environment
```bash
source ~/miniconda3/bin/activate
```
  
  * You would only need to do this to create your first environment

* Create your environment (e.g. `myenv`)
```bash
conda create -n myenv python=3.6
```

* Activate your conda environment (`myenv`)
```bash
source ~/miniconda3/bin/activate myenv
```

* You can create an alias to make activation faster
```bash
alias activate='source ~/miniconda3/bin/activate'
```

  * You can put this in your `.bashrc`

Package Management

* Install package (e.g. `package`) from anaconda repo
```bash
conda install package
```

* Install package from specific repo (e.g. `other_repo`)
```bash
conda install package -c other_repo
```

  * Try to use reputable repos (e.g. conda-forge)kjkj
