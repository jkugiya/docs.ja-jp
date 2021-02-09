---
description: '詳細情報: データ サービスのホスティング (WCF Data Services)'
title: データ サービスのホスティング (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: 519adde3a3e054d68ff9a1b7acf7ff06c0ca7532
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765790"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="3e5ff-103">データ サービスのホスティング (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="3e5ff-103">Hosting the Data Service (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="3e5ff-104">WCF Data Services を使用すると、Open Data Protocol (OData) フィードとしてデータを公開するデータ サービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-104">By using WCF Data Services, you can create a service that exposes data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="3e5ff-105">このデータ サービスは、<xref:System.Data.Services.DataService%601> から継承されたクラスとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-105">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="3e5ff-106">このクラスは、OData からの要件に応じて、要求メッセージを処理し、データ ソースに基づいて更新し、応答メッセージを生成するための機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-106">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="3e5ff-107">ただし、データ サービスは、HTTP 要求を受け付けるネットワーク ソケットにバインドしたり、このソケットでリッスンしたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-107">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="3e5ff-108">この機能要件のため、データ サービスはホスティング コンポーネントに依存します。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-108">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="3e5ff-109">データ サービス ホストは、データ サービスに代わって次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-109">The data service host performs the following tasks on behalf of the data service:</span></span>

- <span data-ttu-id="3e5ff-110">要求をリッスンし、その要求をデータ サービスにルーティングする。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-110">Listens for requests and routes these requests to the data service.</span></span>

- <span data-ttu-id="3e5ff-111">要求ごとにデータ サービスのインスタンスを作成する。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-111">Creates an instance of the data service for each request.</span></span>

- <span data-ttu-id="3e5ff-112">受信要求を処理するようデータ サービスに要求する。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-112">Requests that the data service process the incoming request.</span></span>

- <span data-ttu-id="3e5ff-113">データ サービスに代わって応答を送信する。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-113">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="3e5ff-114">データ サービスのホスティングを簡素化するため、WCF Data Services は Windows Communication Foundation (WCF) と統合するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-114">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="3e5ff-115">データ サービスでは、ASP.NET アプリケーションでデータ サービス ホストとして機能する既定の WCF 実装が提供されています。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-115">The data service provides a default WCF implementation that serves as the data service host in an ASP.NET application.</span></span> <span data-ttu-id="3e5ff-116">そのため、次のいずれかの方法でデータ サービスをホストできます。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-116">Therefore, you can host a data service in one of the following ways:</span></span>

- <span data-ttu-id="3e5ff-117">ASP.NET アプリケーション</span><span class="sxs-lookup"><span data-stu-id="3e5ff-117">In an ASP.NET application.</span></span>

- <span data-ttu-id="3e5ff-118">自己ホスト型 WCF サービスをサポートするマネージド アプリケーション</span><span class="sxs-lookup"><span data-stu-id="3e5ff-118">In a managed application that supports self-hosted WCF services.</span></span>

- <span data-ttu-id="3e5ff-119">その他のカスタム データ サービス ホスト</span><span class="sxs-lookup"><span data-stu-id="3e5ff-119">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="3e5ff-120">ASP.NET アプリケーションでのデータ サービスのホスト</span><span class="sxs-lookup"><span data-stu-id="3e5ff-120">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="3e5ff-121">Visual Studio 2015 の **[新しい項目の追加]** ダイアログを使用して ASP.NET アプリケーションにデータ サービスを定義すると、プロジェクトに 2 つの新しいファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-121">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="3e5ff-122">そのうち一方のファイル (拡張子は `.svc`) は、データ サービスのインスタンス化方法を WCF ランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-122">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="3e5ff-123">次に示すのば、[クイックスタート](quickstart-wcf-data-services.md)を完了したときに作成される Northwind サンプル データ サービスに対するこのファイルの例です。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-123">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](quickstart-wcf-data-services.md):</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="3e5ff-124">このディレクティブは、<xref:System.Data.Services.DataServiceHostFactory> クラスを使用して、名前付きのデータ サービス クラスのサービス ホストを作成するようアプリケーションに指示します。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-124">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="3e5ff-125">`.svc` ファイルの分離コード ページには、データ サービス自体の実装であるクラスが含まれます。Northwind サンプル データ サービスの場合、このクラスは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-125">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="3e5ff-126">データ サービスは WCF サービスと同様に動作するため、データ サービスは ASP.NET と統合され、WCF Web プログラミング モデルに従います。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-126">Because a data service behaves like a WCF service, the data service integrates with ASP.NET and follows the WCF Web programming model.</span></span> <span data-ttu-id="3e5ff-127">詳細については、「[WCF サービスと ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md)」および「[WCF Web HTTP プログラミング モデル](../../wcf/feature-details/wcf-web-http-programming-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-127">For more information, see [WCF Services and ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="3e5ff-128">自己ホスト型 WCF サービス</span><span class="sxs-lookup"><span data-stu-id="3e5ff-128">Self-Hosted WCF Services</span></span>

 <span data-ttu-id="3e5ff-129">WCF の実装が組み込まれている WCF Data Services では、WCF サービスとして自己ホスト型のデータ サービスがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-129">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="3e5ff-130">サービスは、コンソール アプリケーションなどの任意の .NET Framework アプリケーションで自己ホスト型とすることができます。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-130">A service can be self-hosted in any .NET Framework application, such as a console application.</span></span> <span data-ttu-id="3e5ff-131"><xref:System.Data.Services.DataServiceHost> を継承する <xref:System.ServiceModel.Web.WebServiceHost> クラスを使用して、特定のアドレスでデータ サービスをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-131">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="3e5ff-132">自己ホストを使用するとサービスの配置とトラブルシューティングが容易になるので、開発時やテスト時に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-132">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="3e5ff-133">ただし、この種類のホスティングでは、ASP.NET またはインターネット インフォメーション サービス (IIS) に備わっている高度なホスト機能や管理機能を使用できません。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-133">However, this kind of hosting does not provide the advanced hosting and management features provided by ASP.NET or by Internet Information Services (IIS).</span></span> <span data-ttu-id="3e5ff-134">詳細については、「[マネージド アプリケーションのホスト](../../wcf/feature-details/hosting-in-a-managed-application.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-134">For more information, see [Hosting in a Managed Application](../../wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="3e5ff-135">カスタム データ サービス ホストの定義</span><span class="sxs-lookup"><span data-stu-id="3e5ff-135">Defining a Custom Data Service Host</span></span>

 <span data-ttu-id="3e5ff-136">WCF ホストの実装の制限が厳格すぎる場合、データ サービスのカスタム ホストを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-136">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="3e5ff-137"><xref:System.Data.Services.IDataServiceHost> インターフェイスを実装する任意のクラスをデータ サービスのネットワーク ホストとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-137">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="3e5ff-138">カスタム ホストは、<xref:System.Data.Services.IDataServiceHost> インターフェイスを実装し、データ サービス ホストの次の基本的な役割を果たすことができるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-138">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

- <span data-ttu-id="3e5ff-139">データ サービスにサービス ルート パスを提供する。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-139">Provide the data service with the service root path.</span></span>

- <span data-ttu-id="3e5ff-140">適切な <xref:System.Data.Services.IDataServiceHost> メンバーの実装に対する要求ヘッダーおよび応答ヘッダーの情報を処理する。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-140">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

- <span data-ttu-id="3e5ff-141">データ サービスで発生する例外を処理する。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-141">Handle exceptions raised by the data service.</span></span>

- <span data-ttu-id="3e5ff-142">クエリ文字列のパラメーターを検証する。</span><span class="sxs-lookup"><span data-stu-id="3e5ff-142">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e5ff-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e5ff-143">See also</span></span>

- [<span data-ttu-id="3e5ff-144">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="3e5ff-144">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="3e5ff-145">サービスとしてのデータの公開</span><span class="sxs-lookup"><span data-stu-id="3e5ff-145">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="3e5ff-146">データ サービスの構成</span><span class="sxs-lookup"><span data-stu-id="3e5ff-146">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
