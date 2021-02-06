---
description: '詳細情報: インスタンス'
title: インスタンス
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 9cd602164816a419b481ff600a7537593d4f500e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655267"
---
# <a name="instances"></a><span data-ttu-id="b5540-103">インスタンス</span><span class="sxs-lookup"><span data-stu-id="b5540-103">Instances</span></span>

<span data-ttu-id="b5540-104">カウンター名 : インスタンス</span><span class="sxs-lookup"><span data-stu-id="b5540-104">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b5540-105">説明</span><span class="sxs-lookup"><span data-stu-id="b5540-105">Description</span></span>  

 <span data-ttu-id="b5540-106">現在サービスに含まれているインスタンス コンテキストの数。</span><span class="sxs-lookup"><span data-stu-id="b5540-106">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="b5540-107">多くの場合、インスタンス コンテキストの数とインスタンスの数は同じです。</span><span class="sxs-lookup"><span data-stu-id="b5540-107">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="b5540-108">ただし、次のシナリオではこの規則は当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="b5540-108">However, the following scenarios are exception to this rule.</span></span>  
  
- <span data-ttu-id="b5540-109">サービス メソッドが <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> メソッドを明示的に呼び出している場合。</span><span class="sxs-lookup"><span data-stu-id="b5540-109">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
- <span data-ttu-id="b5540-110"><xref:System.ServiceModel.ReleaseInstanceMode> が <xref:System.ServiceModel.OperationBehaviorAttribute> インスタンスに適用されている場合。</span><span class="sxs-lookup"><span data-stu-id="b5540-110">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5540-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5540-111">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
