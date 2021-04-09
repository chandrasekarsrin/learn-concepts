# MAC:

## /bin
There are these 2 paths where the executables can be:
/bin : for key programs like /bin/sh, /bin/bash, /bin/ls, etc..
/sbin. : system managment programs like mount. not used by normal users
/usr/bin. : os provided executables. (for example python2 comes by default from Mac)
/usr/local/bin: user provided can gracefully be overridden (can be overridden)

## /usr/libexec
- generally are read only.
- not intended for direct use by users
- often some internal implementation details
- one example is: /usr/libexec/java_home gives all jdk installation inside the system.

## Homebrew
homebrew uses below path to install apps like maven, python, etc.. 
> /usr/local/opt : will have all user installed software

> /usr/local/Cellar : will have some summary of installation.

/System/Library/Frameworks : is where os provided frameworks are installed (for example: /System/Library/Frameworks/Python.framework/Versions/2.7/bin/python2.7)

## sdkman
- amazing software to maintain multiple versions of sdk like java, maven, etc.
- it maintains all the installation under:
~/.sdkman/candidates/java
~/.sdkman/candidates/java/current

## which command
To see from where this executable is available. </br>
Example: which python3

## symlinks
To view symlinks: </br>
example: ls -la /usr/local/bin

