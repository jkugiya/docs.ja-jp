---
description: '詳細情報: Entity Framework 用 SqlClient'
title: Entity Framework 用 SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: eba5602c13f66d1ee4404bbc27035304e34c1cd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673129"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="b2005-103">Entity Framework 用 SqlClient</span><span class="sxs-lookup"><span data-stu-id="b2005-103">SqlClient for the Entity Framework</span></span>

<span data-ttu-id="b2005-104">このセクションでは、.NET Framework Data Provider for SQL Server (SqlClient) について説明します。これによって、Microsoft SQL Server 上で Entity Framework が機能できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b2005-104">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="b2005-105">Provider スキーマ属性</span><span class="sxs-lookup"><span data-stu-id="b2005-105">Provider Schema Attribute</span></span>  

 <span data-ttu-id="b2005-106">`Provider` は、ストア スキーマ定義言語 (SSDL) の `Schema` 要素の属性です。</span><span class="sxs-lookup"><span data-stu-id="b2005-106">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="b2005-107">SqlClient を使用するには、文字列 "System.Data.SqlClient" を `Provider` 要素の `Schema` 属性に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b2005-107">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="b2005-108">ProviderManifestToken スキーマ属性</span><span class="sxs-lookup"><span data-stu-id="b2005-108">ProviderManifestToken Schema Attribute</span></span>  

 <span data-ttu-id="b2005-109">`ProviderManifestToken` は、SSDL の`Schema` 要素の必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="b2005-109">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="b2005-110">このトークンは、オフライン シナリオ用のプロバイダー マニフェストを読み込むために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b2005-110">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="b2005-111">`ProviderManifestToken` 属性の詳細については、「[Schema 要素 (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2005-111">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="b2005-112">SqlClient は、SQL Server の各バージョンのデータ プロバイダーとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="b2005-112">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="b2005-113">これらのバージョンでは機能が異なります。</span><span class="sxs-lookup"><span data-stu-id="b2005-113">These versions have different capabilities.</span></span> <span data-ttu-id="b2005-114">たとえば、SQL Server 2000 では、SQL Server 2005 で導入された `varchar(max)` 型および `nvarchar(max)` 型はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="b2005-114">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="b2005-115">SqlClient は、SQL Server の各バージョンに対応する次のプロバイダー マニフェスト トークンを生成し、受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b2005-115">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="b2005-116">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="b2005-116">SQL Server 2000</span></span>|<span data-ttu-id="b2005-117">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="b2005-117">SQL Server 2005</span></span>|<span data-ttu-id="b2005-118">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="b2005-118">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="b2005-119">2000</span><span class="sxs-lookup"><span data-stu-id="b2005-119">2000</span></span>|<span data-ttu-id="b2005-120">2005</span><span class="sxs-lookup"><span data-stu-id="b2005-120">2005</span></span>|<span data-ttu-id="b2005-121">2008</span><span class="sxs-lookup"><span data-stu-id="b2005-121">2008</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b2005-122">Visual Studio 2010 以降では、[ADO.NET Entity Data Model ツール](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))によって SQL Server 2000 がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="b2005-122">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="b2005-123">プロバイダーの名前空間名</span><span class="sxs-lookup"><span data-stu-id="b2005-123">Provider Namespace Name</span></span>  

 <span data-ttu-id="b2005-124">すべてのプロバイダーで名前空間を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2005-124">All providers must specify a namespace.</span></span> <span data-ttu-id="b2005-125">このプロパティによって、型や関数など、プロバイダーが特定のコンストラクターに使用するプレフィックスを Entity Framework に通知できます。</span><span class="sxs-lookup"><span data-stu-id="b2005-125">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="b2005-126">SqlClient プロバイダー マニフェストの名前空間は `SqlServer` です。</span><span class="sxs-lookup"><span data-stu-id="b2005-126">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="b2005-127">名前空間の詳細については、「[名前空間](./language-reference/namespaces-entity-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2005-127">For more information about namespaces, see [Namespaces](./language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="b2005-128">型</span><span class="sxs-lookup"><span data-stu-id="b2005-128">Types</span></span>  

 <span data-ttu-id="b2005-129">Entity Framework 用の SqlClient プロバイダーは、概念モデルの型と SQL Server 型の間のマッピング情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b2005-129">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="b2005-130">詳細については、「[Entity Framework 用 SqlClient の型](sqlclient-for-ef-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2005-130">For more information, see [SqlClient for Entity FrameworkTypes](sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="b2005-131">関数</span><span class="sxs-lookup"><span data-stu-id="b2005-131">Functions</span></span>  

 <span data-ttu-id="b2005-132">Entity Framework 用の SqlClient プロバイダーは、プロバイダーがサポートする関数の一覧を定義します。</span><span class="sxs-lookup"><span data-stu-id="b2005-132">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="b2005-133">サポートされている関数の一覧については、「[Entity Framework 用 SqlClient 関数](sqlclient-for-ef-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2005-133">For a list of the supported functions, see [SqlClient for Entity Framework Functions](sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2005-134">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b2005-134">In This Section</span></span>  

 [<span data-ttu-id="b2005-135">Entity Framework 用 SqlClient 関数</span><span class="sxs-lookup"><span data-stu-id="b2005-135">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="b2005-136">Entity Framework 型用 SqlClient</span><span class="sxs-lookup"><span data-stu-id="b2005-136">SqlClient for Entity FrameworkTypes</span></span>](sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="b2005-137">Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) の既知の問題</span><span class="sxs-lookup"><span data-stu-id="b2005-137">Known Issues in SqlClient for Entity Framework</span></span>](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="b2005-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2005-138">See also</span></span>

- [<span data-ttu-id="b2005-139">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="b2005-139">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="b2005-140">言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="b2005-140">Language Reference</span></span>](./language-reference/index.md)
- [<span data-ttu-id="b2005-141">Entity Framework 用の SqlClient プロバイダーの既知の問題</span><span class="sxs-lookup"><span data-stu-id="b2005-141">Known Issues in SqlClient Provider for Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
