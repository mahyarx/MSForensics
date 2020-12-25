# MSForensics
Created for Cloud Forensics team to help detect possible compromised accounts and applications in the Azure/office365 environment.

# MSForensics.ps1 #

MSForensics.ps1 was created by CISA's Cloud Forensics team to help detect possible compromised accounts and applications in the Azure/Office365 environment. The tool is intended for use by incident responders, and focuses on the narrow scope of user and application activity endemic to identity and authentication based attacks seen recently in multiple sectors. It is neither comprehensive nor exhaustive of available data, and is intended to narrow a larger set of available investigation modules and telemetry to those specific to recent attacks on federated identity sources and applications.
 
MSForensics.ps1 will check and install the required PowerShell modules on the analysis machine, check the unified audit log in Azure/Office365 for certain indicators of compromise (IoC's), list Azure AD domains, and check Azure service principals and their Microsoft Graph API permissions to identify potential malicious activity. The tool then outputs the data into multiple CSV files in a default directory.

## Requirements ##

The following AzureAD/m365 permissions are required to run MSForensics.ps1, and provide it read-only access to the Tenant.

   - Azure Active Directory:
     - Security Reader
   - Security and Compliance Center:
     - Compliance Adminstrator
   - Exchange Online Admin Center: Utilize a custom group for these specific permissions:
     - Mail Recipients
     - Security Group Creation and Membership
     - User options
     - View-Only Audit log
     - View-Only Configuration
     - View-Only Recipients

To check for the MailItemsAccessed Operation, your tenant organization requires an Office 365 or Microsoft 365 E5/G5 license.

## Installation ##

MSForensics.ps1 does not require any extra steps for installation once the permissions detailed in Requirements are satisfied.

The function, Check-PSModules, will check to see if the three required PowerShell modules are installed on the system and if not, it will use the default PowerShell repository on the system to reach out and install. If the modules are present but not imported, the script will also import the missing modules so that they are ready for use.

The required PowerShell modules:

  - CloudConnect (https://www.powershellgallery.com/packages/CloudConnect/1.1.2)
  - AzureAD (https://www.powershellgallery.com/packages/AzureAD/2.0.2.128)
  - MSOnline (https://www.powershellgallery.com/packages/MSOnline/1.1.183.57)

## Usage ##

To use MSForensics.ps1, type the following command into a PowerShell window (assuming file is in your working directory):

`.\MSForensics.ps1`

## Issues ##

If you have issues using the code, open an issue on the repository!

You can do this by clicking "Issues" at the top and clicking "New Issue" on the following page.
