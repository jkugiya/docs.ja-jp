---
description: 詳細については、「エンドツーエンドのトレース」を参照してください。
title: エンドツーエンドのトレース
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: c1c4a38d4ef8c445994d42abeafbb25da9a5f326
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759433"
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="00c52-103">エンドツーエンドのトレース</span><span class="sxs-lookup"><span data-stu-id="00c52-103">End-to-End Tracing</span></span>

<span data-ttu-id="00c52-104">エンドツーエンド (e2e) のトレースにより、開発者は、Windows Communication Foundation (WCF) インフラストラクチャでコードの実行に従い、コードパスが失敗した原因を調査したり、容量計画とパフォーマンス分析の詳細なトレースを提供したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="00c52-104">End to End (e2e) Tracing allows developers to follow the execution of code in the Windows Communication Foundation (WCF) infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> <span data-ttu-id="00c52-105">Windows Communication Foundation (WCF) には、エラーの原因を診断するのに役立つ3つの相関関係メカニズム (アクティビティ、転送、および伝達) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="00c52-105">Windows Communication Foundation (WCF) provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="00c52-106">エンドツーエンドのトレースシナリオの一覧と、それぞれのアクティビティとトレースの設計については、「 [エンドツーエンドのトレースのシナリオ](end-to-end-tracing-scenarios.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00c52-106">See [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00c52-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="00c52-107">In This Section</span></span>  

 <span data-ttu-id="00c52-108">[アクティビティ](activity.md): WINDOWS COMMUNICATION FOUNDATION (WCF) トレースモデルのアクティビティトレースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="00c52-108">[Activity](activity.md):  Describes activity traces in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
 <span data-ttu-id="00c52-109">[転送](transfer.md): WINDOWS COMMUNICATION FOUNDATION (WCF) トレースモデルでの転送について説明し、transfer を使用してエンドポイント内のアクティビティを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="00c52-109">[Transfer](transfer.md):  Describes transfer in the Windows Communication Foundation (WCF) tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="00c52-110">[伝達](propagation.md): WINDOWS COMMUNICATION FOUNDATION (WCF) トレースモデルでのアクティビティの伝達、および伝達を使用したエンドポイント間でのアクティビティの関連付けについて説明します。</span><span class="sxs-lookup"><span data-stu-id="00c52-110">[Propagation](propagation.md):  Describes activity propagation in the Windows Communication Foundation (WCF) tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="00c52-111">トレースの種類の概要</span><span class="sxs-lookup"><span data-stu-id="00c52-111">Trace Type Summary</span></span>](trace-type-summary.md)  
  
 <span data-ttu-id="00c52-112">すべてのアクティビティ トレースの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="00c52-112">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00c52-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="00c52-113">See also</span></span>

- [<span data-ttu-id="00c52-114">トレースの構成</span><span class="sxs-lookup"><span data-stu-id="00c52-114">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="00c52-115">サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="00c52-115">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="00c52-116">エンドツーエンドのトレースのシナリオ</span><span class="sxs-lookup"><span data-stu-id="00c52-116">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="00c52-117">サービス トレース ビューアー ツール (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="00c52-117">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
