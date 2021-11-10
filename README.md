# Boston Dynamics Spot Python Development Environment

Documentation about setting up and using a Python development environment for Boston Dynamics Spot development.

## Viewing Hidden (.) Files and Directories in macOS

open the Finder and press Command Shift .

## Displaying Intellisense Options in VSCode

For displaying intellisense options in, say, creating a launch.json file use *ctrl space*.

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

There are multiple ways to do python virtual environments. The Boston Dynamics documentation (<https://dev.bostondynamics.com/docs/python/quickstart>) uses *virtualenv*. *env* is another alternative that is usually part of the standard python library. This documentation uses *virtualenv*.

### Difference Between virtualenv and venv

>venv is a package shipped with Python 3, which you can run using python3 -m venv (although for some reason some distros separate it out into a separate distro package, such as python3-venv on Ubuntu/Debian). It serves the same purpose as virtualenv, **but only has a subset of its features** (see a comparison here). virtualenv continues to be more popular than venv, especially since the former supports both Python 2 and 3.

### How to Install virtualenv

*pip* is used to install *virtualenv*. To make sure you are running the *pip* that goes with the python3.7 install, run *pip* using the python3.7. Unless you have set a path to make running *python3* use python3.7, the fully qualified path to python3.7 needs to be used.

*/Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7* is the path to run python3.7. The following command installs *virtualenv* for python3.7.

>/Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7 -m pip install virtualenv

### Setting Up the Project Folder and Virtual Environmentt

1. Create a folder for the project.

### Creating launch.json in examples

{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "spot",
            "type": "python",
            "request": "launch",
            "program": "${file}",
            "console": "integratedTerminal",
            "args": ["--username=dale", "--password=pleaseletmein", "74.93.9.252"]
        }
    ]
}









