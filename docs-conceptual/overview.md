---
title: Power BI Cmdlets reference
description: Learn about the PowerShell Cmdlets that are available to manage your Power BI tenant.
author: mgblythe
manager: kfile
ms.reviewer: ''

ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: mblythe
---

# Microsoft Power BI Cmdlets for Windows PowerShell and PowerShell Core

Welcome to the PowerShell reference for Microsoft Power BI. Here you will find resources for PowerShell modules targeting Power BI.

## PowerShell Modules

Below is a table of the various Power BI PowerShell modules covered in this reference.

| Description | Module Name | PowerShell Gallery link |
| ----------- | ----------- | ----------------------- |
| Rollup Module for PowerBI Cmdlets | `MicrosoftPowerBIMgmt` | [![MicrosoftPowerBIMgmt](https://img.shields.io/powershellgallery/v/MicrosoftPowerBIMgmt.svg?style=flat-square&label=MicrosoftPowerBIMgmt)](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) |
| Profile module for PowerBI Cmdlets | `MicrosoftPowerBIMgmt.Profile` | [![MicrosoftPowerBIMgmt.Profile](https://img.shields.io/powershellgallery/v/MicrosoftPowerBIMgmt.Profile.svg?style=flat-square&label=MicrosoftPowerBIMgmt.Profile)](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt.Profile/) |
| Workspaces module for PowerBI | `MicrosoftPowerBIMgmt.Workspaces` | [![MicrosoftPowerBIMgmt.Workspaces](https://img.shields.io/powershellgallery/v/MicrosoftPowerBIMgmt.Workspaces.svg?style=flat-square&label=MicrosoftPowerBIMgmt.Workspaces)](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt.Workspaces/) |
| Reports module for PowerBI | `MicrosoftPowerBIMgmt.Reports` | [![MicrosoftPowerBIMgmt.Reports](https://img.shields.io/powershellgallery/v/MicrosoftPowerBIMgmt.Reports.svg?style=flat-square&label=MicrosoftPowerBIMgmt.Reports)](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt.Reports/) |

## Supported Environments and PowerShell Versions

* Windows PowerShell v3.0 and up with .NET 4.6.1 or above.
* _[Future Release]_ PowerShell Core (v6) and up on any OS platform supported by PowerShell Core.

## Installation

The cmdlets are available on PowerShell Gallery and can be installed in an elevated PowerShell session:

```powershell
Install-Module -Name MicrosoftPowerBIMgmt
```

Optionally you could install individual modules (based on your needs) instead of the rollup module, for example if you only wanted the Workspaces module:

```powershell
Install-Module -Name MicrosoftPowerBIMgmt.Workspaces
```

If you have an earlier version, you can update to the latest version by running:

```powershell
Update-Module -Name MicrosoftPowerBIMgmt
```

### Uninstall

If you want to uninstall all the Power BI PowerShell cmdlets, run the following in an elevated PowerShell session:

```powershell
Get-Module MicrosoftPowerBIMgmt* -ListAvailable | Uninstall-Module -Force
```

## Usage

Two scopes are supported by cmdlets that interact with Power BI entities:
- Individual is used to access entities that belong to the current user.
- Organization is used to access entities across the entire company. Only Power BI tenant admins are allowed to use.

### Login to Power BI

```powershell
Connect-PowerBIServiceAccount   # or Login-PowerBIServiceAccount
```

### Get Workspaces

Get all workspaces for the user:

```powershell
Get-PowerBIWorkspace
```

### Update Workspace

Update the name or description of a user's workspace:

```powershell
Set-PowerBIWorkspace -Scope Organization -Id "3244f1c1-01cf-457f-9383-6035e4950fdc" -Name "Test Name" -Description "Test Description"
```

### Add new user to workspace

Add a user to a given workspace:

```powershell
Add-PowerBIWorkspaceUser -Scope Organization -Id 3244f1c1-01cf-457f-9383-6035e4950fdc -UserEmailAddress john@contoso.com -AccessRight Admin
```

### Remove a user from a given workspace

Remove user's permissions from a given workspace:

```powershell
Remove-PowerBIWorkspaceUser -Scope Organization -Id 3244f1c1-01cf-457f-9383-6035e4950fdc -UserEmailAddress john@contoso.com
```

### Restore Workspace

Restores a deleted workspace:

```powershell
Restore-PowerBIWorkspace -Id "3244f1c1-01cf-457f-9383-6035e4950fdc" -RestoredName "TestWorkspace" -AdminEmailAddress "john@contoso.com"
```

### Get Reports

Get all reports for the user:

```powershell
Get-PowerBIReport
```

## Issues and Feedback

If you find any bugs or would like to see certain functionality implemented for the PowerShell Cmdlets for Power BI, please [file an issue](https://github.com/Microsoft/powerbi-powershell/issues).

If your issue is broader than just the PowerShell cmdlets, please submit your feedback to the [Power BI Community](http://community.powerbi.com/) or the official [Power BI Support](https://powerbi.microsoft.com/en-us/support/) site.