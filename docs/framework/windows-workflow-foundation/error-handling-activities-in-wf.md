---
description: 詳細については、「WF でのエラー処理アクティビティ」を参照してください。
title: WF 内のエラー処理アクティビティ
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: ef26c47d8d99f2d2186ef02820f9bebe691c2ff8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742450"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="ddd96-103">WF 内のエラー処理アクティビティ</span><span class="sxs-lookup"><span data-stu-id="ddd96-103">Error Handling Activities in WF</span></span>

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="ddd96-104">には、エラーの処理および回復を実装するためのシステム標準のアクティビティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ddd96-104">provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="ddd96-105">詳細については、「 [例外](exceptions.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。</span><span class="sxs-lookup"><span data-stu-id="ddd96-105">For more information, see [Exceptions](exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="ddd96-106">エラー処理アクティビティ</span><span class="sxs-lookup"><span data-stu-id="ddd96-106">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="ddd96-107">`TryCatch` アクティビティ内からスローされた最後の例外を再スローします。</span><span class="sxs-lookup"><span data-stu-id="ddd96-107">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="ddd96-108">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="ddd96-108">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="ddd96-109">例外処理を実装します。</span><span class="sxs-lookup"><span data-stu-id="ddd96-109">Implements exception handling.</span></span>|
