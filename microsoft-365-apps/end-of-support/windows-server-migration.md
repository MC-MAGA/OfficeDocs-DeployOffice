---
title: "Microsoft 365 Apps migration from Windows Server "
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: o365-proplus-itpro
ms.collection: Tier1
ms.localizationpriority: medium
recommendations: false
description: "Provides guidance to Office admins on moving from Microsoft 365 Apps on Windows Server to either Windows 365 or Azure Virtual Desktop."
ms.date: 12/30/2024
---
# Microsoft 365 Apps migration from Windows Server

> [!NOTE]
> The information in this article is for organizations that host Microsoft 365 Apps on Windows Server 2016, 2019, 2022, or 2025.

Microsoft 365 Apps is supported on the following versions of Windows Server until the dates specified:

- Windows Server 2025: October 2029
- Windows Server 2022: October 2026
- Windows Server 2019: October 2025
- Windows Server 2016: October 2025

> [!NOTE]
> - Only Version 2302 or later of Microsoft 365 Apps is supported on Windows Server 2022.
> - For more information on support dates, see [Windows Server end of support and Microsoft 365 Apps](windows-server-support.md).

To stay current and maintain support as the [Modern Lifecycle Policy](/lifecycle/policies/modern) describes, consider migrating to one of the following client hosting solutions. These solutions might better meet your technical and business requirements.

- [Windows 365](#windows-365)
- [Azure Virtual Desktop](#azure-virtual-desktop)

## Windows 365

[Windows 365](https://www.microsoft.com/windows-365) is a complete software-as-a-service (SaaS) solution that securely streams your Windows experience—including your personalized apps, content, and settings—from the Microsoft cloud to any device.

The Windows 365 service hosts [Cloud PCs](/windows-365/overview#what-is-a-cloud-pc), which are highly available, optimized, and scalable virtual machines that can provide your users with a rich Windows desktop experience.

For more information on Windows 365 plans and Cloud PC configurations available, visit the [Windows 365 Plans and Pricing](https://www.microsoft.com/windows-365/business/compare-plans-pricing) page.

Windows 365 requires no virtualization expertise and enables you to:

- Manage Cloud PCs in Microsoft Intune like other supported devices, including Microsoft 365 Apps.
- Choose preconfigured Cloud PCs (including RAM, CPU, and storage), and then use [resize](/windows-365/enterprise/resize-cloud-pc) as needs change.
- Automatically provision on-demand Cloud PCs using standard gallery images or custom images.
- Request assistance from Microsoft on application issues with [App Assure](https://www.microsoft.com/fasttrack/microsoft-365/app-assure) at no extra cost.
- Purchase Windows 365 licenses per user for a fixed monthly fee.

For more information about Windows 365 Enterprise, see the following resources:

- [Windows 365 frequently asked questions](https://www.microsoft.com/windows-365/faq)
- [Requirements for Windows 365](/windows-365/enterprise/requirements)
- [Planning guide for Windows 365](/windows-365/enterprise/planning-guide)

## Azure Virtual Desktop

[Azure Virtual Desktop](https://azure.microsoft.com/services/virtual-desktop/) is a highly flexible desktop and app virtualization service that runs on the cloud. It provides you with full control, via the Azure portal, to customize virtual desktop management and deployment based on your organization’s needs.

Azure Virtual Desktop enables you to:

- Create a full desktop virtualization environment in your Azure subscription without running any gateway servers.
- Lower costs and reduce operating system overhead using Windows 11 and Windows 10 Enterprise [multi-session capability](/azure/virtual-desktop/windows-multisession-faq).
- Maintain full control over management and deployment.
- Use standard gallery images or create custom images.
- Request assistance from Microsoft on application issues with [App Assure](https://www.microsoft.com/fasttrack/microsoft-365/app-assure) at no extra cost.
- Pay only for what you use on the service (consumption-based pricing).

For more information, see the following resources:

- [What is Azure Virtual Desktop?](/azure/virtual-desktop/overview)
- [Prerequisites for Azure Virtual Desktop](/azure/virtual-desktop/prerequisites)
- [Use the quickstart to create a sample infrastructure](/azure/virtual-desktop/quickstart)

### On-premises session host deployment

> [!IMPORTANT]
> Azure Stack HCI is now part of Azure Local. Product documentation renaming is in progress. However, older versions of Azure Stack HCI, for example 22H2, will continue to reference Azure Stack HCI and won't reflect the name change. [Learn more](https://aka.ms/azloc-promo).

If an on-premises session host deployment is required, Azure Virtual Desktop on Azure Local allows you to deploy session hosts to your on-premises Azure Local infrastructure. This configuration addresses compliance requirements for on-premises data storage and improves performance for Azure Virtual Desktop users in areas with limited connectivity to the Azure public cloud.

Azure Virtual Desktop service components, including host pools, workspaces, and application groups, remain deployed in Azure. However, session hosts can now be deployed on Azure Local instances. This approach supports scenarios where data locality or enhanced performance is critical.

To deploy Azure Virtual Desktop on Azure Local, your Azure Local instances must be running a minimum of version 23H2 and registered with Azure. Supported operating systems for session hosts include Windows 11 Enterprise multi-session, Windows Server 2022, and other current Windows versions. Licensing and activation must align with Azure Local requirements, and the Azure Connected Machine agent is required for communication with Azure Instance Metadata Service.

For more information, see [Azure Virtual Desktop on Azure Local](/azure/virtual-desktop/azure-local-overview).

## Additional information

### End of support dates for Windows Server

Support for Windows Server itself isn't impacted. Here are the end-of-support dates for Windows Server:

- Windows Server 2025: October 2034
- Windows Server 2022: October 2031
- Windows Server 2019: January 2029
- Windows Server 2016: January 2027

For more information, go to the [Search Product and Services Lifecycle Information](/lifecycle/products/) page.

### Support for virtual Windows client devices on Windows Server

Hosting virtual Windows client devices with Microsoft 365 Apps on Windows Server remains supported as long as the Windows Server version is supported.
