---
description: '詳細情報: エンドポイントのパフォーマンスカウンター'
title: エンドポイントのパフォーマンス カウンター
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 60cd94d5d954c87f4b37469688ee809a13fa3cb4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771237"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="cd493-103">エンドポイントのパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="cd493-103">Endpoint Performance Counters</span></span>

<span data-ttu-id="cd493-104">エンドポイントのパフォーマンス カウンターは、エンドポイントがどのようにメッセージを受信しているかを示すデータをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="cd493-104">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="cd493-105">パフォーマンス モニターを使用して表示する場合、これらのカウンターは、`ServiceModelEndpoint 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="cd493-105">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="cd493-106">インスタンスの名前には次のパターンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="cd493-106">The instances are named using this pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 <span data-ttu-id="cd493-107">このデータは、個々の操作で収集されるデータに似ていますが、そのエンドポイントだけで集約されたデータです。</span><span class="sxs-lookup"><span data-stu-id="cd493-107">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="cd493-108">パフォーマンス カウンターのインスタンス名の長さには制限があります。</span><span class="sxs-lookup"><span data-stu-id="cd493-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="cd493-109">Windows Communication Foundation (WCF) カウンターインスタンス名が最大長を超えると、WCF はインスタンス名の一部をハッシュ値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="cd493-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd493-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd493-110">See also</span></span>

- [<span data-ttu-id="cd493-111">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="cd493-111">Performance Counters</span></span>](index.md)
