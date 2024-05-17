---
title: "Configure the iOS app for Microsoft Places"
ms.author: mactra
author: MachelleTranMSFT
manager: jtremper
ms.date: 05/16/2024
audience: ITPro
ms.topic: conceptual
ms.service: o365-proplus-itpro
ms.collection: Tier3
ms.localizationpriority: medium
recommendations: true
description: "Instructions on how to install the Microsoft Places mobile app (iOS only)."
---
# Configure the iOS app for Microsoft Places

To enable the Microsoft Places mobile experience, an IT admin might need to configure the Mobile Application Management (MAM), and users must install Apple’s TestFlight app and the Places app on their iOS devices. This article explains each of these steps.

- These instructions are only in effect for the Private and Public Previews. Testing is managed through Apple’s TestFlight platform.

- TestFlight is an application and service owned by Apple. It's offered to app developers to make it easy to invite users to test apps and collect feedback before releasing their apps in the App Store.

- The Places mobile app can be made available to Private and Public Preview customers and their users who have iOS devices (version 16.4 or later).  

- Because the Places mobile app is still in its pilot phase and not yet available in the App Store, to allow Preview customers to install and test the application we've made the Places mobile iOS available (installed through Apple TestFlight).

## Prerequisites
> [!NOTE]
> The Microsoft Places iOS app is an opt-in feature. For more information, see [Opt in to the Microsoft Places Public Preview](opt-in-places-preview.md).

- Places is Deployed. For more information, see the [Deployment guide for Microsoft Places (preview)](deployment-guide-for-places.md).

- If applicable, your organization’s MAM policy should allow your users to download and install the Apple TestFlight app so they can install, run, and experience the Places iOS.

- If applicable, your organization’s MAM policy needs to be updated to allow employees to install the Places Mobile App (see guidance below).

## Enable Places mobile for your users

Run the following PowerShell cmdlet to enable the opt-in features for your tenant.

```powershell
Set-PlacesSettings -Collection Places -EnablePlacesMobileApp ‘Default:true' 
```

## Places mobile app installation

To install the Places mobile experience (iOS only), an IT admin must update their Intune MAM policy (if applicable). Pilot users need to install the Places app on their mobile devices.

The mobile access installation process is made up of these four steps.

|Step  |Action     |Owner     |
|---------|---------|---------|
|**1**|Review and update mobile policies, if applicable  |Customer IT admin or mobile-security admin  |
|**2**|TestFlight URL is provided through the Opt-In process |Microsoft Places team |
|**3**|Customer distributes the URL to their pilot users |Customer IT admin |
|**4**|The customer's pilot users click on the URL to follow the instructions on the website. They'll install TestFlight, then go back to the URL and join the beta by clicking the Start Testing button. |Pilot users |

> [!NOTE]
> It's a one-time process to install the Places app on your iOS device. Once the Places app is installed, users can open it from their mobile home screens.

### Steps for iOS Places app enablement and installation

#### Step 1: Review and update your mobile policies (IT admin)

- See the MAM Intune configurations section for details and confirmation if your organization requires additional Unified Endpoint Management configuration.

#### Step 2: TestFlight URL is provided through the Opt-In process (Places team)

- During the opt-in process you'll be provided a TestFlight URL that grants access to install the app through TestFlight.

#### Step 3: The IT admin shares the URL to their users (IT admin)

- The IT admin shares the URL with the iOS pilot users in their tenant.

   The following path is a sample URL:

   ![Screenshot of a sample URL to be shared by admins.](../images/places/configure-ios-app-001.png)

> [!NOTE]
> Users must be part of the Opt-in features and the EnablePlaceMobileApp should be set to **default:true**.

#### Step 4: Users click on the URL to download and install the Places iOS app (pilot users)

1. Users navigate to the URL provided by their tenant admin in the browser of the user’s mobile device.
2. The Apple TestFlight app installation directs users to a two-step process to install the Places app. First, install the TestFlight app. Second, return to the URL and tap on **Start Testing.** This launches the TestFlight app on the device and makes the user eligible to install the Places app.

   ![Screenshot of the TestFlight app install on a mobile device.](../images/places/configure-ios-app-002b.png)

3. In the TestFlight app, find the listing for **Microsoft Places** and tap **Install**.

   ![Screenshot of the Microsoft Places app install on a mobile device.](../images/places/configure-ios-app-003.png)

4. Turn on the auto-updates feature to get access to new versions of the app on your mobile device (this feature is an optional step).

   ![Screenshot of the Microsoft Places automatic-updates setting on a mobile device.](../images/places/configure-ios-app-004.png)

5. Open and sign in to the Places mobile app.

   Once the Places app is installed, it shows up in the user's dashboard like any other app installed from the App Store.

   You can tap to open the app and sign in using your corporate credentials that has access to Places opt-in features.

   ![Screenshot of the Places app on a mobile device home screen.](../images/places/configure-ios-app-005.png)

> [!NOTE]
> If you no longer want to test the app, you can also delete it yourself as a tester by visiting the app’s **Information** page in TestFlight and tapping **Stop Testing**.”

## MAM Intune configurations

### Mobile policy scenarios

Read the following four scenarios to determine what action your organization might need to take to allow installation and use of the Places iOS app.

|Scenario  |Action     |
|---------|---------|
|**1**|No Intune Policy.<br>If no Intune policy is applied at your organization, no additional steps are needed to install and run Places through TestFlight. You can skip the rest of the Intune setup instructions.|
|**2**|Mobile Device Management (MDM) as the only Intune Policy (no MAM policy applied).<br>If there is an MDM only Intune Policy applied for all employees in your organization, there are no additional steps needed to install and run MS Places through test flight. You can skip the rest of the Intune setup instructions.  |
|**3**|MDM policy applicable for few employees while MAM policy for others.<br>For employees who are on an MDM only policy, there are no other steps. For employees on MAM policy, see scenario 4. |
|**4**|MAM only or MAM with MDM Policy.<br>Follow the Intune setup instructions to perform similar actions in your organization’s Unified Endpoint Management system.  |

> [!NOTE]
> To learn more about creating Intune policies for custom apps, see "Create an iOS/iPadOS or Android app protection policy" in [How to create and assign app protection policies](/mem/intune/apps/app-protection-policies).

## Add a custom app in your organization’s Intune MAM

The following procedure adds the bundle ID of the Places iOS app as a custom app in an organization’s InTune MAM policy.

1. Click on **Endpoint security** from left menu and navigate to **Endpoint Security Overview**. Then click on **Conditional access**.

   ![Screenshot of the Endpoint security choices.](../images/places/configure-ios-app-010.png)

2. In **Conditional access**, click on **View all policies** to see all of the deployed conditional-access policies.

   ![Screenshot of the Conditional Access overiew.](../images/places/configure-ios-app-011.png)

3. The following summary shows all of the **Policies** for the tenant.

   ![Screenshot of the Policies overiew.](../images/places/configure-ios-app-012.png)

4. Click on **Require approved client apps and app protection policies**, which opens the policy details.

   ![Screenshot of the Required approved client apps and protection policies overview.](../images/places/configure-ios-app-013.png)

5. Under **Access controls**, then **Grant,** enable the **Require app protection policy** option along with the existing policy **Required approved client app**. Then below that section, under **For multiple control**, choose **Require one of the selected controls**.

   ![Screenshot of the Require on the selected apps option.](../images/places/configure-ios-app-014.png)

6. To enable MAM CA protection for the Places app, from the **Intune admin center** home page, navigate to **Apps**, then to **App protection policies**.

   ![Screenshot of the Intune amnin center and App protection policies option.](../images/places/configure-ios-app-015b.png)

   Select your existing app protection policy, then under **Properties**, select **Apps Edit.**
 
   ![Screenshot of your existing app protection policy and the Apps edit option.](../images/places/configure-ios-app-019b.png)
 
   Scroll to the **Custom apps** section, and select **+ Select custom apps**.

   ![Screenshot of the app protection policies option.](../images/places/configure-ios-app-016.png)

   Add the bundle ID **com.microsoft.msplaces** in the text box, and click **Add**.

   ![Screenshot of the Select public apps and Select custom apps option.](../images/places/configure-ios-app-018.png)

   After adding, select the app bundle ID from the list to move to the **Selected Apps** section, and click **Select**.

   ![Screenshot showing the Select apps to target and the Bundle ID.](../images/places/configure-ios-app-017.png)

