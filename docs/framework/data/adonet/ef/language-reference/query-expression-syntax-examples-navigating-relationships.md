---
description: '詳細情報: クエリ式の構文例:リレーションシップの操作'
title: クエリ式の構文例:リレーションシップの操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: 0548cba8d1d3d834da6a8416cb444898981b4123
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696153"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="0f76e-103">クエリ式の構文例:リレーションシップの操作</span><span class="sxs-lookup"><span data-stu-id="0f76e-103">Query Expression Syntax Examples: Navigating Relationships</span></span>

<span data-ttu-id="0f76e-104">Entity Framework のナビゲーション プロパティは、アソシエーションの末尾にあるエンティティを見つけるために使用できるショートカット プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f76e-104">Navigation properties in the Entity Framework are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="0f76e-105">ナビゲーション プロパティを使用すると、ユーザーは、エンティティ間をナビゲートしたり、あるエンティティからアソシエーション セットを介して関連エンティティにナビゲートしたりできます。</span><span class="sxs-lookup"><span data-stu-id="0f76e-105">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="0f76e-106">このトピックでは、LINQ to Entities のクエリ内でナビゲーション プロパティを介してリレーションシップをナビゲートするためのクエリ式の構文例を示します。</span><span class="sxs-lookup"><span data-stu-id="0f76e-106">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="0f76e-107">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="0f76e-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0f76e-108">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="0f76e-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="0f76e-109">例</span><span class="sxs-lookup"><span data-stu-id="0f76e-109">Example</span></span>  

 <span data-ttu-id="0f76e-110">次の例では、<xref:System.Linq.Queryable.Select%2A> メソッドを使用して、姓が "Zhou" である連絡先のすべての連絡先 ID と、各連絡先の合計支払額の総計を取得します。</span><span class="sxs-lookup"><span data-stu-id="0f76e-110">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="0f76e-111">`Contact.SalesOrderHeader` ナビゲーション プロパティは、各連絡先の `SalesOrderHeader` オブジェクトのコレクションを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0f76e-111">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="0f76e-112">`Sum` メソッドは、`Contact.SalesOrderHeader` ナビゲーション プロパティを使用して、それぞれの連絡先のすべての注文の合計支払額を合計します。</span><span class="sxs-lookup"><span data-stu-id="0f76e-112">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="0f76e-113">例</span><span class="sxs-lookup"><span data-stu-id="0f76e-113">Example</span></span>  

 <span data-ttu-id="0f76e-114">次の例では、姓が "Zhou" である連絡先のすべての注文を取得します。</span><span class="sxs-lookup"><span data-stu-id="0f76e-114">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="0f76e-115">`Contact.SalesOrderHeader` ナビゲーション プロパティは、各連絡先の `SalesOrderHeader` オブジェクトのコレクションを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0f76e-115">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="0f76e-116">連絡先の名前と注文が匿名型で返されます。</span><span class="sxs-lookup"><span data-stu-id="0f76e-116">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="0f76e-117">例</span><span class="sxs-lookup"><span data-stu-id="0f76e-117">Example</span></span>  

 <span data-ttu-id="0f76e-118">次の例では、`SalesOrderHeader.Address` ナビゲーション プロパティと `SalesOrderHeader.Contact` ナビゲーション プロパティを使用して、互いに関連付けられている `Address` オブジェクトと `Contact` オブジェクトのコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="0f76e-118">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="0f76e-119">各注文の連絡先の姓、住所、販売注文番号、および Seattle 市に対する合計支払額が匿名型で返されます。</span><span class="sxs-lookup"><span data-stu-id="0f76e-119">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="0f76e-120">例</span><span class="sxs-lookup"><span data-stu-id="0f76e-120">Example</span></span>  

 <span data-ttu-id="0f76e-121">次の例では、`Where` メソッドを使用して、2003 年 12 月 1 日以降に受けた注文を検索します。次に、`order.SalesOrderDetail` ナビゲーション プロパティを使用して、各注文の詳細を取得します。</span><span class="sxs-lookup"><span data-stu-id="0f76e-121">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="0f76e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f76e-122">See also</span></span>

- [<span data-ttu-id="0f76e-123">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="0f76e-123">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
