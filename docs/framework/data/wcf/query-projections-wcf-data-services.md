---
description: '詳細情報: クエリ射影 (WCF Data Services)'
title: クエリ射影 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
ms.openlocfilehash: 35427a4bc74691f366711c30cfa7af23de1caa35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794963"
---
# <a name="query-projections-wcf-data-services"></a><span data-ttu-id="a49b6-103">クエリ射影 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="a49b6-103">Query Projections (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="a49b6-104">射影は Open Data Protocol (OData) の機能の 1 つであり、エンティティの特定のプロパティのみが応答で返されるように指定することで、クエリによって返されるフィードのデータの量を減らします。</span><span class="sxs-lookup"><span data-stu-id="a49b6-104">Projection provides a mechanism in the Open Data Protocol (OData) to reduce the amount of data in the feed returned by a query by specifying that only certain properties of an entity are returned in the response.</span></span> <span data-ttu-id="a49b6-105">詳細については、セクション「4.8.</span><span class="sxs-lookup"><span data-stu-id="a49b6-105">For more information, see section 4.8.</span></span> <span data-ttu-id="a49b6-106">システム クエリ オプションの選択 ($select)」 (「[URI 規則 (OData バージョン 2.0)](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a49b6-106">Select System Query Option ($select) in [URI Conventions (OData Version 2.0)](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).</span></span>

<span data-ttu-id="a49b6-107">このトピックでは、クエリ射影を定義する方法、エンティティ型、エンティティ型以外の要件、射影された結果に対する更新、射影された型の作成について説明すると共に、射影に関する注意事項をリストします。</span><span class="sxs-lookup"><span data-stu-id="a49b6-107">This topic describes how to define a query projection, what the requirements are for entity and non-entity types, making updates to projected results, creating projected types, and lists some projection considerations.</span></span>

## <a name="defining-a-query-projection"></a><span data-ttu-id="a49b6-108">クエリ射影の定義</span><span class="sxs-lookup"><span data-stu-id="a49b6-108">Defining a Query Projection</span></span>

<span data-ttu-id="a49b6-109">クエリに射影句を追加するには、URI で `$select` クエリ オプションを使用するか、LINQ クエリで [select](../../../csharp/language-reference/keywords/select-clause.md) 句 (Visual Basic の場合は [Select](../../../visual-basic/language-reference/queries/select-clause.md)) を使用します。</span><span class="sxs-lookup"><span data-stu-id="a49b6-109">You can add a projection clause to a query either by using the `$select` query option in a URI or by using the [select](../../../csharp/language-reference/keywords/select-clause.md) clause ([Select](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) in a LINQ query.</span></span> <span data-ttu-id="a49b6-110">返されたエンティティ データは、クライアント上のエンティティ型またはエンティティ型以外に射影できます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-110">Returned entity data can be projected into either entity types or non-entity types on the client.</span></span> <span data-ttu-id="a49b6-111">このトピックでは、LINQ クエリで `select` 句を使用する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-111">Examples in this topic demonstrate how to use the `select` clause in a LINQ query.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a49b6-112">射影された型に対して行った更新を保存すると、データ サービスでデータの損失が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a49b6-112">Data loss might occur in the data service when you save updates that were made to projected types.</span></span> <span data-ttu-id="a49b6-113">詳細については、「[射影時の注意事項](#considerations)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a49b6-113">For more information, see [Projection Considerations](#considerations).</span></span>

## <a name="requirements-for-entity-and-non-entity-types"></a><span data-ttu-id="a49b6-114">エンティティ型およびエンティティ型以外の要件</span><span class="sxs-lookup"><span data-stu-id="a49b6-114">Requirements for Entity and Non-Entity Types</span></span>

<span data-ttu-id="a49b6-115">エンティティ型には、エンティティ キーを構成する 1 つ以上の Identity プロパティが必要です。</span><span class="sxs-lookup"><span data-stu-id="a49b6-115">Entity types must have one or more identity properties that make up the entity key.</span></span> <span data-ttu-id="a49b6-116">エンティティ型は、次のいずれかの方法によりクライアントで定義されます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-116">Entity types are defined on clients in one of the following ways:</span></span>

- <span data-ttu-id="a49b6-117"><xref:System.Data.Services.Common.DataServiceKeyAttribute> または <xref:System.Data.Services.Common.DataServiceEntityAttribute> を型に適用する。</span><span class="sxs-lookup"><span data-stu-id="a49b6-117">By applying the <xref:System.Data.Services.Common.DataServiceKeyAttribute> or <xref:System.Data.Services.Common.DataServiceEntityAttribute> to the type.</span></span>

- <span data-ttu-id="a49b6-118">型に `ID` という名前のプロパティがある場合。</span><span class="sxs-lookup"><span data-stu-id="a49b6-118">When the type has a property named `ID`.</span></span>

- <span data-ttu-id="a49b6-119">型に *type*`ID` という名前のプロパティがある場合 (*type* は型の名前)。</span><span class="sxs-lookup"><span data-stu-id="a49b6-119">When the type has a property named *type*`ID`, where *type* is the name of the type.</span></span>

<span data-ttu-id="a49b6-120">既定では、クライアントで定義された型にクエリ結果を射影した場合、射影で要求されたプロパティがクライアント型に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a49b6-120">By default, when you project query results into a type defined at the client, the properties requested in the projection must exist in the client type.</span></span> <span data-ttu-id="a49b6-121">ただし、`true` の <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> プロパテに <xref:System.Data.Services.Client.DataServiceContext> という値を指定した場合、射影で指定されたプロパティがクライアント型に含まれる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a49b6-121">However, when you specify a value of `true` for the <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> property of the <xref:System.Data.Services.Client.DataServiceContext>, properties specified in the projection are not required to occur in the client type.</span></span>

### <a name="making-updates-to-projected-results"></a><span data-ttu-id="a49b6-122">射影された結果に対する更新</span><span class="sxs-lookup"><span data-stu-id="a49b6-122">Making Updates to Projected Results</span></span>

<span data-ttu-id="a49b6-123">クエリ結果をクライアント上のエンティティ型に射影する場合、<xref:System.Data.Services.Client.DataServiceContext> はそれらのオブジェクトを追跡し、<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> メソッドが呼び出されるとデータ サービスに更新内容が送り返されます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-123">When you project query results into entity types on the client, the <xref:System.Data.Services.Client.DataServiceContext> can track those objects with updates to be sent back to the data service when the <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> method is called.</span></span> <span data-ttu-id="a49b6-124">ただし、クライアント上のエンティティ型以外に射影されたデータの更新内容は、データ サービスに送り返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="a49b6-124">However, updates that are made to data projected into non-entity types on the client cannot be sent back to the data service.</span></span> <span data-ttu-id="a49b6-125">これは、エンティティ インスタンスを識別するキーがなければ、データ サービスはデータ ソース内の正しいエンティティを更新できないためです。</span><span class="sxs-lookup"><span data-stu-id="a49b6-125">This is because without a key to identify the entity instance, the data service cannot update the correct entity in the data source.</span></span> <span data-ttu-id="a49b6-126">エンティティ型以外は <xref:System.Data.Services.Client.DataServiceContext> にはアタッチされません。</span><span class="sxs-lookup"><span data-stu-id="a49b6-126">Non-entity types are not attached to the <xref:System.Data.Services.Client.DataServiceContext>.</span></span>

<span data-ttu-id="a49b6-127">データ サービスで定義されたエンティティ型の 1 つ以上のプロパティが、エンティティの射影先のクライアント型に含まれない場合、新しいエンティティの挿入には、これらの欠損しているプロパティは含まれません。</span><span class="sxs-lookup"><span data-stu-id="a49b6-127">When one or more properties of an entity type defined in the data service do not occur in the client type into which the entity is projected, inserts of new entities will not contain these missing properties.</span></span> <span data-ttu-id="a49b6-128">この場合、欠損しているこれらのプロパティは既存のエンティティに対する更新 **にも** 含まれません。</span><span class="sxs-lookup"><span data-stu-id="a49b6-128">In this case, updates that are made to existing entities will **also** not include these missing properties.</span></span> <span data-ttu-id="a49b6-129">そのようなプロパティに対する値が存在する場合、データ ソースの定義に従い、更新ではその値がそのプロパティの既定値としてリセットされます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-129">When a value exists for such a property, the update resets it to the default value for the property, as defined in the data source.</span></span>

### <a name="creating-projected-types"></a><span data-ttu-id="a49b6-130">射影型の作成</span><span class="sxs-lookup"><span data-stu-id="a49b6-130">Creating Projected Types</span></span>

<span data-ttu-id="a49b6-131">次の例では、`Customers` 型のアドレス関連のプロパティを、クライアントで定義されエンティティ型として属性化された新しい `CustomerAddress` 型に射影する匿名の LINQ クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="a49b6-131">The following example uses an anonymous LINQ query that projects the address-related properties of the `Customers` type into a new `CustomerAddress` type, which is defined on the client and is attributed as an entity type:</span></span>

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

<span data-ttu-id="a49b6-132">この例では、コンストラクターを呼び出す代わりに、オブジェクト初期化子パターンを使用して `CustomerAddress` 型の新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a49b6-132">In this example, the object initializer pattern is used to create a new instance of the `CustomerAddress` type instead of calling a constructor.</span></span> <span data-ttu-id="a49b6-133">コンストラクターは、エンティティ型への射影ではサポートされていませんが、エンティティ型以外および匿名型への射影では使用できます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-133">Constructors are not supported when projecting into entity types, but they can be used when projecting into non-entity and anonymous types.</span></span> <span data-ttu-id="a49b6-134">`CustomerAddress` は、エンティティ型であるため、変更を加えてデータ サービスに送り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-134">Because `CustomerAddress` is an entity type, changes can be made and sent back to the data service.</span></span>

<span data-ttu-id="a49b6-135">さらに、`Customer` 型からのデータは、匿名型ではなく `CustomerAddress` エンティティ型のインスタンスに射影されます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-135">Also, the data from the `Customer` type is projected into an instance of the `CustomerAddress` entity type instead of an anonymous type.</span></span> <span data-ttu-id="a49b6-136">匿名型への射影はサポートされていますが、匿名型はエンティティ型以外として扱われるので、データは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="a49b6-136">Projection into anonymous types is supported, but the data is read-only because anonymous types are treated as non-entity types.</span></span>

<span data-ttu-id="a49b6-137"><xref:System.Data.Services.Client.MergeOption> の <xref:System.Data.Services.Client.DataServiceContext> 設定は、クエリ射影時の ID 解決に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-137">The <xref:System.Data.Services.Client.MergeOption> settings of the <xref:System.Data.Services.Client.DataServiceContext> are used for identity resolution during query projection.</span></span> <span data-ttu-id="a49b6-138">これは、`Customer` 型のインスタンスが <xref:System.Data.Services.Client.DataServiceContext> に存在する場合、同じ ID を持つ `CustomerAddress` のインスタンスは <xref:System.Data.Services.Client.MergeOption> で設定された ID 解決ルールに従うことを意味します。</span><span class="sxs-lookup"><span data-stu-id="a49b6-138">This means that if an instance of the `Customer` type already exists in the <xref:System.Data.Services.Client.DataServiceContext>, an instance of `CustomerAddress` with the same identity will follow the identity resolution rules set by the <xref:System.Data.Services.Client.MergeOption></span></span>

<span data-ttu-id="a49b6-139">以下では、結果をエンティティ型またはエンティティ型以外に射影する場合の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="a49b6-139">The following describes the behaviors when projecting results into entity and non-entity types:</span></span>

<span data-ttu-id="a49b6-140">**初期化子を使用して新しい射影インスタンスを作成する**</span><span class="sxs-lookup"><span data-stu-id="a49b6-140">**Creating a new projected instance by using initializers**</span></span>

- <span data-ttu-id="a49b6-141">例:</span><span class="sxs-lookup"><span data-stu-id="a49b6-141">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- <span data-ttu-id="a49b6-142">エンティティ型: サポート状況</span><span class="sxs-lookup"><span data-stu-id="a49b6-142">Entity type: Supported</span></span>

- <span data-ttu-id="a49b6-143">エンティティ型以外: サポート状況</span><span class="sxs-lookup"><span data-stu-id="a49b6-143">Non-entity type: Supported</span></span>

<span data-ttu-id="a49b6-144">**コンストラクターを使用して新しい射影インスタンスを作成する**</span><span class="sxs-lookup"><span data-stu-id="a49b6-144">**Creating a new projected instance by using constructors**</span></span>

- <span data-ttu-id="a49b6-145">例:</span><span class="sxs-lookup"><span data-stu-id="a49b6-145">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- <span data-ttu-id="a49b6-146">エンティティ型: <xref:System.NotSupportedException> 発生</span><span class="sxs-lookup"><span data-stu-id="a49b6-146">Entity type: A <xref:System.NotSupportedException> is raised.</span></span>

- <span data-ttu-id="a49b6-147">エンティティ型以外: サポート状況</span><span class="sxs-lookup"><span data-stu-id="a49b6-147">Non-entity type: Supported</span></span>

<span data-ttu-id="a49b6-148">**射影を使用してプロパティ値を変換する**</span><span class="sxs-lookup"><span data-stu-id="a49b6-148">**Using projection to transform a property value**</span></span>

- <span data-ttu-id="a49b6-149">例:</span><span class="sxs-lookup"><span data-stu-id="a49b6-149">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- <span data-ttu-id="a49b6-150">エンティティ型: この変換は、エンティティ型では混乱の原因となり、別のエンティティに属するデータ ソース内のデータを上書きする可能性があるため、サポートされません。</span><span class="sxs-lookup"><span data-stu-id="a49b6-150">Entity type: This transformation is not supported for entity types because it can lead to confusion and potentially overwriting the data in the data source that belongs to another entity.</span></span> <span data-ttu-id="a49b6-151"><xref:System.NotSupportedException> 発生</span><span class="sxs-lookup"><span data-stu-id="a49b6-151">A <xref:System.NotSupportedException> is raised.</span></span>

- <span data-ttu-id="a49b6-152">エンティティ型以外: サポート状況</span><span class="sxs-lookup"><span data-stu-id="a49b6-152">Non-entity type: Supported</span></span>

<a name="considerations"></a>

## <a name="projection-considerations"></a><span data-ttu-id="a49b6-153">射影時の注意事項</span><span class="sxs-lookup"><span data-stu-id="a49b6-153">Projection Considerations</span></span>

<span data-ttu-id="a49b6-154">クエリ射影を定義する場合は、次の点にも注意してください。</span><span class="sxs-lookup"><span data-stu-id="a49b6-154">The following additional considerations apply when defining a query projection.</span></span>

- <span data-ttu-id="a49b6-155">Atom 形式のフィードを独自に定義する場合、カスタム マッピングが定義されているすべてのエンティティ プロパティが射影に含まれることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a49b6-155">When you define custom feeds for the Atom format, you must make sure that all entity properties that have custom mappings defined are included in the projection.</span></span> <span data-ttu-id="a49b6-156">マップされているエンティティ プロパティがこの射影に含まれていない場合、データの損失が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="a49b6-156">When a mapped entity property is not included in the projection, data loss might occur.</span></span> <span data-ttu-id="a49b6-157">詳細については、「[フィードのカスタマイズ](feed-customization-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a49b6-157">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>

- <span data-ttu-id="a49b6-158">データ サービスのデータ モデルのエンティティのすべてのプロパティを含まない射影型に挿入を行った場合、クライアントで射影に含まれていないプロパティは既定値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-158">When inserts are made to a projected type that does not contain all of the properties of the entity in the data model of the data service, the properties not included in the projection at the client are set to their default values.</span></span>

- <span data-ttu-id="a49b6-159">データ サービスのデータ モデルのエンティティのすべてのプロパティを含まない射影影型に対して更新を行った場合、クライアントで射影に含まれていない既存の値は初期化されていない既定値で上書きされます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-159">When updates are made to a projected type that does not contain all of the properties of the entity in the data model of the data service, existing values not included in the projection on the client will be overwritten with uninitialized default values.</span></span>

- <span data-ttu-id="a49b6-160">射影に複合プロパティが含まれる場合、複合オブジェクト全体が返される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a49b6-160">When a projection includes a complex property, the entire complex object must be returned.</span></span>

- <span data-ttu-id="a49b6-161">射影にナビゲーション プロパティが含まれる場合、<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> メソッドを呼び出す必要はなく、関連オブジェクトが暗黙的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-161">When a projection includes a navigation property, the related objects are loaded implicitly without having to call the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method.</span></span> <span data-ttu-id="a49b6-162">射影されたクエリでの <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> メソッドの使用はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="a49b6-162">The <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is not supported for use in a projected query.</span></span>

- <span data-ttu-id="a49b6-163">クライアント上のクエリ射影クエリは、要求 URI の `$select` クエリ オプションを使用するように変換されます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-163">Query projections queries on the client are translated to use the `$select` query option in the request URI.</span></span> <span data-ttu-id="a49b6-164">`$select` クエリ オプションがサポートされていない WCF Data Services の以前のバージョンに対して、射影のあるクエリを実行すると、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="a49b6-164">When a query with projection is executed against a previous version of WCF Data Services that does not support the `$select` query option, an error is returned.</span></span> <span data-ttu-id="a49b6-165">これは、データ サービスの  <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> の <xref:System.Data.Services.DataServiceBehavior> が <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1> という値に設定されている場合にも発生します。</span><span class="sxs-lookup"><span data-stu-id="a49b6-165">This can also happen when the <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> of the <xref:System.Data.Services.DataServiceBehavior> for the data service is set to a value of <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>.</span></span> <span data-ttu-id="a49b6-166">詳細については、「[データ サービスのバージョン管理](data-service-versioning-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a49b6-166">For more information, see [Data Service Versioning](data-service-versioning-wcf-data-services.md).</span></span>

<span data-ttu-id="a49b6-167">詳細については、[クエリ結果を射影する](how-to-project-query-results-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a49b6-167">For more information, see [How to: Project Query Results](how-to-project-query-results-wcf-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a49b6-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="a49b6-168">See also</span></span>

- [<span data-ttu-id="a49b6-169">データ サービスに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="a49b6-169">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)
