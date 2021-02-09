---
description: '詳細情報: ROW (Entity SQL)'
title: ROW (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 2d0bcf3c5be8ef3b67e170af5159ae7dd8744630
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739275"
---
# <a name="row-entity-sql"></a><span data-ttu-id="75a26-103">ROW (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="75a26-103">ROW (Entity SQL)</span></span>

<span data-ttu-id="75a26-104">1 つまたは複数の値から構造的に型付けされた匿名レコードを構築します。</span><span class="sxs-lookup"><span data-stu-id="75a26-104">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75a26-105">構文</span><span class="sxs-lookup"><span data-stu-id="75a26-105">Syntax</span></span>  
  
```sql  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="75a26-106">引数</span><span class="sxs-lookup"><span data-stu-id="75a26-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="75a26-107">行型で構築する値を返す任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="75a26-107">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="75a26-108">行型で指定された値の別名を指定します。</span><span class="sxs-lookup"><span data-stu-id="75a26-108">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="75a26-109">別名を指定しないと、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 別名生成規則に基づいて別名の生成を試みます。</span><span class="sxs-lookup"><span data-stu-id="75a26-109">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75a26-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="75a26-110">Return Value</span></span>  

 <span data-ttu-id="75a26-111">行型。</span><span class="sxs-lookup"><span data-stu-id="75a26-111">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75a26-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="75a26-112">Remarks</span></span>  

 <span data-ttu-id="75a26-113">1 つまたは複数の値から構造的に型付けされた匿名レコードを構築するには、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の行コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="75a26-113">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="75a26-114">行コンストラクターの結果の型は、行の構築に使用された値の型に対応するフィールド型を持つ行型です。</span><span class="sxs-lookup"><span data-stu-id="75a26-114">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="75a26-115">たとえば、次の式は `Record(a int, b string, c int)`型の値を構築します。</span><span class="sxs-lookup"><span data-stu-id="75a26-115">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```sql  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="75a26-116">行コンストラクターで式の別名が指定されていなければ、Entity Framework は別名の生成を試みます。</span><span class="sxs-lookup"><span data-stu-id="75a26-116">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="75a26-117">詳細については、「 [識別子](identifiers-entity-sql.md) 」トピックの「別名規則」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75a26-117">For more information, see the "Aliasing Rules" section of the [Identifiers](identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="75a26-118">次の規則は、行コンストラクターで別名を定義する式に適用されます。</span><span class="sxs-lookup"><span data-stu-id="75a26-118">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="75a26-119">行コンストラクターの式で同じコンストラクターの他の別名を参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="75a26-119">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="75a26-120">同じ行コンストラクター内の 2 つの式に同じ別名を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="75a26-120">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="75a26-121">クエリ コンストラクターについて詳しくは、「[コンストラクター](constructing-types-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="75a26-121">For more information about query constructors, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75a26-122">例</span><span class="sxs-lookup"><span data-stu-id="75a26-122">Example</span></span>  

 <span data-ttu-id="75a26-123">次の Entity SQL クエリは ROW 演算子を使用して、構造的に型付けされた匿名レコードを構築します。</span><span class="sxs-lookup"><span data-stu-id="75a26-123">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="75a26-124">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="75a26-124">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="75a26-125">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="75a26-125">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="75a26-126">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="75a26-126">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="75a26-127">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="75a26-127">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ROW](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#row)]  
  
## <a name="see-also"></a><span data-ttu-id="75a26-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="75a26-128">See also</span></span>

- [<span data-ttu-id="75a26-129">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="75a26-129">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="75a26-130">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="75a26-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="75a26-131">型定義</span><span class="sxs-lookup"><span data-stu-id="75a26-131">Type Definitions</span></span>](type-definitions-entity-sql.md)
