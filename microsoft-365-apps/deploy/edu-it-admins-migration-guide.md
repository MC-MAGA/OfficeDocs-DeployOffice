---
title: "OneNote Migration Guide for Microsoft 365 Education Admins"
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: o365-proplus-itpro
ms.collection: Tier1
ms.localizationpriority: medium
recommendations: true
description: "Guide for Microsoft 365 Education (EDU) admins on migrating from OneNote for Windows 10 to OneNote on Windows, including supported migration scripts and steps to uninstall old versions"
ms.date: 12/03/2024
---

# OneNote Migration Guide for Microsoft 365 Education Admins

[!INCLUDE [OneNote Windows 10 eos](../includes/onenote-win10-eos.md)]

As OneNote for Windows 10 nears the end of support, it's crucial for IT admins to migrate users to OneNote on Windows. This move ensures users benefit from the latest technology improvements and have a consistent experience with a single OneNote application on Windows. IT admins should plan migrations to OneNote on Windows during periods when students and staff aren't actively using school equipment, such as school breaks or other noninstructional times.

## EDU Tenants current migration approach

Many education institutions plan to handle this migration in one of two ways:

- Device reimage: Wipe devices and install a fresh OS.
- Operating system upgrade from Windows 10 to Windows 11: Windows 11 includes OneNote on Windows, but it doesn't replace or uninstall OneNote for Windows 10. IT administrators need to uninstall OneNote for Windows 10 separately.

## OneNote's supported migration approach

To simplify the transition, the OneNote team developed a [migration script](onenote-for-windows-10-migration-guide.md). The script is designed to prevent common issues, such as data loss due to unsynced notebooks, and ensures that users' notebooks fully sync during the migration. It's especially helpful for users whose notebooks didn't sync completely before the migration.

## Critical final steps: Uninstalling OneNote for Windows 10

To finalize the migration and guarantee that users are accessing the correct version of OneNote, IT admins must uninstall the OneNote for Windows 10 app. If the app isn't removed, users could accidentally revert to the old version, leading to confusion and potential data sync problems.

You can customize this sample PowerShell function to uninstall OneNote for Windows 10 (UWP):

```powershell
function uninstallUWP { 
    $uwpApp = Get-AppxPackage | Where-Object {$_.Name -eq "Microsoft.Office.OneNote"} 
    if ($null -ne $uwpApp) { 
        $uwpApp | Remove-AppxPackage 
        writeLogsToFileAndConsole "OneNote UWP version uninstalled" 
    } 
}
```

## Related articles

- [OneNote for Windows 10 migration guidance](onenote-for-windows-10-migration-guide.md)
- [Frequently Asked Questions about OneNote in Office 2019 and Microsoft 365](https://support.microsoft.com/office/6582c7ae-2ec6-408d-8b7a-3ed71a3c2103)
- [OneNote help & learning](https://support.microsoft.com/onenote)
- [OneNote info for developers](https://developer.microsoft.com/onenote)
- [Deployment guide for OneNote](deployment-guide-onenote.md)
