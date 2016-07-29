---
author: joshbax-msft
title: Win6\_3.MBN.GSM.TestMultiCarrier
description: Win6\_3.MBN.GSM.TestMultiCarrier
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f4443ce4-072c-4d21-ac4f-467350e9350d
---

# Win6\_3.MBN.GSM.TestMultiCarrier


This test attempts to set the home provider if the device supports multicarrier or multimode.

## Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Associated requirements</strong></p></td>
<td><p>Device.Network.MobileBroadband.GSM.MultiCarrierFunctionality</p>
<p>[See the device hardware requirements.](http://go.microsoft.com/fwlink/p/?linkid=254483)</p></td>
</tr>
<tr class="even">
<td><p><strong>Platforms</strong></p></td>
<td><p>Windows RT 8.1 Windows 8.1 x64 Windows 8.1 x86</p></td>
</tr>
<tr class="odd">
<td><p><strong>Expected run time</strong></p></td>
<td><p>~10 minutes</p></td>
</tr>
<tr class="even">
<td><p><strong>Categories</strong></p></td>
<td><p>Certification Functional</p></td>
</tr>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td><p>Automated</p></td>
</tr>
</tbody>
</table>

 

## Running the test


Before you run the test, complete the test setup as described in the test requirements: [Mobile Broadband Testing Prerequisites](mobile-broadband-testing-prerequisites.md).

## Troubleshooting


For troubleshooting information, see [Troubleshooting Device.Network Testing](troubleshooting-devicenetwork-testing.md).

## More information


### Parameters

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MultiCarrierProviderId</p></td>
<td><p>The provider ID</p></td>
</tr>
<tr class="even">
<td><p>MultiCarrierProviderName</p></td>
<td><p>The provider name</p></td>
</tr>
<tr class="odd">
<td><p>MultiCarrierCellClass</p></td>
<td><p>The cellular class that can be either GSM or CDMA.</p></td>
</tr>
</tbody>
</table>

 

 

 





