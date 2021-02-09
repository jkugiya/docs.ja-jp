---
description: '詳細情報: Entity SQL の概要'
title: Entity SQL の概要
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: eb337ff3894b24d787d829838c9cf12c934a823c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724610"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="5295c-103">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="5295c-103">Entity SQL Overview</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5295c-104">は、Entity Framework 内の概念モデルに対するクエリの実行に使用できる SQL に似た言語です。</span><span class="sxs-lookup"><span data-stu-id="5295c-104">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="5295c-105">概念モデルでは、データがエンティティおよびリレーションシップとして表されます。[!INCLUDE[esql](../../../../../../includes/esql-md.md)] を使用すると、SQL を使用したことのあるユーザーが慣れている形式でそれらのエンティティおよびリレーションシップに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5295c-105">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  

 <span data-ttu-id="5295c-106">Entity Framework では、ストレージ固有のデータ プロバイダーとの連携により、汎用的な [!INCLUDE[esql](../../../../../../includes/esql-md.md)] がストレージ固有のクエリに変換されます。</span><span class="sxs-lookup"><span data-stu-id="5295c-106">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="5295c-107">EntityClient プロバイダーには、エンティティ モデルに対して [!INCLUDE[esql](../../../../../../includes/esql-md.md)] コマンドを実行し、スカラー結果、結果セット、オブジェクト グラフなど、さまざまなデータ型を返すための手段が用意されています。</span><span class="sxs-lookup"><span data-stu-id="5295c-107">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="5295c-108"><xref:System.Data.EntityClient.EntityCommand> オブジェクトを構築する場合は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のクエリ文字列を <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> プロパティに割り当てることで、ストアド プロシージャの名前またはクエリのテキストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5295c-108">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5295c-109">EDM に対する <xref:System.Data.EntityClient.EntityDataReader> の実行結果は、<xref:System.Data.EntityClient.EntityCommand> によって公開されます。</span><span class="sxs-lookup"><span data-stu-id="5295c-109">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="5295c-110"><xref:System.Data.EntityClient.EntityDataReader> を返すコマンドを実行するには、<xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5295c-110">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="5295c-111">EntityClient プロバイダーだけでなく Entity Framework でも、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] を使用して概念モデルに対するクエリを実行し、エンティティ型のインスタンスである厳密に型指定された CLR オブジェクトとしてデータを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="5295c-111">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="5295c-112">詳しくは、「[オブジェクトの使用](../working-with-objects.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5295c-112">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="5295c-113">ここでは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="5295c-113">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5295c-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5295c-114">In This Section</span></span>  

 [<span data-ttu-id="5295c-115">Entity SQL と Transact-SQL の相違点</span><span class="sxs-lookup"><span data-stu-id="5295c-115">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="5295c-116">Entity SQL クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="5295c-116">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="5295c-117">型システム</span><span class="sxs-lookup"><span data-stu-id="5295c-117">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="5295c-118">型定義</span><span class="sxs-lookup"><span data-stu-id="5295c-118">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="5295c-119">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="5295c-119">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="5295c-120">クエリ プランのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="5295c-120">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="5295c-121">名前空間</span><span class="sxs-lookup"><span data-stu-id="5295c-121">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="5295c-122">識別子</span><span class="sxs-lookup"><span data-stu-id="5295c-122">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="5295c-123">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5295c-123">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="5295c-124">変数</span><span class="sxs-lookup"><span data-stu-id="5295c-124">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="5295c-125">サポートされていない式</span><span class="sxs-lookup"><span data-stu-id="5295c-125">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="5295c-126">リテラル</span><span class="sxs-lookup"><span data-stu-id="5295c-126">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="5295c-127">NULL リテラルと型推論</span><span class="sxs-lookup"><span data-stu-id="5295c-127">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="5295c-128">入力文字セット</span><span class="sxs-lookup"><span data-stu-id="5295c-128">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="5295c-129">クエリ式</span><span class="sxs-lookup"><span data-stu-id="5295c-129">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="5295c-130">関数</span><span class="sxs-lookup"><span data-stu-id="5295c-130">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="5295c-131">演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="5295c-131">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="5295c-132">ページング</span><span class="sxs-lookup"><span data-stu-id="5295c-132">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="5295c-133">比較セマンティクス</span><span class="sxs-lookup"><span data-stu-id="5295c-133">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="5295c-134">入れ子になった Entity SQL クエリの作成</span><span class="sxs-lookup"><span data-stu-id="5295c-134">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="5295c-135">NULL 値が許容される構造化型</span><span class="sxs-lookup"><span data-stu-id="5295c-135">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="5295c-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="5295c-136">See also</span></span>

- [<span data-ttu-id="5295c-137">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="5295c-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5295c-138">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="5295c-138">Entity SQL Language</span></span>](entity-sql-language.md)
- [<span data-ttu-id="5295c-139">CSDL、SSDL、および MSL 仕様</span><span class="sxs-lookup"><span data-stu-id="5295c-139">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
