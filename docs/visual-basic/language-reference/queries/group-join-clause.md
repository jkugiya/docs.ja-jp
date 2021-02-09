---
description: '詳細情報: Group Join 句 (Visual Basic)'
title: Group Join 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 177dc2b41c923bc8c1ae0477c3905e8adad36fbe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700482"
---
# <a name="group-join-clause-visual-basic"></a><span data-ttu-id="aa99e-103">Group Join 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa99e-103">Group Join Clause (Visual Basic)</span></span>

<span data-ttu-id="aa99e-104">2 つのコレクションを、単一の階層コレクションに結合します。</span><span class="sxs-lookup"><span data-stu-id="aa99e-104">Combines two collections into a single hierarchical collection.</span></span> <span data-ttu-id="aa99e-105">結合操作は、一致するキーに基づきます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-105">The join operation is based on matching keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa99e-106">構文</span><span class="sxs-lookup"><span data-stu-id="aa99e-106">Syntax</span></span>  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="aa99e-107">指定項目</span><span class="sxs-lookup"><span data-stu-id="aa99e-107">Parts</span></span>  
  
|<span data-ttu-id="aa99e-108">用語</span><span class="sxs-lookup"><span data-stu-id="aa99e-108">Term</span></span>|<span data-ttu-id="aa99e-109">定義</span><span class="sxs-lookup"><span data-stu-id="aa99e-109">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="aa99e-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="aa99e-110">Required.</span></span> <span data-ttu-id="aa99e-111">結合されるコレクションの制御変数。</span><span class="sxs-lookup"><span data-stu-id="aa99e-111">The control variable for the collection being joined.</span></span>|  
|`type`|<span data-ttu-id="aa99e-112">任意。</span><span class="sxs-lookup"><span data-stu-id="aa99e-112">Optional.</span></span> <span data-ttu-id="aa99e-113">`element` の型。</span><span class="sxs-lookup"><span data-stu-id="aa99e-113">The type of `element`.</span></span> <span data-ttu-id="aa99e-114">`type` が指定されていない場合、`element` の型は `collection` から推論されます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="aa99e-115">必須です。</span><span class="sxs-lookup"><span data-stu-id="aa99e-115">Required.</span></span> <span data-ttu-id="aa99e-116">`Group Join` 演算子の左側にあるコレクションと結合するコレクション。</span><span class="sxs-lookup"><span data-stu-id="aa99e-116">The collection to combine with the collection that is on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="aa99e-117">`Group Join` 句は、`Join` 句、または別の `Group Join` 句で入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-117">A `Group Join` clause can be nested in a `Join` clause or in another `Group Join` clause.</span></span>|  
|<span data-ttu-id="aa99e-118">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="aa99e-118">`key1` `Equals` `key2`</span></span>|<span data-ttu-id="aa99e-119">必須です。</span><span class="sxs-lookup"><span data-stu-id="aa99e-119">Required.</span></span> <span data-ttu-id="aa99e-120">結合されるコレクションのキーを識別します。</span><span class="sxs-lookup"><span data-stu-id="aa99e-120">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="aa99e-121">`Equals` 演算子を使用して、結合されるコレクションのキーを比較する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa99e-121">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="aa99e-122">結合条件を組み合わせるには、複数のキーを識別するために、`And` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="aa99e-122">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="aa99e-123">`key1` パラメーターは、`Join` 演算子の左側にあるコレクションからのものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa99e-123">The `key1` parameter must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="aa99e-124">`key2` パラメーターは、`Join` 演算子の右側にあるコレクションからのものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa99e-124">The `key2` parameter must be from the collection on the right side of the `Join` operator.</span></span><br /><br /> <span data-ttu-id="aa99e-125">結合条件で使用されるキーは、コレクションからの複数の項目を含む式にすることができます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-125">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="aa99e-126">ただし、各キー式には、それぞれのコレクションからの項目のみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-126">However, each key expression can contain only items from its respective collection.</span></span>|  
|`expressionList`|<span data-ttu-id="aa99e-127">必須です。</span><span class="sxs-lookup"><span data-stu-id="aa99e-127">Required.</span></span> <span data-ttu-id="aa99e-128">コレクションの要素のグループを集計する方法を示す 1 つ以上の式です。</span><span class="sxs-lookup"><span data-stu-id="aa99e-128">One or more expressions that identify how the groups of elements from the collection are aggregated.</span></span> <span data-ttu-id="aa99e-129">グループ化された結果のメンバー名を特定するには、`Group` キーワード (`<alias> = Group`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="aa99e-129">To identify a member name for the grouped results, use the `Group` keyword (`<alias> = Group`).</span></span> <span data-ttu-id="aa99e-130">グループに適用する集計関数を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-130">You can also include aggregate functions to apply to the group.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa99e-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="aa99e-131">Remarks</span></span>  

 <span data-ttu-id="aa99e-132">`Group Join` 句は、結合されるコレクションからの一致するキー値に基づいて、2 つのコレクションを組み合わせます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-132">The `Group Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="aa99e-133">結果のコレクションには、最初のコレクションのキー値に一致する 2 つ目のコレクションの要素のコレクションを参照するメンバーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-133">The resulting collection can contain a member that references a collection of elements from the second collection that match the key value from the first collection.</span></span> <span data-ttu-id="aa99e-134">さらに、2 つ目のコレクションのグループ化された要素に適用する集計関数を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-134">You can also specify aggregate functions to apply to the grouped elements from the second collection.</span></span> <span data-ttu-id="aa99e-135">集計関数の詳細については、「[Aggregate 句 ](aggregate-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa99e-135">For information about aggregate functions, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="aa99e-136">たとえば、マネージャーのコレクションと従業員のコレクションを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="aa99e-136">Consider, for example, a collection of managers and a collection of employees.</span></span> <span data-ttu-id="aa99e-137">両方のコレクションの要素には、特定のマネージャーに報告する従業員を識別する ManagerID プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="aa99e-137">Elements from both collections have a ManagerID property that identifies the employees that report to a particular manager.</span></span> <span data-ttu-id="aa99e-138">結合操作の結果には、一致する ManagerID 値を持つ各マネージャーと従業員の結果が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-138">The results from a join operation would contain a result for each manager and employee with a matching ManagerID value.</span></span> <span data-ttu-id="aa99e-139">`Group Join` 操作の結果には、マネージャーの完全な一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-139">The results from a `Group Join` operation would contain the complete list of managers.</span></span> <span data-ttu-id="aa99e-140">各マネージャーの結果には、特定のマネージャーに一致した従業員の一覧を参照したメンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-140">Each manager result would have a member that referenced the list of employees that were a match for the specific manager.</span></span>  
  
 <span data-ttu-id="aa99e-141">`Group Join` 操作の結果のコレクションには、`From` 句に指定されたコレクションと `Group Join` 句の `Into` 句に指定された式からの値の任意の組み合わせが含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aa99e-141">The collection resulting from a `Group Join` operation can contain any combination of values from the collection identified in the `From` clause and the expressions identified in the `Into` clause of the `Group Join` clause.</span></span> <span data-ttu-id="aa99e-142">`Into` 句の有効な式の詳細については、「[Aggregate 句](aggregate-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa99e-142">For more information about valid expressions for the `Into` clause, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="aa99e-143">`Group Join` 操作では、`Group Join` 演算子の左側に指定されたコレクションからのすべての結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-143">A `Group Join` operation will return all results from the collection identified on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="aa99e-144">これは、結合されているコレクションに一致するものがない場合でも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="aa99e-144">This is true even if there are no matches in the collection being joined.</span></span> <span data-ttu-id="aa99e-145">これは、SQL の `LEFT OUTER JOIN` に似ています。</span><span class="sxs-lookup"><span data-stu-id="aa99e-145">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="aa99e-146">`Join` 句を使用して、コレクションを単一のコレクションに結合することができます。</span><span class="sxs-lookup"><span data-stu-id="aa99e-146">You can use the `Join` clause to combine collections into a single collection.</span></span> <span data-ttu-id="aa99e-147">これは、SQL の `INNER JOIN` と同じです。</span><span class="sxs-lookup"><span data-stu-id="aa99e-147">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa99e-148">例</span><span class="sxs-lookup"><span data-stu-id="aa99e-148">Example</span></span>  

 <span data-ttu-id="aa99e-149">次のコード例では、`Group Join` 句を使用して 2 つのコレクションを結合しています。</span><span class="sxs-lookup"><span data-stu-id="aa99e-149">The following code example joins two collections by using the `Group Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="aa99e-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa99e-150">See also</span></span>

- [<span data-ttu-id="aa99e-151">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="aa99e-151">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="aa99e-152">クエリ</span><span class="sxs-lookup"><span data-stu-id="aa99e-152">Queries</span></span>](index.md)
- [<span data-ttu-id="aa99e-153">Select 句</span><span class="sxs-lookup"><span data-stu-id="aa99e-153">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="aa99e-154">From 句</span><span class="sxs-lookup"><span data-stu-id="aa99e-154">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="aa99e-155">Join 句</span><span class="sxs-lookup"><span data-stu-id="aa99e-155">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="aa99e-156">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="aa99e-156">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="aa99e-157">Group By 句</span><span class="sxs-lookup"><span data-stu-id="aa99e-157">Group By Clause</span></span>](group-by-clause.md)
