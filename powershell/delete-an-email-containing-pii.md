# Delete an Email Containing PII

## Locate Email in Purview

* Microsoft Admin → Purview (formerly known as Compliance) → Solutions → Content Search
* Naming convention for the search is formatted as **Ticket #**
* Be as specific as possible when trying to target the email containing PII
    * Relying on the email title alone can delete portions of the email thread not containing PII
    * Ask the user for as many details as possible – Date, Time, Subject, Sender, Attachments

## Delete Email in PowerShell

Once you've targeted the email(s) containing PII in Content Search, you'll need to delete them using PowerShell.

Initially, I had permission issues when trying to run the command to delete emails from a Content Search query. I was able to troubleshoot the issue with my colleague and had to run these initial commands before moving forward.

### PowerShell Permission Prerequisites

> When running this command I still ran into permission errors with certain filepaths – I had to exit out of Powershell and connect with `sudo` for this portion

Run `Install-WSMan`

This is a PowerShell cmdlet that is used to install and configure the Windows Remote Management (WinRM) service on a local or remote computer. The WinRM service allows for remote management and execution of PowerShell commands on remote computers in a Windows environment.

> Running this command performs the following tasks:
> 1. Installs the WinRM service on the local computer, if it is not already installed.
> 2. Configures the WinRM service to start automatically and sets it to run as a service.
> 3. Sets up the necessary firewall rules to allow WinRM traffic.
> 4. Configures the necessary security settings for WinRM communication, such as enabling authentication and setting up SSL encryption.

Run `Install-Module -Name PSWSMan`

The `PSWSMan` module is a PowerShell module that provides cmdlets for managing the Windows Remote Management (WinRM) service, which allows for remote management and execution of PowerShell commands on remote computers in a Windows environment. The `PSWSMan` module specifically focuses on providing cmdlets for managing the WinRM service configuration and settings.

### Deleting the Email in Exchange Online Management

To [connect to the Security & Compliance PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-scc-powershell?view=exchange-ps) (now known as Purview), you'll need to run the following commands.

Run `Import-Module ExchangeOnlineManagement`
> If you run into issues, see [these steps](https://learn.microsoft.com/en-us/powershell/exchange/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-module)

Once executed, connect to the Security & Compliance PowerShell:

```powershell
Connect-IPPSSession -UserPrincipalName "hello@email.com"
```

To delete the targeted emails in Content Search from earlier, run the following command to locate and **hard delete** from the server:

```powershell
New-ComplianceSearchAction -SearchName "Ticket #" -Purge -PurgeType HardDelete
```

To learn more about `HardDelete`, refer to [this documentation](https://learn.microsoft.com/en-us/powershell/module/exchange/new-compliancesearchaction?view=exchange-ps#-purgetype).

### Other Resources

Microsoft Learn: [Search for and delete email messages](https://learn.microsoft.com/en-us/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization?view=o365-worldwide)