---
title: NFP 推动的外设无线设备配对
description: NFP 推动的外设无线设备配对
keywords:
- NFC
- 近场通信
- 近程
- 近场邻近感应
- NFP
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: fa4a42e268aac84199b2962b44ef2f56b3ae95ca
ms.sourcegitcommit: e47bd7eef2c2b89e3417d7f2dceb7c03d894f3c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97091186"
---
# <a name="nfp-facilitated-peripheral-wireless-device-pairing"></a>NFP 推动的外设无线设备配对


使用 NFP 技术可以实现的一个方案是将无线设备（如蓝牙键盘、鼠标和耳机）与 Windows 配对。 仅支持单向配对。 不支持智能设备（如手机）所需的双向配对。

为了实现这种配对，设备需要将其传输特定的配对信息提供给 NFP 技术。 对于蓝牙鼠标，鼠标需要根据蓝牙 SIG 的定义，发布标准的带外 (OOB) 配对信息的标准蓝牙。 NFP 提供程序需要从设备读取 OOB 数据，并将其提交给为配对类型消息订阅的 Windows 服务。

NFP 提供程序必须了解并处理蓝牙配对类型消息。 它们由 *messageType* 参数的类型组件标识。 例如，"配对：蓝牙" 可能对应于支持静态蓝牙 OOB 配对的设备。 当 NFP 提供程序收到其中一条配对消息时，它必须将消息只转换为标准 OOB 配对数据，并删除任何特定于技术的协议信息 (如 NDEF 标头) 。

 

 
## <a name="related-topics"></a>相关主题
[近现场通信 (NFC) API 参考](/windows-hardware/drivers/ddi/_nfpdrivers/)
