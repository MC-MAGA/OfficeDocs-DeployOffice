---
title: "Configure Microsoft 365 apps for shared device mode on iOS/iPadOS"
ms.author: chinmayjain
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: o365-proplus-itpro
ms.subservice: office-mac
ms.localizationpriority: medium
ms.collection: Tier3
recommendations: false
description: "Provides information to admins on how to set up and configure shared iOS device mode"
ms.date: 01/09/2025
---

# Configure Microsoft 365 apps on iOS for shared device mode

This article provides guidance on setting up shared device mode for Microsoft 365 Apps on iOS/iPadOS devices. Shared device mode enables multiple users to securely share the same device while accessing Microsoft 365 Apps. The configuration process involves enrolling devices, assigning necessary applications, and applying a configuration policy to enable shared device mode.

### Prerequisites

To configure shared device mode for Microsoft 365 Apps on iOS devices, the device must first be set up in shared device mode. This setup can be completed using [Microsoft Intune](/mem/intune/enrollment/automated-device-enrollment-shared-device-mode) or a supported Mobile Device Management (MDM) solution. 

For guidance on setting up shared device mode for iOS devices, see [Shared device mode for iOS devices](/entra/msal/objc/shared-devices-ios). Ensure that the shared device mode configuration is complete before proceeding to the steps specific to Microsoft 365 Apps.

### Assign Microsoft 365 apps and configure shared device mode

To enable shared device mode for Microsoft 365 apps on iOS devices, set up the device in shared device mode first. Use Microsoft Intune or a supported MDM solution to complete this configuration.

For guidance on setting up shared device mode, including assigning apps to devices, assigning groups, and configuring general app policies, see [Shared device mode for iOS devices](/entra/msal/objc/shared-devices-ios).

Once the device is set up, follow these steps to configure Microsoft 365 apps for shared device functionality:

1. Navigate to **Apps > App Configuration Policies > Add > Managed Device** in your MDM portal.
2. Provide a name for the configuration policy (for example, "Shared Device Mode Policy").
3. Under **Platform**, select **iOS/iPadOS**.
4. Select **Select app**, then choose the Microsoft 365 app you want to configure (such as Unified Microsoft 365, Word, Excel, or PowerPoint), and select **OK**.
5. In the **Settings** tab, under **Configuration settings format**, select **Use configuration designer**.
6. Add the following key-value pair:
   - **Configuration key**: `shareddevicemodeenabled`
   - **Value type**: `Boolean`
   - **Configuration value**: `true`
7. Save and deploy the configuration policy to the devices that require Microsoft 365 apps in shared device mode.
