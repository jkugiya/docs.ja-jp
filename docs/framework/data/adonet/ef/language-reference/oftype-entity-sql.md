---
description: '詳細情報: OFTYPE (Entity SQL)'
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: d916ea4487fcc7a21f5fb62aa7e6f8a23d73fed2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739340"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="d70ae-103">OFTYPE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d70ae-103">OFTYPE (Entity SQL)</span></span>

<span data-ttu-id="d70ae-104">クエリ式を使用して、指定された型のオブジェクトのコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="d70ae-104">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70ae-105">構文</span><span class="sxs-lookup"><span data-stu-id="d70ae-105">Syntax</span></span>  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="d70ae-106">引数</span><span class="sxs-lookup"><span data-stu-id="d70ae-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="d70ae-107">オブジェクトのコレクションを返す任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="d70ae-107">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="d70ae-108">`expression` から返される各オブジェクトを判定するための型。</span><span class="sxs-lookup"><span data-stu-id="d70ae-108">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="d70ae-109">型は名前空間で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d70ae-109">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d70ae-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="d70ae-110">Return Value</span></span>  

 <span data-ttu-id="d70ae-111">`test_type`型であるか、 `test_type`の基本データ型または派生型であるオブジェクトのコレクション。</span><span class="sxs-lookup"><span data-stu-id="d70ae-111">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="d70ae-112">ONLY を指定した場合、 `test_type` のインスタンスまたは空のコレクションのみ返されます。</span><span class="sxs-lookup"><span data-stu-id="d70ae-112">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d70ae-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="d70ae-113">Remarks</span></span>  

 <span data-ttu-id="d70ae-114">`OFTYPE` 式は、コレクションの各要素の型を判定するための式です。</span><span class="sxs-lookup"><span data-stu-id="d70ae-114">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="d70ae-115">`OFTYPE` 式では、指定された型の新しいコレクションが生成されます。生成されたコレクションには、指定された型と同じか、そのサブタイプの要素だけが格納されます。</span><span class="sxs-lookup"><span data-stu-id="d70ae-115">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="d70ae-116">`OFTYPE` 式は、次のクエリ式の省略形です。</span><span class="sxs-lookup"><span data-stu-id="d70ae-116">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="d70ae-117">Manager が Employee のサブタイプである場合、次の式からは、従業員 (employee) のコレクションのうち、マネージャー (manager) のコレクションだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="d70ae-117">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="d70ae-118">型フィルターを使用してコレクションをアップ キャストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d70ae-118">It is also possible to up cast a collection using the type filter:</span></span>  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="d70ae-119">すべての企業幹部はマネージャーであるので、結果のコレクションには元の企業幹部がすべて含まれたままですが、コレクションはマネージャーのコレクションとして型指定されています。</span><span class="sxs-lookup"><span data-stu-id="d70ae-119">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="d70ae-120">次の表は、いくつかのパターンにおける `OFTYPE` 演算子の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="d70ae-120">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="d70ae-121">すべての例外はクライアント側にスローされてから、プロバイダーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d70ae-121">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="d70ae-122">パターン</span><span class="sxs-lookup"><span data-stu-id="d70ae-122">Pattern</span></span>|<span data-ttu-id="d70ae-123">動作</span><span class="sxs-lookup"><span data-stu-id="d70ae-123">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="d70ae-124">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="d70ae-124">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="d70ae-125">Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="d70ae-125">Collection(EntityType)</span></span>|  
|<span data-ttu-id="d70ae-126">OFTYPE(Collection(ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="d70ae-126">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="d70ae-127">スロー</span><span class="sxs-lookup"><span data-stu-id="d70ae-127">Throws</span></span>|  
|<span data-ttu-id="d70ae-128">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="d70ae-128">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="d70ae-129">スロー</span><span class="sxs-lookup"><span data-stu-id="d70ae-129">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d70ae-130">例</span><span class="sxs-lookup"><span data-stu-id="d70ae-130">Example</span></span>  

 <span data-ttu-id="d70ae-131">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、OFTYPE 演算子を使用して、Course オブジェクトのコレクションから OnsiteCourse オブジェクトのコレクションを取得して返します。</span><span class="sxs-lookup"><span data-stu-id="d70ae-131">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="d70ae-132">このクエリは、 [School モデル](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d70ae-132">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="d70ae-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="d70ae-133">See also</span></span>

- [<span data-ttu-id="d70ae-134">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="d70ae-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
