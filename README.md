# Boston Dynamics Spot Python Development Environment

Documentation about setting up and using a Python 3.7 development environment for Boston Dynamics Spot development on macOS.

## Helpful Notes

### Viewing Hidden (.) Files and Directories in macOS

open the Finder and press Command Shift .

That is used to toggle between showing and not showing hidden files.

### Displaying Intellisense Options in VSCode

For displaying intellisense options in, say, creating a launch.json file use *ctrl space*.

## Python Installation on macOS

The current (as of Nov 2021) Boston Dynamics Spot documentation states that only Python 3.6 and 3.7 are supported. The current version of Python, as of writing this, is 3.10.

<https://www.python.org/downloads/>

"3.7.9 was the last release to provide binary installers for Windows and macOS."

The downloads for macOS are at <https://www.python.org/downloads/macos/>.

Download the macOS 64-bit installer for Python 3.7.9 - Aug. 17, 2020 and install it.

At the end of the installation it states:

>One more thing: to verify the identity of secure network connections, this Python needs a set of SSL root certificates. You can download and install a current curated set from the Certifi project by double-clicking on the Install Certificates icon in the Finder window. See the ReadMe file for more information.

In the *Applications > Python 3.7* directory double-click on *Install Certificates.command* to launch it and install the certificates.

*pip* is installed with Python, but it may not be up-to-date. If you get messages that pip is not up-to-date, run the provided command with the message to do the update.

>/Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7 -m pip install --upgrade pip

Note that the above shows the location for the installation of python3.7: /Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7

The path to python3.7 is needed to create virtual environments based on that python.

## Install Virtual Environment Software for Python

There are multiple ways to do python virtual environments. The Boston Dynamics documentation (<https://dev.bostondynamics.com/docs/python/quickstart>) uses *virtualenv*. *venv* is another alternative that is usually part of the standard python library. This documentation uses *virtualenv*.

### Difference Between virtualenv and venv

>venv is a package shipped with Python 3, which you can run using python3 -m venv (although for some reason some distros separate it out into a separate distro package, such as python3-venv on Ubuntu/Debian). It serves the same purpose as virtualenv, **but only has a subset of its features**... virtualenv continues to be more popular than venv, especially since the former supports both Python 2 and 3.

### How to Install virtualenv

*pip* is used to install *virtualenv*. To make sure you are running the *pip* that goes with the python3.7 install, run *pip* using the python3.7. Unless you have set a path to make running *python3* use python3.7, the fully qualified path to python3.7 needs to be used.

*/Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7* is the path to run python3.7. The following command installs *virtualenv* for python3.7.

>/Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7 -m pip install virtualenv

### Setting Up the Project Folder and Virtual Environmentt

1. Create a folder for the project. For the purposes of this documentation "spotdev" is used. Replace "spotdev" with the folder you want to use.

2. Inside the project folder ("spotdev"), create a virtual environment with the name of ".venv".

To make sure that the python3.7 is used to create the virtual environment, the fully qualified path to it is specified.

Be inside the project folder ("spotdev") and execute the follwing.

>/Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7 -m virtualenv .venv

Putting the virtual environment in *.venv* inside of the project folder enables Visual Studio Code to automatically recognize the virtual environment. The virtual environment folder is inside the project folder rather than the project folder being inside the virtual environment folder. Once you activate a virtual environment, you can go anywhere in the file system to work while being in that virtual environment that was activated.

3. Activate the virtual environment and install the Boston Dynamics packages.

Activate the virtual environment. The assumption below is that the current directory is the project folder ("spotdev").

>source ./.venv/bin/activate

Install the Boston Dynamics packages in the virtual environment.

>python3 -m pip install --upgrade bosdyn-client bosdyn-mission bosdyn-choreography-client

Note: python3 is used here and not the fullied qualified path, because we are now using the python3 in the activated virtual environment.

4. Put the Spot SDK in the project folder ("spotdev").

Unzip the spot_sdk_v3.0.1.zip inside the project folder ("spotdev").

At the commandline, you can unzip using unzip.

>unzip spot_sdk_v3.0.1.zip

5. Launch Visual Studio Code to Work with Examples in SDK

Navigate to the examples directory in the SDK using a Terminal. Go to:

>cd spot-sdk-3.0.1/python/examples

Then launch Visual Studio Code using:

>code .

Once Visual Studio Code launches the working directory should be examples and the folders for the examples should be listed.

If you open a Terminal in Visual Studio Code, the current directory should be *examples*.

6. Create a *launch.json* file to set the parameters needed by the examples such as username, password, and hostname.

In Visual Studio Code, click on the Run and Debug button on the left toolbar.

Click on the "create a launch.json file" link that is presented under Run and Debug.

In the lower right the following is displayed.

>Unable to open 'launch.json': Unable to read file '/Users/dalemusser/Documents/spotdev/spot-sdk-3.0.1/python/examples/.vscode/launch.json' (Error: Unable to resolve nonexistent file '/Users/dalemusser/Documents/spotdev/spot-sdk-3.0.1/python/examples/.vscode/launch.json').

Below that message click the Create File button.

In the launch.json file that is created (in examples), put the following and save the file then close it. Note that you have to put your own username, password, and hostname in the contents.

```
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
            "args": ["--username=<username>", "--password=<password>", "<hostname>"]
        }
    ]
}
```

7. Run and use Visual Studio Code.

Run Visual Studio Code with examples as the Current Directory. Go to an example, such as estop, and select the python program, such as estop_nogiu.py, and then go to the Run menu in Visual Studio Code and select Start Debugging.

When/if Visual Studio Code asks for the Python interpreter, provide it with the following.

>~Documents/spotdev/.venv/bin/python3

The ~Documents/spotdev is where you have your project folder. The path must be fully-qualified.

When the python program is run, it may pop up "Select a debug configuration".  If so, select "Python File Debug the currently active Python file".

When the python program is running the Terminal prompt should be preceded with (.venv) to show the virtual environment is active.









