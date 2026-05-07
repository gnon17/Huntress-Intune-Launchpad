<img width="599" height="399" alt="HuntressLaunchpad1 (1)" src="https://github.com/user-attachments/assets/b5c6c4a0-56e0-48e3-b127-badfe99c8cf9" />

# Huntress Windows Launchpad

A single PowerShell script that automates the full Huntress deployment for Windows devices in Microsoft Intune. Currently Windows-only — macOS support is planned.

## What it does

Run once per client tenant. The script handles:

1. **Huntress Agent Win32 app**
2. **SIEM Audit Logging policy**
3. **Defender AV baseline policy**
4. **Tamper Protection policy**
5. **Additional Recommended Defender AV Settings**

You'll be prompted for your Huntress Account Key, Organization Key, and whether to assign the app and policies to All Devices. The tool takes ~20 seconds to run, after which it cleans up the downloaded files and prints a summary of everything created.

## Customizing

Policy configurations are **not embedded in the script** — they're pulled at runtime from JSON files (Huntress-hosted for SIEM, this repo for everything else). You can download and edit the script to use your own baseline JSON URLs. 

A couple of other things worth noting:
* The Win32 app detection script looks for the HuntressAgent service. 
* Only the Huntress-recommended exclusions are included in the Defender AV policy. You'll need to add any client-specific exclusions for line-of-business apps.

## Full instructions
* Click the latest release from the right side of the screen, download the HuntressIntuneLaunchpad.ps1 script and run with PowerShell
* For full details, screenshots, and additional context, see the blog post -

## Requirements
- PowerShell 5.1+
- Microsoft Graph permissions: `DeviceManagementApps.ReadWrite.All`, `DeviceManagementConfiguration.ReadWrite.All`
- The script installs the required PowerShell modules (`Microsoft.Graph.Authentication`, `Microsoft.Graph.Beta.DeviceManagement`) if they aren't already present.
