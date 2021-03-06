---
title: bs（更新断点命令）
description: Bs.1770 命令更改遇到指定断点时执行的命令。
keywords:
- bs.1770 (更新断点命令) Windows 调试
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- bs (Update Breakpoint Command)
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 01615a446d5fef6b32885ac45c231c1dea9084ba
ms.sourcegitcommit: 418e6617e2a695c9cb4b37b5b60e264760858acd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96788885"
---
# <a name="bs-update-breakpoint-command"></a>bs（更新断点命令）


**Bs.1770** 命令更改遇到指定断点时执行的命令。

```dbgcmd
bs ID ["CommandString"] 
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


<span id="_______ID______"></span><span id="_______id______"></span>*ID*   
指定断点的 ID 号。

<span id="_______CommandString______"></span><span id="_______commandstring______"></span><span id="_______COMMANDSTRING______"></span>*Command.commandstring*   
指定每次遇到断点时要执行的命令的新列表。 必须用引号将 *command.commandstring* 参数引起来。 使用分号分隔多个命令。

*Command.commandstring* 中的调试器命令可以包含参数。 可以使用标准的 C 控制字符 (如 **\\ n** 和 **\\ "**) 。 第二级引号中包含的分号 (**\\ "**) 被解释为嵌入的带引号字符串的一部分。

仅当在应用程序执行时响应 **g (中转)** 命令时，才会执行 *command.commandstring* 命令。 如果要逐句通过此点的代码或跟踪，则不会执行这些命令。

在断点 (（如 **g** 或 **t**) 后恢复程序执行的任何命令都将结束命令列表的执行。

### <a name="span-idenvironmentspanspan-idenvironmentspanspan-idenvironmentspanenvironment"></a><span id="Environment"></span><span id="environment"></span><span id="ENVIRONMENT"></span>环境

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>交货</strong></p></td>
<td align="left"><p>用户模式，内核模式</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>目标</strong></p></td>
<td align="left"><p>仅限实时调试</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>平台</strong></p></td>
<td align="left"><p>全部</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idadditional_informationspanspan-idadditional_informationspanspan-idadditional_informationspanadditional-information"></a><span id="Additional_Information"></span><span id="additional_information"></span><span id="ADDITIONAL_INFORMATION"></span>附加信息

有关如何使用断点、其他断点命令和控制断点的方法以及如何在用户空间中从内核调试器设置断点的详细信息，请参阅 [使用断点](using-breakpoints.md)。 有关条件断点的详细信息，请参阅 [设置条件断点](setting-a-conditional-breakpoint.md)。

<a name="remarks"></a>备注
-------

如果未指定 *command.commandstring* ，则将删除已在该断点上设置的任何命令。

 

 





