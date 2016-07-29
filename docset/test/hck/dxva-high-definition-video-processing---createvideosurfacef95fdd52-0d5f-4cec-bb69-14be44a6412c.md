---
author: joshbax-msft
title: DXVA High Definition Video Processing - CreateVideoSurface
description: DXVA High Definition Video Processing - CreateVideoSurface
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0b817dbb-e352-4e64-b9bb-0021eb8f0b4c
---

# DXVA High Definition Video Processing - CreateVideoSurface


This automated test calls the GetVideoProcessorDeviceCaps. Then, using those caps, it generates multiple test cases based on a default memory pool width size of the content from the generated dxvahd device.

The test case also checks the supported input and output formats of each device. It verifies that a surface can be created for each input and output surface, and confirms that unknown formats fail. The test case also verifies creation of multiple surfaces for each format as well.

Test will for the most part just show a ticker like window incrementing pass fail counts and showing which test case variables are being iterated upon.

The test might return SKIP if the driver does not expose D3DCAPS3\_DXVAHD. In some cases, it might skip if certain surface formats are not-supported.

## Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Associated requirements</strong></p></td>
<td><p>Device.Graphics.AdapterRender.YUVSupport Device.Graphics.WDDM11.Render.DXVAHD.DXVAHD</p>
<p>[See the device hardware requirements.](http://go.microsoft.com/fwlink/p/?linkid=254483)</p></td>
</tr>
<tr class="even">
<td><p><strong>Platforms</strong></p></td>
<td><p>Windows 7 (x64) Windows 7 (x86) Windows RT (ARM-based) Windows 8 (x64) Windows 8 (x86) Windows Server 2012 (x64) Windows Server 2008 R2 (x64) Windows RT 8.1 Windows 8.1 x64 Windows 8.1 x86 Windows Server 2012 R2</p></td>
</tr>
<tr class="odd">
<td><p><strong>Expected run time</strong></p></td>
<td><p>~2 minutes</p></td>
</tr>
<tr class="even">
<td><p><strong>Categories</strong></p></td>
<td><p>Certification Functional</p></td>
</tr>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td><p>Manual</p></td>
</tr>
</tbody>
</table>

 

## Running the test


Before you run the test, complete the test setup as described in the test requirements: [Graphic Adapter or Chipset Testing Prerequisites](graphic-adapter-or-chipset-testing-prerequisites.md).

In addition, this test requires the following software:

-   A display driver that supports D3D9Caps.Caps3 D3DCAPS3\_DXVAHD, specifically:

    -   D3D9 support exposing D3DCAPS3\_DXVAHD.

    -   Required Output Formats: D3DFMT\_X8R8G8B8, D3DFMT\_A8R8G8B8.

    -   Required Input Formats: D3DFMT\_X8R8G8B8, D3DFMT\_A8R8G8B8, D3DFMT\_YUY2, D3DFMT\_AYUV and Any Decode Render targets supported.

-   dxvahdsw.dll.

## Troubleshooting


For troubleshooting information, see [Troubleshooting Device.Graphics Testing](troubleshooting-devicegraphics-testing.md).

## More information


This test verifies the following requirements:

-   Verify Success with valid pointer to DXVAHD\_VPDEVCAPS.

    -   Verify OutputFormat and InputFormat Counts are correct and function properly with associated get routines.

    -   Verify VideoProcessorCount correctly maps to number of video processors.

    -   Verify MaxInputStreams greater than zero.

    -   Verify MaxStreamStates greater than zero.

-   Verify success when DXVAHD\_VPDEVCAPS.InputFormatCount is used.

-   Verify failure when less than and greater than InputFormatCount is used.

-   Verify that D3DFMT\_X8R8G8B8 is supported.

-   Verify success when DXVAHD\_VPDEVCAPS.InputFormatCount is used.

-   Verify failure when less than and greater than InputFormatCount is used.

-   Verify that D3DFMT\_X8R8G8B8, D3DFMT\_A8R8G8B8, D3DFMT\_YUY2, and AYUV (FourCC) are reported as supported.

-   Verify that all decode render target formats report as supported as well.

-   Create Surface with Width Height that of the content description input width height.

-   Create Surface with Width Height different both larger and smaller of the content description input width height.

-   Create Surface with D3DPOOL type from DXVAHD\_VPDEVCAPS.InputPool. Then with a different InputPool, verify during Processing VPBltHD returns E\_INVALIDCALL.

-   Verify any usage value other than 0 results in return value (E\_INVALIDARG).

-   Create a surface of DXVAHD\_SURFACE\_TYPE\_VIDEO\_INPUT, and attempt to manipulate it some way with D3D9 API. Validate success. (Off-screen plain.)

    -   Iterate over all supported input D3D formats obtained by IDXVAHD\_Device::GetVideoProcessorInputFormats. Then check an unsupported D3D format.

-   Create a surface of DXVAHD\_SURFACE\_TYPE\_VIDEO\_INPUT\_PRIVATE. Confirm that manipulation of it through the D3D 9 API fails. (Off-screen plain.)

    -   Iterate over all supported input D3D formats obtained by IDXVAHD\_Device::GetVideoProcessorInputFormats. Then check an unsupported D3D format.

-   Create a surface of DXVAHD\_SURFACE\_TYPE\_VIDEO\_OUTPUT, and validate as a render target.

    -   Iterate over all supported input D3D formats obtained by IDXVAHD\_Device::GetVideoProcessorOutputFormats. Then check an unsupported D3D format.

-   Attempt to create a single surface, and then verify ppSurfaces only contains one surface.

-   Create multiple surfaces, and verify the number of surfaces equals the number of surfaces represented by NumSurfaces passed.

-   Confirm that ppSurfaces that fail are NULL.

### Command syntax

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Command option</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>DXVAHDVideoProcessing CreateVideoSurface</strong></p></td>
<td><p>Without any options, the test enumerates all but some extreme invalid argument test cases.</p></td>
</tr>
<tr class="even">
<td><p><strong>TestPriority:[0, 1, 2]</strong></p></td>
<td><p>By default, tests at a priority 1 level; however, priority 2 will test every permutation, including extreme invalid argument test cases. 0 is for BVT level.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SoftwareOnly</strong></p></td>
<td><p>Tests only the software implementation of the video processor. This was mainly used for initial testing before drivers supported the test cases.</p></td>
</tr>
<tr class="even">
<td><p><strong>SaveAllFrames</strong></p></td>
<td><p>The test has hard coded save count of invalid frames set to 100. I you want all of them saved, then use this flag. Good for high frame count test case failures.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LogLevel:[0, 1, 2]</strong></p></td>
<td><p>The test has the ability to be very verbose in its logging methods. By default level 0 is set, however; level one will gather increased logging info per test cases, including many stream states/blt states set. Level 2 will gather all adjusted stream states and blt states, as well as any configuration information.</p></td>
</tr>
</tbody>
</table>

 

### File list

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DXVAHDVideoProcessing.exe</p></td>
<td><p>[testbinroot]\nttest\windowstest\graphics\d3d\func\</p></td>
</tr>
<tr class="even">
<td><p>Dxvahdsw.dll</p></td>
<td><p>[osbinroot]\nttest\windowstest\graphics\dxva\</p></td>
</tr>
</tbody>
</table>

 

 

 





