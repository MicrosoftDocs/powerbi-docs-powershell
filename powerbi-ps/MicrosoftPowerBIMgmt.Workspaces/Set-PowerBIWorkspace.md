---
external help file: Microsoft.PowerBI.Commands.Workspaces.dll-Help.xml
Module Name: MicrosoftPowerBIMgmt.Workspaces
online version: https://docs.microsoft.com/en-us/powershell/module/microsoftpowerbimgmt.workspaces/set-powerbiworkspace?view=powerbi-ps
schema: 2.0.0
---

# Set-PowerBIWorkspace

## SYNOPSIS
Updates a Power BI workspace.

## SYNTAX

### Properties (Default)
```
Set-PowerBIWorkspace [-Scope <PowerBIUserScope>] -Id <Guid> [-Name <String>] [-Description <String>]
 [<CommonParameters>]
```

### Workspace
```
Set-PowerBIWorkspace [-Scope <PowerBIUserScope>] -Workspace <Workspace> [<CommonParameters>]
```

### Capacity
```
Set-PowerBIWorkspace [-Scope <PowerBIUserScope>] -Id <Guid> -CapacityId <Guid> [<CommonParameters>]
```

## DESCRIPTION
Updates the name or description of a Power BI workspace.
Only workspaces in the new workspace experiences preview are supported.
Only -Scope Organization is supported and you must have the appropriate permissions or role (such as ower BI Service Administrator) to call this command.
Before you run this command, make sure you log in using Connect-PowerBIServiceAccount. 

## EXAMPLES

### Example 1
```powershell
PS C:\> Set-PowerBIWorkspace -Scope Organization -Id "3244f1c1-01cf-457f-9383-6035e4950fdc" -Name "Test Name" -Description "Test Description"
```

If the current user is an administrator, this will update the workspace matching the specified ID with the specified name and description values for a workspace in the caller's organization.

### Example 2
```powershell
PS C:\> $workspaces = Get-PowerBIWorkspace -Scope Organization
PS C:\> $workspace = $workspaces[0]
PS C:\> $workspace.Name = "Test Name"
PS C:\> $workspace.Description = "Test Description"
PS C:\> Set-PowerBIWorkspace -Scope Organization -Workspace $workspace
```

If the current user is an administrator, this will update the specified workspace object with the specified name and description values for a workspace in the caller's organization.

## PARAMETERS

### -CapacityId
The capacity object id which a workspace will be assigned to. If CapacityId is set to "00000000-0000-0000-0000-000000000000", the workspace will be migrated to shared capacity.

```yaml
Type: Guid
Parameter Sets: Capacity
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description
The new description to give to the workspace to update.

```yaml
Type: String
Parameter Sets: Properties
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
ID of the workspace to update.

```yaml
Type: Guid
Parameter Sets: Properties, Capacity
Aliases: GroupId, WorkspaceId

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name
The new name to give to the workspace to update. If the name matches another workspace in the organization, the update operation will fail.

```yaml
Type: String
Parameter Sets: Properties
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope
Indicates scope of the call. Only Organization is supported with this cmdlet.
Organization operates against all workspaces within a tenant (must be an administrator to initiate). Individual is the default.

```yaml
Type: PowerBIUserScope
Parameter Sets: (All)
Aliases:
Accepted values: Individual, Organization

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Workspace
The workspace entity to update. The workspace will be updated with the name and description on the object.

```yaml
Type: Workspace
Parameter Sets: Workspace
Aliases: Group

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS
