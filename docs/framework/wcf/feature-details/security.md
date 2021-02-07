---
description: '詳細情報: Windows Communication Foundation セキュリティ'
title: Windows Communication Foundation セキュリティ
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: 8cf748504c85844f82f8941be1b60bb29478f730
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726794"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="93fd2-103">Windows Communication Foundation セキュリティ</span><span class="sxs-lookup"><span data-stu-id="93fd2-103">Windows Communication Foundation Security</span></span>

<span data-ttu-id="93fd2-104">このセクションのトピックでは、Windows Communication Foundation (WCF) のセキュリティ機能と、それらを使用してメッセージをセキュリティで保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-104">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="93fd2-105">Windows Server AppFabric とセキュリティの詳細については、「 [Windows Server appfabric のセキュリティモデル](/previous-versions/appfabric/ee677202(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93fd2-105">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="93fd2-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="93fd2-106">In This Section</span></span>  

 [<span data-ttu-id="93fd2-107">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="93fd2-107">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="93fd2-108">WCF のセキュリティ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-108">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="93fd2-109">セキュリティの概念</span><span class="sxs-lookup"><span data-stu-id="93fd2-109">Security Concepts</span></span>](security-concepts.md)  
 <span data-ttu-id="93fd2-110">WCF セキュリティで使用される基本的な用語と概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-110">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="93fd2-111">一般的なセキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="93fd2-111">Common Security Scenarios</span></span>](common-security-scenarios.md)  
 <span data-ttu-id="93fd2-112">WCF で構成できるシナリオとトポロジについて説明します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-112">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="93fd2-113">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="93fd2-113">Security Behaviors</span></span>](security-behaviors-in-wcf.md)  
 <span data-ttu-id="93fd2-114">資格情報の設定など、セキュリティに影響する WCF の動作に関する概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-114">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="93fd2-115">バインディングとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="93fd2-115">Bindings and Security</span></span>](bindings-and-security.md)  
 <span data-ttu-id="93fd2-116">カスタム セキュリティ バインディングの作成方法を示すトピックなど、バインディングをセキュリティの観点から説明します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-116">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="93fd2-117">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="93fd2-117">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
 <span data-ttu-id="93fd2-118">WCF のセキュリティ機能を使用してメッセージをセキュリティで保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-118">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="93fd2-119">認証</span><span class="sxs-lookup"><span data-stu-id="93fd2-119">Authentication</span></span>](authentication-in-wcf.md)  
 <span data-ttu-id="93fd2-120">一般的な認証タスクを示します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-120">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="93fd2-121">承認</span><span class="sxs-lookup"><span data-stu-id="93fd2-121">Authorization</span></span>](authorization-in-wcf.md)  
 <span data-ttu-id="93fd2-122">セキュリティ実装を使用した一般的な承認シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-122">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="93fd2-123">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="93fd2-123">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
 <span data-ttu-id="93fd2-124">フェデレーションの基本事項と、フェデレーション サーバーと通信するクライアントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-124">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="93fd2-125">部分信頼</span><span class="sxs-lookup"><span data-stu-id="93fd2-125">Partial Trust</span></span>](partial-trust.md)  
 <span data-ttu-id="93fd2-126">部分的に信頼されている場合に、部分信頼シナリオと WCF 制限を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-126">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="93fd2-127">監査</span><span class="sxs-lookup"><span data-stu-id="93fd2-127">Auditing</span></span>](auditing-security-events.md)  
 <span data-ttu-id="93fd2-128">セキュリティ イベントを監査する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="93fd2-128">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="93fd2-129">セキュリティ ガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="93fd2-129">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
 <span data-ttu-id="93fd2-130">セキュリティで保護された WCF アプリケーションを作成するためのガイドライン。</span><span class="sxs-lookup"><span data-stu-id="93fd2-130">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="93fd2-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="93fd2-131">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="93fd2-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="93fd2-132">Related Sections</span></span>  

 [<span data-ttu-id="93fd2-133">WCF 機能の詳細</span><span class="sxs-lookup"><span data-stu-id="93fd2-133">WCF Feature Details</span></span>](index.md)  
  
 [<span data-ttu-id="93fd2-134">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="93fd2-134">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="93fd2-135">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="93fd2-135">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)  
  
 [<span data-ttu-id="93fd2-136">概念の概要</span><span class="sxs-lookup"><span data-stu-id="93fd2-136">Conceptual Overview</span></span>](../conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="93fd2-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="93fd2-137">See also</span></span>

- [<span data-ttu-id="93fd2-138">アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="93fd2-138">Configuring Your Application</span></span>](../diagnostics/configuring-your-application.md)
