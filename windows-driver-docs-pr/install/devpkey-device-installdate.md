---
title: DEVPKEY_Device_InstallDate
description: DEVPKEY_Device_InstallDate
keywords:
- DEVPKEY_Device_InstallDate 设备和驱动程序安装
topic_type:
- apiref
api_name:
- DEVPKEY_Device_InstallDate
api_location:
- Devpkey.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 0ec7667455a001cd6ec24987be488dbfbd2905ab
ms.sourcegitcommit: 418e6617e2a695c9cb4b37b5b60e264760858acd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96825153"
---
# <a name="devpkey_device_installdate"></a>DEVPKEY_Device_InstallDate


"DEVPKEY_Device_InstallDate 设备" 属性指定上次在系统中安装设备实例时的时间戳。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr>
<th>Attribute</th>
<th>值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>属性键</strong></p></td>
<td align="left"><p>DEVPKEY_Device_InstallDate</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>属性数据类型标识符</strong></p></td>
<td align="left"><p><a href="devprop-type-filetime.md" data-raw-source="[&lt;strong&gt;DEVPROP_TYPE_FILETIME&lt;/strong&gt;](devprop-type-filetime.md)"><strong>DEVPROP_TYPE_FILETIME</strong></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>和</strong></p></td>
<td align="left"><p>安装应用程序和安装程序的只读访问。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>各种?</strong></p></td>
<td align="left"><p>否</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

Windows 将 DEVPKEY_Device_InstallDate 的值设置为时间戳，该时间戳指定上次在系统中安装设备实例的时间。

对于每次更新设备驱动程序，此时间戳值都会发生变化。 例如，此时间戳报告上次通过 Windows 更新更新设备驱动程序的日期和时间。

可以调用 [**SetupDiGetDeviceProperty**](/windows/win32/api/setupapi/nf-setupapi-setupdigetdevicepropertyw) 来检索 DEVPKEY_Device_FirstInstallDate 属性的值。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>版本</p></td>
<td align="left"><p>在 windows 7 和更高版本的 Windows 中可用。</p></td>
</tr>
<tr class="even">
<td align="left"><p>标头</p></td>
<td align="left">Devpkey (包含 Devpkey) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**SetupDiGetDeviceProperty**](/windows/win32/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)

 

