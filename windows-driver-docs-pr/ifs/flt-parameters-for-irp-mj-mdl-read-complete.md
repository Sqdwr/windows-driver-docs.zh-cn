---
title: IRP_MJ_MDL_READ_COMPLETE 联合的 FLT_PARAMETERS
description: 当操作的 FLT \_ IO \_ 参数块结构的 MajorFunction 字段 \_ 为 IRP \_ MJ \_ MDL \_ 读取 \_ 完成时，将使用以下联合组件。
keywords:
- IRP_MJ_MDL_READ_COMPLETE 联合可安装文件系统驱动程序的 FLT_PARAMETERS
- FLT_PARAMETERS 联合可安装文件系统驱动程序
- PFLT_PARAMETERS 联合指针可安装的文件系统驱动程序
topic_type:
- apiref
api_name:
- FLT_PARAMETERS
api_location:
- fltkernel.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 00f107d7ecf6e474ef825d12a4c17988b8d04af5
ms.sourcegitcommit: 418e6617e2a695c9cb4b37b5b60e264760858acd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96839271"
---
# <a name="flt_parameters-for-irp_mj_mdl_read_complete-union"></a>\_IRP MJ MDL 的 FLT 参数 \_ \_ \_ 读取 \_ 完成联合


当操作的 [**FLT \_ IO \_ 参数 \_ 块**](/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_io_parameter_block)结构的 **MajorFunction** 字段为 IRP \_ MJ \_ MDL \_ 读取 \_ 完成时，将使用以下联合组件。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef union _FLT_PARAMETERS {
  ...    ;
  struct {
    PMDL MdlChain;
  } MdlReadComplete;
  ...    ;
} FLT_PARAMETERS, *PFLT_PARAMETERS;
```

<a name="members"></a>成员
-------

**MdlReadComplete**  
包含以下成员的结构。

**MdlChain**  
指向一个变量的指针，该变量接收指向一个或多个内存描述符的链的指针 (MDL) 描述包含要从缓存文件中读取的数据的页面。

<a name="remarks"></a>备注
-------

IRP MJ MDL 读取完成操作的 [**FLT \_ 参数**](/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_parameters) 结构 \_ \_ \_ \_ 包含由回调数据表示的快速 I/o **MdlReadComplete** 操作的参数 ([**FLT \_ 回叫 \_ 数据**](/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_callback_data)) 结构。 它包含在 FLT \_ IO \_ 参数 \_ 块结构中。

IRP \_ MJ \_ MDL \_ 读取 \_ 完成是一种快速的 i/o 操作。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>标头</p></td>
<td align="left">Fltkernel (包含 Fltkernel) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**FLT \_ 回调 \_ 数据**](/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_callback_data)

[**FLT \_ IO \_ 参数 \_ 块**](/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_io_parameter_block)

[**FLT \_ 是 \_ FASTIO \_ 操作**](/windows-hardware/drivers/ddi/index)

[**FLT \_ 为 \_ FS \_ 筛选器 \_ 操作**](/previous-versions/ff544648(v=vs.85))

[**FLT \_ 是 \_ IRP \_ 操作**](/previous-versions/ff544654(v=vs.85))

[**FLT \_ 参数**](/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_parameters)

 

