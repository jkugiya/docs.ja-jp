---
description: 詳細については、「Windows Communication Foundation バインド」を参照してください。
title: Windows Communication Foundation バインディング
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF]
ms.assetid: 845df323-be53-4848-92ef-ba67a406484d
ms.openlocfilehash: 1d21fb9593917b50a22bd0b0bf0f4506fd99b8df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781169"
---
# <a name="windows-communication-foundation-bindings"></a><span data-ttu-id="6d310-103">Windows Communication Foundation バインディング</span><span class="sxs-lookup"><span data-stu-id="6d310-103">Windows Communication Foundation Bindings</span></span>

<span data-ttu-id="6d310-104">バインディングは、Windows Communication Foundation (WCF) サービスエンドポイントが他のエンドポイントと通信する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="6d310-104">Bindings specify how a Windows Communication Foundation (WCF) service endpoint communicates with other endpoints.</span></span> <span data-ttu-id="6d310-105">バインディングでは、まず、使用するトランスポート (HTTP や TCP など) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d310-105">At its most basic, a binding must specify the transport (for example, HTTP or TCP) to use.</span></span> <span data-ttu-id="6d310-106">セキュリティやトランザクションのサポートなど、その他の特性もバインディングによって設定できます。</span><span class="sxs-lookup"><span data-stu-id="6d310-106">You can also set other characteristics, such as security and transaction support, through bindings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d310-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6d310-107">In This Section</span></span>  

 [<span data-ttu-id="6d310-108">WCF のバインディングの概要</span><span class="sxs-lookup"><span data-stu-id="6d310-108">WCF Bindings Overview</span></span>](bindings-overview.md)  
 <span data-ttu-id="6d310-109">WCF バインディングの概要、システムが提供するバインディング、およびそれらを定義または変更する方法の概要。</span><span class="sxs-lookup"><span data-stu-id="6d310-109">Overview of what WCF bindings do, what bindings the system provides, and how you can define or modify them.</span></span>  
  
 [<span data-ttu-id="6d310-110">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="6d310-110">System-Provided Bindings</span></span>](system-provided-bindings.md)  
 <span data-ttu-id="6d310-111">WCF に含まれるバインディングの一覧。</span><span class="sxs-lookup"><span data-stu-id="6d310-111">A list of bindings included with WCF.</span></span> <span data-ttu-id="6d310-112">これらのバインディングは、ほとんどのセキュリティ要件およびメッセージ パターン要件を満たします。</span><span class="sxs-lookup"><span data-stu-id="6d310-112">These bindings cover the majority of security and message pattern requirements.</span></span>  
  
 [<span data-ttu-id="6d310-113">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="6d310-113">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
 <span data-ttu-id="6d310-114">WCF バインディングには、クライアントがサービスエンドポイントに接続するために使用する必要がある重要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6d310-114">A WCF binding contains important information that clients must use to connect to service endpoints.</span></span>  
  
 [<span data-ttu-id="6d310-115">サービスのバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="6d310-115">Configuring Bindings for Services</span></span>](configuring-bindings-for-wcf-services.md)  
 <span data-ttu-id="6d310-116">管理者やインストール担当者は、構成を使用してサービス エンドポイントのバインディングをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="6d310-116">Configuration enables administrators and installers to customize the bindings for service endpoints.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6d310-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d310-117">Reference</span></span>  

 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="6d310-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d310-118">Related Sections</span></span>  

 [<span data-ttu-id="6d310-119">エンドポイント:アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="6d310-119">Endpoints: Addresses, Bindings, and Contracts</span></span>](./feature-details/endpoints-addresses-bindings-and-contracts.md)  
  
 [<span data-ttu-id="6d310-120">バインド</span><span class="sxs-lookup"><span data-stu-id="6d310-120">Bindings</span></span>](./feature-details/bindings.md)  
  
## <a name="see-also"></a><span data-ttu-id="6d310-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d310-121">See also</span></span>

- [<span data-ttu-id="6d310-122">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="6d310-122">Custom Bindings</span></span>](./extending/custom-bindings.md)
