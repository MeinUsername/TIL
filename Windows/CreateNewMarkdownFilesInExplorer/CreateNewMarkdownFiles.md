How To Register the .md Fileextension in the Explorer New Context Entry
=======================================================================

Not Working for Win10: Sources: https://superuser.com/questions/34704/how-can-i-add-an-item-to-the-new-context-menu
Working for Win10: https://superuser.com/questions/638755/add-item-to-new-context-menu-in-windows-8

Add the addreg-md.reg to the registry. 
Then LogOff and Logon again. Then a new context entry should be there ( Blank Markdown File). 


Specify a Template
Create a new string value in HKEY_LOCAL_MACHINE\SOFTWARE\Classes\.md\ShellNew
with the name FileName. The value is the name of the template
The Template should be stored in C:\Windows\ShellNew
Not tested: this should be optional






