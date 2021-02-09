---
description: '詳細情報: WCF Data Services の定義'
title: WCF Data Services の定義
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: 43a4887226b03e80c4a966a118f210fe8a28000d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766089"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="8e434-103">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="8e434-103">Defining WCF Data Services</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="8e434-104">このセクションでは、WCF Data Services を作成し、Open Data Protocol (OData) フィードとしてデータを公開するように構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e434-104">This section describes how to create and configure WCF Data Services to expose data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="8e434-105">データ サービスの基本的な作成手順については、「[サービスとしてのデータの公開](exposing-your-data-as-a-service-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e434-105">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8e434-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8e434-106">In This Section</span></span>

 [<span data-ttu-id="8e434-107">データ サービスの構成</span><span class="sxs-lookup"><span data-stu-id="8e434-107">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="8e434-108">WCF Data Services によって提供されるデータ サービス構成オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8e434-108">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="8e434-109">Data Services プロバイダー</span><span class="sxs-lookup"><span data-stu-id="8e434-109">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)

 <span data-ttu-id="8e434-110">データ サービスとしてデータを公開するプロバイダー モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8e434-110">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="8e434-111">サービス操作</span><span class="sxs-lookup"><span data-stu-id="8e434-111">Service Operations</span></span>](service-operations-wcf-data-services.md)

 <span data-ttu-id="8e434-112">サーバー上でメソッドを公開するサービス操作を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e434-112">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="8e434-113">フィードのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="8e434-113">Feed Customization</span></span>](feed-customization-wcf-data-services.md)

 <span data-ttu-id="8e434-114">データ サービス プロバイダーおよびデータ フィードの要素によって定義されるデータ モデルのエンティティ間のマッピングを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e434-114">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="8e434-115">インターセプター</span><span class="sxs-lookup"><span data-stu-id="8e434-115">Interceptors</span></span>](interceptors-wcf-data-services.md)

 <span data-ttu-id="8e434-116">インターセプター メソッドを定義してデータ サービスへの要求に対してカスタム ビジネス ロジックを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e434-116">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="8e434-117">WCF Data Services の開発と配置</span><span class="sxs-lookup"><span data-stu-id="8e434-117">Developing and Deploying WCF Data Services</span></span>](developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="8e434-118">Visual Studio を使用してデータ サービスを開発および配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e434-118">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="8e434-119">WCF Data Services のセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="8e434-119">Securing WCF Data Services</span></span>](securing-wcf-data-services.md)

 <span data-ttu-id="8e434-120">データ サービスの認証と承認およびセキュリティに関するその他の考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e434-120">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="8e434-121">データ サービスのホスティング</span><span class="sxs-lookup"><span data-stu-id="8e434-121">Hosting the Data Service</span></span>](hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="8e434-122">データ サービスのホストを選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e434-122">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="8e434-123">データ サービスのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="8e434-123">Data Service Versioning</span></span>](data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="8e434-124">異なるバージョンの OData を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e434-124">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="8e434-125">WCF Data Services プロトコル実装の詳細</span><span class="sxs-lookup"><span data-stu-id="8e434-125">WCF Data Services Protocol Implementation Details</span></span>](wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="8e434-126">WCF Data Services で現在実装されていない OData プロトコルのオプション機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e434-126">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e434-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e434-127">See also</span></span>

- [<span data-ttu-id="8e434-128">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8e434-128">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="8e434-129">データ サービス リソースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="8e434-129">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="8e434-130">はじめに</span><span class="sxs-lookup"><span data-stu-id="8e434-130">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
