# spot-python-dev-environ

Documentation about setting up and using a Python development environment for Boston Dynamics Spot development.


## Python Installation on macOS

The current (as of Nov 2021) Boston Dynamics Spot documentation states that only Python 3.6 and 3.7 are supported. The current version of Python, as of writing this, is 3.10.

<https://www.python.org/downloads/>

"3.7.9 was the last release to provide binary installers for Windows and macOS."

The downloads for macOS are at <https://www.python.org/downloads/macos/>.

Download the macOS 64-bit installer for Python 3.7.9 - Aug. 17, 2020 and install it.

At the end of the installation it states:

>One more thing: to verify the identity of secure network connections, this Python needs a set of SSL root certificates. You can download and install a current curated set from the Certifi project by double-clicking on the Install Certificates icon in the Finder window.  ee the ReadMe file for more information.

In the *Applications > Python 3.7* directory double-click on *Install Certificates.command* to launch it and install the certificates.

*pip* is installed with Python, but it may not be up-to-date. If you get messages that pip is not up-to-date, run the provided command with the message to do the update.

>/Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7 -m pip install --upgrade pip

Note that the above shows the location for the installation of python3.7: /Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7

The path to python3.7 is needed to create virtual environments based on that python.

## Install Virtual Environemnt Software for Python

There are multiple ways to do python virtual environments. The Boston Dynamics documentation (<https://dev.bostondynamics.com/docs/python/quickstart>) uses *virtualenv*. For the purposes of working with VSCode and doing debugging, I found that I needed to use *venv*.

### How to Install virtualenv

*pip* is used to install *virtualenv*. To make sure you are running the *pip* that goes with the python3.7 install, run *pip* using the python3.7. Unless you have set a path to make running *python3* use python3.7, the fully qualified path to python3.7 needs to be used.

*/Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7* is the path to run python3.7. The following command installs *virtualenv* for python3.7.

>/Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7 -m pip install virtualenv

### How to Install venv





