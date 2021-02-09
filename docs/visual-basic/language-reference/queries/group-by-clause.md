---
description: '詳細情報: Group By 句 (Visual Basic)'
title: Group By 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: f5cfb76b0f4b1d191f959ae1812140c6872e93bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700508"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="125f5-103">Group By 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="125f5-103">Group By Clause (Visual Basic)</span></span>

<span data-ttu-id="125f5-104">クエリ結果の要素をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="125f5-104">Groups the elements of a query result.</span></span> <span data-ttu-id="125f5-105">これを使用して、グループごとに集計関数を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="125f5-105">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="125f5-106">グループ化操作は、1 つ以上のキーに基づきます。</span><span class="sxs-lookup"><span data-stu-id="125f5-106">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="125f5-107">構文</span><span class="sxs-lookup"><span data-stu-id="125f5-107">Syntax</span></span>  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="125f5-108">指定項目</span><span class="sxs-lookup"><span data-stu-id="125f5-108">Parts</span></span>  
  
- <span data-ttu-id="125f5-109">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="125f5-109">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="125f5-110">任意。</span><span class="sxs-lookup"><span data-stu-id="125f5-110">Optional.</span></span> <span data-ttu-id="125f5-111">グループ化された結果に含めるフィールドを明示的に示す、クエリ変数の 1 つ以上のフィールドです。</span><span class="sxs-lookup"><span data-stu-id="125f5-111">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="125f5-112">フィールドを指定しない場合、グループ化された結果にはクエリ変数のすべてのフィールドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="125f5-112">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="125f5-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="125f5-113">Required.</span></span> <span data-ttu-id="125f5-114">要素のグループを決定するために使用するキーを識別する式です。</span><span class="sxs-lookup"><span data-stu-id="125f5-114">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="125f5-115">複数のキーを指定して、複合キーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="125f5-115">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="125f5-116">任意。</span><span class="sxs-lookup"><span data-stu-id="125f5-116">Optional.</span></span> <span data-ttu-id="125f5-117">`keyExp1` と結合して複合キーを作成する 1 つ以上の追加キーです。</span><span class="sxs-lookup"><span data-stu-id="125f5-117">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="125f5-118">必須です。</span><span class="sxs-lookup"><span data-stu-id="125f5-118">Required.</span></span> <span data-ttu-id="125f5-119">グループの集計方法を示す 1 つ以上の式です。</span><span class="sxs-lookup"><span data-stu-id="125f5-119">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="125f5-120">グループ化された結果のメンバー名を示すには、次のいずれかの形式で、 `Group` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="125f5-120">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```vb  
    Into Group  
    ```  
  
     <span data-ttu-id="125f5-121">\- または -</span><span class="sxs-lookup"><span data-stu-id="125f5-121">-or-</span></span>  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="125f5-122">グループに適用する集計関数を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="125f5-122">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="125f5-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="125f5-123">Remarks</span></span>  

 <span data-ttu-id="125f5-124">`Group By` 句を使用して、クエリの結果をグループに分割できます。</span><span class="sxs-lookup"><span data-stu-id="125f5-124">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="125f5-125">グループ化は、1 つのキー、または複数のキーで構成される複合キーに基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="125f5-125">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="125f5-126">一致するキー値と関連付けられた要素は、同じグループに入れられます。</span><span class="sxs-lookup"><span data-stu-id="125f5-126">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="125f5-127">グループの参照に使用するメンバー名を示すには、 `aggregateList` 句の `Into` パラメーターと `Group` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="125f5-127">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="125f5-128">`Into` 句に集計関数を含めることで、グループ化された要素の値を計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="125f5-128">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="125f5-129">標準的な集計関数の一覧については、「 [Aggregate Clause](aggregate-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="125f5-129">For a list of standard aggregate functions, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="125f5-130">例</span><span class="sxs-lookup"><span data-stu-id="125f5-130">Example</span></span>  

 <span data-ttu-id="125f5-131">以下のコード例では、場所 (国/地域) に基づいて顧客の一覧をグループ化し、各グループ内の顧客の数を返します。</span><span class="sxs-lookup"><span data-stu-id="125f5-131">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span></span> <span data-ttu-id="125f5-132">結果は、国/地域名によって並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="125f5-132">The results are ordered by country/region name.</span></span> <span data-ttu-id="125f5-133">グループ化した結果は、市区町村名によって並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="125f5-133">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="125f5-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="125f5-134">See also</span></span>

- [<span data-ttu-id="125f5-135">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="125f5-135">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="125f5-136">クエリ</span><span class="sxs-lookup"><span data-stu-id="125f5-136">Queries</span></span>](index.md)
- [<span data-ttu-id="125f5-137">Select 句</span><span class="sxs-lookup"><span data-stu-id="125f5-137">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="125f5-138">From 句</span><span class="sxs-lookup"><span data-stu-id="125f5-138">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="125f5-139">Order By 句</span><span class="sxs-lookup"><span data-stu-id="125f5-139">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="125f5-140">Aggregate 句</span><span class="sxs-lookup"><span data-stu-id="125f5-140">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="125f5-141">Group Join 句</span><span class="sxs-lookup"><span data-stu-id="125f5-141">Group Join Clause</span></span>](group-join-clause.md)
