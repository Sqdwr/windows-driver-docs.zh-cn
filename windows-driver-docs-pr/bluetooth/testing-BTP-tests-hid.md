---
title: Microsoft 蓝牙测试平台-HID
description: " (BTP) HID 测试的蓝牙测试平台。"
ms.date: 2/14/2020
ms.localizationpriority: medium
ms.openlocfilehash: 3c94a9ca125cc6817f88f533dbf908e5bd16e503
ms.sourcegitcommit: 418e6617e2a695c9cb4b37b5b60e264760858acd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96789183"
---
# <a name="btp-hid-tests"></a>BTP HID 测试 #

BTP HID 测试将测试本地系统如何通过 BR/EDR 或 LE 与远程收音机配对，并验证 HID 功能。

## <a name="setting-up"></a>设置 ##

首先检查绿色电源指示器、可选的黄色测试 LED 和 Traduci 上的3个橙色 Led 是否亮起。 确认 SUT 的蓝牙无线电已打开，并且相应的无线电 () 正确插入到 Traduci。 目前，RN42 收音机 **只能** 插入到作业中。 Simlarly Bluefruit 收音机 **只能** 插入 JC。 有关设置的更多详细信息，请参阅 [设置 BTP](testing-BTP-setup.md)。

可在 [BTP 硬件](testing-BTP-hw.md)中找到支持的无线电收发器信息和购买信息。

## <a name="running-the-hid-tests"></a>运行 HID 测试 ##

导航到从中提取 BTP 包的文件夹。 它通常位于下 `C:\BTP` 。 在以包的版本命名的文件夹中，你将找到下面引用的脚本。 然后运行以下任一文件：

- `RunHidTests.bat <radio name>` 从提升的命令提示符或
- `RunHidTests.ps1 <radio name>` 从提升权限的 PowerShell 控制台

可以找到有关可用的无线电名称参数的信息 [蓝牙测试平台支持的硬件](testing-BTP-hw.md#supported-radios)

你还可以在末尾添加可选参数 `-VerboseLogs` ，以获取 BTP 的内部操作的更详细输出。

当测试开始时，12针适配器旁边的红色 LED 将打开，一旦测试中的命令已发送给无线电，就会打开。 每次测试结束时，此 LED 都将关闭。 如果在上一次测试失败时，它在下一次测试开始时处于打开状态，我们将尝试关闭电源，并重新开机，使其返回到已知状态。 如果电源周期失败，则测试将失败，因为无线电处于未知状态。

## <a name="capturing-logs"></a>捕获日志 ##

若要捕获蓝牙日志，请按照 [GitHub 上适用于 Windows 存储库的总线工具](https://github.com/microsoft/busiotools/blob/master/bluetooth/tracing/readme.md)中的说明进行操作。

## <a name="known-issues"></a>已知问题 ##

- 压力测试：使用 LE 无线电在严格循环中运行测试可能导致配对或取消配对失败。
