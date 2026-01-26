# Powershell Commands

| Cmdlet           | Alias     | Bash Equivalent | Description                                                                                                                                                                                                                          |
| ---------------- | --------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Get-ChildItem`  | `gci`     | `ls`            | List the directories and files in the current location.                                                                                                                                                                              |
| `Set-Location`   | `sl`      | `cd`            | Change to the directory at the given path. Typing `..` rather than a path will move up one directory.                                                                                                                                |
| `Push-Location`  | `pushd`   | `pushd`         | Changes to the directory.                                                                                                                                                                                                            |
| `Pop-Location`   | `popd`    | `popd`          | Changes back to the previous directory after using `pushd`                                                                                                                                                                           |
| `New-Item`       | `ni`      | (`touch`)       | Creates a new item. Used with no parameter, the item is by default a file. Using `mkdir` is a shortcut for including the parameter `-ItemType dir`.                                                                                  |
| `mkdir`          | none      | `mkdir`         | Creates a new directory. (See `New-Item`.)                                                                                                                                                                                           |
| `Explorer`       | none      | (`open`)        | Open something using File Explorer (the GUI)                                                                                                                                                                                         |
| `Remove-Item`    | `rm`      | `rm`            | Deletes something. Permanently!                                                                                                                                                                                                      |
| `Move-Item`      | `mv`      | `mv`            | Moves something. Takes two arguments - first a filename (i.e. its present path), then a path for its new location (including the name it should have there). By not changing the path, it can be used to rename files.               |
| `Copy-Item`      | `cp`      | `cp`            | Copies a file to a new location. Takes same arguments as move, but keeps the original file in its location.                                                                                                                          |
| `Write-Output`   | `write`   | `echo`          | Outputs whatever you type. Use redirection to output to a file. Redirection with `>>` will add to the file, rather than overwriting contents.                                                                                        |
| `Get-Content`    | `gc`      | `cat`           | Gets the contents of a file and prints it to the screen. Adding the parameter `-TotalCount` followed by a number x prints only the first x lines. Adding the parameter `-Tail` followed by a number x prints only the final x lines. |
| `Select-String`  | `sls`     | (`grep`)        | Searches for specific content.                                                                                                                                                                                                       |
| `Measure-Object` | `measure` | (`wc`)          | Gets statistical information about an object. Use `Get-Content` and pipe the output to `Measure-Object` with the parameters `-line`, `-word`, and `-character` to get word count information.                                        |
| `>`              | none      | `>`             | Redirection. Puts the output of the command to the left of `>` into a file to the right of `>`.                                                                                                                                      |
| `\|`             | none      | `\|`            | Piping. Takes the output of the command to the left and uses it as the input for the command to the right.                                                                                                                           |
| `Get-Help`       | none      | `man`           | Gets the help file for a cmdlet. Adding the parameter `-online` opens the help page on TechNet.                                                                                                                                      |
| `exit`           | none      | `exit`          | Exits PowerShell                                                                                                                                                                                                                     |

***

## Windows Powershell Course

### Review Windows Powershell

Windows powershell uses Cmdlets, using Verb-Noun naming convention. There are two versions of Powershell, Windows Powershell and Powershell (current version 7.5).

There are two types of powershell installed on Windows machine, the console (like cmd.exe), and ISE (Integrated Scripting Enviornment), which provides more functionality.

In Windows PowerShell, the executable is powershell.exe, in version 6+, it is named pwsh.exe. Use `$PSVersionTable` to get version info. Powershell runs in both 64 and 32-bit versions. The 32-bit versions will say (x86). If you want to perform administrative actions, run powershell as administrator.

{% hint style="info" %}
Use Ctrl + "+" and Ctrl + "-" to zoom in and out of your powershell console.
{% endhint %}

#### Execution Policy

Script execution policies are enabled to stop people from unintentionally running malicious scripts. You can find the execution policy with `Get-ExecutionPolicy` . There are different types of policies.

<table><thead><tr><th width="137">Policy</th><th>Description</th></tr></thead><tbody><tr><td><strong>AllSigned</strong></td><td>Requires all scripts to be signed.</td></tr><tr><td><strong>Default</strong></td><td>Restricted for Windows Clients, and RemoteSigned for Windows Servers</td></tr><tr><td><strong>RemoteSigned</strong></td><td>Requires a digital signature, doesn't require digital signature for scripts written on the computer.</td></tr><tr><td><strong>Restricted</strong></td><td>Allows individual commands, but not scripts</td></tr><tr><td><strong>Unrestricted</strong></td><td>Default execution policy for non-Windows computers. Allows all scripts to run.</td></tr><tr><td><strong>Undefined</strong></td><td>No execution policy, reverts to Default.</td></tr></tbody></table>

To set an execution policy, use the following command:

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

#### PowerShell ISE

There are multiple different window panes on ISE, the **Script** pane, the **Console** pane and the **Commands** list pane, allowing you to write and test scripts. You can also use Visual Studo code to replicate ISE with the Powershell extension and enabling "ISE Mode."

### Understand command syntax in Windows Powershell

Powershell functions off of cmdlets, using _Verb-Noun_ notation. Some cmdlet verbs include **Get, Set, New, Add**, and **Remove.**

{% hint style="info" %}
Use `Get-Verb` to get all supported verbs.
{% endhint %}

The noun indicates what resource the cmdlet is affecting. For example, AD stands for Active Directory, SharePoint servers start with SP, and Az is Azure.

**Parameters** start with a dash (-) to pass a value. Some parameters are required, and some are optional. If a parameter is required and you don't pass a value for it, it'll prompt you for a value.&#x20;

**Switches** are parameters that are a Boolean value. By specifying the parameter, you are setting the boolean value to false. For example, using `GetChildItem C:\ -Recurse` is a switch.

Powershell provides **Tab Completion** to autocomplete commands with Tab. Tab completion also supports **Wildcards** so you can type `*-service`  to display anything that matches. &#x20;

Use the Get-Help command to list articles about command issues.&#x20;

### Find commands and Get-Help in Windows PowerShell

Commands are provided through modules, which group cmdlets into a single unit. Use this `Get-Module -ListAvailable` to list all available modules. In PowerShell 3.0+, modules will automatically load. The modules are stored in `%systemdir%\WindowsPowerShell\v1.0\Modules and %userprofiles%\Documents\WindowsPowerShell\Modules`  or `$env:PSModulePath` .&#x20;

To find a command, use the `Get-Help` and `Get-Command`  to get info. These commands accept wild card. Use -Noun and -Verb to filter. For example:

```powershell
Get-Command –Noun event* –Verb Get
```

You can also search via modules. Certain modules contain logically grouped cmdlets. For example the module NetAdapter contains a lot of commands about NetAdapters:

```powershell
Get-Command –Module NetAdapter
```

To find outside cmdlets, look through the PowerShell gallery with Find-Command and pipe it to the Install-Module command to install.

#### Aliases

Use Get-Alias -definition to get all the aliases of a command, or just plain Get-Alias to find the original command. You can create your own aliases with the New-Alias command, but it only saves during the current session. You'll have to create a PowerShell profile. It's recommended that you not use aliases as it makes scripts harder to read. In addition, aliases like cd or curl do not accept the same paramters that you think, as they map to a different cmdlet than cd, instead mapping to Set-Location or Invoke-WebRequest.

Show-Command will open a different window displaying all the parameters you can add. Get-Help will display full command information.&#x20;

#### Get-Help

**Parameters**

* Full: Displays all information
* ShowWindow: Displays info in a separate window
* Online: Sends you to Microsoft documentation
* Parameter: Displays specific parameter information
* Category: Displays help for certain categories of commands

#### Summary

* Modules are groups of related PowerShell capabilities that are bundled together into a single unit. Modules help with organizing cmdlets into distributable units.
* Finding the cmdlet that you need from the extensive built-in help of Windows PowerShell can be a challenge. Using the –Module parameter and **Get Help** can make this task easier.
* Batch commands used in the traditional Windows Command Prompt shell (**cmd.exe**) can also be used within Windows PowerShell. This is because these batch commands are aliases of the cmdlets that perform the equivalent action.
* The **Show-Command** cmdlet opens a window that displays either a list of commands or a specific command's parameters. To display a specific command's parameters, provide the name of the command as the value for the _‑Name_ parameter.
* The **Get-Help** command can help you access the extensive in-product help for commands that Windows PowerShell provides.
* Learning to interpret the help-file syntax can help you to identify all capabilities of a given command.

### Managing user accounts in Powershell

| **New-ADUser**            | Creates a user account                                                                                       |
| ------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Get-ADUser**            | Retrieves a user account                                                                                     |
| **Set-ADUser**            | Modifies properties of a user account                                                                        |
| **Remove-ADUser**         | Deletes a user account                                                                                       |
| **Set-ADAccountPassword** | Resets the password of a user account                                                                        |
| **Unlock-ADAccount**      | Unlocks a user account that's been locked after exceeding the permitted number of incorrect sign-in attempts |
| **Enable-ADAccount**      | Enables a user account                                                                                       |
| **Disable-ADAccount**     | Disables a user account                                                                                      |

| ‑AccountExpirationDate | Defines the expiration date for a user account                              |
| ---------------------- | --------------------------------------------------------------------------- |
| ‑AccountPassword       | Defines the password for a user account                                     |
| ‑ChangePasswordAtLogon | Requires a user account to change passwords at the next sign-in             |
| ‑Department            | Defines the department for a user account                                   |
| ‑DisplayName           | Defines the display name for a user account                                 |
| ‑HomeDirectory         | Defines the location of the home directory for a user account               |
| ‑HomeDrive             | Defines the drive letters that map to the home directory for a user account |
| ‑GivenName             | Defines the first name of a user account                                    |

| **New-ADGroup**                       | Creates a new group                     |
| ------------------------------------- | --------------------------------------- |
| **Set-ADGroup**                       | Modifies properties of a group          |
| **Get-ADGroup**                       | Displays properties of a group          |
| **Remove-ADGroup**                    | Deletes a group                         |
| **Add-ADGroupMember**                 | Adds members to a group                 |
| **Get-ADGroupMember**                 | Displays members of a group             |
| **Remove-ADGroupMember**              | Removes members from a group            |
| **Add-ADPrincipalGroupMembership**    | Adds group membership to an object      |
| **Get-ADPrincipalGroupMembership**    | Displays group membership of an object  |
| **Remove-ADPrincipalGroupMembership** | Removes group membership from an object |

| ‑Name           | Defines the name of a group                                                                                                   |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| ‑GroupScope     | Defines the scope of a group as **DomainLocal**, **Global**, or **Universal**; you must provide this parameter                |
| ‑DisplayName    | Defines the Lightweight Directory Access Protocol (LDAP) display name for an object                                           |
| ‑GroupCategory  | Defines whether a group is a security group or a distribution group; if you don't specify either, a security group is created |
| ‑ManagedBy      | Defines a user or group that can manage a group                                                                               |
| ‑Path           | Defines the OU or container in which a group is created                                                                       |
| ‑SamAccountName | Defines a name that is backward-compatible with older operating systems                                                       |

| Cmdlet                            | Description                                                                  |
| --------------------------------- | ---------------------------------------------------------------------------- |
| **New-ADComputer**                | Creates a new computer account                                               |
| **Set-ADComputer**                | Modifies properties of a computer account                                    |
| **Get-ADComputer**                | Displays properties of a computer account                                    |
| **Remove-ADComputer**             | Deletes a computer account                                                   |
| **Test-ComputerSecureChannel**    | Verifies or repairs the trust relationship between a computer and the domain |
| **Reset-ComputerMachinePassword** | Resets the password for a computer account                                   |

| Cmdlet                          | Description                  |
| ------------------------------- | ---------------------------- |
| **New-ADOrganizationalUnit**    | Creates an OU                |
| **Set-ADOrganizationalUnit**    | Modifies properties of an OU |
| **Get-ADOrganizationalUnit**    | Displays properties of an OU |
| **Remove-ADOrganizationalUnit** | Deletes an OU                |

### Manage network service settings for Windows devices using PowerShell cmdlets

| Cmdlet                  | Description                          |
| ----------------------- | ------------------------------------ |
| **New-NetIPAddress**    | Creates a new IP address             |
| **Get-NetIPAddress**    | Displays properties of an IP address |
| **Set-NetIPAddress**    | Modifies properties of an IP address |
| **Remove-NetIPAddress** | Deletes an IP address                |

| Parameter       | Description                                                  |
| --------------- | ------------------------------------------------------------ |
| -IPAddress      | Defines the IPv4 or IPv6 address to create                   |
| -InterfaceIndex | Defines the network interface, by index, for the IP address  |
| -InterfaceAlias | Defines the network interface, by name, for the IP address   |
| -DefaultGateway | Defines the IPv4 or IPv6 address of the default gateway host |
| -PrefixLength   | Defines the subnet mask for the IP address                   |

```powershell
New-NetIPAddress -IPAddress 192.168.1.10 -InterfaceAlias "Ethernet" -PrefixLength 24 -DefaultGateway 192.168.1.1
```

Use pipe Select-Object to get a specific part of a result.

#### Firewall

| Cmdlet                      | Description                            |
| --------------------------- | -------------------------------------- |
| **New-NetFirewallRule**     | Creates a new firewall rule            |
| **Set-NetFirewallRule**     | Sets properties for a firewall rule    |
| **Get-NetFirewallRule**     | Gets properties for a firewall rule    |
| **Remove-NetFirewallRule**  | Deletes a firewall rule                |
| **Rename-NetFirewallRule**  | Renames a firewall rule                |
| **Copy-NetFirewallRule**    | Makes a copy of a firewall rule        |
| **Enable-NetFirewallRule**  | Enables a firewall rule                |
| **Disable-NetFirewallRule** | Disables a firewall rule               |
| **Get-NetFirewallProfile**  | Gets properties for a firewall profile |
| **Set-NetFirewallProfile**  | Sets properties for a firewall profile |

### Manage Windows 10 using PowerShell <a href="#module-unit-title" id="module-unit-title"></a>

| **Get-ComputerInfo** | Retrieves all system and operating system properties from the computer                                     |
| -------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Get-Service**      | Retrieves a list of all services on the computer                                                           |
| **Get-EventLog**     | Retrieves events and event logs from local and remote computers (only available in Windows PowerShell 5.1) |
| **Get-Process**      | Retrieves a list of all active processes on a local or remote computer                                     |
| **Stop-Service**     | Stops one or more running services                                                                         |
| **Stop-Process**     | Stops one or more running processes                                                                        |
| **Stop-Computer**    | Shuts down local and remote computers                                                                      |
| **Clear-EventLog**   | Deletes all of the entries from the specified event logs on the local computer or on remote computers      |
| **Clear-RecycleBin** | Deletes the content of a computer's recycle bin                                                            |
| **Restart-Computer** | Restarts the operating system on local and remote computers                                                |
| **Restart-Service**  | Stops and then starts one or more services                                                                 |

```powershell
Get-EventLog -LogName Application -Newest 5 -EntryType Error
Clear-EventLog -LogName Application


Get-Acl -Path C:\Folder1|Format-List
(Get-Acl -Path C:\Folder1).Access
(Get-Acl -Path C:\Folder1).Access|Format-Table IdentityReference, FileSystemRights, AccessControlType, IsInherited

$AccessRule = New-Object System.Security.AccessControl.FileSystemAccessRule("User1","Modify","Allow")
$ACL.SetAccessRule($AccessRule)
$ACL | Set-Acl -Path C:\Folder1

Get-Acl -Path C:\Folder1|Set-ACL -Path C:\Folder2
    
Invoke-WebRequest -Uri "http://www.example.com" | Select-Object -ExpandProperty Content

```

