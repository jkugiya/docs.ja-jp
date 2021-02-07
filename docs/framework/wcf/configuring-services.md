---
description: 詳細については、「WCF サービスの構成」を参照してください。
title: WCF サービスの構成
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 1c0df8c7d9b4e2b1a032f02e74db2de4a8de020c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720840"
---
# <a name="configuring-wcf-services"></a><span data-ttu-id="b4087-103">WCF サービスの構成</span><span class="sxs-lookup"><span data-stu-id="b4087-103">Configuring WCF services</span></span>

<span data-ttu-id="b4087-104">サービス コントラクトの設計、実装が終われば、サービスを構成できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="b4087-104">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="b4087-105">クライアント側から見たサービスの動作は、ここで定義、カスタマイズします。サービスと通信するためのアドレス、メッセージの送受信に使うトランスポートやエンコーディング、必要なセキュリティ型などを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b4087-105">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="b4087-106">定義やカスタマイズは、コード内で強制的に (簡単には変更できないような形で) 行う方法と、構成ファイルに記述して行う方法があります。エンドポイントのアドレス、実際に使うトランスポート、セキュリティ スキーマなど、サービスに関するさまざまな事項を定義、カスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="b4087-106">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="b4087-107">実際には、構成の記述は、WCF アプリケーションのプログラミングの主要な部分です。</span><span class="sxs-lookup"><span data-stu-id="b4087-107">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4087-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b4087-108">In This Section</span></span>  

 [<span data-ttu-id="b4087-109">簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="b4087-109">Simplified Configuration</span></span>](simplified-configuration.md)  
 <span data-ttu-id="b4087-110">.NET Framework 4 以降、wcf には、WCF の構成要件を簡略化する新しい既定の構成モデルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b4087-110">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="b4087-111">特定のサービスに対して WCF の構成を指定しない場合、ランタイムは既定のエンドポイント、バインド、および動作を使用してサービスを自動的に構成します。</span><span class="sxs-lookup"><span data-stu-id="b4087-111">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="b4087-112">構成ファイルを使用してサービスを構成する方法</span><span class="sxs-lookup"><span data-stu-id="b4087-112">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
 <span data-ttu-id="b4087-113">Windows Communication Foundation (WCF) サービスは、.NET Framework 構成テクノロジを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="b4087-113">A Windows Communication Foundation (WCF) service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="b4087-114">通常、XML 要素は、WCF サービスをホストするインターネットインフォメーションサービス (IIS) サイトの Web.config ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b4087-114">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="b4087-115">この要素によって、コンピューターごとにエンドポイント アドレス (サービスと通信するために使用する実際のアドレス) などの詳細情報を変更できます。</span><span class="sxs-lookup"><span data-stu-id="b4087-115">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="b4087-116">バインド</span><span class="sxs-lookup"><span data-stu-id="b4087-116">Bindings</span></span>](bindings.md)  
 <span data-ttu-id="b4087-117">さらに、WCF には、システムによって提供されるいくつかの共通構成がバインド形式で含まれており、使用されるトランスポート、セキュリティ、メッセージエンコーディングなど、クライアントとサービスの通信方法に関する最も基本的な機能を簡単に選択できます。</span><span class="sxs-lookup"><span data-stu-id="b4087-117">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="b4087-118">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="b4087-118">Endpoints</span></span>](endpoints.md)  
 <span data-ttu-id="b4087-119">WCF サービスとの通信はすべて、サービスの *エンドポイント* を介して行われます。</span><span class="sxs-lookup"><span data-stu-id="b4087-119">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="b4087-120">エンドポイントには、コントラクト、バインディングで指定されている構成情報、およびサービスの検索場所やサービスに関する情報の取得場所を示すアドレスが設定されています。</span><span class="sxs-lookup"><span data-stu-id="b4087-120">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="b4087-121">サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="b4087-121">Securing Services</span></span>](securing-services.md)  
 <span data-ttu-id="b4087-122">WCF と既存のセキュリティメカニズムを使用すると、機密性、整合性、認証、および承認を任意のサービスに実装できます。</span><span class="sxs-lookup"><span data-stu-id="b4087-122">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="b4087-123">また、セキュリティに関する成功および失敗を監査することも可能です。</span><span class="sxs-lookup"><span data-stu-id="b4087-123">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="b4087-124">WS-I Basic Profile 1.1 の相互運用可能サービスの作成</span><span class="sxs-lookup"><span data-stu-id="b4087-124">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="b4087-125">他のプラットフォームやオペレーティング システム上で動作するサービスやクライアントと、相互に運用できるような形でサービスを配置するために必要な事項は、WS-I Basic Profile 1.1 の仕様に記載されています。</span><span class="sxs-lookup"><span data-stu-id="b4087-125">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b4087-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4087-126">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="b4087-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4087-127">Related Sections</span></span>  

 [<span data-ttu-id="b4087-128">基本的なプログラミング ライフサイクル</span><span class="sxs-lookup"><span data-stu-id="b4087-128">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="b4087-129">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="b4087-129">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
 [<span data-ttu-id="b4087-130">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="b4087-130">Hosting Services</span></span>](hosting-services.md)  
  
 [<span data-ttu-id="b4087-131">クライアントを構築する</span><span class="sxs-lookup"><span data-stu-id="b4087-131">Building Clients</span></span>](building-clients.md)  
  
 [<span data-ttu-id="b4087-132">拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="b4087-132">Introduction to Extensibility</span></span>](introduction-to-extensibility.md)  
  
 [<span data-ttu-id="b4087-133">管理と診断</span><span class="sxs-lookup"><span data-stu-id="b4087-133">Administration and Diagnostics</span></span>](./diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="b4087-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4087-134">See also</span></span>

- [<span data-ttu-id="b4087-135">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="b4087-135">Basic WCF Programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="b4087-136">概念の概要</span><span class="sxs-lookup"><span data-stu-id="b4087-136">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="b4087-137">WCF 機能の詳細</span><span class="sxs-lookup"><span data-stu-id="b4087-137">WCF Feature Details</span></span>](./feature-details/index.md)
