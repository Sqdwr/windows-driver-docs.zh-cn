---
title: Bug 检查 0xA0 INTERNAL_POWER_ERROR
description: INTERNAL_POWER_ERROR bug 检查的值为0x000000A0。 此 bug 检查表明电源策略管理器遇到错误。
keywords:
- Bug 检查 0xA0 INTERNAL_POWER_ERROR
- INTERNAL_POWER_ERROR
ms.date: 12/09/2020
topic_type:
- apiref
api_name:
- INTERNAL_POWER_ERROR
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 855ec5eecd3f4be5438c628bc0defaa48ff12046
ms.sourcegitcommit: 11a82f18ee7874537597792cb77f749d5ce6eee5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "96999155"
---
# <a name="bug-check-0xa0-internal_power_error"></a>Bug 检查0xA0：内部 \_ 电源 \_ 错误

内部 \_ 电源 \_ 错误 bug 检查的值为0x000000A0。 此 bug 检查表明电源策略管理器遇到错误。

> [!IMPORTANT]
> 本主题面向程序员。 如果您是在使用计算机时收到蓝屏错误代码的客户，请参阅[蓝屏错误疑难解答](https://www.windows.com/stopcode)。

## <a name="internal_power_error-parameters"></a>内部 \_ 电源 \_ 错误参数


参数1指示违规类型。 其他参数的意义取决于参数1的值。

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
<th align="left">参数 1</th>
<th align="left">参数2</th>
<th align="left">参数3</th>
<th align="left">参数4</th>
<th align="left">原因</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>0x1</p></td>
<td align="left"><p><strong>1：</strong> 设备的引用计数的最大数目已溢出。</p>
<p><strong>2、3或4：</strong>  过多的涌入电源 Irp 已排入队列。</p>
<p><strong>5：</strong>  已将 power IRP 发送到被动级别设备对象。</p>
<p><strong>6：</strong> 系统无法分配所需的电源 IRP。</p></td>
<td align="left"><p>如果参数2的值为1，则为允许的最大引用数。</p>
<p>如果参数2的值为2、3或4，则为允许的最大挂起 Irp 数。</p>
<p>如果参数2的值为6，则为目标设备对象。</p></td>
<td align="left">如果参数2的值为6，则指示这是否为系统 (0x0) 或设备 (0x1) power IRP。</td>
<td align="left"><p>处理 (IRP) 的电源 i/o 请求包时出错。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x2</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>尝试处理电源事件时出现内部错误。 有关详细信息，请参阅 <a href="#parameter-1-equals-0x2" data-raw-source="[Debugging bug check 0xA0 when parameter 1 equals 0x2](#parameter-1-equals-0x2)">当参数1等于0x2 时调试错误检查 0xA0</a>。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x3</p></td>
<td align="left"><p>预期的校验和</p></td>
<td align="left"><p>实际校验和</p></td>
<td align="left"><p>错误的行号</p></td>
<td align="left"><p>休眠上下文页的校验和与预期的校验和不匹配。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x4</p></td>
<td align="left"><p>预期的校验和</p></td>
<td align="left"><p>实际校验和</p></td>
<td align="left"><p>错误的行号</p></td>
<td align="left"><p>要写入休眠文件的页面的校验和与预期的校验和不匹配。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x5</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>未知的关闭代码已发送到系统关闭处理程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x7</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>发生了未经处理的异常。 有关详细信息，请参阅 <a href="#parameter-1-equals-0x7" data-raw-source="[Debugging bug check 0xA0 when parameter 1 equals 0x7](#parameter-1-equals-0x7)">当参数1等于0x7 时，调试错误检查 0xA0</a>。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x8</p></td>
<td align="left"><p>此参数始终设置为0x100。</p></td>
<td align="left"><p>Device 对象</p></td>
<td align="left"><p>POWER_CHANNEL_SUMMARY</p>
<p></p></td>
<td align="left"><p>处理系统电源事件时出现严重错误。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x9</p></td>
<td align="left"><p>状态代码</p></td>
<td align="left"><p>镜像阶段</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>准备休眠文件时出现严重错误。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0xA</p></td>
<td align="left"><p><strong>0：</strong> 继续操作时，立即请求了 bug 检查。</p>
<p><strong>1：</strong> 在所有非分页设备都已打开之后，在恢复期间请求了 bug 检查。</p>
<p><strong>2：</strong> 在所有设备都已通电后，在恢复期间请求了 bug 检查。</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>出于调试目的而唤醒时，请求了 bug 检查。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0xB</p></td>
<td align="left"><p>休眠文件的大小。</p></td>
<td align="left"><p>空间不足之前的休眠进度</p>
<p><strong>0：</strong> HIBERFILE_PROGRESS_FREE_MAP</p>
<p><strong>1：</strong> HIBERFILE_PROGRESS_RESUME_CONTEXT</p>
<p><strong>2：</strong> HIBERFILE_PROGRESS_PROCESSOR_STATE</p>
<p><strong>3：</strong> HIBERFILE_PROGRESS_SECURE_RANGES</p>
<p><strong>4：</strong> HIBERFILE_PROGRESS_MEMORY_RANGES</p>
<p><strong>5：</strong> HIBERFILE_PROGRESS_TABLE_PAGES</p>
<p><strong>6：</strong> HIBERFILE_PROGRESS_MEMORY_IMAGE</p></td>
<td align="left"><p>当 param 2 为4时，为剩余内存范围的大小。</p></td>
<td align="left"><p>休眠文件太小。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0xC</p></td>
<td align="left"><p>状态代码</p></td>
<td align="left"><p>转储堆栈上下文</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>转储堆栈初始化失败。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0xD</p></td>
<td align="left"><p>转换中的系统电源状态。</p></td>
<td align="left"><p>最近到达的睡眠检查点。</p></td>
<td align="left"><p>指向 POP_POWER_ACTION 结构的指针。</p></td>
<td align="left"><p>系统无法及时完成电源转换。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0xF</p></td>
<td align="left"><p>转换中的系统电源状态。 </p></td>
<td align="left"><p>最近到达的睡眠检查点。</p></td>
<td align="left"><p>指向当前正在处理请求的线程的指针。</p></td>
<td align="left"><p>系统无法及时完成电源转换。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0xF0</p></td>
<td align="left"><p>转换中的系统电源状态。</p></td>
<td align="left"><p>最近到达的睡眠检查点。</p></td>
<td align="left"><p>指向当前正在处理请求的线程的指针。</p></td>
<td align="left"><p>系统无法完成 (挂起) 一种及时的电源转换。 </p></td>
</tr>
<tr class="odd">
<td align="left"><p>0xF1</p></td>
<td align="left"><p>转换中的系统电源状态。</p></td>
<td align="left"><p>最近到达的睡眠检查点。</p></td>
<td align="left"><p>指向当前正在处理请求的线程的指针。</p></td>
<td align="left"><p>系统无法完成 (恢复) 一种及时的电源转换。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x101</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>异常指针。</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>处理系统电源事件时出现未处理的异常。 有关详细信息，请参阅 <a href="#parameter-1-equals-0x101" data-raw-source="[Debugging bug check 0xA0 when parameter 1 equals 0x101](#parameter-1-equals-0x101)">当参数1等于0x101 时，调试错误检查 0xA0</a>。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x102</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>DUMP_INITIALIZATION_CONTEXT</p></td>
<td align="left"><p>POP_HIBER_CONTEXT</p></td>
<td align="left"><p>休眠工作缓冲区大小不是页面对齐。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x103</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>POP_HIBER_CONTEXT</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>在休眠过程中，所有工作页都无法进行处理。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x104</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>POP_HIBER_CONTEXT</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>尝试在内部内存结构被锁定时映射内部休眠内存。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x105</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>POP_HIBER_CONTEXT</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>尝试使用不受支持的内存类型标志映射内部休眠内存。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x106</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p> (MDL 的内存描述符列表) </p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>内存描述符列表是在休眠过程中创建的，该过程描述未分页的内存。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x107</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>POP_HIBER_CONTEXT</p></td>
<td align="left"><p>PO_MEMORY_RANGE_ARRAY</p></td>
<td align="left"><p>内部休眠数据结构中发生数据不匹配。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x108</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>POP_HIBER_CONTEXT</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>磁盘子系统无法正确写入部分休眠文件。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x109</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预期校验和</p></td>
<td align="left"><p>实际校验和</p></td>
<td align="left"><p>处理器状态数据的校验和与预期的校验和不匹配。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x10A</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>POP_HIBER_CONTEXT</p></td>
<td align="left"><p>NTSTATUS 故障代码</p></td>
<td align="left"><p>磁盘子系统无法正确读取或写入部分休眠文件。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x10B</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>当前休眠进度</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>尝试使用 PoSetHiberRange API 在错误的时间为休眠启动阶段标记页面。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x10C</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>提供给 API 的标志</p></td>
<td align="left"><p>要标记的长度</p></td>
<td align="left"><p>调用 PoSetHiberRange API 时参数无效。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x10D</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>POP_HIBER_CONTEXT</p></td>
<td align="left"><p>NTSTATUS 故障代码</p></td>
<td align="left"><p>安全内核子系统在为恢复提供数据时失败。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x10E</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>校验和不正确</p></td>
<td align="left"><p>上一次磁盘读取的校验和</p></td>
<td align="left"><p>在从休眠文件读取数据时，磁盘子系统返回了损坏的数据。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x10F</p></td>
<td align="left"><p>当前系统睡眠检查点。</p></td>
<td align="left"><p>内部错误的类型。</p>
<p>0：分页已禁用，但在对所有处理器禁用了采购订单之前，已写入检查点。</p>
<p>1：0以外的 CPU 尝试在系统睡眠的中断禁用阶段写入检查点。</p>
<p>2：系统中的另一段代码正在执行 EFI 运行时服务。</p>
</td>
<td align="left"><p>预留</p></td>
<td align="left"><p>检查系统睡眠进度的检查点时出现内部错误。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x110</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>系统无法禁用系统睡眠状态，但必须这样做才能确保数据的完整性。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x111</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>驱动程序指示存在用户，并且用户已启用调试选项来捕获调用堆栈。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x200</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>DEVICE_OBJECT</p></td>
<td align="left"><p>DEVICE_OBJECT_POWER_EXTENSION</p></td>
<td align="left"><p>正在检查未知设备类型是否处于空闲状态。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x300</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>DEVICE_OBJECT</p></td>
<td align="left"><p>IRP</p></td>
<td align="left"><p>电池电源 IRP 返回未知状态。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x301</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>DEVICE_OBJECT</p></td>
<td align="left"><p>IRP</p></td>
<td align="left"><p>电池进入未知状态。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x400</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>IO_STACK_LOCATION</p></td>
<td align="left"><p>DEVICE_OBJECT</p></td>
<td align="left"><p>设备的引用计数的最大数目已溢出。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x401</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>挂起的 IRP 列表</p></td>
<td align="left"><p>DEVICE_OBJECT</p></td>
<td align="left"><p>过多的涌入电源 Irp 已排入队列。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x402</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>挂起的 IRP 列表</p></td>
<td align="left"><p>DEVICE_OBJECT</p></td>
<td align="left"><p>过多的涌入电源 Irp 已排入队列。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x403</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>挂起的 IRP 列表</p></td>
<td align="left"><p>DEVICE_OBJECT</p></td>
<td align="left"><p>过多的涌入电源 Irp 已排入队列。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x404</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>IO_STACK_LOCATION</p></td>
<td align="left"><p>DEVICE_OBJECT</p></td>
<td align="left"><p>已将电源 IRP 发送到被动级别设备对象。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x500</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>IRP</p></td>
<td align="left"><p>DEVICE_OBJECT</p></td>
<td align="left"><p>热电源 IRP 返回未知状态。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x600</p></td>
<td align="left"><p>DEVICE_OBJECT PDO</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>驱动程序已尝试使用 Power Runtime Framework 进行重复的注册。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x601</p></td>
<td align="left"><p>POP_FX_DEVICE 设备</p></td>
<td align="left"><p>PEP_DEVICE_REGISTER PEP</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>没有 Power Engine 插件接受设备注册。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x602</p></td>
<td align="left"><p>DEVICE_NODE 设备节点</p></td>
<td align="left"><p>睡眠计数</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>设备节点睡眠计数与激活计数不匹配。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x603</p></td>
<td align="left"><p>POP_FX_PLUGIN</p></td>
<td align="left"><p>工作请求类型</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>Power Engine 插件发出了无效的工作请求。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x605</p></td>
<td align="left"><p>通知 ID</p></td>
<td align="left"><p>POP_FX_PLUGIN</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>Power Engine 插件未能接受必需的设备电源管理通知。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x606</p></td>
<td align="left"><p>POP_FX_COMPONENT</p></td>
<td align="left"><p>POP_FX_COMPONENT_FLAGS</p></td>
<td align="left"><p>组件的新条件</p></td>
<td align="left"><p>当资源已经处于活动 (或) 空闲状态时，Power Engine 插件尝试将关键系统资源组件转换为活动 (或空闲) 情况。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x607</p></td>
<td align="left"><p>POP_FX_DEVICE</p></td>
<td align="left"><p>NTSTATUS</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>如果需要成功，则运行时电源管理框架设备删除锁定会失败。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x608</p></td>
<td align="left"><p>POP_FX_COMPONENT</p></td>
<td align="left"><p>POP_FX_COMPONENT_FLAGS</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>驱动程序已尝试将组件转换为空闲状态，但没有前面的活动请求。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x609</p></td>
<td align="left"><p>POP_FX_PLUGIN</p></td>
<td align="left"><p>POP_FX_DEVICE</p></td>
<td align="left"><p>请求类型重复</p>
<p><strong>0：</strong> DevicePowerRequired</p>
<p><strong>1：</strong> DevicePowerNotRequired</p></td>
<td align="left"><p>Power Engine 插件要求设备电源为 "必需" 或 "设备电源不需要"，而无需干预相对类型的请求。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x610</p></td>
<td align="left"><p>POP_FX_PLUGIN</p></td>
<td align="left"><p>POP_FX_DEVICE</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>当上一个设备的电源要求未完成时，Power Engine 插件请求不需要设备电源。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x611</p></td>
<td align="left"><p>POP_FX_PLUGIN</p></td>
<td align="left"><p>POP_FX_DEVICE</p></td>
<td align="left"><p>组件索引无效</p></td>
<td align="left"><p>Power Engine 插件已请求对无效组件进行操作。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x612</p></td>
<td align="left"><p>POP_FX_PLUGIN PowerEnginePlugin</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>Power Engine 插件已请求在设备通知上下文中完成额外的工作，在此情况下，请求的 PO 未提供任何缓冲区。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x613</p></td>
<td align="left"><p>POP_FX_DEVICE</p></td>
<td align="left"><p>组件索引</p></td>
<td align="left"><p>操作</p>
<p><strong>0：</strong> 不需要完成设备电源</p>
<p><strong>1：</strong> 已打开的报表设备</p>
<p><strong>2：</strong> 完成空闲条件</p></td>
<td align="left"><p>当没有此类未处理请求挂起时，驱动程序已尝试完成请求。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x614</p></td>
<td align="left"><p>POP_FX_DEVICE</p></td>
<td align="left"><p>组件索引</p></td>
<td align="left"><p>非法参数</p>
<p><strong>0：</strong>在 IRQL = DISPATCH_LEVEL 使用的 PO_FX_FLAG_BLOCKING &gt;</p>
<p><strong>1：</strong> 指定的 PO_FX_FLAG_BLOCKING 和 PO_FX_FLAG_ASYNC_ONLY</p>
<p><strong>2：</strong> 组件索引无效</p></td>
<td align="left"><p>驱动程序已在具有非法参数的组件上请求活动/空闲转换。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x615</p></td>
<td align="left"><p>POP_FX_PLUGIN</p></td>
<td align="left"><p>POP_FX_COMPONENT</p></td>
<td align="left"><p>非法操作</p>
<p><strong>0：</strong> 组件未处于空闲状态0</p>
<p><strong>1：</strong>组件已处于活动状态</p>
<p><strong>2：</strong> 无未完成的激活请求</p>
<p><strong>3：</strong> 未完成的空闲状态转换</p></td>
<td align="left"><p>Power Engine 插件已非法指示组件激活完成。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x616</p></td>
<td align="left"><p>POP_FX_PLUGIN</p></td>
<td align="left"><p>POP_FX_COMPONENT</p></td>
<td align="left"><p>非法操作</p>
<p><strong>0：</strong> 空闲状态无效</p>
<p><strong>1：</strong> 组件已处于请求的状态</p>
<p><strong>2：</strong> 请求未通过空闲状态0的非零空闲状态</p></td>
<td align="left"><p>Power Engine 插件已非法请求组件空闲状态转换。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x617</p></td>
<td align="left"><p>POP_FX_PLUGIN PowerEnginePlugin</p></td>
<td align="left"><p>UNICODE_STRING DeviceId</p></td>
<td align="left"><p>PEP_DEVICE_REGISTER PEP 注册</p></td>
<td align="left"><p>当处理设备注册通知时，Power Engine 插件返回了无效的接受类型。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x618</p></td>
<td align="left"><p>POP_FX_WORK_ORDER_WATCHDOG_INFO WorkOrder</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>已阻止运行时电源工作线程的时间太长。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x619</p></td>
<td align="left"><p>POP_FX_DEVICE 设备</p></td>
<td align="left"><p>组件索引</p></td>
<td align="left"><p>实际负责的子设备为空或 DEVICE_NODE</p></td>
<td align="left"><p>设备阻止进入最深运行时空闲电源状态的时间太长。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x61A</p></td>
<td align="left"><p>POP_FX_PLUGIN 电源引擎插件</p></td>
<td align="left"><p>POP_FX_DEVICE 设备</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>Power Engine 插件提供了有关组件性能状态信息的无效信息。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x61B</p></td>
<td align="left"><p>POP_FX_DEVICE 设备</p></td>
<td align="left"><p>组件索引</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>在注册设备性能状态之前，驱动程序已发出 perf 状态请求。 </p></td>
</tr>
<tr class="even">
<td align="left"><p>0x61C</p></td>
<td align="left"><p>POP_FX_DEVICE 设备</p></td>
<td align="left"><p>组件索引</p></td>
<td align="left"><p>参数无效</p>
<p>分隔</p>
<p>  0： PerfChangesCount 超出为此组件注册的性能状态集的数目</p></td>
<td align="left"><p> 驱动程序发出了包含无效参数的 perf 状态请求。
</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x61D</p></td>
<td align="left"><p>POP_FX_DEVICE 设备</p></td>
<td align="left"><p>组件索引</p></td>
<td align="left"><p>未完成的请求上下文</p></td>
<td align="left"><p>在上一个请求未完成时，驱动程序已发出 perf 状态请求。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x61E</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p> 启用自动转换时，Power Engine 插件尝试在调试器设备上执行关键转换。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x61F</p></td>
<td align="left"><p>POP_FX_DEVICE 设备</p></td>
<td align="left"><p>协调式空闲状态索引</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>Power Engine 插件尝试为不是整个平台的状态的协调式空闲状态启用自动调试器转换。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x620</p></td>
<td align="left"><p>POP_FX_DEVICE 设备</p></td>
<td align="left"><p> 协调式空闲状态索引</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p> Power Engine 插件尝试为不是整个平台的状态的协调式空闲状态注册 D 状态依赖关系。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x621</p></td>
<td align="left"><p>POP_FX_DEVICE 设备</p></td>
<td align="left"><p>组件索引</p></td>
<td align="left"><p>协调式空闲状态索引</p></td>
<td align="left"><p> Power Engine 插件尝试为不是整个平台的状态的协调式空闲状态注册 F 状态依赖关系。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x622</p></td>
<td align="left"><p>父 POP_FX_COMPONENT</p></td>
<td align="left"><p>子 POP_FX_COMPONENT</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>驱动程序已尝试从 PoFx 的未处理依赖项中注销。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x666</p></td>
<td align="left"><p>PPOP_PEP_ACTIVITY</p></td>
<td align="left"><p>新活动类型</p>
<p><strong>0：</strong> DevicePowerOn</p>
<p><strong>1：</strong> ComponentIdleStateChange</p>
<p><strong>2：</strong> ComponentActivating</p>
<p><strong>3：</strong> ComponentActive</p>
<p><strong>4：</strong> DevicePowerOff</p>
<p><strong>5：</strong> DeviceSuspend</p></td>
<td align="left"><p>冲突活动类型</p>
<p><strong>0：</strong> DevicePowerOn</p>
<p><strong>1：</strong> ComponentIdleStateChange</p>
<p><strong>2：</strong> ComponentActivating</p>
<p><strong>3：</strong> ComponentActive</p>
<p><strong>4：</strong> DevicePowerOff</p>
<p><strong>5：</strong> DeviceSuspend</p></td>
<td align="left"><p>默认的 Power Engine 插件尝试触发与其他活动冲突的新活动。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x667</p></td>
<td align="left"><p>POP_PEP_ACTIVITY</p></td>
<td align="left"><p>活动类型</p>
<p><strong>0：</strong> DevicePowerOn</p>
<p><strong>1：</strong> ComponentIdleStateChange</p>
<p><strong>2：</strong> ComponentActivating</p>
<p><strong>3：</strong> ComponentActive</p>
<p><strong>4：</strong> DevicePowerOff</p>
<p><strong>5：</strong> DeviceSuspend</p></td>
<td align="left"><p>POP_PEP_ACTIVITY_STATUS</p></td>
<td align="left"><p>默认电源引擎插件试图完成未在运行的活动。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x668</p></td>
<td align="left"><p>正在更新其引用计数的 PPPM_COORDINATED_STATE。</p></td>
<td align="left"><p>此函数观察到的引用计数值无效。</p></td>
<td align="left"><p>正在更新的平台空闲状态的掩码。</p></td>
<td align="left"><p> 默认电源引擎插件已尝试删除之前未被约束的平台空闲状态约束。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x669</p></td>
<td align="left"><p>正在更新其引用计数的 PPPM_COORDINATED_STATE。</p></td>
<td align="left"><p>此函数观察到的引用计数值无效。</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>当尝试独占通知 PoFx 有关平台空闲状态的可用性时，默认 Power Engine 插件遇到了内部一致性错误。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x680</p></td>
<td align="left"><p>NTSTATUS 故障代码。</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>由于运行时 power framework 缺少或格式不正确，无法分析所需的 ACPI 表。 这通常是由于 BIOS 错误引起的。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x700</p></td>
<td align="left"><p>PEPHANDLE</p></td>
<td align="left"><p>PEP_PPM_IDLE_SELECT</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>Power Engine 插件指定的处理器空闲依赖关系无效。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x701</p></td>
<td align="left"><p>挂起处理器的选定空闲状态的索引</p></td>
<td align="left"><p>挂起的处理器的 PRCB 地址</p></td>
<td align="left"><p>挂起的处理器的索引</p></td>
<td align="left"><p>处理器无法在分配的时间间隔内完成空闲转换。 这表明指定的处理器挂起。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x702</p></td>
<td align="left"><p>处理器的选定空闲状态的索引</p></td>
<td align="left"><p>处理器的空闲同步状态</p></td>
<td align="left"><p>挂起的处理器的 PRCB 地址</p></td>
<td align="left"><p>在没有操作系统的情况下，通过使用必要的 PPM 空闲同步) 使用必要的 PPM 空闲同步启动显式唤醒 (，处理器从不可中断状态唤醒。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x703</p></td>
<td align="left"><p>PEPHANDLE</p></td>
<td align="left"><p>PEP_PPM_QUERY_PLATFORM_STATE</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>在查询平台状态通知期间，Power Engine 插件指定了无效的处理器空闲依赖关系。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x704</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>协调式空闲状态过渡未能及时完成。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x705</p></td>
<td align="left"><p>PEPHANDLE</p></td>
<td align="left"><p>通知</p></td>
<td align="left"><p>标识非法篡改字段的四个字符的标记。 使用：. formats 标记的内核调试器中的解码标记，其中标记包含在 < > 中。 </p></td>
<td align="left"><p>Power Engine 插件已更改传入通知的缓冲区中的只读字段。 </p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x706</p></td>
<td align="left"><p>通知</p></td>
<td align="left"><p>标识包含非法值的字段的四字符标记。 使用：. formats 标记的内核调试器中的解码标记，其中标记包含在 < > 中。 </p></td>
<td align="left"><p>对于存在非法值的数组，值或索引非法</p></td>
<td align="left"><p>Power Engine 插件在传入通知的缓冲区的某个字段中返回了非法值。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x800</p></td>
<td align="left"><p>当前 CS 状态</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>系统处于连接待机状态时，监视器意外开启。
</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x801</p></td>
<td align="left"><p>显示状态更改原因</p></td>
<td align="left"><p>更新显示状态的会话 ID</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>发生了无效的显示状态转换。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x802</p></td>
<td align="left"><p>导致显示关闭的 POWER_MONITOR_REQUEST_REASON</p></td>
<td align="left"><p>如果启用电源事件处理器，则为 1; 否则为0。</p></td>
<td align="left"><p>指向 POP_PDC_IDLE_PHASE_WATCHDOG_CONTEXT 全局的指针。</p></td>
<td align="left"><p>PDC 系统空闲阶段 (NoCsPhase) 已阻止转换到新式备用时间比预期时间长。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x900</p></td>
<td align="left"><p>指向负责的电源设置回调的指针</p></td>
<td align="left"><p>在调用电源设置回调之前</p></td>
<td align="left"><p>从电源设置回调返回后的 IRQL</p></td>
<td align="left"><p> 使用修改后的 IRQL 返回的已注册的电源设置回调。 这表明回调更改了 IRQL，但没有在返回前还原原始 IRQL。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x901</p></td>
<td align="left"><p>DEVICE_OBJECT</p></td>
<td align="left"><p>IRP</p></td>
<td align="left"><p>线程的 APC 禁用计数</p></td>
<td align="left"><p>处理 power IRP 时，驱动程序已启用/禁用内核 Apc。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x4001</p></td>
<td align="left"><p>KE 错误子代码。</p>
<p>分隔</p>
<p>0x100： (INTERNAL_POWER_ERROR_KE_PROCESSOR_ON_TIMED_OUT) 固件花费了太长时间才能通电处理器。</p>
<p>0x101： (INTERNAL_POWER_ERROR_KE_INVALID_INTERRUPT_TARGET) 指定了无效的中断目标。</p>
<p>0x102： (INTERNAL_POWER_ERROR_KE_SETDESTINATION_FAILED) 无法更改中断行的目标目标。</p>
<p>0x103： (INTERNAL_POWER_ERROR_KE_IPI_REQUEST_FAILED) 在重定向中断时无法发出 IPI。</p>
<p>0x104： (INTERNAL_POWER_ERROR_KE_ARCH_NOT_SUPPORTED) 不受支持的处理器体系结构。</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p>预留</p></td>
<td align="left"><p> () INTERNAL_POWER_ERROR_KE_SUBCODE 在电源操作期间内核执行程序中出现内部故障。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0xAA64</p></td>
<td align="left"><p>错误代码</p></td>
<td align="left"><p>PSCI 函数 ID 正在进行</p></td>
<td align="left"><p>可选的内部上下文相关数据</p></td>
<td align="left"><p>AArm64 电源状态协调接口 (PSCI) 函数遇到无法恢复的严重错误。</p></td>
</tr>
</tbody>
</table>

<a name="resolution"></a>解决方法
----------

**一般说明**

在上表中，有几个参数是指向结构的指针。 例如，如果参数2作为设备 \_ 对象列出，则参数2是指向设备 \_ 对象结构的指针。 其中的某些结构是在 Windows 驱动程序工具包中包含的 wdm .h 中定义的。 例如，在 wdm .h 中定义以下结构。

-   异常 \_ 指针
-   设备 \_ 对象
-   IO \_ 堆栈 \_ 位置
-   PEP \_ 设备 \_ 注册

上表中出现的某些结构未在任何公共标头文件中定义。 您可以使用 [**dt**](dt--display-type-.md) 调试器命令查看这些结构的定义。 下面的示例演示如何使用 **dt** 命令查看 **设备 \_ 对象的 \_ 电源 \_ 扩展** 结构。

```dbgcmd
3: kd> dt nt!DEVICE_OBJECT_POWER_EXTENSION
   +0x000 IdleCount        : Uint4B
   +0x004 BusyCount        : Uint4B
   +0x008 BusyReference    : Uint4B
   +0x00c TotalBusyCount   : Uint4B
   +0x010 ConservationIdleTime : Uint4B
   +0x014 PerformanceIdleTime : Uint4B
   +0x018 DeviceObject     : Ptr64 _DEVICE_OBJECT
   +0x020 IdleList         : _LIST_ENTRY
   +0x030 IdleType         : _POP_DEVICE_IDLE_TYPE
   +0x034 IdleState        : _DEVICE_POWER_STATE
   +0x038 CurrentState     : _DEVICE_POWER_STATE
   +0x040 Volume           : _LIST_ENTRY
   +0x050 Specific         : <unnamed-tag>
```

以下过程将帮助你调试此 bug 检查的某些实例。

<span id="parameter-1-equals-0x2"></span><span id="PARAMETER-1-EQUALS-0X2"></span>
**当参数1等于0x2 时，调试 bug 检查0xA0**

1.  检查堆栈。 查找 **ntoskrnl.exe！PopExceptionFilter** 函数。 此函数包含以下代码作为其第一个参数。

    ```cpp
     (error_code << 16) | _LINE_
    ```

    如果调用方为 **PopExceptionFilter**，则此函数的第一个参数的类型为 PEXCEPTION \_ 指针。 请注意此参数的值。

2.  使用 [**dt (显示类型)**](dt--display-type-.md) 命令，并指定你在上一步中找到的作为 *参数* 的值。

    ```dbgcmd
    dt nt!_EXCEPTION_POINTERS argument 
    ```

    此命令显示结构。 请注意上下文记录的地址。

3.  使用 [**. .cxr (显示上下文记录)**](-cxr--display-context-record-.md) 命令，并指定你在上一步中找到的上下文记录作为 *记录*。

    ```dbgcmd
    .cxr record 
    ```

    此命令将注册上下文设置为正确的值。

4.  使用各种命令分析错误源。 从 [**kb 开始 (显示 Stack Backtrace)**](k--kb--kc--kd--kp--kp--kv--display-stack-backtrace-.md) 。

<span id="parameter-1-equals-0x7"></span><span id="PARAMETER-1-EQUALS-0X7"></span>
**当参数1等于0x7 时，调试 bug 检查0xA0**

1.  检查堆栈。 查找 **ntoskrnl.exe！PopExceptionFilter** 函数。 此函数的第一个参数的类型为 PEXCEPTION \_ 指针。 请注意此参数的值。

2.  使用 [**dt (显示类型)**](dt--display-type-.md) 命令，并指定你在上一步中找到的作为 *参数* 的值。

    ```dbgcmd
    dt nt!_EXCEPTION_POINTERS argument 
    ```

    此命令显示结构。 请注意上下文记录的地址。

3.  使用 [**. .cxr (显示上下文记录)**](-cxr--display-context-record-.md) 命令，并指定你在上一步中找到的上下文记录作为 *记录*。

    ```dbgcmd
    .cxr record 
    ```

    此命令将注册上下文设置为正确的值。

4.  使用各种命令分析错误源。 从 [**kb 开始 (显示 Stack Backtrace)**](k--kb--kc--kd--kp--kp--kv--display-stack-backtrace-.md) 。

<span id="parameter-1-equals-0x101"></span><span id="PARAMETER-1-EQUALS-0X101"></span>
**当参数1等于0x101 时，调试 bug 检查0xA0**

1.  使用 [**dt (显示类型)**](dt--display-type-.md) 命令，并将参数3的值指定为 *参数*。

    ```dbgcmd
    dt nt!_EXCEPTION_POINTERS argument 
    ```

    此命令显示结构。 请注意上下文记录的地址。

2.  使用 [**. .cxr (显示上下文记录)**](-cxr--display-context-record-.md) 命令，并指定你在上一 *步中找到* 的上下文记录。

    ```dbgcmd
    .cxr record 
    ```

    此命令将注册上下文设置为正确的值。

3.  使用各种命令分析错误源。 从 [**kb 开始 (显示 Stack Backtrace)**](k--kb--kc--kd--kp--kp--kv--display-stack-backtrace-.md) 。

 

 




