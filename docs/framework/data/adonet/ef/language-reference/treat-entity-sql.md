---
description: '詳細情報: TREAT (Entity SQL)'
title: TREAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 3f014cac631d246b35d145cdb80c9aa6ac401524
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673428"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="12f9d-103">TREAT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="12f9d-103">TREAT (Entity SQL)</span></span>

<span data-ttu-id="12f9d-104">特定の基本データ型のオブジェクトを指定の派生型のオブジェクトとして処理します。</span><span class="sxs-lookup"><span data-stu-id="12f9d-104">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f9d-105">構文</span><span class="sxs-lookup"><span data-stu-id="12f9d-105">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="12f9d-106">引数</span><span class="sxs-lookup"><span data-stu-id="12f9d-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="12f9d-107">エンティティを返す任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="12f9d-107">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12f9d-108">指定の式の型は、特定のデータ型のサブタイプである必要があります。または、データ型は式の型のサブタイプである必要があります。</span><span class="sxs-lookup"><span data-stu-id="12f9d-108">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="12f9d-109">エンティティ型。</span><span class="sxs-lookup"><span data-stu-id="12f9d-109">An entity type.</span></span> <span data-ttu-id="12f9d-110">型は名前空間で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12f9d-110">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12f9d-111">指定の式は、特定のデータ型のサブタイプである必要があります。または、データ型は式のサブタイプである必要があります。</span><span class="sxs-lookup"><span data-stu-id="12f9d-111">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12f9d-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="12f9d-112">Return Value</span></span>  

 <span data-ttu-id="12f9d-113">指定されたデータ型の値。</span><span class="sxs-lookup"><span data-stu-id="12f9d-113">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12f9d-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="12f9d-114">Remarks</span></span>  

 <span data-ttu-id="12f9d-115">TREAT は関連クラス間でキャストを実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="12f9d-115">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="12f9d-116">たとえば、 `Employee` が `Person` から派生し、p が `Person`型である場合、 `TREAT(p AS NamespaceName.Employee)` はジェネリック型の `Person` インスタンスを `Employee`にキャストします。つまり、p を `Employee`として処理できます。</span><span class="sxs-lookup"><span data-stu-id="12f9d-116">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="12f9d-117">TREAT は、次のようにクエリを実行できる継承シナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="12f9d-117">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 <span data-ttu-id="12f9d-118">このクエリは、 `Person` エンティティを `Employee` 型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="12f9d-118">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="12f9d-119">p の値が実際には `Employee`型でない場合、この式は `null`値を返します。</span><span class="sxs-lookup"><span data-stu-id="12f9d-119">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12f9d-120">指定する式 `Employee` は、指定するデータ型 `Person` のサブタイプである必要があります。または、データ型は式のサブタイプである必要があります。</span><span class="sxs-lookup"><span data-stu-id="12f9d-120">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="12f9d-121">そうでない場合は、コンパイル時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="12f9d-121">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="12f9d-122">次の表に、いくつかの通常パターンと一般的でないパターンにおける TREAT の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="12f9d-122">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="12f9d-123">すべての例外はクライアント側にスローされてから、プロバイダーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="12f9d-123">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="12f9d-124">パターン</span><span class="sxs-lookup"><span data-stu-id="12f9d-124">Pattern</span></span>|<span data-ttu-id="12f9d-125">動作</span><span class="sxs-lookup"><span data-stu-id="12f9d-125">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="12f9d-126">`DbNull`を返します。</span><span class="sxs-lookup"><span data-stu-id="12f9d-126">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="12f9d-127">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="12f9d-127">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="12f9d-128">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="12f9d-128">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="12f9d-129">`EntityType` または `null`を返します。</span><span class="sxs-lookup"><span data-stu-id="12f9d-129">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="12f9d-130">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="12f9d-130">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="12f9d-131">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="12f9d-131">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="12f9d-132">例</span><span class="sxs-lookup"><span data-stu-id="12f9d-132">Example</span></span>  

 <span data-ttu-id="12f9d-133">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、TREAT 演算子を使用して、Course 型のオブジェクトを OnsiteCourse 型のオブジェクトのコレクションに変換します。</span><span class="sxs-lookup"><span data-stu-id="12f9d-133">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="12f9d-134">このクエリは、 [School モデル](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))に基づいています。</span><span class="sxs-lookup"><span data-stu-id="12f9d-134">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="12f9d-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="12f9d-135">See also</span></span>

- [<span data-ttu-id="12f9d-136">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="12f9d-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="12f9d-137">NULL 値が許容される構造化型</span><span class="sxs-lookup"><span data-stu-id="12f9d-137">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
