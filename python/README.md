# Python

## Package (Module) Management
Modules in python are packaged for distribution and `pip` is what manages them locally. It is both a command and a module. Though calling it as a module is preferred for consistency.
```pwsh
# verify module exists
python -m pip
# other commands and options
python -m pip --help
# upgrade pip with itself
python -m pip install -U pip
# install PyAudio module
python -m pip install pyaudio
```
These modules have multiple options on how they can be installed. The new hotness is a configuration in TOML, falling back to a `setup.py` file in the module package or using the `wheel` module. Considering this, it's helpful to install `wheel`.
```pwsh
python -m pip install wheel
```

## Virtual Environments
In situations where you may be using multiple versions of the same python module across projects, it's best to use a virtual environment for python. After activating the virtual environment the shell/terminal/command window will be modified so that running `python` will point to the copied one that was created, and any `pip install` operations will place files in the current virtual environment instead of user or system wide. This helps avoid conflicting versions or other nonsense.
```pwsh
# create the virtual environment
python -m venv venv
# the only argument that is passed is the name of the directory it places the environment into. "venv" is the common choice, but it could be anything specified.
python -m venv env
python -m venv pyenv
python -m venv .env
```
Browsing the content beneath the new directory should provide insight into what it did.

To activate the environment, source the appropriate script from the new directory:
```pwsh
# linux
source ./venv/bin/activate
# windows powershell
.\venv\Scripts\Activate.ps1
```

In powershell we can verify the activation by first noticing our prompt change to have `(venv)` in front of it. The source of the `python` command can also be compared before and after:
```pwsh
PS C:\angelichorsey> $(Get-Command python).Source
C:\Users\<user>\AppData\Local\Programs\Python\Python39\python.exe
PS C:\src\angelichorsey> .\venv\Scripts\Activate.ps1
(venv) PS C:\src\angelichorsey> $(Get-Command python).Source
C:\src\angelichorsey\venv\Scripts\python.exe
```
