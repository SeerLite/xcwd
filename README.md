xcwd - X current working directory
==================================
xcwd is a simple tool which print the current working directory of the
currently focused window.
The main goal is to launch applications directly into the same directory
as the focused applications. This is especially useful if you want to open
a new terminal for debugging or compiling purpose.

How does it works
-----------------
Since there is no proper options to get the pid of the currently focused
windows,
xcwd first try to read the \_NET\_WM\_PID property. If it fails, it reads the
\_NET\_WM\_CLASS and compares it to the name of all the processes (it's kind of
`pidof name`).

When xcwd has got the PID, it search the deepest child he has, thus avoiding
getting the working directory of the terminal emulator instead of the shell.

Finally it prints the content of `/proc/pid/cwd` on the standard output.  If
xcwd was unable to find the PID, it prints the content of the HOME variable.

Requirements
------------
- libX11-dev

Running xwcd
------------
Simply invoke the 'xcwd' command.
You probably want to use it this way:
    ``urxvt -cd `xcwd` ``