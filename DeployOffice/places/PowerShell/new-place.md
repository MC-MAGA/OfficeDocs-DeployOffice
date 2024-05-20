---
title: "New-Place"
ms.author: mactra
author: MachelleTranMSFT
manager: jtremper
ms.reviewer: julia.foran
ms.date: 05/15/2024
audience: ITPro
ms.topic: conceptual
ms.service: o365-proplus-itpro
ms.collection: Tier3
ms.localizationpriority: medium
recommendations: true
description: "Places PowerShell cmdlet to create new places."
---

# New-Place

Use the New-Place cmdlet to create buildings or floors within your Places directory.

> [!NOTE]
> To create rooms or workspaces, you will need to continue to use the New-Mailbox cmdlet documented [here.](/powershell/module/exchange/new-mailbox)

## Syntax

### Building

```powershell
New-Place
 [-City]
 [-CountryOrRegion]
 [-Description]
 [-GeoCoordinates]
 [-Name]
 [-PostalCode]
 [-State]
 [-Street]
 [-ResourceLinks]
 [-Tags]
 [-Type]
```

#### Floor

```powershell
New-Place
 [-Description]
 [-Name]
 [-ParentId]
 [-ParentType]
 [-Tags]
 [-Type]
```

## Description

Microsoft Places experiences are dependent upon a fully set up hierarchy among your rooms/workspaces, floors, and buildings. Once buildings and floors are created, you can use ParentId define the hierarchy relationships between rooms/workspaces to floors and floors to buildings.

You need to be assigned permissions before you can run this cmdlet. You must have either the Exchange MailRecipients role or the Places TenantPlacesManagement role.

> [!CAUTION]
> You might find additional parameters in the PowerShell cmdlet, but those are not currently supported.  It is not recommended to use any parameter that is not documented on this page.

## Examples

### Example 1

This example creates a new building and a floor within that building.

```powershell
New-Place -Type Building -Name 'Building 3'
```

After Building 3 is created successfully, read its PlaceId to use when setting the ParentId on the floors.

```powershell
New-Place -Type Floor -Name 'Lobby' -ParentId f12172b6-195d-4e6e-8f4f-eb72e41de99a -ParentType Building
New-Place -Type Floor -Name '1' -ParentId f12172b6-195d-4e6e-8f4f-eb72e41de99a -ParentType Building
```

### Example 2

This example creates a new building with address information.

```powershell
New-Place -Name 'Building 3' -Type Building -Description 'Building 3 in North of Redmond Campus' -CountryOrRegion US -State WA -City Redmond -Street 'Street 3' -PostalCode 98052 -GeoCoordinates "47.644125;-122.122411"
```

### Example 3

This example creates a new building with resource links.

```powershell
New-Place -Name 'Building 3' -Type Building -ResourceLinks @{name="TestLink"; Value="https://contoso.com/"; type="Url"}'
```

## Parameters

### -City

The City parameter specifies the room's city. If the value contains spaces, enclose the value in quotation marks ("). The maximum length is 200 characters.

|Attribute|Description|
| -------- | -------- |
|Type:|String|
|Position:|Named|
|Default value:|None|
|Required:|False|
|Accept pipeline input:|False|
|Accept wildcard characters:|False|

### -CountryOrRegion

The CountryOrRegion parameter specifies the room's country or region. A valid value is a valid ISO 3166-1 two-letter country code (for example, AU for Australia) or the corresponding friendly name for the country (which might be different from the official ISO 3166 Maintenance Agency short name).

A reference for two-letter country codes is available at [Country Codes List](https://www.nationsonline.org/oneworld/country_code_list.htm).

Address information is used by the Places Explore page to show nearby buildings.

|Attribute|Description|
| -------- | -------- |
|Type:|CountryInfo|
|Position:|Named|
|Default value:|None|
|Required:|False|
|Accept pipeline input:|False|
|Accept wildcard characters:|False|

### -Description

The Description parameter specifies a descriptive label for the place. If the value contains spaces, enclose the value in quotation marks ("). The maximum length is 200 characters.

|Attribute|Description|
| -------- | -------- |
|Type:|String|
|Position:|Named|
|Default value:|None|
|Required:|False|
|Accept pipeline input:|True|
|Accept wildcard characters:|False|

### -GeoCoordinates

The GeoCoordinates parameter specifies the building's location in latitude, longitude, and (optionally) altitude coordinates. A valid value for this parameter uses one of the following formats:

* Latitude and longitude: For example, "47.644125;-122.122411"
* Latitude, longitude, and altitude: For example, "47.644125;-122.122411;161.432"

_Note: If period separators don't work for you, use commas instead._

|Attribute|Description|
| -------- | -------- |
|Type:|GeoCoordinates|
|Position:|Named|
|Default value:|None|
|Required:|False|
|Accept pipeline input:|False|
|Accept wildcard characters:|False|

### -Name

The Name parameter specifies the display name of the place. The maximum length is 200 characters.  

A building's display name is visible:

* In Outlook when users are setting up their work hours and location, they are able to select a building.
* In Places Explore page that shows who else is in the same building, nearby buildings, and more.
* In Places Finder as a filter when searching for a conference room or workspace.

A floor's display name is visible in Places Finder as a filter when searching for a conference room or workspace.

|Attribute|Description|
| -------- | -------- |
|Type:|String|
|Default value:|None|
|Required:|True|
|Accept pipeline input:|False|
|Accept wildcard characters:|False|

### -ParentId

The ParentId parameter specifies the ID of a Place in the parent location hierarchy in Microsoft Places.  

* A room or workspace should have a parent floor. _(optional in the cmdlet, but without this parameter set, Places experiences will be very limited)_
* A floor must have a parent building. _(required)_

Once the ParentId has been set on a room or workspace, legacy room/workspace properties that are actually about the floor (such as floor number) or about the building (such as address and location information) will be read-only for that room/workspace using Set-PlaceV3. The same properties can be updated by updating the Floor or Building directly using Set-PlaceV3.

|Attribute|Description|
| -------- | -------- |
|Type:|String|
|Position:|Named|
|Default value:|None|
|Required:|False|
|Accept pipeline input:|False|
|Accept wildcard characters:|False|

### -ParentType

The ParentType parameter specifies the type of the place that is being set as the parent. Valid values are:

* Building
* Floor

_This property is currently required if you are setting ParentId, but we plan to deprecate it soon because ParentId is sufficient to validate parent type._

|Attribute|Description|
| -------- | -------- |
|Type:|String|
|Position:|Named|
|Default value:|None|
|Required:|False|
|Accept pipeline input:|False|
|Accept wildcard characters:|False|

### -PostalCode

The PostalCode parameter specifies the room's postal code. The maximum length is 200 characters.

|Attribute|Description|
| -------- | -------- |
|Type:|String|
|Position:|Named|
|Default value:|None|
|Required:|False|
|Accept pipeline input:|False|
|Accept wildcard characters:|False|

### -ResourceLinks

The ResourceLinks parameter specifies external links that should be associated to this building, such as a dining menu, a link to services or a building website.

The value must be provided as an array of type Link. For each link you need to pass the properties: Name, Value, and Type. For type the possible values are: Unspecified, BlobId, Url:
`-ResourceLinks @{name="TestLink"; Value="https://contoso.com/"; type="Url"}`. The maximum length is 200 characters.

|Attribute|Description|
| -------- | -------- |
|Type:|Link[]|
|Position:|Named|
|Default value:|None|
|Required:|False|
|Accept pipeline input:|False|
|Accept wildcard characters:|False|

### -State

The State parameter specifies the room's state or province. The maximum length is 200 characters.

|Attribute|Description|
| -------- | -------- |
|Type:|String|
|Position:|Named|
|Default value:|None|
|Required:|False|
|Accept pipeline input:|False|
|Accept wildcard characters:|False|

### -Street

The Street parameter specifies the room's physical address. The maximum length is 200 characters.

|Attribute|Description|
| -------- | -------- |
|Type:|String|
|Position:|Named|
|Default value:|None|
|Required:|False|
|Accept pipeline input:|False|
|Accept wildcard characters:|False|

### -Tags

The Tags parameter specifies additional features of the room (for example, details like the type of view or furniture type). There's no maximum length currently.

You can specify multiple labels separated by commas. If the labels contains spaces, enclose the values in quotation marks: `"Label 1","Label 2",..."Label N"`.

_Note: The entire set will be replaced on update. To add or remove a value, be sure to include previous values that should be persisted._

|Attribute|Description|
| -------- | -------- |
|Type:|String|
|Position:|Named|
|Default value:|None|
|Required:|False|
|Accept pipeline input:|False|
|Accept wildcard characters:|False|

### -Type

The Type parameter specifies the type of the place that is being created. Valid values are:

* Building
* Floor

|Attribute|Description|
| -------- | -------- |
|Type:|String|
|Position:|Named|
|Default value:|None|
|Required:|True|
|Accept pipeline input:|True|
|Accept wildcard characters:|False|
