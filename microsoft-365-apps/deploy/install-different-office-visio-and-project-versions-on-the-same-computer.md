---
title: "Supported scenarios for installing different versions of Office, Project, and Visio on the same computer"
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: o365-proplus-itpro
ms.collection: Tier1
ms.localizationpriority: medium
recommendations: true
description: "Provides IT admins with information about which versions of Office, Project, and Visio can be installed together on the same computer."
ms.date: 11/01/2024
---

# Supported scenarios for installing different versions of Office, Project, and Visio on the same computer

In many cases, you can install Office, Project, and Visio on the same computer. However, there are some combinations of Office, Project, and Visio that can't be installed together.

The two main factors that determine compatibility are the [version](#office-releases-and-their-version-number) of the product and the [installation technology](#installation-technologies-used-by-office). The following rules govern compatibility:

- You can't install two products with the same version but different installation technologies.
- You can't install two products of different versions if both use Click-to-Run and have overlapping Office applications.

See the [example installation scenarios](#example-installation-scenarios) section for supported and unsupported scenarios, with explanations.

## Office releases and their version number

The following table lists supported Office releases, their versions, and installation technology. This information applies to Project and Visio as well.

| Office release                                      | Version | Installation technologies                     |
|-----------------------------------------------------|---------|-----------------------------------------------|
| Microsoft 365                                       | 16.0    | Click-to-Run                                  |
| Office Long Term Servicing Channel (LTSC) 2024      | 16.0    | Click-to-Run                                  |
| Office LTSC 2021                                    | 16.0    | Click-to-Run                                  |
| Office 2021                                         | 16.0    | Click-to-Run                                  |
| Office 2019                                         | 16.0    | Click-to-Run                                  |
| Office 2016                                         | 16.0    | Click-to-Run, Windows Installer (MSI)         |

Find this version information in **Control Panel** > **Programs and Features** or in an app’s **About** dialog, for example, **File** > **Account** > **About Word**. For more information, see [Find details for other versions of Office](https://support.microsoft.com/office/8e83dd74-3b83-4528-bda6-6ff6118f8293).

> [!NOTE]
> - Microsoft 365, Office LTSC 2024, Office LTSC 2021, Office 2021, Office 2019, and Office 2016 share the same version number: 16.0.
> - Office 2013, which is no longer supported, had version 15.0.
> - Office 2010, also unsupported, had version 14.0 and used Windows Installer (MSI).

## Installation technologies used by Office

Office, Project, and Visio can be purchased through a Microsoft 365 plan, as a one-time purchase, or via a volume licensing agreement. The purchase method and Office version—such as Microsoft 365 or Office 2016—determine the installation technology used.

There are two types of installation technology covered here:

- Click-to-Run
- Windows Installer (MSI)

To check the installation technology in newer releases, go to **File** > **Account** in an Office app and look under **Product Information**.

You can also identify a Click-to-Run installation by the presence of **Update Options** in **Product Information**. If **Update Options** isn't shown, the installation uses Windows Installer (MSI).

## Example installation scenarios

Here are some example installation scenarios with explanations for whether they're supported.

| Products to install                                       | Supported?                  | Explanation                                                                  |
|----------------------------------------------------------|----------------------------|-----------------------------------------------------------------------------|
| Microsoft 365 Apps + Visio LTSC Professional 2024 (volume licensed) | Yes, with a caveat<sup>1</sup> | Both use Click-to-Run and are the same version (16.0).                     |
| Microsoft 365 Apps + Project Standard 2024 (retail)      | Yes, with a caveat<sup>1</sup> | Both use Click-to-Run and are the same version (16.0).                      |
| Microsoft 365 Apps + Visio LTSC Professional 2021 (volume licensed)  | Yes, with a caveat<sup>2</sup>   | Both use Click-to-Run and are the same version (16.0).                     |
| Microsoft 365 Apps + Project Standard 2021 (retail)      | Yes, with a caveat<sup>2</sup>  | Both use Click-to-Run and are the same version (16.0).                      |
| Microsoft 365 Apps + Project Professional 2019 (volume licensed) | Yes, with a caveat<sup>3</sup> | Both use Click-to-Run and are the same version (16.0).                      |
| Microsoft 365 Apps + Visio Standard 2019 (retail)        | Yes, with a caveat<sup>3</sup> | Both use Click-to-Run and are the same version (16.0).                      |
| Office Professional Plus 2019 (volume licensed) + Visio Professional 2016 (volume licensed) | No, alternative available  | Different installation technologies (Click-to-Run vs. MSI), but same version (16.0).<br>See [Use the Office Deployment Tool to install volume licensed versions of Project 2016 and Visio 2016](use-the-office-deployment-tool-to-install-volume-licensed-editions-of-visio-2016.md) |
| Microsoft 365 Apps + Visio Professional 2016 (volume licensed) | No, alternative available | Different installation technologies, same version (16.0).<br>See [Use the Office Deployment Tool to install volume licensed versions of Project 2016 and Visio 2016](use-the-office-deployment-tool-to-install-volume-licensed-editions-of-visio-2016.md) |

<sup>1</sup> Requires Version 2408 of Microsoft 365 Apps or later for compatibility with Project 2024, Visio LTSC 2024, and Visio 2024.  
<sup>2</sup> Requires Version 2108 of Microsoft 365 Apps or later for compatibility with Project 2021, Visio LTSC 2021, and Visio 2021.  
<sup>3</sup> Requires Version 1808 of Microsoft 365 Apps or later for compatibility with Office 2019 products.

## Additional information

- All installed products must match in bit (32-bit or 64-bit) version. For example, you can't install a 32-bit version of Visio on the same computer with a 64-bit version of Office.
- Volume licensed versions of Office LTSC 2024, Office LTSC 2021, and Office 2019 use Click-to-Run, while Office 2016 uses Windows Installer (MSI).
- Products installed on the same computer must use the same [update channel](../updates/overview-update-channels.md). For example, the volume licensed version of Office Professional Plus 2019 can only use the PerpetualVL2019 update channel.
- Volume licensed Project and Visio installations must be configured to use the same update channel as Microsoft 365 Apps.
- Only subscription versions of Project and Visio receive regular feature updates; volume licensed versions don't.

## Related articles

- [Deployment guide for Project](deployment-guide-for-project.md)
- [Deployment guide for Visio](deployment-guide-for-visio.md)
