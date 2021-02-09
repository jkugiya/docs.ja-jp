---
description: '詳細情報: Order By 句 (Visual Basic)'
title: Order By 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: b5e7cc93b11393ef2f256e90e402975fbf6633a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653616"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="3f56a-103">Order By 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f56a-103">Order By Clause (Visual Basic)</span></span>

<span data-ttu-id="3f56a-104">クエリ結果の並べ替え順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f56a-104">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f56a-105">構文</span><span class="sxs-lookup"><span data-stu-id="3f56a-105">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="3f56a-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="3f56a-106">Parts</span></span>  

 `orderExp1`  
 <span data-ttu-id="3f56a-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="3f56a-107">Required.</span></span> <span data-ttu-id="3f56a-108">返される値の順序付け方法を示す、現在のクエリ結果の 1 つまたは複数のフィールド。</span><span class="sxs-lookup"><span data-stu-id="3f56a-108">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="3f56a-109">フィールド名は、コンマ (,) で区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f56a-109">The field names must be separated by commas (,).</span></span> <span data-ttu-id="3f56a-110">`Ascending` または `Descending` キーワードを使用して、昇順または降順で並べ替えて各フィールドを識別できます。</span><span class="sxs-lookup"><span data-stu-id="3f56a-110">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="3f56a-111">`Ascending` または `Descending` キーワードが指定されていない場合、既定の並べ替え順序は昇順です。</span><span class="sxs-lookup"><span data-stu-id="3f56a-111">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="3f56a-112">並べ替え順序のフィールドは、左から右に優先されます。</span><span class="sxs-lookup"><span data-stu-id="3f56a-112">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f56a-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="3f56a-113">Remarks</span></span>  

 <span data-ttu-id="3f56a-114">`Order By` 句を使用して、クエリの結果を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="3f56a-114">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="3f56a-115">`Order By` 句では、現在のスコープの範囲変数に基づいてのみ結果を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="3f56a-115">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="3f56a-116">たとえば、`Select` 句では、クエリ式に新しいスコープを導入し、そのスコープの新しい繰り返し変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f56a-116">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="3f56a-117">クエリ内の `Select` 句の前に定義された範囲変数は、`Select` 句の後では使用できません。</span><span class="sxs-lookup"><span data-stu-id="3f56a-117">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="3f56a-118">そのため、`Select` 句で使用できないフィールドで結果を並べ替える場合は、`Order By` 句を `Select` 句の前に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f56a-118">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="3f56a-119">これを行う必要がある場合の 1 つの例は、結果の一部として返されないフィールドによってクエリを並べ替える場合です。</span><span class="sxs-lookup"><span data-stu-id="3f56a-119">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="3f56a-120">フィールドの昇順と降順の順序は、フィールドのデータ型の <xref:System.IComparable> インターフェイスの実装によって決まります。</span><span class="sxs-lookup"><span data-stu-id="3f56a-120">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="3f56a-121">データ型で <xref:System.IComparable> インターフェイスを実装していない場合、並べ替え順序は無視されます。</span><span class="sxs-lookup"><span data-stu-id="3f56a-121">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f56a-122">例</span><span class="sxs-lookup"><span data-stu-id="3f56a-122">Example</span></span>  

 <span data-ttu-id="3f56a-123">次のクエリ式では、`From` 句を使用して、`books` コレクションに対して `book` 範囲変数を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="3f56a-123">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="3f56a-124">`Order By` 句によって、クエリの結果を価格の昇順で並べ替えます (既定値)。</span><span class="sxs-lookup"><span data-stu-id="3f56a-124">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="3f56a-125">同じ価格の書籍は、タイトルの昇順で並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="3f56a-125">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="3f56a-126">`Select` 句によって、クエリで返される値として `Title` および `Price` プロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="3f56a-126">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="3f56a-127">例</span><span class="sxs-lookup"><span data-stu-id="3f56a-127">Example</span></span>  

 <span data-ttu-id="3f56a-128">次のクエリ式では、`Order By` 句を使用して、クエリ結果を価格の降順で並べ替えています。</span><span class="sxs-lookup"><span data-stu-id="3f56a-128">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="3f56a-129">同じ価格の書籍は、タイトルの昇順で並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="3f56a-129">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="3f56a-130">例</span><span class="sxs-lookup"><span data-stu-id="3f56a-130">Example</span></span>  

 <span data-ttu-id="3f56a-131">次のクエリ式では、`Select` 句を使用して、書籍のタイトル、価格、発行日、および作者を選択しています。</span><span class="sxs-lookup"><span data-stu-id="3f56a-131">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="3f56a-132">次に、新しいスコープの範囲変数の `Title`、`Price`、`PublishDate`、および `Author` の各フィールドを設定します。</span><span class="sxs-lookup"><span data-stu-id="3f56a-132">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="3f56a-133">`Order By` 句によって、作成者名、書籍のタイトル、さらに価格で新しい範囲変数を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="3f56a-133">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="3f56a-134">各列を、既定の順序 (昇順) で並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="3f56a-134">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="3f56a-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f56a-135">See also</span></span>

- [<span data-ttu-id="3f56a-136">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="3f56a-136">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3f56a-137">クエリ</span><span class="sxs-lookup"><span data-stu-id="3f56a-137">Queries</span></span>](index.md)
- [<span data-ttu-id="3f56a-138">Select 句</span><span class="sxs-lookup"><span data-stu-id="3f56a-138">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="3f56a-139">From 句</span><span class="sxs-lookup"><span data-stu-id="3f56a-139">From Clause</span></span>](from-clause.md)
