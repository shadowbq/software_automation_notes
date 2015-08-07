## Silent Install

You should be able to use the /quiet or /qn options with msiexec to perform a silent install.

MSI packages export public properties, which you can set with the PROPERTY=value syntax on the end of the msiexec parameters.

For example, this command installs a package with no UI and no reboot, with a log and two properties:

```
msiexec /i c:\path\to\package.msi /quiet /qn /norestart /log c:\path\to\install.log PROPERTY1=value1 PROPERTY2=value2
```

You can read the options for msiexec by just running it with no options from Start -> Run.

	
Here is the predefined properties list: 
* http://msdn.microsoft.com/en-us/library/windows/desktop/aa370905(v=VS.85).aspx

The installation folder property is different for each setup authoring tool.

## Bootstrapping applications
https://msdn.microsoft.com/en-us/library/aa367832(v=vs.85).aspx

Using an .ini File
Creating an initialization file may be easier than creating a long command line. Using the /settings option, the Setup.exe application reads the specified .ini file and constructs a command line to pass to the Msiexec.exe application. Only properties supported on the command line are supported in the .ini file. If a property or value is found in both the .ini file and on the command line, the command line settings override the .ini file settings.

msistuff.exe
Msistuff.exe is a command line utility that can be used to display or configure the resources in the Setup.exe bootstrap executable.

## Digging into MSIs

Ocra to dissect the MSI,
https://msdn.microsoft.com/en-us/library/aa370557(v=vs.85).aspx

Instmsi.exe
https://msdn.microsoft.com/en-us/library/aa369548(v=vs.85).aspx

### lessmsi
http://lessmsi.activescott.com/
https://github.com/activescott/lessmsi
