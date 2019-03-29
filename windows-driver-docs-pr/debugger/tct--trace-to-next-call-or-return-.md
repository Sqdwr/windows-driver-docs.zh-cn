---
title: tct（跟踪到下一个 Call 或 Return）
description: Tct 命令执行程序，直到它达到调用指令，或返回指令。
ms.assetid: 059d8071-577f-4306-8273-8fdff6a80626
keywords:
- tct (到下一个调用或返回的 Trace) Windows 调试
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- tct (Trace to Next Call or Return)
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 43b24ebc7ea342f21c9570734235d3e81b7832b9
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56562576"
---
# <a name="tct-trace-to-next-call-or-return"></a>tct（跟踪到下一个 Call 或 Return）


**Tct**命令执行程序，直到它达到调用指令，或返回指令。

User-Mode

```dbgcmd
[~Thread] tct [r] [= StartAddress] [Count] 
```

Kernel-Mode

```dbgcmd
tct [r] [= StartAddress] [Count] 
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="_______Thread______"></span><span id="_______thread______"></span><span id="_______THREAD______"></span> *线程*   
指定线程继续执行。 所有其他线程均已冻结。 有关语法的详细信息，请参阅[线程语法](thread-syntax.md)。 仅在用户模式下，可以指定线程。

<span id="_______r______"></span><span id="_______R______"></span> **r**   
开启和关闭显示器的寄存器和标志。 默认情况下，显示的寄存器和标志。 可以使用禁用注册显示**tctr**， [ **pr**](p--step-.md)， [ **tr**](t--trace-.md)，或.prompt\_允许-reg 命令。 所有这些命令控制的相同设置，可以使用其中任何一个重写任何以前使用这些命令。

此外可以使用 l os 命令来禁用注册显示。 此设置是独立于其他四个命令。 控制要显示的寄存器和标志，使用[ **rm （注册掩码）** ](rm--register-mask-.md)命令。

<span id="_______StartAddress______"></span><span id="_______startaddress______"></span><span id="_______STARTADDRESS______"></span> *StartAddress*   
指定调试器开始执行的位置的地址。 如果不使用*StartAddress*，指令指针指向的指令处开始执行。 有关语法的详细信息，请参阅[地址和地址范围语法](address-and-address-range-syntax.md)。

<span id="_______Count______"></span><span id="_______count______"></span><span id="_______COUNT______"></span> *Count*   
指定的数量**调用**或**返回**调试器必须遇到有关的说明**tct**命令以结束。 默认值为 1。

### <a name="span-idenvironmentspanspan-idenvironmentspanspan-idenvironmentspanenvironment"></a><span id="Environment"></span><span id="environment"></span><span id="ENVIRONMENT"></span>环境

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>模式</strong></p></td>
<td align="left"><p>用户模式下，内核模式</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>目标</strong></p></td>
<td align="left"><p>仅实时调试</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>平台</strong></p></td>
<td align="left"><p>全部</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idadditionalinformationspanspan-idadditionalinformationspanspan-idadditionalinformationspanadditional-information"></a><span id="Additional_Information"></span><span id="additional_information"></span><span id="ADDITIONAL_INFORMATION"></span>其他信息

有关相关命令的详细信息，请参阅[控制目标](controlling-the-target.md)。

<a name="remarks"></a>备注
-------

**Tct**命令将导致目标开始执行。 此执行将继续直至调试器到达**调用**或**返回**指令或遇到断点。

如果已经打开的程序计数器**调用**或**返回**指令，调试器调用或返回到跟踪，并继续执行直到它遇到另一个**调用**或**返回**。 此跟踪，而不是执行中的，在调用之间的唯一区别是**tct**并[**百分比 （下一步调用或返回到步骤）**](pct--step-to-next-call-or-return-.md)。

在源模式中，可以将一个源行与多个程序集指令相关联。 此命令不会停止处**调用**或**返回**与当前的源行相关联的指令。

 

 




