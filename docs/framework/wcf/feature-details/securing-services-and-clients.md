---
description: 詳細については、「サービスとクライアントのセキュリティ保護」を参照してください。
title: サービスおよびクライアントのセキュリティ保護
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: ff947e8bf975fd3fb3c6513ee0bf49bb21a951dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632634"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="4cc5c-103">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="4cc5c-103">Securing Services and Clients</span></span>

<span data-ttu-id="4cc5c-104">このセクションの情報は、Windows Communication Foundation (WCF) でのセキュリティのプログラミングに焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="4cc5c-104">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="4cc5c-105">一般に、これには、システムが提供する適切なバインディングを選択すること、セキュリティ要素のプロパティを適切に設定すること、サービス側/クライアント側で使う資格情報の検索方法にまつわる、サービスの動作に関するプロパティを適切に設定することなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4cc5c-105">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="4cc5c-106">これらの手法は、 [一般的なセキュリティシナリオ](common-security-scenarios.md)に示すように、ほとんどのシナリオでほとんどのユーザーのセキュリティ要件に対応しています。</span><span class="sxs-lookup"><span data-stu-id="4cc5c-106">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](common-security-scenarios.md).</span></span> <span data-ttu-id="4cc5c-107">シナリオにより多くの機能が必要な場合は、まず「 [カスタムバインドを使用したセキュリティ機能](security-capabilities-with-custom-bindings.md)」を参照してください。ソリューションが明らかでない場合は、「 [セキュリティの拡張](../extending/extending-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4cc5c-107">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../extending/extending-security.md).</span></span> <span data-ttu-id="4cc5c-108">豊富な信頼性情報を使用するシステムを作成 (または相互運用) する場合は、「 [承認](authorization-in-wcf.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4cc5c-108">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4cc5c-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4cc5c-109">In This Section</span></span>  

 [<span data-ttu-id="4cc5c-110">WCF セキュリティのプログラミング</span><span class="sxs-lookup"><span data-stu-id="4cc5c-110">Programming WCF Security</span></span>](programming-wcf-security.md)  
 <span data-ttu-id="4cc5c-111">メッセージを保護するために使うプログラミング モデルの概要</span><span class="sxs-lookup"><span data-stu-id="4cc5c-111">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="4cc5c-112">トランスポート セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="4cc5c-112">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="4cc5c-113">トランスポート層を介してやり取りするメッセージを保護する方法の概要</span><span class="sxs-lookup"><span data-stu-id="4cc5c-113">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="4cc5c-114">メッセージのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="4cc5c-114">Message Security</span></span>](message-security-in-wcf.md)  
 <span data-ttu-id="4cc5c-115">Windows Communication Foundation (WCF) でメッセージレベルのセキュリティを使用する理由の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="4cc5c-115">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="4cc5c-116">セキュリティで保護されたセッション</span><span class="sxs-lookup"><span data-stu-id="4cc5c-116">Secure Sessions</span></span>](secure-sessions.md)  
 <span data-ttu-id="4cc5c-117">WCF セッションをセキュリティで保護する場合に必要な考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="4cc5c-117">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="4cc5c-118">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="4cc5c-118">Working with Certificates</span></span>](working-with-certificates.md)  
 <span data-ttu-id="4cc5c-119">X.509 証明書を使用する際に必要となる主なタスクの解説</span><span class="sxs-lookup"><span data-stu-id="4cc5c-119">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4cc5c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cc5c-120">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="4cc5c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cc5c-121">Related Sections</span></span>  

 [<span data-ttu-id="4cc5c-122">セキュリティの概念</span><span class="sxs-lookup"><span data-stu-id="4cc5c-122">Security Concepts</span></span>](security-concepts.md)  
  
 [<span data-ttu-id="4cc5c-123">セキュリティの拡張</span><span class="sxs-lookup"><span data-stu-id="4cc5c-123">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="4cc5c-124">一般的なセキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="4cc5c-124">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
 [<span data-ttu-id="4cc5c-125">バインディングとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="4cc5c-125">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="4cc5c-126">カスタム バインディングを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="4cc5c-126">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="4cc5c-127">セキュリティの拡張</span><span class="sxs-lookup"><span data-stu-id="4cc5c-127">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="4cc5c-128">承認</span><span class="sxs-lookup"><span data-stu-id="4cc5c-128">Authorization</span></span>](authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="4cc5c-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cc5c-129">See also</span></span>

- [<span data-ttu-id="4cc5c-130">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="4cc5c-130">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- <span data-ttu-id="4cc5c-131">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4cc5c-131">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
