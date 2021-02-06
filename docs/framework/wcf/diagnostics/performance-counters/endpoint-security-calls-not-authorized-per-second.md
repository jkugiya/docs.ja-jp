---
description: '詳細情報: エンドポイント: 1 秒あたりの承認されていないセキュリティ呼び出し'
title: 'エンドポイント : 1 秒あたりの承認されていないセキュリティ呼び出し'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: 55a49091426538304aceda52308e3f8df2010d6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655462"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="b089f-103">エンドポイント : 1 秒あたりの承認されていないセキュリティ呼び出し</span><span class="sxs-lookup"><span data-stu-id="b089f-103">Endpoint: Security Calls Not Authorized Per Second</span></span>

<span data-ttu-id="b089f-104">カウンター名 : 1 秒あたりの承認されていないセキュリティ呼び出し。</span><span class="sxs-lookup"><span data-stu-id="b089f-104">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b089f-105">説明</span><span class="sxs-lookup"><span data-stu-id="b089f-105">Description</span></span>  

 <span data-ttu-id="b089f-106">有効なユーザーから適切な保護を適用して送信されたが、特定のタスクの実行がユーザーに許可されていない、受信メッセージの 1 秒あたりの数です。</span><span class="sxs-lookup"><span data-stu-id="b089f-106">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="b089f-107">このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="b089f-107">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="b089f-108">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="b089f-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b089f-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b089f-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
