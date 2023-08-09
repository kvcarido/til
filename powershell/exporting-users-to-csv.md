# Exporting Users to a CSV

## Cmdlets Used
- [Get-DistributionGroupMember](https://learn.microsoft.com/en-us/powershell/module/exchange/get-distributiongroupmember?view=exchange-ps)
- [Select-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.3)
- [Export-CSV](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-7.3)

I received a ticket asking about the accuracy of users in a Microsoft 365 mail-enabled security group. Since I had prior experience running census reports and updating users' department titles, my approach was to export the list of users to a CSV file, which then can be compared to an updated census report of users in a specific department.

Using the `Exchange Online` module, I started with `Get-DistributionGroupMember` which is pretty straight-foward. Instead of outputting the results within the command line, I knew I wanted it to be contained within a CSV file so the data is structured and accessible. With the help of ChatGPT, I was able to build out this PowerShell script:

```powershell
# Replace "groupName" with the actual name of your mail-enabled security group
$groupName = "alias@email.com"
$members = Get-DistributionGroupMember -Identity $groupName

# Select specific attributes (properties) to be exported in CSV
$selectedMembers = $members | Select-Object Identity, Alias

# Specify the output CSV file path
$outputPath = "/Path/To/Save/export-file.csv"

# Export the results to a CSV file
$selectedMembers | Export-CSV -Path $outputPath
```

Although `Get-DistributionGroupMember` did the trick, the results came with a bunch of attributes like office location, notes, etc. that weren't needed for this report. Using `Select-Object` helped me pick and choose which attributes to include in the export, and in this case all I needed was Identity and Alias.

## Takeaways
Up until this point I've been running PowerShell commands directly within the command line, but this task gave me some hands-on experience with executing script files. I was also able to get a better understanding of when to use variables in PowerShell and how it can make reading code more efficient.