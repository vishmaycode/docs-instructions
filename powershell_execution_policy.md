# Powershell execution policy setting

Excecution policy restricted issue

 - [https://learn.microsoft.com/en-us/answers/questions/506985/powershell-execution-setting-is-overridden-by-a-po](https://learn.microsoft.com/en-us/answers/questions/506985/powershell-execution-setting-is-overridden-by-a-po)


using windows run i.e Win + R

open "gpedit.msc"



```shell
> Computer Configuration 

    > Administrative Templates 

        > Windows Components 

            > Windows PowerShell.

            Look for settings related to "Turn on Script Execution" or "Execution Policy".
```

Adjust Policy: Double-click on the appropriate policy setting and adjust it to a less restrictive setting (e.g., "Allow all scripts"). Apply Changes:

After modifying the policy, close the Group Policy Editor and run gpupdate /force in an elevated Command Prompt to apply the changes immediately.
