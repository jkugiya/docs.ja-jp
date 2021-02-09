---
description: '詳細情報: LINQ to Entities の既知の問題および注意点'
title: LINQ to Entities の既知の問題および注意点
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 61377fc27770cb16583e0347fff1a03b6cd44af6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748311"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="2ee25-103">LINQ to Entities の既知の問題および注意点</span><span class="sxs-lookup"><span data-stu-id="2ee25-103">Known Issues and Considerations in LINQ to Entities</span></span>

<span data-ttu-id="2ee25-104">ここでは、LINQ to Entities クエリの既知の問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ee25-104">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="2ee25-105">キャッシュできない LINQ クエリ</span><span class="sxs-lookup"><span data-stu-id="2ee25-105">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="2ee25-106">失われた情報の収集の順序付け</span><span class="sxs-lookup"><span data-stu-id="2ee25-106">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="2ee25-107">サポートされていない符号なし整数</span><span class="sxs-lookup"><span data-stu-id="2ee25-107">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="2ee25-108">型変換エラー</span><span class="sxs-lookup"><span data-stu-id="2ee25-108">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="2ee25-109">非スカラー変数の参照がサポートされていない</span><span class="sxs-lookup"><span data-stu-id="2ee25-109">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="2ee25-110">入れ子になったクエリは、SQL Server 2000 では失敗する可能性がある</span><span class="sxs-lookup"><span data-stu-id="2ee25-110">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="2ee25-111">匿名型への投影</span><span class="sxs-lookup"><span data-stu-id="2ee25-111">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>

## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="2ee25-112">キャッシュできない LINQ クエリ</span><span class="sxs-lookup"><span data-stu-id="2ee25-112">LINQ Queries That cannot be Cached</span></span>  

 <span data-ttu-id="2ee25-113">.NET Framework 4.5 以降では、LINQ to Entities クエリは自動的にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="2ee25-113">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="2ee25-114">ただし、メモリ内コレクションへ `Enumerable.Contains` 演算子を追加する LINQ to Entities クエリは自動的にキャッシュされません。</span><span class="sxs-lookup"><span data-stu-id="2ee25-114">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="2ee25-115">またコンパイル済み LINQ クエリのメモリ内コレクションをパラメーターで表すことは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="2ee25-115">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>

## <a name="ordering-information-lost"></a><span data-ttu-id="2ee25-116">失われた情報の収集の順序付け</span><span class="sxs-lookup"><span data-stu-id="2ee25-116">Ordering Information Lost</span></span>  

 <span data-ttu-id="2ee25-117">匿名型に列を投影すると、互換性レベルが "80" に設定された SQL Server 2005 データベースに対して実行されるクエリの一部で順序付けが失われます。</span><span class="sxs-lookup"><span data-stu-id="2ee25-117">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="2ee25-118">この状況は、次の例に示すように、ORDER BY リストの列名がセレクターの列名と一致する場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="2ee25-118">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>

## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="2ee25-119">サポートされていない符号なし整数</span><span class="sxs-lookup"><span data-stu-id="2ee25-119">Unsigned Integers Not Supported</span></span>  

 <span data-ttu-id="2ee25-120">Entity Framework によって符号なし整数がサポートされていないため、LINQ to Entities クエリでの符号なし整数型の指定はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2ee25-120">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the Entity Framework does not support unsigned integers.</span></span> <span data-ttu-id="2ee25-121">次の例に示すように、符号なし整数を指定すると、クエリ式の変換時に <xref:System.ArgumentException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2ee25-121">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="2ee25-122">この例では、ID 48000 を持つ注文に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="2ee25-122">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>

## <a name="type-conversion-errors"></a><span data-ttu-id="2ee25-123">型変換エラー</span><span class="sxs-lookup"><span data-stu-id="2ee25-123">Type Conversion Errors</span></span>  

 <span data-ttu-id="2ee25-124">Visual Basic では、`CByte` 関数を使用して 1 の値を持つ SQL Server の bit 型の列にプロパティがマップされると、"算術オーバーフロー エラー" というメッセージと共に <xref:System.Data.SqlClient.SqlException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2ee25-124">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="2ee25-125">次の例では、AdventureWorks サンプル データベースの `Product.MakeFlag` 列をクエリし、クエリ結果が反復処理されると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2ee25-125">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>

## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="2ee25-126">非スカラー変数の参照はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2ee25-126">Referencing Non-Scalar Variables Not Supported</span></span>  

 <span data-ttu-id="2ee25-127">クエリでの非スカラー変数 (エンティティなど) の参照はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2ee25-127">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="2ee25-128">そのようなクエリを実行すると、<xref:System.NotSupportedException> 例外がスローされ、"型 `EntityType` の定数値を作成できません。</span><span class="sxs-lookup"><span data-stu-id="2ee25-128">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="2ee25-129">このコンテキストでサポートされるのはプリミティブ型 ('Int32、String、Guid など') だけです" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ee25-129">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ee25-130">スカラー変数のコレクションの参照はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2ee25-130">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>

## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="2ee25-131">入れ子になったクエリは、SQL Server 2000 では失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2ee25-131">Nested Queries May Fail with SQL Server 2000</span></span>  

 <span data-ttu-id="2ee25-132">SQL Server 2000 では、LINQ to Entities クエリは、3 ～ 4 レベルの深さの入れ子になった Transact-SQL クエリを生成する場合に失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2ee25-132">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>

## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="2ee25-133">匿名型への投影</span><span class="sxs-lookup"><span data-stu-id="2ee25-133">Projecting to an Anonymous Type</span></span>  

 <span data-ttu-id="2ee25-134"><xref:System.Data.Objects.ObjectQuery%601.Include%2A> に <xref:System.Data.Objects.ObjectQuery%601> メソッドを使用して、関連オブジェクトを含めるように最初のクエリ パスを定義してから LINQ を使用して、返されたオブジェクトを匿名の型に投影した場合、include メソッドで指定されたオブジェクトはクエリ結果に含まれません。</span><span class="sxs-lookup"><span data-stu-id="2ee25-134">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="2ee25-135">関連オブジェクトを取得するには、返された型を匿名の型に投影しないでください。</span><span class="sxs-lookup"><span data-stu-id="2ee25-135">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="2ee25-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ee25-136">See also</span></span>

- [<span data-ttu-id="2ee25-137">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="2ee25-137">LINQ to Entities</span></span>](linq-to-entities.md)
