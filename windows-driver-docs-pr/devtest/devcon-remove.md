---
title: DevCon Remove
description: 从设备树中删除设备，并删除设备的设备堆栈。
keywords:
- DevCon 删除驱动程序开发工具
topic_type:
- apiref
api_name:
- DevCon Remove
api_type:
- NA
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: f4b73409dcd9a5629d713cae99669c1173142963
ms.sourcegitcommit: 418e6617e2a695c9cb4b37b5b60e264760858acd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96783371"
---
# <a name="devcon-remove"></a>DevCon Remove

从设备树中删除设备，并删除设备的设备堆栈。 由于这些操作，将从设备树中删除子设备，并卸载支持该设备的驱动程序。

此操作不会删除设备驱动程序或设备上安装的任何文件。 从设备树中删除设备后，文件将保留，并且设备仍在内部表示为可 reenumerated 的 nonpresent 设备。

仅在本地计算机上有效。

```
    devcon [/r] remove {* | ID [ID ...] | =class [ID [ID ...]]}
```

## <a name="span-idddk_devcon_remove_toolsspanspan-idddk_devcon_remove_toolsspanparameters"></a><span id="ddk_devcon_remove_tools"></span><span id="DDK_DEVCON_REMOVE_TOOLS"></span>参数

<span id="________r______"></span><span id="________R______"></span>**/r** 条件重启。 仅当需要重新启动才能使更改生效时，才能在完成操作后重新启动系统。

<span id="______________"></span> **\** _ 表示计算机上的所有设备。

<span id="_______ID______"></span><span id="_______id______"></span> _ID * 指定设备的硬件 ID、兼容 ID 或设备实例 ID 的全部或部分。 指定多个 Id 时，请在每个 ID 之间键入一个空格。 包含与号字符 () 的 Id **&** 必须用引号引起来。

以下特殊字符修改 ID 参数。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字符</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong><em></strong></p></td>
<td align="left"><p>匹配任何字符或不匹配任何字符。 使用通配符 (</em>) 创建 ID 模式，例如 <em>磁盘</em>。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>@</strong></p></td>
<td align="left"><p>指示设备实例 ID，例如 <strong><xref href="ROOT\FTDISK\0000" data-throw-if-not-resolved="False" data-raw-source="@ROOT\FTDISK\0000"></xref></strong> 。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>'</strong></p>
<p> (单引号) </p></td>
<td align="left"><p>按原义 (与) 显示的内容完全匹配。 在字符串前面加上单引号，指示星号是 ID 名称的一部分，并且不是通配符，例如 <strong>"* PNP0600</strong>，其中，* PNP0600 (包括星号) 为硬件 ID。</p></td>
</tr>
</tbody>
</table>  

<span id="________class______"></span><span id="________CLASS______"></span>**=**<em>类</em>指定设备的设备安装程序类。 等号 (**=**) 将字符串标识为类名。

你还可以在类名称后指定硬件 Id、兼容 Id、设备实例 Id 或 ID 模式。 键入每个 ID 或模式之间的空格。 DevCon 在类中查找与指定 Id 相匹配的设备。

### <a name="span-idcommentsspanspan-idcommentsspancomments"></a><span id="comments"></span><span id="COMMENTS"></span>提出

系统可能需要重新启动才能使此更改生效。 若要让 DevCon 重新启动系统，请将 (/r) 的条件重新启动参数添加到命令中。

### <a name="span-idsample_usagespanspan-idsample_usagespansample-usage"></a><span id="sample_usage"></span><span id="SAMPLE_USAGE"></span>示例用法

```
devcon /r remove "PCI\VEN_8086&DEV_7110"
devcon /r remove =printer
devcon /r remove =printer *deskj*
```

### <a name="span-idexamplesspanspan-idexamplesspanexamples"></a><span id="examples"></span><span id="EXAMPLES"></span>示例

[示例35：按设备实例 ID 模式删除设备](devcon-examples.md#ddk_example_35_remove_devices_by_device_instance_id_pattern_tools)

[示例36：删除特定网络设备](devcon-examples.md#ddk_example_36_remove_a_particular_network_device_tools)
