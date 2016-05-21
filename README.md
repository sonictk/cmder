# Cmder

[![Join the chat at https://gitter.im/bliker/cmder](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/cmderdev/cmder?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

![Build Status](https://ci.appveyor.com/api/projects/status/32r7s2skrgm9ubva?retina=true)

Cmder is a **software package** created out of pure frustration over absence of usable console emulator on Windows. It is based on [ConEmu](https://conemu.github.io/) with *major* config overhaul, comes with a Monokai color scheme, amazing [clink](https://github.com/mridgers/clink) (further enhanced by [clink-completions](https://github.com/vladimir-kotikov/clink-completions)) and a custom prompt layout.

![Cmder Screenshot](http://i.imgur.com/g1nNf0I.png)

## Why use it

The main advantage of Cmder is portability. It is designed to be totally self-contained with no external dependencies, that is makes it great for **USB Sticks** or **cloud storage**. So you can carry your console, aliases and binaries (like wget, curl and git) with you anywhere.

## Installation

1. Download the [latest release](https://github.com/cmderdev/cmder/releases/)
2. Extract
3. (optional) Place your own executable files into the `bin` folder to be injected into your PATH.
4. Run Cmder

## Integration

So you've experimented with Cmder a little and want to give it a shot in a more permanent home;

### Shortcut to open Cmder in a chosen folder

1. Open a terminal as an Administrator
2. Navigate to the directory you have placed Cmder
3. Execute `.\cmder.exe /REGISTER ALL`
   _If you get a message "Access Denied" ensure you are executing the command in an **Administrator** prompt._

In a file explorer window right click in or on a directory to see "Cmder Here" in the context menu.

## Keyboard shortcuts

### Tab manipulation

* <kbd>Ctrl</kbd> + <kbd>T</kbd> : New tab dialog (maybe you want to open cmd as admin?)
* <kbd>Ctrl</kbd> + <kbd>W</kbd> : Close tab
* <kbd>Ctrl</kbd> + <kbd>D</kbd> : Close tab (if pressed on empty command)
* <kbd>Shift</kbd> + <kbd>Alt</kbd> + <kbd>#Number</kbd> : Fast new tab: <kbd>1</kbd> - CMD, <kbd>2</kbd> - PowerShell
* <kbd>Alt</kbd> + <kbd>Enter</kbd>: Fullscreen

### Shell

* <kbd>Shift</kbd> + <kbd>Up</kbd> : Traverse up in directory structure (lovely feature!)
* <kbd>End</kbd>, <kbd>Home</kbd>, <kbd>Ctrl</kbd> : Traversing text with as usual on Windows
* <kbd>Ctrl</kbd> + <kbd>R</kbd> : History search
* <kbd>Shift</kbd> + Mouse : Select and copy text from buffer

(Some shortcuts are not yet documented, thought they exist - please document them here)

## Features

### Access to multiple shells in one window using tabs
You can open multiple tabs each containing one of the following shells:

* Cmder | Cmder as Admin             - Enhanced Windows 'cmd.exe' shell.
* Powershell | Powershell as Admin   - Enhanced Windows Powershell.
* Bash/mintty | Bash/mintty as Admin - Unix/Linux like bash shell running on Windows.

Cmder, Powershell, and Bash tabs all run on top of the Windows Console API and work as you might expect in Cmder with access to use ConEmu's color schemes, key bindings and other settings defined in the ConEmu Settings dialog.

Mintty tabs use a program called 'mintty' as the terminal that is not based on the Windows Console API so some differences in functionality are normal, as a result mintty specific config is done via the '[%USERPROFILE%|$HOME]/.minttyrc' file.

Mintty differs from the other tabs in that it supports xterm/xterm-256color TERM types, and does not work with ConEmu settings like color schemes and key bindings. For more on Mintty and its config click [here](https://code.google.com/p/mintty/).

An example of setting Cmder portable terminal colors for mintty:

From a bash/mintty shell:

```
cd $CMDER_ROOT/vendor
git clone https://github.com/karlin/mintty-colors-solarized.git
cd mintty-colors-solarized/
echo source \$CMDER_ROOT/vendor/mintty-colors-solarized/mintty-solarized-dark.sh>>$CMDER_ROOT/config/user-cmder.sh
```

### Cmder Portable Shell User Config
User specific configuration is possible using the cmder specific shell config files.  Edit the below files to add your own configuration:

* Cmder       - %CMDER_ROOT%\config\user-startup.cmd
* Powershell  - $ENV:CMDER_ROOT\config\user-profile.ps1
* Bash/Mintty - $CMDER_ROOT/config/user-cmder.sh

Bash and Mintty sessions will also source the '$HOME/.bashrc' file it it exists before it sources '$CMDER_ROOT/config/user-cmder.sh'.

### Aliases
You can define simple aliases with command `alias name=command`.

For example there is one defined for you `alias e.=explorer .`

All aliases will be saved in `/config/aliases` file

### SSH Agent

To start SSH agent simply call `start-ssh-agent`, which is in the `vendor/git-for-windows/cmd` folder.

If you want to run SSH agent on startup, include the line `@call "%GIT_INSTALL_ROOT%/cmd/start-ssh-agent.cmd"` in `/config/user-startup.bat` (usually just uncomment it).

## Todo

1. Check for clink and git before injecting them (Sort of done)

## Current development branch

You can download builds of the current development branch by going to Appveyor via the following link:

[![AppVeyor](https://ci.appveyor.com/api/projects/status/github/cmderdev/cmder?svg=True)](https://ci.appveyor.com/project/MartiUK/cmder/branch/development/artifacts)

## License

All software included is bundled with own license

The MIT License (MIT)

Copyright (c) 2015 Samuel Vasko

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
