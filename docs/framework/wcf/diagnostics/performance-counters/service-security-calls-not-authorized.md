---
description: '詳細情報: サービス: 承認されていないセキュリティ呼び出し'
title: 'サービス : 承認されていないセキュリティ呼び出し'
ms.date: 03/30/2017
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
ms.openlocfilehash: 2185f478d534696ea308e06d8411df6888420914
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735752"
---
# <a name="service-security-calls-not-authorized"></a><span data-ttu-id="182d5-103">サービス : 承認されていないセキュリティ呼び出し</span><span class="sxs-lookup"><span data-stu-id="182d5-103">Service: Security Calls Not Authorized</span></span>

<span data-ttu-id="182d5-104">カウンター名 : 承認されていないセキュリティ呼び出し。</span><span class="sxs-lookup"><span data-stu-id="182d5-104">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="182d5-105">説明</span><span class="sxs-lookup"><span data-stu-id="182d5-105">Description</span></span>  

 <span data-ttu-id="182d5-106">このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="182d5-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="182d5-107">受信メッセージが有効なユーザーから適切な保護を適用して送信されたものであり、その一方でそのユーザーが特定のタスクの実行を許可されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="182d5-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
