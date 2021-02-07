---
description: 詳細については、Windows Communication Foundation エンドポイント」を参照してください。
title: Windows Communication Foundation エンドポイント
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: caa918f2dd7ca7b0289cc1faf6d189270596808b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756774"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="40e93-103">Windows Communication Foundation エンドポイント</span><span class="sxs-lookup"><span data-stu-id="40e93-103">Windows Communication Foundation Endpoints</span></span>

<span data-ttu-id="40e93-104">Windows Communication Foundation (WCF) サービスとの通信はすべて、サービスの *エンドポイント* を介して行われます。</span><span class="sxs-lookup"><span data-stu-id="40e93-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="40e93-105">エンドポイントは、クライアントが WCF サービスによって提供される機能にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="40e93-105">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="40e93-106">エンドポイントを作成する方法の概要については、「 [エンドポイントの作成の概要](endpoint-creation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40e93-106">For an overview about how to create an endpoint, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="40e93-107">エンドポイントは次の要素から成ります。</span><span class="sxs-lookup"><span data-stu-id="40e93-107">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="40e93-108">そのエンドポイントの場所を示すアドレス。</span><span class="sxs-lookup"><span data-stu-id="40e93-108">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="40e93-109">クライアントがエンドポイントと通信する方法を指定するバインディング。</span><span class="sxs-lookup"><span data-stu-id="40e93-109">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="40e93-110">利用可能なメソッドを指定するためのコントラクト。</span><span class="sxs-lookup"><span data-stu-id="40e93-110">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="40e93-111">エンドポイントを構成する個々の要素を指定する方法については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40e93-111">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="40e93-112">エンドポイント アドレスの指定</span><span class="sxs-lookup"><span data-stu-id="40e93-112">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="40e93-113">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="40e93-113">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="40e93-114">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="40e93-114">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="40e93-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="40e93-115">In This Section</span></span>  

 [<span data-ttu-id="40e93-116">エンドポイントの作成の概要</span><span class="sxs-lookup"><span data-stu-id="40e93-116">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)  
 <span data-ttu-id="40e93-117">エンドポイントの構造を説明し、構成やコード内にエンドポイントを定義する方法と、ランタイムによって提供される既定のエンドポイント、バインディング、および動作の使用方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="40e93-117">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="40e93-118">エンドポイント アドレスの指定</span><span class="sxs-lookup"><span data-stu-id="40e93-118">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
 <span data-ttu-id="40e93-119">WCF サービスとの通信がエンドポイントを介してどのように行われるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="40e93-119">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="40e93-120">方法: 構成にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="40e93-120">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="40e93-121">構成でサービス エンドポイントを作成する方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="40e93-121">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="40e93-122">方法: コード内にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="40e93-122">How to: Create a Service Endpoint in Code</span></span>](./feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="40e93-123">コードでサービス エンドポイントを作成する方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="40e93-123">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="40e93-124">メタデータ エンドポイントを公開する</span><span class="sxs-lookup"><span data-stu-id="40e93-124">Publishing Metadata Endpoints</span></span>](publishing-metadata-endpoints.md)  
 <span data-ttu-id="40e93-125">構成およびコードでメタデータ エンドポイントを公開することによりってメタデータを公開する方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="40e93-125">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="40e93-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="40e93-126">Reference</span></span>  

 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="40e93-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="40e93-127">Related Sections</span></span>  

 [<span data-ttu-id="40e93-128">基本的なプログラミング ライフサイクル</span><span class="sxs-lookup"><span data-stu-id="40e93-128">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)
