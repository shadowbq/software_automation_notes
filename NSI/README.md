4.12 Silent Installers/Uninstallers

Silent installers are installers which require no user intervention and have no user interface. The user doesn't see any dialog and isn't asked any questions. This is useful for network administrators who wish to install or uninstall something without user intervention so they can perform the operation quickly over any number of computers. It is also useful for other developers who wish to embed another installer in their own and collect all of the required information on their installer instead of showing two installers.

NSIS installers and uninstallers can be both silent and not silent. When an installer or an uninstaller is silent, not all callback functions are called. .onGUIInit, .onGUIEnd, their uninstaller equivalents and any callback related to a specific page or page type will not be called.

There are several methods to make an installer or an uninstaller silent:

SilentInstall and SilentUninstall
SetSilent
Passing /S on the command line (case sensitive)
To check if the installer/uninstaller is silent use IfSilent.

To make sure your installer will be silent when it needs to, you should check with IfSilent before each command that might require user intervention or create a window. The MessageBox command, which is the most common culprit in silent installers, has the /SD switch to set a default answer for silent installers. If you want your installer/uninstaller to be able to be completely silent you should use this switch. All internal NSIS message boxes have defaults for silent installers. The silent.nsi example demonstrates all aspects of this topic.

Since the directory page can not be shown on silent installers, the user has an option to specify the installation directory on the command line (this also works on non-silent installers/uninstallers). To do that, the user uses the /D switch as in the following example:

foo.exe /S /D=C:\Program Files\Foo
If your installer/uninstaller requires some more information that can not be gathered when silent, you can allow the user to specify that information on the command line and process it in .onInit. You can use GetOptions.

!include FileFunc.nsh
!insertmacro GetParameters
!insertmacro GetOptions

Function .onInit
  ${GetParameters} $R0
  ClearErrors
  ${GetOptions} $R0 /USERNAME= $0
FunctionEnd
The above example will copy the value the user passes on after /USERNAME= into $0. This allows the user to specify the required information on the command line instead of using the interactive user interface. The user can use:

foo.exe /S /USERNAME=Bar /D=C:\Program Files\Foo
or:

foo.exe /S /USERNAME=string with spaces /D=C:\Program Files\Foo
or:

foo.exe /S /USERNAME="string with spaces" /D=C:\Program Files\Foo
If your installer/uninstaller requires a lot of information and you want it to be able to be silent, you should allow the user to pass on a path to an answers file. This would be much more comfortable than writing all of the information on the command line.
