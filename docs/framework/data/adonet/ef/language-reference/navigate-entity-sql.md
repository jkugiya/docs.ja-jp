---
description: '詳細情報: NAVIGATE (Entity SQL)'
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 7fa39a988429fe0a658b01078d2369ad4767f4a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696504"
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="23ac5-103">NAVIGATE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="23ac5-103">NAVIGATE (Entity SQL)</span></span>

<span data-ttu-id="23ac5-104">エンティティ間で確立されたリレーションシップをナビゲートします。</span><span class="sxs-lookup"><span data-stu-id="23ac5-104">Navigates over the relationship established between entities.</span></span>

## <a name="syntax"></a><span data-ttu-id="23ac5-105">構文</span><span class="sxs-lookup"><span data-stu-id="23ac5-105">Syntax</span></span>

```sql
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a><span data-ttu-id="23ac5-106">引数</span><span class="sxs-lookup"><span data-stu-id="23ac5-106">Arguments</span></span>

<span data-ttu-id="23ac5-107">`instance-expression` エンティティのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="23ac5-107">`instance-expression` An instance of an entity.</span></span>

<span data-ttu-id="23ac5-108">`relationship-type` 概念スキーマ定義言語 (CSDL) ファイルで指定されたリレーションシップの種類の名前。</span><span class="sxs-lookup"><span data-stu-id="23ac5-108">`relationship-type` The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="23ac5-109">`relationship-type` は \<namespace>.\<relationship type name> として修飾されます。</span><span class="sxs-lookup"><span data-stu-id="23ac5-109">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>

<span data-ttu-id="23ac5-110">`to` リレーションシップの終端。</span><span class="sxs-lookup"><span data-stu-id="23ac5-110">`to` The end of the relationship.</span></span>

<span data-ttu-id="23ac5-111">`from` リレーションシップの開始。</span><span class="sxs-lookup"><span data-stu-id="23ac5-111">`from` The beginning of the relationship.</span></span>

## <a name="return-value"></a><span data-ttu-id="23ac5-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="23ac5-112">Return Value</span></span>

<span data-ttu-id="23ac5-113">終端のカーディナリティが 1 の場合、戻り値は `Ref<T>` になります。</span><span class="sxs-lookup"><span data-stu-id="23ac5-113">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="23ac5-114">終端のカーディナリティが n の場合、戻り値は `Collection<Ref<T>>` になります。</span><span class="sxs-lookup"><span data-stu-id="23ac5-114">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>

## <a name="remarks"></a><span data-ttu-id="23ac5-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="23ac5-115">Remarks</span></span>

<span data-ttu-id="23ac5-116">リレーションシップは、Entity Data Model (EDM) における最上位のコンストラクトです。</span><span class="sxs-lookup"><span data-stu-id="23ac5-116">Relationships are first-class constructs in the Entity Data Model (EDM).</span></span> <span data-ttu-id="23ac5-117">リレーションシップは、複数のエンティティ型の間で確立され、ユーザーはエンティティ間のリレーションシップをナビゲートできます。</span><span class="sxs-lookup"><span data-stu-id="23ac5-117">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="23ac5-118">`from` と `to` は、リレーションシップ内の名前解決があいまいでない場合の条件付きのオプションです。</span><span class="sxs-lookup"><span data-stu-id="23ac5-118">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>

<span data-ttu-id="23ac5-119">NAVIGATE は、O および C 空間で有効です。</span><span class="sxs-lookup"><span data-stu-id="23ac5-119">NAVIGATE is valid in O and C space.</span></span>

<span data-ttu-id="23ac5-120">ナビゲーション構造の一般的な形式は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="23ac5-120">The general form of a navigation construct is the following:</span></span>

<span data-ttu-id="23ac5-121">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span><span class="sxs-lookup"><span data-stu-id="23ac5-121">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>

<span data-ttu-id="23ac5-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="23ac5-122">For example:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

<span data-ttu-id="23ac5-123">ここで、OrderCustomer は `relationship`であり、Customer と Order はリレーションシップの `to-end` (顧客) と `from-end` (注文) です。</span><span class="sxs-lookup"><span data-stu-id="23ac5-123">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="23ac5-124">OrderCustomer が n:1 リレーションシップの場合、ナビゲーション式の結果型は Ref\<Customer> となります。</span><span class="sxs-lookup"><span data-stu-id="23ac5-124">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>

<span data-ttu-id="23ac5-125">この式をより簡略化すると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="23ac5-125">The simpler form of this expression is the following:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

<span data-ttu-id="23ac5-126">同様に、次の形式のクエリでは、ナビゲーション式は Collection<Ref\<Order>> のようになります。</span><span class="sxs-lookup"><span data-stu-id="23ac5-126">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

<span data-ttu-id="23ac5-127">インスタンス式は、エンティティ/参照型になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="23ac5-127">The instance-expression must be an entity/ref type.</span></span>

## <a name="example"></a><span data-ttu-id="23ac5-128">例</span><span class="sxs-lookup"><span data-stu-id="23ac5-128">Example</span></span>

<span data-ttu-id="23ac5-129">次の Entity SQL クエリでは、NAVIGATE 演算子を使用して、Address エンティティ型と SalesOrderHeader エンティティ型間で確立されたリレーションシップをナビゲートします。</span><span class="sxs-lookup"><span data-stu-id="23ac5-129">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="23ac5-130">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="23ac5-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="23ac5-131">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="23ac5-131">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="23ac5-132">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="23ac5-132">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="23ac5-133">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="23ac5-133">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

 [!code-sql[DP EntityServices Concepts#NAVIGATE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#navigate)]

## <a name="see-also"></a><span data-ttu-id="23ac5-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="23ac5-134">See also</span></span>

- [<span data-ttu-id="23ac5-135">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="23ac5-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="23ac5-136">方法: Navigate 演算子でリレーションシップをナビゲートする</span><span class="sxs-lookup"><span data-stu-id="23ac5-136">How to: Navigate Relationships with Navigate Operator</span></span>](navigate-entity-sql.md)
