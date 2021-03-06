---
title: 平台性能阈值
description: 有两种类型的性能阈值：静态阈值，适用于在运行时更改的平台和动态阈值。
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: e34ecf137a711194ff21db247cadf78c4a6eb8eb
ms.sourcegitcommit: 418e6617e2a695c9cb4b37b5b60e264760858acd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96829535"
---
# <a name="platform-performance-thresholds"></a>平台性能阈值


有两种类型的性能阈值：静态阈值，适用于在运行时更改的平台和动态阈值。 本主题描述了平台的静态性能阈值和动态阈值的允许范围。

静态性能阈值具有以下定义：

<a href="" id="highest-performance"></a>*最高性能*  
单个处理器可能达到的绝对最大性能（假定为理想条件）。 此性能级别可能会持续很长时间，并且仅在其他平台组件处于特定状态时才可实现 (例如，可能需要其他处理器处于空闲状态) 。

<a href="" id="nominal-performance"></a>*额定性能*  
处理器的最大持续性能级别，假定理想的环境条件 (即，最佳环境温度、处理器尚未由于先前的活动而处于热状态，当前可用的不受) 的低/冷电池限制。 所有处理器都应该能够同时在其额定性能上维持连续活动至少一秒钟。

<a href="" id="lowest-nonlinear-performance"></a>*非线性性能最低*  
性能调整后，可在其中达到非线性节能的最低性能级别。 例如，由于电压和频率缩放的组合效果优于合成功能，因此可通过以较低的性能状态运行来实现。 超过此阈值时，性能级别越低，性能级别越低。

<a href="" id="lowest-performance"></a>*最低性能*  
平台的绝对最低性能级别。 如果选择的性能级别低于最低的非线性性能级别，则可能会相当于效率方面的考虑，也可能实际上会导致效率降低，但应降低处理器的瞬间能耗。

**注意**  所有静态性能级别都不需要是唯一的。 例如，平台的标称性能级别也可能是其最高性能级别。

 

平台也可以选择表示动态性能阈值，这是一个有 *保证的性能* 阈值。 如果存在这种情况，则表示处理器的最大持续性能级别，考虑到所有已知的外部约束 (功率预算、温度限制、电源等 ) 。 所有处理器都应该能够同时维持其保证的性能级别，至少一秒钟。 有保证的性能级别需要处于 \[ 最高性能（包括在内）的范围内 \] 。

## <a name="heterogeneous-performance-thresholds"></a>异类性能阈值


PEP 对于系统中的所有处理器都必须使用相同的性能。 在具有异类处理器的平台上，所有处理器的性能特征可能不完全相同。 在这种情况下，PEP 必须合成可调整以适应处理器差异的性能调整，以便在相同的性能级别运行相同工作负荷的任意两个处理器大致同时完成。 PEP 应为不同的处理器类公开不同的功能，以便准确反映每个处理器的性能特征。

 

 




