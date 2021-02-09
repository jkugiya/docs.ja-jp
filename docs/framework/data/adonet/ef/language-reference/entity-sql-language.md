---
description: '詳細情報: Entity SQL 言語'
title: Entity SQL 言語
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: c05e561e5da3f9ee8788a25f8ca97b22444e109f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724571"
---
# <a name="entity-sql-language"></a><span data-ttu-id="1cd68-103">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="1cd68-103">Entity SQL Language</span></span>

<span data-ttu-id="1cd68-104">Entity SQL は、ストレージに依存しない SQL と似たクエリ言語です。</span><span class="sxs-lookup"><span data-stu-id="1cd68-104">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="1cd68-105">Entity SQL を使用すると、オブジェクトとして、または表形式でエンティティ データに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="1cd68-105">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="1cd68-106">次の場合には Entity SQL の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="1cd68-106">You should consider using Entity SQL in the following cases:</span></span>  
  
- <span data-ttu-id="1cd68-107">クエリを実行時に動的に作成する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="1cd68-107">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="1cd68-108">その場合、実行時に Entity SQL クエリ文字列を作成する代わりに、<xref:System.Data.Objects.ObjectQuery%601> のクエリ ビルダー メソッドを使用することも検討してください。</span><span class="sxs-lookup"><span data-stu-id="1cd68-108">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
- <span data-ttu-id="1cd68-109">モデル定義の一部としてクエリを定義する場合。</span><span class="sxs-lookup"><span data-stu-id="1cd68-109">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="1cd68-110">データ モデルでは Entity SQL のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1cd68-110">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="1cd68-111">詳細については、「[QueryView 要素 (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="1cd68-111">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
- <span data-ttu-id="1cd68-112">EntityClient で <xref:System.Data.EntityClient.EntityDataReader> を使用して行セットとして読み取り専用エンティティ データを返す場合。</span><span class="sxs-lookup"><span data-stu-id="1cd68-112">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="1cd68-113">詳細については、「 [Entity Framework 用の EntityClient プロバイダー](../entityclient-provider-for-the-entity-framework.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cd68-113">For more information, see [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span></span>  
  
- <span data-ttu-id="1cd68-114">SQL ベースのクエリ言語に詳しい場合、Entity SQL の使用が最も適切に思われるでしょう。</span><span class="sxs-lookup"><span data-stu-id="1cd68-114">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="1cd68-115">Entity SQL と EntityClient プロバイダーの使用</span><span class="sxs-lookup"><span data-stu-id="1cd68-115">Using Entity SQL with the EntityClient provider</span></span>  

 <span data-ttu-id="1cd68-116">Entity SQL を EntityClient プロバイダーと一緒に使用する際の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cd68-116">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="1cd68-117">Entity Framework 用の EntityClient プロバイダー</span><span class="sxs-lookup"><span data-stu-id="1cd68-117">EntityClient Provider for the Entity Framework</span></span>](../entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="1cd68-118">方法: EntityConnection の接続文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="1cd68-118">How to: Build an EntityConnection Connection String</span></span>](../how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="1cd68-119">方法: PrimitiveType の結果を返すクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="1cd68-119">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="1cd68-120">方法: StructuralType の結果を返すクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="1cd68-120">How to: Execute a Query that Returns StructuralType Results</span></span>](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="1cd68-121">方法: RefType の結果を返すクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="1cd68-121">How to: Execute a Query that Returns RefType Results</span></span>](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="1cd68-122">方法: 複合型を返すクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="1cd68-122">How to: Execute a Query that Returns Complex Types</span></span>](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="1cd68-123">方法: 入れ子になったコレクションを返すクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="1cd68-123">How to: Execute a Query that Returns Nested Collections</span></span>](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="1cd68-124">方法: EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="1cd68-124">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="1cd68-125">方法: EntityCommand を使用してパラメーター化されたストアド プロシージャを実行する</span><span class="sxs-lookup"><span data-stu-id="1cd68-125">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="1cd68-126">方法: ポリモーフィック クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="1cd68-126">How to: Execute a Polymorphic Query</span></span>](../how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="1cd68-127">方法: Navigate 演算子でリレーションシップをナビゲートする</span><span class="sxs-lookup"><span data-stu-id="1cd68-127">How to: Navigate Relationships with the Navigate Operator</span></span>](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="1cd68-128">Entity SQL とオブジェクト クエリの使用</span><span class="sxs-lookup"><span data-stu-id="1cd68-128">Using Entity SQL with object queries</span></span>  

 <span data-ttu-id="1cd68-129">Entity SQL をオブジェクト クエリと一緒に使用する際の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cd68-129">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="1cd68-130">[方法: エンティティ型オブジェクトを返すクエリを実行する](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-130">[How to: Execute a Query that Returns Entity Type Objects](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-131">[方法: パラメーター化されたクエリを実行する](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-131">[How to: Execute a Parameterized Query](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-132">[方法: ナビゲーション プロパティを使用して関係をナビゲートする](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-132">[How to: Navigate Relationships Using Navigation Properties](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-133">[方法: ユーザー定義関数を呼び出す](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-133">[How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-134">[方法: データのフィルター処理](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-134">[How to: Filter Data](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-135">[方法: データを並べ替える](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-135">[How to: Sort Data](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-136">[方法: データのグループ化](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-136">[How to: Group Data](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-137">[方法: データの集計](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-137">[How to: Aggregate Data](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-138">[方法: 匿名型のコレクションを返すクエリを実行する](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-138">[How to: Execute a Query that Returns Anonymous Type Objects](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-139">[方法: プリミティブ型のコレクションを返すクエリを実行する](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-139">[How to: Execute a Query that Returns a Collection of Primitive Types](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-140">[方法: EntityCollection 内の関連するオブジェクトにクエリを実行する](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-140">[How to: Query Related Objects in an EntityCollection](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-141">[方法: 2 つのクエリの結合を並べ替える](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-141">[How to: Order the Union of Two Queries](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="1cd68-142">[方法: クエリの結果をページングする](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cd68-142">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1cd68-143">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1cd68-143">In This Section</span></span>  

 [<span data-ttu-id="1cd68-144">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="1cd68-144">Entity SQL Overview</span></span>](entity-sql-overview.md)  
  
 [<span data-ttu-id="1cd68-145">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="1cd68-145">Entity SQL Reference</span></span>](entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="1cd68-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cd68-146">See also</span></span>

- [<span data-ttu-id="1cd68-147">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="1cd68-147">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="1cd68-148">言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="1cd68-148">Language Reference</span></span>](index.md)
