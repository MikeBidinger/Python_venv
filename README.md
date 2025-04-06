# `venv`

The `venv` module supports creating lightweight “virtual environments”, each with their own independent set of Python packages installed in their [site](https://docs.python.org/3/library/site.html#module-site) directories.
A virtual environment is created on top of an existing Python installation, known as the virtual environment’s “base” Python, and may optionally be isolated from the packages in the base environment, so only those explicitly installed in the virtual environment are available.

When used from within a virtual environment, common installation tools such as [pip](https://pypi.org/project/pip/) will install Python packages into a virtual environment without needing to be told to do so explicitly.

For more detailed information, see the documentation: [venv](https://docs.python.org/3/library/venv.html)

## Creating Virtual Environments

Virtual environments are created by executing the `venv` module in the CLI (make sure that your located within the correct directory, use the command `cd` to do so):

-   MacOS:

```bash
python3 -m venv <name_of_virtual_environment>
```

-   Windows:

```cmd
python -m venv C:\path\to\new\virtual\environment
```

This creates the target directory (including parent directories as needed) and places a `pyvenv.cfg` file in it with a `home` key pointing to the Python installation from which the command was run.
It also creates a `bin` (or `Scripts` on Windows) subdirectory containing a copy or symlink of the Python executable (as appropriate for the platform or arguments used at environment creation time).
It also creates a `lib/pythonX.Y/site-packages` subdirectory (on Windows, this is `Libsite-packages`).
If an existing directory is specified, it will be re-used.

## Activate Virtual Environments

A virtual environment may be “activated” using a script in its binary directory (bin on POSIX; Scripts on Windows). This will prepend that directory to your PATH, so that running python will invoke the environment’s Python interpreter and you can run installed scripts without having to use their full path. The invocation of the activation script is platform-specific (<venv> must be replaced by the path to the directory containing the virtual environment):

-   POSIX:

    | Shell    | Command to activate virtual environment |
    | -------- | --------------------------------------- |
    | bash/zsh | `$ source <venv>/bin/activate`          |
    | fish     | `$ source <venv>/bin/activate.fish`     |
    | csh/tcsh | `$ source <venv>/bin/activate.csh`      |
    | pwsh     | `$ <venv>/bin/Activate.ps1`             |

-   Windows:

    | Shell      | Command to activate virtual environment |
    | ---------- | --------------------------------------- |
    | cmd.exe    | `C:\> <venv>\Scripts\activate.bat`      |
    | PowerShell | `PS C:\> <venv>\Scripts\Activate.ps1`   |

## Installing Packages

To use Python packages that are not supplied by default for the installation of a Python version, we can use `pip` to install them.
Use the following command, after you activated the virtual environment, to install a specific package (can also be executed without version):

```bash
pip install <package>==1.3.2
```

### `requirements.txt`

To simplify the installation of the required packages, using a `requirements.txt` file can be very useful.
This file should contain all the packages that are required to be installed within the virtual environment.
The structure of the file should be as follows (or excluding versions):

```text
ollama==0.4.7
streamlit==1.41.1
```

Using the following command the environment's `pip` will install the packages:

-   MacOS:

```bash
pip3 install -r requirements.txt
```

-   Windows:

```cmd
pip install -r requirements.txt
```

## Deactivate Virtual Environments

When a virtual environment is activated the following command can be executed to deactivate the current active virtual environment:

```bash
deactivate
```

## Anaconda

For more detailed information, see [Python_Anaconda](https://github.com/MikeBidinger/Python_Anaconda).

### Deactivate Anaconda Base

```bash
conda config --set auto_activate_base false
```

### Activate Anaconda Base

```bash
conda config --set auto_activate_base true
```
