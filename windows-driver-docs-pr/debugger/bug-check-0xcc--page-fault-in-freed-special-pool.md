---
title: Bug 检查 0xCC PAGE_FAULT_IN_FREED_SPECIAL_POOL
description: PAGE_FAULT_IN_FREED_SPECIAL_POOL bug 检查的值为0x000000CC。 这表示系统已引用先前释放的内存。
keywords:
- Bug 检查 0xCC PAGE_FAULT_IN_FREED_SPECIAL_POOL
- PAGE_FAULT_IN_FREED_SPECIAL_POOL
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- PAGE_FAULT_IN_FREED_SPECIAL_POOL
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 1dbd6578b5c1a81ac5a2c9c9a801aa3e76b76a25
ms.sourcegitcommit: 418e6617e2a695c9cb4b37b5b60e264760858acd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96825213"
---
# <a name="bug-check-0xcc-page_fault_in_freed_special_pool"></a>Bug 检查0xCC： \_ \_ \_ 释放的 \_ 特殊 \_ 池中的页错误


\_ \_ \_ 释放 \_ 特殊池 BUG 检查中的页错误的 \_ 值为0x000000CC。 这表示系统已引用先前释放的内存。

> [!IMPORTANT]
> 本主题面向程序员。 如果您是在使用计算机时收到蓝屏错误代码的客户，请参阅[蓝屏错误疑难解答](https://www.windows.com/stopcode)。


## <a name="page_fault_in_freed_special_pool-parameters"></a>\_ \_ \_ 释放 \_ 特殊 \_ 池参数时出现页面错误


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">参数</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>1</p></td>
<td align="left"><p>引用的内存地址</p></td>
</tr>
<tr class="even">
<td align="left"><p>2</p></td>
<td align="left"><p><strong>0：</strong> 读取</p>
<p><strong>1：</strong> 写入</p></td>
</tr>
<tr class="odd">
<td align="left"><p>3</p></td>
<td align="left"><p>引用内存的地址（如果已知）</p></td>
</tr>
<tr class="even">
<td align="left"><p>4</p></td>
<td align="left"><p>预留</p></td>
</tr>
</tbody>
</table>

 

如果能够识别出导致错误的驱动程序，则其名称将打印在蓝屏上，并存储在内存中的 (PUNICODE\_STRING) KiBugCheckDriver  位置。

<a name="cause"></a>原因
-----

"驱动程序验证程序特殊池" 选项已捕获到系统访问之前已释放的内存。 这通常表示系统驱动程序同步问题。

有关特殊池的信息，请参阅 Windows 驱动程序工具包的驱动程序验证程序部分。

<a name="remarks"></a>备注
-------

这不能通过 **try-except** 处理程序来保护--它只能通过探测进行保护。

 

 




