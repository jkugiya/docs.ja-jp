---
description: '詳細情報: サービスとしてデータを公開する (WCF Data Services)'
title: サービスとしてのデータの公開 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 496cf18b264672814295916467e1bff93feebdde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765972"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a><span data-ttu-id="aeb19-103">サービスとしてデータを公開する (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="aeb19-103">Expose Your Data as a Service (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="aeb19-104">WCF Data Services を Visual Studio に統合すると、サービスを簡単に定義し、Open Data Protocol (OData) フィードとしてデータを公開できます。</span><span class="sxs-lookup"><span data-stu-id="aeb19-104">WCF Data Services integrates with Visual Studio to enable you to more easily define services to expose your data as Open Data Protocol (OData) feeds.</span></span> <span data-ttu-id="aeb19-105">OData フィードを公開するデータ サービスを作成するには、次のような基本的な手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="aeb19-105">Creating a data service that exposes an OData feed involves the following basic steps:</span></span>

1. <span data-ttu-id="aeb19-106">**データ モデルを定義します。**</span><span class="sxs-lookup"><span data-stu-id="aeb19-106">**Define the data model.**</span></span> <span data-ttu-id="aeb19-107">WCF Data Services では、[ADO.NET Entity Framework](../adonet/ef/index.md) に基づくデータ モデルがネイティブでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="aeb19-107">WCF Data Services natively supports data models that are based on the [ADO.NET Entity Framework](../adonet/ef/index.md).</span></span> <span data-ttu-id="aeb19-108">詳細については、[ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する](create-a-data-service-using-an-adonet-ef-data-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeb19-108">For more information, see [How to: Create a Data Service Using an ADO.NET Entity Framework Data Source](create-a-data-service-using-an-adonet-ef-data-wcf.md).</span></span>

     <span data-ttu-id="aeb19-109">WCF Data Services では、<xref:System.Linq.IQueryable%601> インターフェイスのインスタンスを返す共通言語ランタイム (CLR) オブジェクトに基づくデータ モデルもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="aeb19-109">WCF Data Services also supports data models that are based on common language runtime (CLR) objects that return an instance of the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="aeb19-110">そのため、.NET Framework のリスト、配列、およびコレクションに基づいてデータ サービスを配置できます。</span><span class="sxs-lookup"><span data-stu-id="aeb19-110">This enables you to deploy data services that are based on lists, arrays, and collections in the .NET Framework.</span></span> <span data-ttu-id="aeb19-111">これらのデータ構造での作成、更新、および削除操作を有効にするには、<xref:System.Data.Services.IUpdatable> インターフェイスも実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aeb19-111">To enable create, update, and delete operations over these data structures, you must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="aeb19-112">詳細については、[リフレクション プロバイダーを使用してデータ サービスを作成する](create-a-data-service-using-rp-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeb19-112">For more information, see [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md).</span></span>

     <span data-ttu-id="aeb19-113">より高度なシナリオの場合、WCF Data Services には、遅延バインディング データ型に基づいてデータ モデルを定義できるプロバイダーのセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aeb19-113">For more advanced scenarios, WCF Data Services includes a set of providers that enable you to define a data model based on late-bound data types.</span></span> <span data-ttu-id="aeb19-114">詳しくは、「[カスタム データ サービス プロバイダー](custom-data-service-providers-wcf-data-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="aeb19-114">For more information, see [Custom Data Service Providers](custom-data-service-providers-wcf-data-services.md).</span></span>

2. <span data-ttu-id="aeb19-115">**データ サービスを作成します。**</span><span class="sxs-lookup"><span data-stu-id="aeb19-115">**Create the data service.**</span></span> <span data-ttu-id="aeb19-116">最も基本的なデータ サービスでは、 <xref:System.Data.Services.DataService%601> クラスを継承するクラスを `T` 型 (エンティティ コンテナーの名前空間修飾名) と一緒に公開します。</span><span class="sxs-lookup"><span data-stu-id="aeb19-116">The most basic data service exposes a class that inherits from the <xref:System.Data.Services.DataService%601> class, with a type `T` that is the namespace-qualified name of the entity container.</span></span> <span data-ttu-id="aeb19-117">詳細については、「 [Defining WCF Data Services](defining-wcf-data-services.md)の開発と配置について説明します。</span><span class="sxs-lookup"><span data-stu-id="aeb19-117">For more information, see [Defining WCF Data Services](defining-wcf-data-services.md).</span></span>

3. <span data-ttu-id="aeb19-118">**データ サービスを構成します。**</span><span class="sxs-lookup"><span data-stu-id="aeb19-118">**Configure the data service.**</span></span> <span data-ttu-id="aeb19-119">既定では、WCF Data Services では、エンティティ コンテナーによって公開されているリソースへのアクセスは無効になります。</span><span class="sxs-lookup"><span data-stu-id="aeb19-119">By default, WCF Data Services disables access to resources that are exposed by an entity container.</span></span> <span data-ttu-id="aeb19-120"><xref:System.Data.Services.DataServiceConfiguration> インターフェイスを使用すると、リソースとサービス操作へのアクセスの構成、サポートされる OData のバージョンの指定、およびサービス全体のその他の動作 (バッチ動作や 1 つの応答で返すことができるエンティティの最大数など) を定義できます。</span><span class="sxs-lookup"><span data-stu-id="aeb19-120">The <xref:System.Data.Services.DataServiceConfiguration> interface enables you to configure access to resources and service operations, specify the supported version of OData, and to define other service-wide behaviors, such as batching behaviors or the maximum number of entities that can be returned in a single response.</span></span> <span data-ttu-id="aeb19-121">詳細については、「[データ サービスの構成](configuring-the-data-service-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeb19-121">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>

<span data-ttu-id="aeb19-122">Northwind サンプル データベースに基づく単純なデータ サービスを作成する方法の例については、「[クイックスタート](quickstart-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeb19-122">For an example of how to create a simple data service that is based on the Northwind sample database, see [Quickstart](quickstart-wcf-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aeb19-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="aeb19-123">See also</span></span>

- [<span data-ttu-id="aeb19-124">はじめに</span><span class="sxs-lookup"><span data-stu-id="aeb19-124">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="aeb19-125">概要</span><span class="sxs-lookup"><span data-stu-id="aeb19-125">Overview</span></span>](wcf-data-services-overview.md)
