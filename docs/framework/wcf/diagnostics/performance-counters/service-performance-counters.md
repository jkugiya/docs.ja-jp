---
description: 詳細については、「サービスパフォーマンスカウンター」を参照してください。
title: サービス パフォーマンス カウンター
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 16f6f2548cf7f92b64264ac606423c69e62cd110
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686038"
---
# <a name="service-performance-counters"></a><span data-ttu-id="4aa3d-103">サービス パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="4aa3d-103">Service Performance Counters</span></span>

<span data-ttu-id="4aa3d-104">サービスのパフォーマンス カウンターはサービス動作全体を測定し、サービス全体のパフォーマンスを診断するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="4aa3d-104">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="4aa3d-105">パフォーマンス モニター (Perfmon.exe) を使用して表示する場合、これらのカウンターは、`ServiceModelService 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="4aa3d-105">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="4aa3d-106">インスタンスには次のパターンの名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="4aa3d-106">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> <span data-ttu-id="4aa3d-107">パフォーマンス カウンターのインスタンス名の長さには制限があります。</span><span class="sxs-lookup"><span data-stu-id="4aa3d-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="4aa3d-108">Windows Communication Foundation (WCF) カウンターインスタンス名が最大長を超えると、WCF はインスタンス名の一部をハッシュ値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4aa3d-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa3d-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="4aa3d-109">See also</span></span>

- [<span data-ttu-id="4aa3d-110">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="4aa3d-110">Performance Counters</span></span>](index.md)
