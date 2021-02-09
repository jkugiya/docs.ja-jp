---
description: '詳細情報: ISOF (Entity SQL)'
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 4a44ddc74ef16ec16285132f6567ca2500e173a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748350"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="e415c-103">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e415c-103">ISOF (Entity SQL)</span></span>

<span data-ttu-id="e415c-104">式の型が指定の型であるか、またはそのサブタイプであるかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e415c-104">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e415c-105">構文</span><span class="sxs-lookup"><span data-stu-id="e415c-105">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="e415c-106">引数</span><span class="sxs-lookup"><span data-stu-id="e415c-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="e415c-107">型を判断するための任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="e415c-107">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="e415c-108">NOT</span><span class="sxs-lookup"><span data-stu-id="e415c-108">NOT</span></span>  
 <span data-ttu-id="e415c-109">IS OF の EDM.Boolean の結果を否定します。</span><span class="sxs-lookup"><span data-stu-id="e415c-109">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="e415c-110">ONLY</span><span class="sxs-lookup"><span data-stu-id="e415c-110">ONLY</span></span>  
 <span data-ttu-id="e415c-111">`true` が `expression` 型であり、そのサブタイプでない場合に限り、IS OF が `type` を返すことを指定します。</span><span class="sxs-lookup"><span data-stu-id="e415c-111">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="e415c-112">`expression` を判定するための型。</span><span class="sxs-lookup"><span data-stu-id="e415c-112">The type to test `expression` against.</span></span> <span data-ttu-id="e415c-113">型は名前空間で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e415c-113">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e415c-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="e415c-114">Return Value</span></span>  

 <span data-ttu-id="e415c-115">`true` が型 T で、T が基本データ型または `expression` の派生型である場合は、`type` となります。`expression` が実行時に null である場合は null となり、それ以外の場合は `false` となります。</span><span class="sxs-lookup"><span data-stu-id="e415c-115">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e415c-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="e415c-116">Remarks</span></span>  

 <span data-ttu-id="e415c-117">式 `expression IS NOT OF (type)` および `expression IS NOT OF (ONLY type)` は、構文的にはそれぞれ `NOT (expression IS OF (type))` および `NOT (expression IS OF (ONLY type))` に相当します。</span><span class="sxs-lookup"><span data-stu-id="e415c-117">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="e415c-118">次の表に、いくつかの通常およびコーナー パターンにおける `IS OF` 演算子の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="e415c-118">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="e415c-119">すべての例外はクライアント側にスローされてから、プロバイダーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e415c-119">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="e415c-120">パターン</span><span class="sxs-lookup"><span data-stu-id="e415c-120">Pattern</span></span>|<span data-ttu-id="e415c-121">動作</span><span class="sxs-lookup"><span data-stu-id="e415c-121">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="e415c-122">null IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="e415c-122">null IS OF (EntityType)</span></span>|<span data-ttu-id="e415c-123">スロー</span><span class="sxs-lookup"><span data-stu-id="e415c-123">Throws</span></span>|  
|<span data-ttu-id="e415c-124">null IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e415c-124">null IS OF (ComplexType)</span></span>|<span data-ttu-id="e415c-125">スロー</span><span class="sxs-lookup"><span data-stu-id="e415c-125">Throws</span></span>|  
|<span data-ttu-id="e415c-126">null IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="e415c-126">null IS OF (RowType)</span></span>|<span data-ttu-id="e415c-127">スロー</span><span class="sxs-lookup"><span data-stu-id="e415c-127">Throws</span></span>|  
|<span data-ttu-id="e415c-128">TREAT (null AS EntityType) IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="e415c-128">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="e415c-129">DBNull を返します。</span><span class="sxs-lookup"><span data-stu-id="e415c-129">Returns DBNull</span></span>|  
|<span data-ttu-id="e415c-130">TREAT (null AS ComplexType) IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e415c-130">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="e415c-131">スロー</span><span class="sxs-lookup"><span data-stu-id="e415c-131">Throws</span></span>|  
|<span data-ttu-id="e415c-132">TREAT (null AS RowType) IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="e415c-132">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="e415c-133">スロー</span><span class="sxs-lookup"><span data-stu-id="e415c-133">Throws</span></span>|  
|<span data-ttu-id="e415c-134">EntityType IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="e415c-134">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="e415c-135">true または false を返します。</span><span class="sxs-lookup"><span data-stu-id="e415c-135">Returns true/false</span></span>|  
|<span data-ttu-id="e415c-136">ComplexType IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e415c-136">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="e415c-137">スロー</span><span class="sxs-lookup"><span data-stu-id="e415c-137">Throws</span></span>|  
|<span data-ttu-id="e415c-138">RowType IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="e415c-138">RowType IS OF (RowType)</span></span>|<span data-ttu-id="e415c-139">スロー</span><span class="sxs-lookup"><span data-stu-id="e415c-139">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e415c-140">例</span><span class="sxs-lookup"><span data-stu-id="e415c-140">Example</span></span>  

 <span data-ttu-id="e415c-141">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の次のクエリでは、IS OF 演算子を使用してクエリ式の型を判定し、次に TREAT 演算子を使用して Course 型のオブジェクトを OnsiteCourse 型のオブジェクトのコレクションに変換します。</span><span class="sxs-lookup"><span data-stu-id="e415c-141">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="e415c-142">このクエリは、 [School モデル](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e415c-142">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 <span data-ttu-id="e415c-143">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span><span class="sxs-lookup"><span data-stu-id="e415c-143">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e415c-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="e415c-144">See also</span></span>

- [<span data-ttu-id="e415c-145">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="e415c-145">Entity SQL Reference</span></span>](entity-sql-reference.md)
