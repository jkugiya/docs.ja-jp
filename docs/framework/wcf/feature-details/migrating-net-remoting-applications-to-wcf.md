---
description: 詳細については、「.NET リモート処理アプリケーションの WCF への移行」を参照してください。
title: .NET リモート処理アプリケーションの WCF への移行
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 551ad759c11ab24d6ab83a466e8e94b8226bf4d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733763"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="2b863-103">.NET リモート処理アプリケーションの WCF への移行</span><span class="sxs-lookup"><span data-stu-id="2b863-103">Migrating .NET Remoting Applications to WCF</span></span>

<span data-ttu-id="2b863-104">**このトピックは、既存のアプリケーションとの下位互換性を維持するために残されているレガシテクノロジに固有のものであり、新規開発にはお勧めしません。これで、分散アプリケーションを WCF を使用して開発する必要があります。**</span><span class="sxs-lookup"><span data-stu-id="2b863-104">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="2b863-105">既存の .NET リモート処理アプリケーションで WCF を利用するには、統合と移行という2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="2b863-105">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="2b863-106">統合を使用すると、.NET リモート処理2.0 と WCF を並行して実行できるため、既存の .NET リモート処理2.0 コードを変更しなくても、両方のテクノロジで同じビジネスオブジェクトを同時に公開できます。</span><span class="sxs-lookup"><span data-stu-id="2b863-106">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="2b863-107">統合を行うには .NET Framework 2.0 以上で実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b863-107">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="2b863-108">WCF 機能を利用し、リモート処理2.0 システムとのワイヤ互換性を必要としない場合は、サービス全体を WCF に移行することができます。</span><span class="sxs-lookup"><span data-stu-id="2b863-108">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="2b863-109">.NET リモート処理2.0 から WCF への移行では、リモートオブジェクトのインターフェイスとその構成設定を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b863-109">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="2b863-110">これらのトピックはどちらも [、「リモート処理から Windows Communication Foundation へ](/previous-versions/aa730857(v=vs.80))」で説明されています。</span><span class="sxs-lookup"><span data-stu-id="2b863-110">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](/previous-versions/aa730857(v=vs.80)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b863-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b863-111">See also</span></span>

- [<span data-ttu-id="2b863-112">概念の概要</span><span class="sxs-lookup"><span data-stu-id="2b863-112">Conceptual Overview</span></span>](../conceptual-overview.md)
