---
title: WDI_TLV_WAKE_PACKET_IPv6_TCP_SYNC
description: WDI_TLV_WAKE_PACKET_IPv6_TCP_SYNC 是包含 LAN 唤醒 IPv6 TCP 同步数据包信息的 TLV。
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 WDI_TLV_WAKE_PACKET_IPv6_TCP_SYNC 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: 33ce66d32cfea1fcde7971ce88e17d380e9d9c19
ms.sourcegitcommit: 418e6617e2a695c9cb4b37b5b60e264760858acd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96821925"
---
# <a name="wdi_tlv_wake_packet_ipv6_tcp_sync"></a>WDI \_ TLV \_ 唤醒 \_ 数据包 \_ IPv6 \_ TCP \_ 同步


WDI \_ tlv \_ 唤醒 \_ 数据包 \_ IPv6 \_ tcp \_ SYNC 是包含 LAN 唤醒 IPV6 tcp 同步数据包信息的 tlv。

## <a name="tlv-type"></a>TLV 类型


0x5E

## <a name="length"></a>长度


Sum (所有包含的元素的大小) 。

## <a name="values"></a>值


| 类型        | 描述                                                      |
|-------------|------------------------------------------------------------------|
| UINT32      | 指定 WoL 模式 ID。                                    |
| UINT8 \[ 16\] | 指定 TCP SYN 数据包中的 IPv6 源地址。         |
| UINT8 \[ 16\] | 指定 TCP SYN 数据包中的 IPv6 目标地址。    |
| UINT16      | 指定 TCP SYN 数据包中的 TCP 源端口号。      |
| UINT16      | 指定 TCP SYN 数据包中的 TCP 目标端口号。 |

 

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>最低受支持的客户端</p></td>
<td><p>Windows 10</p></td>
</tr>
<tr class="even">
<td><p>最低受支持的服务器</p></td>
<td><p>Windows Server 2016</p></td>
</tr>
<tr class="odd">
<td><p>标头</p></td>
<td>Wditypes.hpp</td>
</tr>
</tbody>
</table>

 

 




