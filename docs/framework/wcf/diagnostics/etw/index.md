---
description: 詳細については、ETW を使用した分析トレースに関するページをご覧ください。
title: ETW を使用した分析トレース
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: fd40d40de2508fd251c793e4455c1e656a1cbbf6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798798"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="3a274-103">ETW を使用した分析トレース</span><span class="sxs-lookup"><span data-stu-id="3a274-103">Analytic Tracing with ETW</span></span>

<span data-ttu-id="3a274-104">Windows Communication Foundation (WCF) 分析トレースには、WCF サービスの実行中に診断情報をキャプチャする方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="3a274-104">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="3a274-105">Wcf 分析トレースイベントは、運用環境での WCF サービスのトラブルシューティングを可能にするために、WCF スタックの主要なポイントで生成されます。</span><span class="sxs-lookup"><span data-stu-id="3a274-105">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="3a274-106">WCF サービスの分析トレースは、wcf サービスをホストする製品サーバーのパフォーマンスにほとんど影響を与え [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] ません。これらのイベントは、Windows イベントトレーシング (ETW) セッションに非常に効率的に出力されるためです。</span><span class="sxs-lookup"><span data-stu-id="3a274-106">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a274-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3a274-107">In This Section</span></span>  

 [<span data-ttu-id="3a274-108">分析トレースの概要</span><span class="sxs-lookup"><span data-stu-id="3a274-108">Analytic Tracing Overview</span></span>](analytic-tracing-overview.md)  
 <span data-ttu-id="3a274-109">での WCF 分析トレースの動作について説明 [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="3a274-109">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="3a274-110">分析トレースの動的な有効化</span><span class="sxs-lookup"><span data-stu-id="3a274-110">Dynamically Enabling Analytic Tracing</span></span>](dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="3a274-111">ETW を使用してトレースを動的に有効化または無効化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3a274-111">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="3a274-112">メッセージ フローのトレースの構成</span><span class="sxs-lookup"><span data-stu-id="3a274-112">Configuring Message Flow Tracing</span></span>](configuring-message-flow-tracing.md)  
 <span data-ttu-id="3a274-113">メッセージ フローのトレースを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3a274-113">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="3a274-114">分析トレース イベント リファレンス</span><span class="sxs-lookup"><span data-stu-id="3a274-114">Analytic Trace Event Reference</span></span>](analytic-trace-event-reference.md)  
 <span data-ttu-id="3a274-115">イベント ID とそれらのイベント レベル、イベント メッセージ、およびキーワードを表で示します。</span><span class="sxs-lookup"><span data-stu-id="3a274-115">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a274-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a274-116">See also</span></span>

- [<span data-ttu-id="3a274-117">WCF サービスと Event Tracing for Windows</span><span class="sxs-lookup"><span data-stu-id="3a274-117">WCF Services and Event Tracing for Windows</span></span>](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [<span data-ttu-id="3a274-118">Windows のイベント トレースへの追跡イベント</span><span class="sxs-lookup"><span data-stu-id="3a274-118">Tracking Events into Event Tracing in Windows</span></span>](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
