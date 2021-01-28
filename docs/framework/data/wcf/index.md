---
title: WCF Data Services 4.5
description: REST セマンティクスを使用してデータを公開および使用するためのサービスをサポートする .NET Framework コンポーネント、WCF Data Services について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 2d3da2ca9cd958fc70d3b91362dde71d68dc9d8a
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898758"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="d1067-103">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="d1067-103">WCF Data Services 4.5</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

## <a name="overview"></a><span data-ttu-id="d1067-104">概要</span><span class="sxs-lookup"><span data-stu-id="d1067-104">Overview</span></span>

<span data-ttu-id="d1067-105">WCF Data Services (従来の "ADO.NET Data Services") は .NET Framework のコンポーネントです。これを使用すると、[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) のセマンティクスを使用し、Open Data Protocol (OData) を使用して Web またはイントラネット上のデータを公開および使用するサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1067-105">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="d1067-106">OData は、URI でアドレス指定できるリソースとしてデータを公開します。</span><span class="sxs-lookup"><span data-stu-id="d1067-106">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="d1067-107">標準的な HTTP 動詞である GET、PUT、POST、および DELETE を使用してデータにアクセスし、変更できます。</span><span class="sxs-lookup"><span data-stu-id="d1067-107">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="d1067-108">OData では、[Entity Data Model](../adonet/entity-data-model.md) のエンティティとリレーションシップの規則を使用して、アソシエーションで関連付けられた一連のエンティティとしてリソースを公開します。</span><span class="sxs-lookup"><span data-stu-id="d1067-108">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="d1067-109">WCF Data Services は、OData プロトコルを使用してリソースのアドレス指定および更新を行います。</span><span class="sxs-lookup"><span data-stu-id="d1067-109">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="d1067-110">これにより、OData をサポートする任意のクライアントからサービスにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d1067-110">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="d1067-111">OData を使用すると、XML としてデータを交換および更新するための標準のセットである Atom と、AJAX アプリケーションで広範に使用されるテキスト ベースのデータ交換形式である JavaScript Object Notation (JSON) という広く知られている転送形式を使用して、データをリソースに要求または書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="d1067-111">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="d1067-112">WCF Data Services では、さまざまなソースからのデータを OData フィードとして公開できます。</span><span class="sxs-lookup"><span data-stu-id="d1067-112">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="d1067-113">Visual Studio のツールを使用すると、ADO.NET Entity Framework データ モデルを使用して OData ベースのサービスを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1067-113">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="d1067-114">OData フィードは、共通言語ランタイム (CLR) クラスに基づいて作成できます。また、遅延バインディング データまたは型指定されていないデータに基づいて作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1067-114">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="d1067-115">WCF Data Services には、クライアント ライブラリのセット (一般的な .NET Framework クライアント アプリケーション用と Silverlight ベースのアプリケーション用) も含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1067-115">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="d1067-116">これらのクライアント ライブラリは、.NET Framework や Silverlight などの環境から OData フィードにアクセスするときにオブジェクト ベースのプログラミング モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="d1067-116">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="d1067-117">開始すべき場所</span><span class="sxs-lookup"><span data-stu-id="d1067-117">Where Should I Start?</span></span>

<span data-ttu-id="d1067-118">各自の興味に応じて、次のトピックのいずれかから WCF Data Services の使用を開始することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="d1067-118">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="d1067-119">すぐに使用を開始する…</span><span class="sxs-lookup"><span data-stu-id="d1067-119">I want to jump right in...</span></span>

- [<span data-ttu-id="d1067-120">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="d1067-120">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="d1067-121">はじめに</span><span class="sxs-lookup"><span data-stu-id="d1067-121">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="d1067-122">コードを見たい...</span><span class="sxs-lookup"><span data-stu-id="d1067-122">Just show me some code...</span></span>

- [<span data-ttu-id="d1067-123">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="d1067-123">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="d1067-124">方法: データ サービス クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="d1067-124">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="d1067-125">方法: Windows Presentation Foundation 要素にデータをバインドする</span><span class="sxs-lookup"><span data-stu-id="d1067-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="d1067-126">OData について詳しく知りたい...</span><span class="sxs-lookup"><span data-stu-id="d1067-126">I want to know more about OData...</span></span>

- [<span data-ttu-id="d1067-127">ホワイト ペーパー: OData の概要</span><span class="sxs-lookup"><span data-stu-id="d1067-127">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="d1067-128">Open Data Protocol Web サイト</span><span class="sxs-lookup"><span data-stu-id="d1067-128">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="d1067-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="d1067-129">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="d1067-130">エンド ツー エンドのサンプルを見たい...</span><span class="sxs-lookup"><span data-stu-id="d1067-130">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="d1067-131">[WCF Data Services クイックスタート](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="d1067-131">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="d1067-132">OData SDK - サンプル コード</span><span class="sxs-lookup"><span data-stu-id="d1067-132">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="d1067-133">Visual Studio との統合について知りたい</span><span class="sxs-lookup"><span data-stu-id="d1067-133">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="d1067-134">データ サービス クライアント ライブラリの生成</span><span class="sxs-lookup"><span data-stu-id="d1067-134">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="d1067-135">データ サービスの作成</span><span class="sxs-lookup"><span data-stu-id="d1067-135">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="d1067-136">Entity Framework プロバイダー</span><span class="sxs-lookup"><span data-stu-id="d1067-136">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="d1067-137">何に使用できるかを知りたい</span><span class="sxs-lookup"><span data-stu-id="d1067-137">What can I do with it?</span></span>

- [<span data-ttu-id="d1067-138">概要</span><span class="sxs-lookup"><span data-stu-id="d1067-138">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="d1067-139">アプリケーション シナリオ</span><span class="sxs-lookup"><span data-stu-id="d1067-139">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="d1067-140">LINQ を使用したい...</span><span class="sxs-lookup"><span data-stu-id="d1067-140">I want to use LINQ...</span></span>

- [<span data-ttu-id="d1067-141">データ サービスに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="d1067-141">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="d1067-142">LINQ に関する留意点</span><span class="sxs-lookup"><span data-stu-id="d1067-142">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="d1067-143">方法: データ サービス クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="d1067-143">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="d1067-144">より詳しい情報が欲しい...</span><span class="sxs-lookup"><span data-stu-id="d1067-144">I still need some more information...</span></span>

- [<span data-ttu-id="d1067-145">WCF Data Services チームのブログ</span><span class="sxs-lookup"><span data-stu-id="d1067-145">WCF Data Services Team Blog</span></span>](/archive/blogs/astoriateam/)

- [<span data-ttu-id="d1067-146">リソース</span><span class="sxs-lookup"><span data-stu-id="d1067-146">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="d1067-147">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d1067-147">In This Section</span></span>

[<span data-ttu-id="d1067-148">概要</span><span class="sxs-lookup"><span data-stu-id="d1067-148">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="d1067-149">WCF Data Services で使用可能な機能の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1067-149">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="d1067-150">[WCF Data Services 5.0 の新機能](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="d1067-150">[What's New in WCF Data Services 5.0](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="d1067-151">WCF Data Services の新機能と、OData の新機能のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d1067-151">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="d1067-152">はじめに</span><span class="sxs-lookup"><span data-stu-id="d1067-152">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="d1067-153">WCF Data Services を使用して OData フィードを公開および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1067-153">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="d1067-154">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="d1067-154">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="d1067-155">OData フィードを公開するデータ サービスを作成および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1067-155">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="d1067-156">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="d1067-156">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="d1067-157">クライアント ライブラリを使用して .NET Framework クライアント アプリケーションから OData フィードを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1067-157">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1067-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1067-158">See also</span></span>

- [<span data-ttu-id="d1067-159">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="d1067-159">Representational State Transfer (REST)</span></span>](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
