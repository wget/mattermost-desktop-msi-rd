# Purpose of this repository

This repository aims at research and development purposes about msi and update process of msi installers in general.

As an example case, we worked on the Mattermost Desktop project:
* we wanted to build a fully featured msi installer, without relying on the limited msi provided by electron builder;
* we want to have an eye catchy interface communicating with the msi using an IPC system;
* solve the auto updater issue by reusing the Mozilla Update Service in this regard.

## Build instructions

```
rm .\test.log; candle.exe -dPlatform=x64 .\installer.wxs; light.exe .\installer.wixobj -loc .\i18n\en_US.wxl -o test.msi
```
We specify whether we want 32 bits or 64 bits installer by specifying the `Platform` value passed as argument.

To create a GUID in uppercase with Powershell:
```
([string](New-Guid)).ToUpper()
```

## Silent install
```
msiexec /i test.msi /l*v test.log INSTALLDIR="C:\mattertest1" /qb
```

## License

As this work will be reused for a project I have at OpenVPN Inc, this repository is licensed under the MIT License.