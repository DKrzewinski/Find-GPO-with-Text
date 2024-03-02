# GPO Search Script

## Overview
This PowerShell script is designed to search for a specified string within the XML reports of Group Policy Objects (GPOs) in the current domain. It prompts the user for a search string, retrieves all GPOs in the domain, and then searches through each GPO's XML report for the specified string.

## Prerequisites
- PowerShell environment
- Active Directory module installed (Import-Module grouppolicy)

## Usage
1. Run the script in a PowerShell environment.
2. Enter the string you want to search for when prompted.
3. The script will then iterate through all GPOs in the current domain and display whether the specified string is found in each GPO's XML report.

## Script Details
- The script uses the `Read-Host` cmdlet to get the string to search for from the user.
- It sets the domain name to search for GPOs based on the environment variable `$env:USERDNSDOMAIN`.
- The `Import-Module grouppolicy` cmdlet is used to import the Group Policy module.
- It retrieves all GPOs in the current domain using `Get-GPO -All -Domain $DomainName`.
- The script then iterates through each GPO, retrieves its XML report using `Get-GPOReport`, and checks if the specified string is present in the report.
- Matches are displayed with the GPO's display name in green, and non-matches are displayed in regular text.
- The final results are summarized, showing the GPOs where the specified string was found.

## Example
```powershell
PS C:\Scripts> .\GPO_Search.ps1
What string do you want to search for? ExampleString
Finding all the GPOs in exampledomain.com
Starting search....

********** Match found in: GPO1 **********   <-- Example output for a match
No match in: GPO2
...
No match in: GPON

Results: **************
Match found in: GPO1                           <-- Example summary of matches
Match found in: GPO3
...
Match found in: GPOX
```

## Notes
- Ensure that the PowerShell execution policy allows running scripts on the system.
- The script assumes the availability of the Group Policy module.

Feel free to customize and integrate this script into your workflow for efficient GPO searching.