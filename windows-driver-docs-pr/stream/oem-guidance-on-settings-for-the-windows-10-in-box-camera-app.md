---
title: 适用于 OEM 的 Windows 10 内置相机应用设置指南
description: 适用于 Windows 10 的新的内置相机应用程序适用于 Windows 平台支持的各种硬件，无需 OEM 进行任何配置。
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 078a6f7f22e13ce9fc5d034fd6a6106a40db649f
ms.sourcegitcommit: 418e6617e2a695c9cb4b37b5b60e264760858acd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96840521"
---
# <a name="oem-guidance-on-settings-for-the-windows-10-in-box-camera-app"></a>适用于 OEM 的 Windows 10 内置相机应用设置指南


适用于 Windows 10 的新的内置相机应用程序适用于 Windows 平台支持的各种硬件，无需 OEM 进行任何配置。 相机应用程序旨在确定设备硬件播发的设置，并为用户选择适当的默认值和选项。

以下部分介绍了内置相机应用使用的逻辑，以便 Oem 可以了解应用如何自行配置，如有必要，请相应地调整其驱动程序。

建议 Oem 首先将驱动程序配置为正确公布设备功能、测试其应用程序，然后考虑根据需要进行修改。

## <a name="background-and-legacy-behavior"></a>背景和旧行为


在 Windows Phone 7.5 (Mango) 中，引入了 ( # A0) 的照相机清单文件，为 Oem 提供了指定支持的照相机配置和自定义相机应用程序的方式。 在 Windows 10 中，不再支持此机制，已使用相机应用中的内置逻辑对其进行了替代，以便为用户选择和显示适当的设置。

## <a name="logic-for-choosing-resolutions-to-display"></a>选择要显示的分辨率的逻辑


-   **静止图像逻辑**

    对于静止图像分辨率，内置相机应用程序向用户显示纵横比列表，该列表将派生自驱动程序所支持的分辨率。 应用始终会在每个纵横比支持的最高分辨率中捕获。 1% 内的纵横比被视为相同。

    **建议 oem：** Oem 应确保其驱动程序支持与设备的屏幕纵横比匹配的分辨率设置。 此解决方案应提供高质量的捕获体验，因为它将被选为默认值 (请参阅下面) 的 *用于选择默认解决方法的逻辑* 。

-   **视频逻辑**

    对于视频捕获，照相机应用程序将向用户提供三个分辨率最高的分辨率指定的驱动程序，该驱动程序支持的帧速率超过15帧/秒 (fps) 。 对于这三个分辨率，照相机应用将向用户显示 15 fps 以上的所有可用帧速率 (因此支持高帧速率捕获) 。

    **建议 oem：** Oem 应确保它们的驱动程序支持其所需的视频捕获分辨率超过 15 fps (建议为获得最佳的客户体验) 使用25个 fps，并确保所公布的三个最高的分辨率是 OEM 希望向用户显示的分辨率。 确保驱动程序还指定高帧速率的功能。

## <a name="logic-for-choosing-default-resolution"></a>用于选择默认分辨率的逻辑


-   **静止图像逻辑**

    相机应用程序将通过选择驱动程序所播发的分辨率（最接近设备屏幕的纵横比），选择默认的 "仍可捕获" 选项，除非分辨率低于最高分辨率选项的60%。 这样做是为了筛选出会导致用户体验不佳的低分辨率。

-   **视频逻辑**

    照相机应用将选择支持 30 fps 捕获的最高分辨率，为视频捕获选择默认分辨率。

    如果可用分辨率超过 1080p@30 fps，则该应用将不会默认使用。 相反，应用程序将选择 1080p@30 fps，以限制有关电池、存储和散热问题的问题。 用户仍可以选择4K 分辨率。

## <a name="logic-for-choosing-default-camera"></a>选择默认照相机的逻辑


如果指定默认传感器，则默认情况下，照相机应用将使用该传感器。 如果未指定默认传感器，则照相机应用将使用后传感器。 如果没有背面传感器，应用将使用前传感器。

## <a name="legacy-oem-settings-and-settings-not-supported-in-windows-10-camera"></a>Windows 10 相机中不支持旧 OEM 设置和设置


不再支持通过相机清单文件为 Windows Phone 8 和 Windows Phone 8.1 设备指定的旧 OEM 设置。

这包括以下设置：

| 设置                  | 描述                                                                                                                                                                                                    |
|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| QuickBar 操作         | QuickBar 在 Windows 10 中不再存在。 此时，屏幕顶部将显示一个仪表板。 仪表板上的设置是由硬件功能决定的，不能由 OEM 自定义。 |
| 场景模式              | 新的相机应用程序不再提供场景模式或 OEM 自定义场景模式的功能。                                                                                                          |
| 自定义属性设置 | Windows 10 相机应用程序不再支持按属性 GUID 和值设置自定义属性。                                                                                                      |
| 自定义菜单项        | Windows 10 相机应用程序不再支持添加自定义菜单项。                                                                                                                                |

 

 

 




