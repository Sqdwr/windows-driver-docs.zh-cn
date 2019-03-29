---
title: KSPROPERTY\_EXTXPORT\_INPUT\_SIGNAL\_MODE
description: KSPROPERTY\_EXTXPORT\_输入\_信号\_模式属性设置或获取外部设备的当前输入的信号模式。 例如 DV-SD/NTSC/PAL、 DV-SL/NTSC/PAL、 MPEG2-TS，等等。
ms.assetid: 3af5c2fb-c7dc-4dfb-b66d-fc16091fa5ad
keywords:
- KSPROPERTY_EXTXPORT_INPUT_SIGNAL_MODE 流式处理媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_EXTXPORT_INPUT_SIGNAL_MODE
api_location:
- ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 9411c954cb8468f34ea1565d834cf5cd4ced70d4
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56566199"
---
# <a name="kspropertyextxportinputsignalmode"></a>KSPROPERTY\_EXTXPORT\_INPUT\_SIGNAL\_MODE


KSPROPERTY\_EXTXPORT\_输入\_信号\_模式属性设置或获取外部设备的当前输入的信号模式。 例如 DV-SD/NTSC/PAL、 DV-SL/NTSC/PAL、 MPEG2-TS，等等。

## <span id="ddk_ksproperty_extxport_input_signal_mode_ks"></span><span id="DDK_KSPROPERTY_EXTXPORT_INPUT_SIGNAL_MODE_KS"></span>


### <a name="usage-summary-table"></a>使用率摘要表

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Get</th>
<th>设置</th>
<th>目标</th>
<th>属性描述符类型</th>
<th>属性值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>设备</p></td>
<td><p><a href="https://msdn.microsoft.com/library/windows/hardware/ff565167" data-raw-source="[&lt;strong&gt;KSPROPERTY_EXTXPORT_S&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff565167)"><strong>KSPROPERTY_EXTXPORT_S</strong></a></p></td>
<td><p>ULONG</p></td>
</tr>
</tbody>
</table>

 

属性值 （操作数据） 为的 ULONG 的指定外部传输的当前输入的信号模式。

<a name="remarks"></a>备注
-------

**SignalMode** KSPROPERTY 成员\_EXTXPORT\_S 结构指定的输入的信号模式。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Header</p></td>
<td>Ksmedia.h （包括 Ksmedia.h）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**KSPROPERTY**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ks/ns-ks-ksidentifier)

[**KSPROPERTY\_EXTXPORT\_S**](https://msdn.microsoft.com/library/windows/hardware/ff565167)

 

 





