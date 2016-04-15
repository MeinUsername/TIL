# Config a blank Windows 10

## Programs to install:

(X) --> indicates, found as package

    - Keepass  (X)  
    - Opera  (X)
    - Dropbox (X)
    - Sublime with Package Manager and Markdown Extend Plugin (X, as Version 2)
    - Notepad++ (X)
    - Winmerge (X)
    - IntelliJ (X) / PHPStorm (X, version 9.. old)/ Webstorm (X)
    - Speedcommander
    - Autohotkey (X)
    - Spotify (X, seems old)
    - Eclipse  (X)
    - Irfanview (X)
    - SourceCodePro (X)
    - Git (X)
    - Paint.net (X)
    - Winscp (X)
    - Putty (X)
    - LibreOffice (X
    - Office365HomePremion (X... seem sensible)
    - Chrome
    - Firefox
    





## How to automate these installations?



 
Allow the script execution in powershell, otherwise is the installer not working:

```powershell
Set-ExecutionPolicy RemoteSigned 
```


General it is useful to *run powershell as Administrator*

1. Execute in Powershell get-packageprovider -name chocolatey
2. get-packageprovider -name nuget ( or try to find a package)

A package can be found with:

```powershell
 find-package {PackageName}
 ```

 A package can be found with:

```powershell
 install-package {PackageName}
```

A package can be found with:

```powershell
 uninstall-package {PackageName}
 ```
 










