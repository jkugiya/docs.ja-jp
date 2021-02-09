---
description: '詳細情報: Where 句 (Visual Basic)'
title: Where 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 11f9a7e586a1fdea826df4fb34a7227747c8cebd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730318"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="4fe21-103">Where 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fe21-103">Where Clause (Visual Basic)</span></span>

<span data-ttu-id="4fe21-104">クエリのフィルター処理条件を示します。</span><span class="sxs-lookup"><span data-stu-id="4fe21-104">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe21-105">構文</span><span class="sxs-lookup"><span data-stu-id="4fe21-105">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="4fe21-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="4fe21-106">Parts</span></span>  

 `condition`  
 <span data-ttu-id="4fe21-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="4fe21-107">Required.</span></span> <span data-ttu-id="4fe21-108">コレクション内の現在の項目の値が出力コレクションに含まれるかどうかを決定する式。</span><span class="sxs-lookup"><span data-stu-id="4fe21-108">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="4fe21-109">式は、`Boolean` 値または `Boolean` 値と等価の値に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fe21-109">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="4fe21-110">条件が `True` に評価される場合、要素はクエリ結果に含まれます。それ以外の場合、要素はクエリ結果から除外されます。</span><span class="sxs-lookup"><span data-stu-id="4fe21-110">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fe21-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="4fe21-111">Remarks</span></span>  

 <span data-ttu-id="4fe21-112">`Where` 句を使用すると、特定の条件を満たす要素のみを選択することで、クエリ データをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="4fe21-112">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="4fe21-113">値が `Where` 句を `True` に評価させる要素は、クエリ結果に含まれます。その他の要素は除外されます。</span><span class="sxs-lookup"><span data-stu-id="4fe21-113">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="4fe21-114">`Where` 句で使用される式は、`Boolean` または `Boolean` と等価 (値が 0 の場合に `False` に評価される整数など) に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fe21-114">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="4fe21-115">`Where` 句では、`And`、`Or`、`AndAlso`、`OrElse`、`Is`、`IsNot` などの論理演算子を使用して、複数の式を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="4fe21-115">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="4fe21-116">既定では、クエリ式は、アクセスされるまで評価されません。たとえば、データ バインドされたり、`For` ループ内で反復処理されたりするときです。</span><span class="sxs-lookup"><span data-stu-id="4fe21-116">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="4fe21-117">その結果、`Where` 句は、クエリがアクセスされるまで評価されません。</span><span class="sxs-lookup"><span data-stu-id="4fe21-117">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="4fe21-118">`Where` 句で使用されているクエリの外部の値がある場合は、クエリの実行時に `Where` 句で適切な値が使用されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4fe21-118">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="4fe21-119">クエリの実行の詳細については、「[初めての LINQ クエリの作成](../../programming-guide/concepts/linq/writing-your-first-linq-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fe21-119">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="4fe21-120">`Where` 句内で関数を呼び出して、コレクション内の現在の要素の値に対して計算または操作を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="4fe21-120">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="4fe21-121">`Where` 句で関数を呼び出すと、クエリを、アクセス時ではなく定義された直後に実行することができます。</span><span class="sxs-lookup"><span data-stu-id="4fe21-121">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="4fe21-122">クエリの実行の詳細については、「[初めての LINQ クエリの作成](../../programming-guide/concepts/linq/writing-your-first-linq-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fe21-122">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fe21-123">例</span><span class="sxs-lookup"><span data-stu-id="4fe21-123">Example</span></span>  

 <span data-ttu-id="4fe21-124">次のクエリ式では、`From` 句を使用して、`customers` コレクション内の各 `Customer` オブジェクトに対して `cust` 範囲変数を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="4fe21-124">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="4fe21-125">`Where` 句では、範囲変数を使用して、指定した地域の顧客に出力を制限します。</span><span class="sxs-lookup"><span data-stu-id="4fe21-125">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="4fe21-126">`For Each` ループによって、クエリ結果に各顧客の会社名を表示します。</span><span class="sxs-lookup"><span data-stu-id="4fe21-126">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="4fe21-127">例</span><span class="sxs-lookup"><span data-stu-id="4fe21-127">Example</span></span>  

 <span data-ttu-id="4fe21-128">次の例では、`Where` 句で `And` および `Or` 論理演算子を使用しています。</span><span class="sxs-lookup"><span data-stu-id="4fe21-128">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="4fe21-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fe21-129">See also</span></span>

- [<span data-ttu-id="4fe21-130">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="4fe21-130">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4fe21-131">クエリ</span><span class="sxs-lookup"><span data-stu-id="4fe21-131">Queries</span></span>](index.md)
- [<span data-ttu-id="4fe21-132">From 句</span><span class="sxs-lookup"><span data-stu-id="4fe21-132">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="4fe21-133">Select 句</span><span class="sxs-lookup"><span data-stu-id="4fe21-133">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="4fe21-134">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="4fe21-134">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
