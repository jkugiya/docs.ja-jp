---
description: '詳細情報: 方法:リフレクション プロバイダーを使用してデータ サービスを作成する (WCF Data Services)'
title: '方法: リフレクション プロバイダーを使用してデータ サービスを作成する (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 1c4d131b21c69e11dd6d8b574e4c22a6af7c5a25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766231"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="db700-103">方法: リフレクション プロバイダーを使用してデータ サービスを作成する (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="db700-103">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="db700-104">WCF Data Services では、<xref:System.Linq.IQueryable%601> インターフェイスを実装するオブジェクトとして公開されているクラスに基づいてデータ モデルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="db700-104">WCF Data Services enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="db700-105">詳細については、「[Data Services プロバイダー](data-services-providers-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db700-105">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db700-106">例</span><span class="sxs-lookup"><span data-stu-id="db700-106">Example</span></span>  

 <span data-ttu-id="db700-107">次の例は、`Orders` および `Items` を含むデータ モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="db700-107">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="db700-108">エンティティ コンテナー クラス `OrderItemData` には、<xref:System.Linq.IQueryable%601> インターフェイスを返す 2 つのパブリック メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="db700-108">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="db700-109">これらのインターフェイスは、`Orders` エンティティ型と `Items` エンティティ型のエンティティ セットです。</span><span class="sxs-lookup"><span data-stu-id="db700-109">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="db700-110">`Order` には複数の `Items` を含めることができるので、`Orders` エンティティ型には `Items` オブジェクトのコレクションを返す `Items` ナビゲーション プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="db700-110">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="db700-111">`OrderItemData` エンティティ コンテナー クラスは、<xref:System.Data.Services.DataService%601> データ サービスが派生する `OrderItems` クラスのジェネリック型です。</span><span class="sxs-lookup"><span data-stu-id="db700-111">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db700-112">この例はメモリ内のデータ プロバイダーを示し、変更は現在のオブジェクト インスタンスの外部で永続化されないので、<xref:System.Data.Services.IUpdatable> インターフェイスを実装する利点はありません。</span><span class="sxs-lookup"><span data-stu-id="db700-112">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="db700-113"><xref:System.Data.Services.IUpdatable> インターフェイスを実装する例については、「[方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する](create-a-data-service-using-linq-to-sql-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db700-113">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="db700-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="db700-114">See also</span></span>

- [<span data-ttu-id="db700-115">方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="db700-115">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="db700-116">Data Services プロバイダー</span><span class="sxs-lookup"><span data-stu-id="db700-116">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="db700-117">方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="db700-117">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
