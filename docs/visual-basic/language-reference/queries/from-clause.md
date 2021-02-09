---
description: '詳細情報: From 句 (Visual Basic)'
title: From 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: e35188412deb7fd9f2d8306c85057d050a60d030
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700560"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="d2b3b-103">From 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2b3b-103">From Clause (Visual Basic)</span></span>

<span data-ttu-id="d2b3b-104">クエリを実行する 1 つ以上の範囲変数とコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-104">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2b3b-105">構文</span><span class="sxs-lookup"><span data-stu-id="d2b3b-105">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d2b3b-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="d2b3b-106">Parts</span></span>  
  
|<span data-ttu-id="d2b3b-107">用語</span><span class="sxs-lookup"><span data-stu-id="d2b3b-107">Term</span></span>|<span data-ttu-id="d2b3b-108">定義</span><span class="sxs-lookup"><span data-stu-id="d2b3b-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="d2b3b-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-109">Required.</span></span> <span data-ttu-id="d2b3b-110">コレクションの要素の反復処理に使用される *範囲変数*。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-110">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="d2b3b-111">範囲変数は、クエリによって `collection` を反復処理するときに、`collection` の各メンバーを参照するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-111">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="d2b3b-112">列挙可能な型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-112">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="d2b3b-113">任意。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-113">Optional.</span></span> <span data-ttu-id="d2b3b-114">`element` の型。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-114">The type of `element`.</span></span> <span data-ttu-id="d2b3b-115">`type` が指定されていない場合、`element` の型は `collection` から推論されます。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-115">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="d2b3b-116">必須です。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-116">Required.</span></span> <span data-ttu-id="d2b3b-117">クエリ対象のコレクションを参照します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-117">Refers to the collection to be queried.</span></span> <span data-ttu-id="d2b3b-118">列挙可能な型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-118">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2b3b-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="d2b3b-119">Remarks</span></span>  

 <span data-ttu-id="d2b3b-120">`From` 句は、クエリのソース データと、ソース コレクションの要素を参照するために使用される変数を識別するために使用します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-120">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="d2b3b-121">このような変数は *範囲変数* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-121">These variables are called *range variables*.</span></span> <span data-ttu-id="d2b3b-122">`Aggregate` 句を使用して、集計結果のみを返すクエリを識別する場合を除き、クエリには `From` 句が必要です。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-122">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="d2b3b-123">詳細については、「[Aggregate 句](aggregate-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-123">For more information, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="d2b3b-124">クエリで複数の `From` 句を指定して、結合する複数のコレクションを識別できます。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-124">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="d2b3b-125">複数のコレクションを指定している場合、それらは個別に反復処理するか、またはそれらが関連付けられている場合は結合できます。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-125">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="d2b3b-126">コレクションは、`Select` 句を使用して暗黙的に結合することも、`Join` または `Group Join` 句を使用して明示的に結合することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-126">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="d2b3b-127">または、1 つの `From` 句で、関連する各範囲変数とコレクションをそれぞれコンマで区切って、複数の範囲変数とコレクションを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-127">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="d2b3b-128">次のコード例に、`From` 句の両方の構文オプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-128">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="d2b3b-129">`From` 句は、クエリのスコープを定義します。これは、`For` ループのスコープに似ています。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-129">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="d2b3b-130">そのため、クエリのスコープ内の各 `element` 範囲変数には、一意の名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-130">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="d2b3b-131">クエリに対して複数の `From` 句を指定できるので、後続の `From` 句で `From` 句内の範囲変数を参照できます。または、前の `From` 句内の範囲変数を参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-131">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="d2b3b-132">たとえば、次の例は、入れ子になった `From` 句を示しています。2 つ目の句のコレクションは、最初の句の範囲変数のプロパティに基づいています。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-132">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="d2b3b-133">各 `From` 句の後に、追加のクエリ句の任意の組み合わせを指定して、クエリを絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-133">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="d2b3b-134">クエリは、次の方法で絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-134">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="d2b3b-135">`From` 句と `Select` 句を使用して暗黙的に、または `Join` 句または `Group Join` 句を使用して明示的に、複数のコレクションを結合します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-135">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="d2b3b-136">`Where` 句を使用して、クエリ結果をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-136">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="d2b3b-137">`Order By` 句を使用して、結果を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-137">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="d2b3b-138">`Group By` 句を使用して、類似した結果をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-138">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="d2b3b-139">`Aggregate` 句を使用して、クエリ結果全体を評価する集計関数を特定します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-139">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="d2b3b-140">`Let` 句を使用して、コレクションではなく式によって値が決定される反復変数を導入します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-140">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="d2b3b-141">`Distinct` 句を使用して、重複するクエリ結果を無視します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-141">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="d2b3b-142">`Skip`、`Take`、`Skip While`、および `Take While` 句を使用して、返される結果の部分を特定します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-142">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2b3b-143">例</span><span class="sxs-lookup"><span data-stu-id="d2b3b-143">Example</span></span>  

 <span data-ttu-id="d2b3b-144">次のクエリ式では、`From` 句を使用して、`customers` コレクション内の各 `Customer` オブジェクトに対して `cust` 範囲変数を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-144">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="d2b3b-145">`Where` 句では、範囲変数を使用して、指定した地域の顧客に出力を制限します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-145">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="d2b3b-146">`For Each` ループによって、クエリ結果に各顧客の会社名を表示します。</span><span class="sxs-lookup"><span data-stu-id="d2b3b-146">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="d2b3b-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2b3b-147">See also</span></span>

- [<span data-ttu-id="d2b3b-148">クエリ</span><span class="sxs-lookup"><span data-stu-id="d2b3b-148">Queries</span></span>](index.md)
- [<span data-ttu-id="d2b3b-149">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="d2b3b-149">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d2b3b-150">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="d2b3b-150">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="d2b3b-151">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="d2b3b-151">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="d2b3b-152">Select 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-152">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="d2b3b-153">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-153">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="d2b3b-154">Aggregate 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-154">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="d2b3b-155">Distinct 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-155">Distinct Clause</span></span>](distinct-clause.md)
- [<span data-ttu-id="d2b3b-156">Join 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-156">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="d2b3b-157">Group Join 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-157">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="d2b3b-158">Order By 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-158">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="d2b3b-159">Let 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-159">Let Clause</span></span>](let-clause.md)
- [<span data-ttu-id="d2b3b-160">Skip 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-160">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="d2b3b-161">Take 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-161">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="d2b3b-162">Skip While 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-162">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="d2b3b-163">Take While 句</span><span class="sxs-lookup"><span data-stu-id="d2b3b-163">Take While Clause</span></span>](take-while-clause.md)
