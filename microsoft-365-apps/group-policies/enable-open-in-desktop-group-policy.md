---
title: "Enabling Open in Desktop Setting by Group Policy"
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: reference
ms.service: o365-proplus-itpro
ms.localizationpriority: medium
ms.collection: Tier1
recommendations: false
description: "This article describes how tenant admins can enable the Open in Desktop feature using Group Policy."
ms.date: 01/28/2025
---

# Enabling Open in Desktop Setting by Group Policy

The Open in Desktop Group Policy setting allows tenant admins to configure Word, Excel, and PowerPoint file links hosted in OneDrive and SharePoint to open in desktop applications by default. This setting applies only to Windows users. It's useful for tenants with compliance, policy, or usability requirements that necessitate opening files in desktop applications.

## Scope of the setting

The Open in desktop group policy applies to file links hosted in OneDrive and SharePoint and opened from Word, Excel, PowerPoint, and classic Outlook.

## In app file open setting and group policy interaction

When you enable this group policy, file links from Word, Excel, and PowerPoint opened from classic Outlook, Word, Excel, or PowerPoint apps open in their respective desktop app. This ensures that users can access files in the desktop app environment by default.

If a user [sets a different file opening preference](https://support.microsoft.com/topic/7c1a08d0-54d0-499e-992e-2c41f70b59a1) from within the application, their preference overrides the tenant-admin-defined Group Policy. This setting allows individual users to maintain control over their default file opening behavior, even when the policy is in effect.

## Policy scope

This group policy applies to file links opened from classic Outlook, Word, Excel, and PowerPoint.

> [!NOTE]
> The setting that this group policy controls is independent of the SharePoint site admin setting to open files in the Microsoft 365 desktop app. The SharePoint site admin setting is only effective for files opened from the SharePoint or One Drive web page.

## Policy behavior

- **Enabled**: Files open in desktop applications (Word, Excel, and PowerPoint) by default.
- **Disabled**: Files open in a web browser by default.
- **Not Configured**: The system determines the default behavior, typically opening files in a web browser.

> [!NOTE]
> This policy applies only to Microsoft 365 apps.

## Registry information

To manually configure this setting via the registry, use the following details:

- **Registry Hive**: `HKEY_CURRENT_USER`
- **Registry Path**: `software\policies\microsoft\office\16.0\common\internet`
- **Value Name**: `linksopenrightdefaultsettingisnative`
- **Value Type**: `REG_DWORD`
- **Enabled Value**: `1`
- **Disabled Value**: `0`
