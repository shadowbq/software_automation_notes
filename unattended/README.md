# Unattended

This is a system for fully automating the installation of Windows 2000 Professional and Server, Windows XP, and Windows Server 2003.

## App loading section.

http://unattended.sourceforge.net/apps.php

The process goes like this:

* Map the install share as the Z: drive.
* Install Perl.
* Install everything else.

Perl is required because the handy utility scripts are written in Perl. You do not need to know Perl to use the scripts, but you should learn it anyway because it is a good tool.

Note that this process is normally invoked immediately after the unattended OS installation by the GuiRunOnce section in the unattend.txt file. In particular, this process assumes that the machine is already configured to automatically log on as the local Administrator after every reboot. To invoke this procedure standalone, you can use the autolog.pl script to enable or disable automatic logon.



Todo.pl

http://sourceforge.net/p/unattended/code/HEAD/tree/trunk/install/bin/todo.pl


Example Scripts

http://sourceforge.net/p/unattended/code/HEAD/tree/trunk/install/scripts/

### Adobe Reader
The adobe-reader.bat script installs Adobe Reader. This is about as simple as an installation script can get.

To invoke this script manually, you would type:

```
    Z:\bin\todo.pl adobe-reader.bat
    Z:\bin\todo.pl --go
```

Obviously, you could just invoke the Adobe installer directly. But that would lose the consistent environment and error checking performed by todo.pl.

