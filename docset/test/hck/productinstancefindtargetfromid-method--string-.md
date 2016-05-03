---
author: joshbax-msft
title: ProductInstance.FindTargetFromId Method (String)
description: ProductInstance.FindTargetFromId Method (String)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7ff9682c-14bc-4f15-b4e1-72aaa4e58cbb
---

# ProductInstance.FindTargetFromId Method (String)


This method returns an appropriate target type based on information associated with &lt;paramref name="targetId"/&gt;.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel **Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## Usage


**Visual Basic**`Dim instance As ProductInstance``Dim targetId As String``Dim returnValue As ReadOnlyCollection(Of TargetData)``returnValue = instance.FindTargetFromId(targetId)`

## Syntax


**Visual Basic**`Public Function FindTargetFromId ( _`           `targetId As String _``) As ReadOnlyCollection(Of TargetData)`

**C#**`public ReadOnlyCollection<TargetData> FindTargetFromId (`           `string targetId``)`

## Parameters


*targetId*      The ID value that identifies the test target. This can be found in the SysParse data.

## Return Value


Returns **ReadOnlyCollection**. If &lt;paramref name="targetId"/&gt; is not found on the machine (test computer) associated with the product instance, **null** is returned. Otherwise, an instance of the test target is returned.

## Remarks


An exception occurs if *targetId* is null or empty.

## Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20ProductInstance.FindTargetFromId%20Method%20%28String%29%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



