---
title: WCF Data Services クライアント ライブラリ
description: WCF Data Services クライアント ライブラリを使用して .NET Framework クライアント アプリケーションからデータにアクセスしてデータを変更する方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 3d8a0f869454ce24d847127c2097239886f3395b
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805663"
---
# <a name="wcf-data-services-client-library"></a><span data-ttu-id="ec41b-103">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="ec41b-103">WCF Data Services Client Library</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="ec41b-104">HTTP 要求を送信し、データ サービスが返す Open Data Protocol (OData) フィードを処理できるのであれば、どのようなアプリケーションでも OData ベースのデータ サービスと対話できます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-104">Any application can interact with an Open Data Protocol (OData)-based data service if it can send an HTTP request and process the OData feed that a data service returns.</span></span> <span data-ttu-id="ec41b-105">この相互運用性によって、広範な Web 対応アプリケーションから OData ベースのサービスにアクセスすることが可能になります。</span><span class="sxs-lookup"><span data-stu-id="ec41b-105">This interoperability enables you to access OData-based services from a broad range of Web-enabled applications.</span></span> <span data-ttu-id="ec41b-106">WCF Data Services には、.NET Framework ベースのアプリケーションまたは Silverlight ベースのアプリケーションから OData フィードを使用する際のプログラミング エクスペリエンスを向上させるクライアント ライブラリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec41b-106">WCF Data Services includes client libraries that provide a richer programming experience when you consume OData feeds from .NET Framework or Silverlight-based applications.</span></span>  
  
 <span data-ttu-id="ec41b-107">クライアント ライブラリの 2 つの主要なクラスは、<xref:System.Data.Services.Client.DataServiceContext> クラスと <xref:System.Data.Services.Client.DataServiceQuery%601> クラスです。</span><span class="sxs-lookup"><span data-stu-id="ec41b-107">The two main classes of the client library are the <xref:System.Data.Services.Client.DataServiceContext> class and the <xref:System.Data.Services.Client.DataServiceQuery%601> class.</span></span> <span data-ttu-id="ec41b-108"><xref:System.Data.Services.Client.DataServiceContext> クラスは、特定のデータ サービスに対してサポートされている操作をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-108">The <xref:System.Data.Services.Client.DataServiceContext> class encapsulates operations that are supported against a specified data service.</span></span> <span data-ttu-id="ec41b-109">OData サービスはステートレスですが、コンテキストはステートレスではありません。</span><span class="sxs-lookup"><span data-stu-id="ec41b-109">Although OData services are stateless, the context is not.</span></span> <span data-ttu-id="ec41b-110">このため <xref:System.Data.Services.Client.DataServiceContext> クラスを使用すると、変更管理などの機能をサポートするためにデータ サービスとの対話操作間におけるクライアントの状態を保持できます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-110">Therefore, you can use the <xref:System.Data.Services.Client.DataServiceContext> class to maintain state on the client between interactions with the data service in order to support features such as change management.</span></span> <span data-ttu-id="ec41b-111">このクラスは、ID の管理と変更の追跡も行います。</span><span class="sxs-lookup"><span data-stu-id="ec41b-111">This class also manages identities and tracks changes.</span></span> <span data-ttu-id="ec41b-112"><xref:System.Data.Services.Client.DataServiceQuery%601> クラスは、特定のエンティティ セットに対するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-112">The <xref:System.Data.Services.Client.DataServiceQuery%601> class represents a query against a specific entity set.</span></span>  
  
 <span data-ttu-id="ec41b-113">このセクションでは、クライアント ライブラリを使用して .NET Framework クライアント アプリケーションからデータにアクセスしてデータを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-113">This section describes how to use client libraries to access and change data from a .NET Framework client application.</span></span> <span data-ttu-id="ec41b-114">Silverlight ベースのアプリケーションで WCF Data Services クライアント ライブラリを使用する方法については、「[WCF Data Services (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-114">For more information about how to use the WCF Data Services client library with a Silverlight-based application, see [WCF Data Services (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).</span></span> <span data-ttu-id="ec41b-115">その他の種類のアプリケーションで OData フィードを使用する場合は、それぞれに対応したクライアント ライブラリが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ec41b-115">Other client libraries are available that enable you to consume an OData feed in other kinds of applications.</span></span> <span data-ttu-id="ec41b-116">OData SDK の詳細については、[OData SDK のサンプルコード](https://www.odata.org/ecosystem/#sdk)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-116">For more information on OData SDK, see [OData SDK - Sample Code](https://www.odata.org/ecosystem/#sdk).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="ec41b-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ec41b-117">In This Section</span></span>  

 [<span data-ttu-id="ec41b-118">データ サービス クライアント ライブラリの生成</span><span class="sxs-lookup"><span data-stu-id="ec41b-118">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)  
 <span data-ttu-id="ec41b-119">クライアント ライブラリ、および OData フィードに基づくクライアント データ サービス クラスを生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-119">Describes how to generate a client library and client data service classes that are based on OData feeds.</span></span>  
  
 [<span data-ttu-id="ec41b-120">データ サービスに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="ec41b-120">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="ec41b-121">クライアント ライブラリを使用して .NET Framework ベースのアプリケーションからデータ サービスを照会する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-121">Describes how to query a data service from a .NET Framework-based application by using client libraries.</span></span>  
  
 [<span data-ttu-id="ec41b-122">遅延コンテンツの読み込み</span><span class="sxs-lookup"><span data-stu-id="ec41b-122">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)  
 <span data-ttu-id="ec41b-123">最初のクエリ応答に含まれない追加のコンテンツを読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-123">Describes how to load additional content not included in the initial query response.</span></span>  
  
 [<span data-ttu-id="ec41b-124">データ サービスの更新</span><span class="sxs-lookup"><span data-stu-id="ec41b-124">Updating the Data Service</span></span>](updating-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="ec41b-125">クライアント ライブラリを使用してエンティティおよびリレーションシップを作成、変更、および削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-125">Describes how to create, modify, and delete entities and relationships by using the client libraries.</span></span>  
  
 [<span data-ttu-id="ec41b-126">非同期操作</span><span class="sxs-lookup"><span data-stu-id="ec41b-126">Asynchronous Operations</span></span>](asynchronous-operations-wcf-data-services.md)  
 <span data-ttu-id="ec41b-127">非同期でデータ サービスを操作するためにクライアント ライブラリで提供される機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-127">Describes the facilities provided by the client libraries for working with a data service in an asynchronous manner.</span></span>  
  
 [<span data-ttu-id="ec41b-128">バッチ処理</span><span class="sxs-lookup"><span data-stu-id="ec41b-128">Batching Operations</span></span>](batching-operations-wcf-data-services.md)  
 <span data-ttu-id="ec41b-129">クライアント ライブラリを使用して複数の要求を 1 つのバッチでデータ サービスに送信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-129">Describes how to send multiple requests to the data service in a single batch by using the client libraries.</span></span>  
  
 [<span data-ttu-id="ec41b-130">コントロールへのデータのバインド</span><span class="sxs-lookup"><span data-stu-id="ec41b-130">Binding Data to Controls</span></span>](binding-data-to-controls-wcf-data-services.md)  
 <span data-ttu-id="ec41b-131">コントロールをデータ サービスによって返される OData フィードにバインドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-131">Describes how to bind controls to a OData feed returned by a data service.</span></span>  
  
 [<span data-ttu-id="ec41b-132">サービス操作の呼び出し</span><span class="sxs-lookup"><span data-stu-id="ec41b-132">Calling Service Operations</span></span>](calling-service-operations-wcf-data-services.md)  
 <span data-ttu-id="ec41b-133">クライアント ライブラリを使用してサービス操作を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-133">Describes how to use the client library to call service operations.</span></span>  
  
 [<span data-ttu-id="ec41b-134">データ サービス コンテキストの管理</span><span class="sxs-lookup"><span data-stu-id="ec41b-134">Managing the Data Service Context</span></span>](managing-the-data-service-context-wcf-data-services.md)  
 <span data-ttu-id="ec41b-135">クライアント ライブラリの動作を管理するオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-135">Describes options for managing the behavior of the client library.</span></span>  
  
 [<span data-ttu-id="ec41b-136">バイナリ データの操作</span><span class="sxs-lookup"><span data-stu-id="ec41b-136">Working with Binary Data</span></span>](working-with-binary-data-wcf-data-services.md)  
 <span data-ttu-id="ec41b-137">データ サービスによってデータ ストリームとして返されるバイナリ データにアクセスしてバイナリ データを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-137">Describes how to access and change binary data returned by the data service as a data stream.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec41b-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec41b-138">See also</span></span>

- [<span data-ttu-id="ec41b-139">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="ec41b-139">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="ec41b-140">はじめに</span><span class="sxs-lookup"><span data-stu-id="ec41b-140">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
