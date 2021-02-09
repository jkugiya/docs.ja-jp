---
description: '詳細情報: カスタム データ サービス プロバイダー (WCF Data Services)'
title: カスタム データ サービス プロバイダー (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: df0cafae46cfdbd71a96341686a9200f032a9938
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766154"
---
# <a name="custom-data-service-providers-wcf-data-services"></a><span data-ttu-id="55cfa-103">カスタム データ サービス プロバイダー (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="55cfa-103">Custom Data Service Providers (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="55cfa-104">WCF Data Services には、遅延バインディング データ型に基づいてデータ モデルを定義できるプロバイダーのセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55cfa-104">WCF Data Services includes a set of providers that enables you to define a data model based on late-bound data types.</span></span>  
  
|<span data-ttu-id="55cfa-105">プロバイダー</span><span class="sxs-lookup"><span data-stu-id="55cfa-105">Provider</span></span>|<span data-ttu-id="55cfa-106">説明</span><span class="sxs-lookup"><span data-stu-id="55cfa-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="55cfa-107">メタデータ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="55cfa-107">Metadata provider</span></span>|<span data-ttu-id="55cfa-108">これは、<xref:System.Data.Services.Providers.IDataServiceMetadataProvider> インターフェイスを実装することによって実行時にカスタム データ モデルを定義できるコア カスタム データ サービス プロバイダーです。</span><span class="sxs-lookup"><span data-stu-id="55cfa-108">This is the core custom data service provider that enables you to define a custom data model at runtime by implementing the <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.</span></span>|  
|<span data-ttu-id="55cfa-109">クエリ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="55cfa-109">Query provider</span></span>|<span data-ttu-id="55cfa-110">このプロバイダーを使用すると、<xref:System.Data.Services.Providers.IDataServiceMetadataProvider> インターフェイスを使用して定義されたカスタム データ モデルに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="55cfa-110">This provider enables you to execute queries against a custom data model that is defined by using the <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.</span></span> <span data-ttu-id="55cfa-111">クエリ プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceQueryProvider> インターフェイスを実装することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="55cfa-111">The query provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceQueryProvider> interface.</span></span>|  
|<span data-ttu-id="55cfa-112">更新プロバイダー</span><span class="sxs-lookup"><span data-stu-id="55cfa-112">Update provider</span></span>|<span data-ttu-id="55cfa-113">このプロバイダーを使用すると、カスタム データ サービス プロバイダー内で公開されている型を更新してコンカレンシーを管理できます。</span><span class="sxs-lookup"><span data-stu-id="55cfa-113">This provider enables you to make updates to types that are exposed in a custom data service provider and to manage concurrency.</span></span> <span data-ttu-id="55cfa-114">更新プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceUpdateProvider> インターフェイスを実装することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="55cfa-114">An update provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> interface</span></span>|  
|<span data-ttu-id="55cfa-115">ページング プロバイダー</span><span class="sxs-lookup"><span data-stu-id="55cfa-115">Paging provider</span></span>|<span data-ttu-id="55cfa-116">このプロバイダーは、サーバー ドリブン ページング サポートを有効にするためにカスタム データ サービス プロバイダーと一緒に使用します。</span><span class="sxs-lookup"><span data-stu-id="55cfa-116">This provider is used with the custom data service provider to enable server-driven paging support.</span></span> <span data-ttu-id="55cfa-117">カスタム データ サービスのページング プロバイダーは、<xref:System.Data.Services.Providers.IDataServicePagingProvider> インターフェイスを実装することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="55cfa-117">A paging provider for a custom data service is created by implementing the <xref:System.Data.Services.Providers.IDataServicePagingProvider> interface.</span></span>|  
|<span data-ttu-id="55cfa-118">ストリーミング プロバイダー</span><span class="sxs-lookup"><span data-stu-id="55cfa-118">Streaming provider</span></span>|<span data-ttu-id="55cfa-119">このプロバイダーを使用すると、ストリームとしてバイナリ ラージ オブジェクト データ型を公開できます。</span><span class="sxs-lookup"><span data-stu-id="55cfa-119">This provider enables you to expose binary large object data types as a stream.</span></span> <span data-ttu-id="55cfa-120">ストリーミング プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceStreamProvider> インターフェイスを実装することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="55cfa-120">A streaming provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interface.</span></span> <span data-ttu-id="55cfa-121">ストリーミング プロバイダーは、Entity Framework プロバイダーおよびリフレクション データ ソース プロバイダーと共に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="55cfa-121">The streaming provider can also be used with Entity Framework and reflection data source providers.</span></span> <span data-ttu-id="55cfa-122">詳細については、「[ストリーミング プロバイダー](streaming-provider-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55cfa-122">For more information, see [Streaming Provider](streaming-provider-wcf-data-services.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55cfa-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="55cfa-123">See also</span></span>

- [<span data-ttu-id="55cfa-124">Data Services プロバイダー</span><span class="sxs-lookup"><span data-stu-id="55cfa-124">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="55cfa-125">Entity Framework プロバイダー</span><span class="sxs-lookup"><span data-stu-id="55cfa-125">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)
- [<span data-ttu-id="55cfa-126">リフレクション プロバイダー</span><span class="sxs-lookup"><span data-stu-id="55cfa-126">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
