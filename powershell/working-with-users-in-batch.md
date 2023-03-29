# Working with Users in Batch

One of the ongoing projects I've been involved in at work is standardizing the way departments and titles appear in our Microsoft 365 organization. With the agency scaling a bit more every year, I was tasked with updating all existing users’ titles and department information to syntactically match our new set of standards.

> All of the cmdlets used in this guide are used in the **Exchange Online module**. To connect to the module, use `Connect-ExchangeOnline`.

## Working with multiple users
In order to select multiple users, first create a CSV file containing the emails of all users you'd like to manipulate. The single column of emails should have a header of `UserPrincipalName`.

Once the file is created, you can use a pipeline with the `ForEach-Object` cmdlet and `Import-Csv` cmdlet to read the user data:

```powershell
Import-Csv "/path/to/users.csv" | ForEach-Object { Set-User -Identity $_.UserPrincipalName -Title "Director" -Confirm:$false }
```

The code above reads the user data from the CSV file and uses the `Set-User` cmdlet to the change the title of each user to **Director**. To see the full list of what information can be edited in `Set-User`, see [this article](https://learn.microsoft.com/en-us/powershell/module/exchange/set-user?view=exchange-ps).

By default, PowerShell has a safety feature to prevent accidental execution of dangerous commands. To bypass this prompt, an additional paramater has been added: `-Confirm:$false`. This will suppress the confirmation prompt and automatically confirm the action for each user.

## Add users to a group

Aside from updating user information, another reoccurring task is adding users to a mail-enabled security group. It uses the same `ForEach-Object` and `Import-Csv` cmdlets, with the addition of the `Add-DistributionGroupMember` cmdlet.

```powershell
Import-Csv "/path/to/users.csv" | ForEach-Object { Add-DistributionGroupMember -Identity "group@company.com" -Member $_.UserPrincipalName -BypassSecurityGroupManagerCheck }
```

Here the script will add all users in the CSV file to the mail-enabled security group using the `-Identity` parameter. The addition of `-BypassSecurityGroupManagerCheck` suppresses the confirmation prompt.