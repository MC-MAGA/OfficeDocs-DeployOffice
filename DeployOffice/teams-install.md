---
title: "Deploy Microsoft Teams with Microsoft 365 Apps"
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: o365-proplus-itpro
ms.collection: Tier2
ms.localizationpriority: medium
recommendations: false
description: "Provides Office admins with an overview of how Microsoft Teams is automatically installed with Microsoft 365 Apps."
ms.date: 03/25/2024
---

# Deploy Microsoft Teams with Microsoft 365 Apps

> [!IMPORTANT]
> As of October 23rd, 2023, new installations of Microsoft 365 and Office 365 will include Teams only if a Teams service plan is in place. For more information on available plans, see [Microsoft Teams service description](/office365/servicedescriptions/teams-service-description#available-plans)

> [!NOTE]
> The new Teams client is not bundled with the Microsoft 365 Apps offline package. For new installations of Microsoft 365 Apps, an active internet connection is required to download the new Teams app. In cases where an internet connection is unavailable during the installation of Microsoft 365 Apps, [admins will need to deploy new Teams client separately](/MicrosoftTeams/new-teams-bulk-install-client).

In the past, Microsoft Teams was a separate installation from Microsoft 365 Apps. But starting with Version 1902, Teams was included as part of ***new*** installations of Microsoft 365 Apps. If Teams was already installed on the device, no changes were made to that installation of Teams.

In late August, the new Teams began installing with ***new*** and ***existing*** installations of Microsoft 365 Apps on Windows. Users can opt to try the new Teams using the "Try the new Teams" toggle switch in classic Teams or, admins can [bulk deploy the new Microsoft Teams client](/MicrosoftTeams/new-teams-bulk-install-client).

> [!NOTE]
> To complete the installation of Teams on new or existing installations of Microsoft 365 Apps, either restart the device or have the user log off and log back on. If the classic Teams app is already installed, the Microsoft 365 Apps deployment will install new Teams alongside classic Teams on the device. The classic Teams installation will not change.

If Skype for Business is already installed on the device, Skype for Business isn't removed and continues to function as before. Skype for Business continues to be installed with new installations of Microsoft 365 Apps, unless you configure your installation to exclude it.

We also have the steps you can take to exclude Teams from [new](#how-to-exclude-microsoft-teams-from-new-installations-of-microsoft-365-apps) or [existing](#what-about-existing-installations-of-microsoft-365-apps) installations of Microsoft 365 Apps if your organization isn't ready to deploy Teams.

> [!IMPORTANT]
> If you're in a GCC High or DoD environment, currently you need to exclude Teams from being installed with Microsoft 365 Apps. Instead, you need to install Teams by using the separate MSI-based installer. For links to the correct version of the MSI-based installer for your environment, see [Install Microsoft Teams using Microsoft Configuration Manager](/MicrosoftTeams/msi-deployment). In the future, you'll be able to install Teams along with Microsoft 365 Apps in GCC High or DoD environments without needing to use the separate MSI-based installer.

If you're using Office for Mac, see [Microsoft Teams installations on a Mac](#microsoft-teams-installations-on-a-mac).

If you're using shared computers or Virtual Desktop Infrastructure (VDI), see [Shared computer and VDI environments with Microsoft Teams](#shared-computer-and-vdi-environments-with-microsoft-teams).


## When did Microsoft Teams start being included with new installations of Microsoft 365 Apps?

The date that Teams was included with ***new*** installations of Microsoft 365 Apps depended on which [update channel](updates/overview-update-channels.md) you were using. The following table shows the schedule.

| Update channel | Version | Date |
|---------|---------|---------|
|Current Channel |Version 1902 | March 4, 2019  |
|Monthly Enterprise Channel |Version 2003 | May 12, 2020  |
|Semi-Annual Enterprise Channel (Preview)| Version 1902   | March 12, 2019  |
|Semi-Annual Enterprise Channel| Version 1902  |July 9, 2019 |

> [!NOTE]
> Teams is also included with the following ***new*** installations:
> - Microsoft 365 Apps for business, starting with Version 1901, which was released on January 31, 2019. Microsoft 365 Apps for business is the version of Office that's included with some Microsoft 365 business plans, such as Microsoft 365 Business Premium.
> - Office for Mac, starting with Version 16.21, which was released on January 16, 2019. Office for Mac comes with any plan that includes Microsoft 365 Apps. For more information, see [Microsoft Teams installations on a Mac](#microsoft-teams-installations-on-a-mac).

## When will installations of Microsoft 365 Apps include the new Teams?

> [!NOTE]
> After the new Teams is installed, users will automatically switch to the new Teams. Afterward, they can switch back to classic Teams by selecting the "New Teams" toggle switch.

The date when the new Microsoft Teams starts being installed with Microsoft 365 Apps depends on which update channel you're using. The following table shows the schedule.

| Plan | Channel | Date |
|---------|---------|---------|
|Business | |Late September 2023 |
|Enterprise |Office Beta Channel and Current Channel (Preview) |Late September 2023 |
|Enterprise |Current Channel |October 2023 |
|Enterprise |Monthly Enterprise Channel and Semi-Annual Enterprise Channel (Preview) |November 2023|
|Enterprise |Semi-Annual Enterprise Channel |December 2023| 

## How to exclude Microsoft Teams from new installations of Microsoft 365 Apps

If you don't want Teams included when you install Microsoft 365 Apps on devices running Windows, you can use [Group Policy](#use-group-policy-to-control-the-installation-of-microsoft-teams) or the Office Deployment Tool (ODT). As an alternative, you can let Teams be installed, but use Group Policy to [prevent Teams from automatically starting](#use-group-policy-to-prevent-microsoft-teams-from-starting-automatically-after-installation) when the user signs in to the device.

If you want to use the [Office Deployment Tool](overview-office-deployment-tool.md), you can use the [ExcludeApp element](office-deployment-tool-configuration-options.md#excludeapp-element) in your configuration.xml file, as shown in the following example.

```xml
<Configuration>
   <Add OfficeClientEdition="64" Channel="Current">
      <Product ID="O365ProPlusRetail">
       <Language ID="en-us" />
       <ExcludeApp ID="Teams" />
      </Product>
      <Product ID="VisioProRetail">
       <Language ID="en-us" />
      </Product>
      <Product ID="ProjectProRetail">
       <Language ID="en-us" />
      </Product>
      <Product ID="LanguagePack">
       <Language ID="de-de" />
      </Product>
    </Add>
</Configuration>
```

> [!TIP]
> Instead of using a text editor to create your configuration.xml, we recommend that you use the [Office Customization Tool (OCT)](https://config.office.com). The OCT provides a web-based interface for making your selections and creating your configuration.xml file to be used with the ODT. For more information, see [Overview of the Office Customization Tool](admincenter/overview-office-customization-tool.md).

If you're deploying Microsoft 365 Apps by using the Office 365 Client Installation wizard in Microsoft Configuration Manager (current branch), you can set **Teams** to the **Off** position in the configuration UI.

If you're deploying Microsoft 365 Apps by using Microsoft Intune, there's a checkbox to exclude Teams on the **Configure App Suite** pane.  

If you're letting your users install Microsoft 365 Apps for themselves from the Office 365 portal, you can't exclude Teams from being included as part of the installation, unless you use [Group Policy](#use-group-policy-to-control-the-installation-of-microsoft-teams).

To remove Teams after it's installed, go to **Control Panel** > **Uninstall a program** and uninstall **Microsoft Teams** and any instances of **Teams Machine-Wide Installer**. If you previously installed Teams separately from installing Microsoft 365 Apps, you might see multiple instances of **Teams Machine-Wide Installer**. You can also use PowerShell to remove Teams as shown in this [script sample](/microsoftteams/scripts/powershell-script-teams-deployment-clean-up).


## What about existing installations of Microsoft 365 Apps?

Teams was added to ***existing*** installations of Microsoft 365 Apps on devices running Windows as part of the normal update process. There was no change to existing installations of Mac.

The installed version and the update version determine the addition of Teams to existing Microsoft 365 Apps installations. Version 1906 that was released in Current Channel in July 2019 was the first version that included Teams as part of the update process. However, the rollout was phased, so not all devices updating to Version 1906 or subsequent versions immediately received Teams. As of Version 1908 or later, Teams was added to all Microsoft 365 Apps installations. 

The date when Teams was added to ***existing*** installations of Microsoft 365 Apps depended on the update channel you were using. The following table shows the schedule.

| Update channel | Version | Date |
|---------|---------|---------|
|Current Channel |Version 1906 | July 9, 2019  |
|Monthly Enterprise Channel |Version 2003 | May 12, 2020  |
|Semi-Annual Enterprise Channel (Preview)| Version 1908  | September 10, 2019  |
|Semi-Annual Enterprise Channel| Version 1908  | January 14, 2020 |

If you don't want Teams to be added to ***existing*** installations of Microsoft 365 Apps when you update to a newer version, follow these steps to opt out. 

1. Sign in to the [Microsoft 365 Apps admin center](https://config.office.com) with an admin account.
2. Go to **customize** > **Device Configuration** > **Modern Apps Settings**. 
3. Select **Microsoft Teams (work or school)**, then clear the **Enable automatic installation of new Microsoft Teams** check box.  

Use [Group Policy](#use-group-policy-to-control-the-installation-of-microsoft-teams) or the ODT. As an alternative, you can let Teams be added, but use Group Policy to [prevent Teams from automatically starting](#use-group-policy-to-prevent-microsoft-teams-from-starting-automatically-after-installation) when the user signs in to the device.

If you want to use the [Office Deployment Tool](overview-office-deployment-tool.md), you need to run the ODT in /configure mode on each device before you update to the new version of Microsoft 365 Apps. Use this configuration.xml file with the ODT to exclude Teams from being added to your existing installation of Microsoft 365 Apps for enterprise.

```xml
<Configuration>
   <Add Version="MatchInstalled">
      <Product ID="O365ProPlusRetail">
       <Language ID="MatchInstalled" TargetProduct="All" />
       <ExcludeApp ID="Teams" />
      </Product>
   </Add>
   <Display Level="None" />
</Configuration>
```

> [!NOTE]
> - Be sure you're using the most current version of the ODT available on the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49117).
> - If your existing installation of Microsoft 365 Apps has excluded other apps, such as Access, you need to include a line in your configuration.xml file for each of those excluded apps. Otherwise, those apps will be installed on the device.
> - If you have Microsoft 365 Apps for business installed, use O365BusinessRetail for the Product ID in your configuration.xml file.

Also, in some situations, doing an Online Repair results in Teams being installed. For example, if Microsoft 365 Apps is configured to get updates from the Office Content Delivery Network (CDN) and the update channel or version you're using includes Teams as part of the installation.

## Use Group Policy to control the installation of Microsoft Teams

If your organization isn't ready to deploy Teams and you use Group Policy, you can enable the *Don't install Microsoft Teams with new installations or updates of Office* policy setting. You can find this policy setting under Computer Configuration\Policies\Administrative Templates\Microsoft Office 2016 (Machine)\Updates.

> [!NOTE]
> - This policy setting only applies if you are installing or updating to Version 1905 or later of Microsoft 365 Apps.
> - To use this policy setting, download at least version 4882.1000 of the [Administrative Template files (ADMX/ADML)](https://www.microsoft.com/download/details.aspx?id=49030), which were released on July 9, 2019.

If you enable this policy setting, Teams isn't installed in the following scenarios for Version 1905 or later:

- New installations of Microsoft 365 Apps
- Updates to existing installations of Microsoft 365 Apps
- Users installing Microsoft 365 Apps for themselves from the Office 365 portal
- An Online Repair of an existing installation of Microsoft 365 Apps

If you have Microsoft 365 Apps for business or can't use Group Policy for some other reason, you can add the preventteamsinstall value to the HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\16.0\common\officeupdate key in the registry. The type for preventteamsinstall is REG_DWORD and the value should be set to 1 if you don't want Teams installed.

## Use Group Policy to prevent Microsoft Teams from starting automatically after installation

If you need to install Teams without having it start automatically for the user post-installation, enable the *Prevent Microsoft Teams from starting automatically after installation* policy setting in Group Policy. You can find this policy setting under User Configuration\Policies\Administrative Templates\Microsoft Teams.

Enabling this policy setting before installing Teams prevents Teams from starting automatically when the user logs into the device. Once a user signs in to Teams for the first time, Teams is configured to start automatically the next time the user logs into the device. The user can configure Teams to not start automatically by configuring user settings within Teams or by clearing the **Open Teams on startup** check box on the sign in screen for Teams.

> [!TIP]
> If you've already installed Teams but you want to use this policy setting to prevent Teams from starting automatically, enable this policy setting and then [run this script](/MicrosoftTeams/scripts/powershell-script-teams-reset-autostart) on a per-user basis to reset the autostart setting for Teams.

But even if you enable this policy setting so that Teams doesn't start automatically, an icon for Microsoft Teams appears on the user's desktop.

> [!IMPORTANT]
> - This policy setting only applies if you are installing or updating to the following versions of Microsoft 365 Apps:
>    - Version 1906 or later of Current Channel
>    - Version 1902 or later of Semi-Annual Enterprise Channel or Semi-Annual Enterprise Channel (Preview)
>    - Version 2003 or later of Monthly Enterprise Channel
> - To use this policy setting, download at least version 4882.1000 of the [Administrative Template files (ADMX/ADML)](https://www.microsoft.com/download/details.aspx?id=49030), which were released on July 9, 2019.

If you have Microsoft 365 Apps for business or can't use Group Policy for some other reason, you can add the PreventFirstLaunchAfterInstall value to the HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Office\16.0\Teams key in the registry. The type for PreventFirstLaunchAfterInstall is REG_DWORD and the value should be set to 1 if you don't want Teams to automatically start after installation.

## Shared computer and VDI environments with Microsoft Teams

If devices in your organization are shared by multiple users, Teams is installed separately for each user that signs into that device. Installations of Teams average about 500 mb, so hard disk space, as well network bandwidth for updates, might become an issue for these shared devices installed with Teams. In cases where shared devices are used by a significant number of users, you might want to consider not installing Teams on those shared devices.

If you plan to use Teams in a Virtual Desktop Infrastructure (VDI) environment, see [Teams for Virtualized Desktop Infrastructure](/microsoftteams/teams-for-vdi). Teams installed with Microsoft 365 Apps as described in this article is ***NOT*** currently supported in VDI environments.

## Feature and quality updates for Microsoft Teams

After Teams is installed, it's automatically updated approximately every two weeks with new features and quality updates. This update process for Teams is different than the update process for the other Office apps, such as Word and Excel. For more information, see [Teams update process](/microsoftteams/teams-client-update).

## Microsoft Teams installations on a Mac

If you're using Version 16.21, or later, of the Office suite install package to deploy on a Mac, Teams is included as part of the installation.

If you don't want Teams included as part of the installation, there's an Office suite install package available that doesn't include Teams. You can also use the install packages for individual applications, such as Word or Excel. For links to the most current install packages, see [Update history for Office for Mac](/officeupdates/update-history-office-for-mac).  

If you're letting your users install Office for themselves on a Mac, such as from [https://teams.microsoft.com/downloads](https://teams.microsoft.com/downloads), you can't exclude Teams from being included as part of the installation.

To uninstall Teams on a Mac, quit Teams by right-clicking the Teams app in the dock, then hold down Option and choose **Force Quit**. Open the **Application Folder**, select **Microsoft Teams**, and move it to the **Trash**.

## What about Office 365 plans that don't include Microsoft Teams?

Some Office 365 plans include Microsoft 365 Apps, but don't include the Teams service. Teams is installed with Microsoft 365 Apps even if a plan doesn't have the Teams service.

For Office 365 plans that don't include the Teams service, a free trial version of Teams that's valid for one year is available. Your users can start using it when they sign in to Teams. For more information about this free trial version and providing your users access to it, see [Manage the Microsoft Teams Exploratory license](/microsoftteams/teams-exploratory).

## Additional information about installing Microsoft Teams

- There's no change to new or existing installations of Office 2019, such as Office Professional Plus 2019.
- Teams is installed with Microsoft 365 Apps in the same way that Teams is installed if you use the [MSI-based installer for Teams](/MicrosoftTeams/msi-deployment). For each new user that signs into the device, the Teams installer runs and the Teams application is installed in the user's AppData folder.
- The architecture (sometimes referred to as the *bitness*) of Teams and Microsoft 365 Apps installed on the device don't have to match. For example, you can install the 32-bit version of Teams on a device running the 64-bit versions of Microsoft 365 Apps. To change the architecture of Teams, for example from 32-bit to 64-bit, you need to uninstall the 32-bit version of Teams and then install the 64-bit version of Teams.
- If you previously excluded Teams and want to add it back (for example, by using the ODT), make sure the settings in your configuration.xml file match the bitness, channel, and excluded apps of your existing installation of Microsoft 365 Apps.
- For more information for IT Pros about Microsoft Teams, see [Microsoft Teams documentation](/MicrosoftTeams/Microsoft-Teams).
