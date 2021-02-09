---
description: '詳細情報: Let 句 (Visual Basic)'
title: Let 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 88a7d96bb790a1e6ec5adfa4337c51f807930168
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653642"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="63062-103">Let 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63062-103">Let Clause (Visual Basic)</span></span>

<span data-ttu-id="63062-104">値を計算し、その値をクエリ内の新しい変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="63062-104">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63062-105">構文</span><span class="sxs-lookup"><span data-stu-id="63062-105">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="63062-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="63062-106">Parts</span></span>  
  
|<span data-ttu-id="63062-107">用語</span><span class="sxs-lookup"><span data-stu-id="63062-107">Term</span></span>|<span data-ttu-id="63062-108">定義</span><span class="sxs-lookup"><span data-stu-id="63062-108">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="63062-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="63062-109">Required.</span></span> <span data-ttu-id="63062-110">指定された式の結果を参照するために使用できる別名。</span><span class="sxs-lookup"><span data-stu-id="63062-110">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="63062-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="63062-111">Required.</span></span> <span data-ttu-id="63062-112">評価され、指定された変数に割り当てられる式。</span><span class="sxs-lookup"><span data-stu-id="63062-112">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63062-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="63062-113">Remarks</span></span>  

 <span data-ttu-id="63062-114">`Let` 句を使用すると、各クエリ結果の値を計算し、別名を使用してその値を参照できます。</span><span class="sxs-lookup"><span data-stu-id="63062-114">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="63062-115">別名は、`Where` 句などの他の句で使用できます。</span><span class="sxs-lookup"><span data-stu-id="63062-115">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="63062-116">`Let` 句を使用すると、クエリに含まれる式の句の別名を指定し、その式の句が使用されるたびに別名を置き換えることができるため、読みやすいクエリ ステートメントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="63062-116">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="63062-117">`Let` 句には、任意の数の `variable` と `expression` の代入を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="63062-117">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="63062-118">各代入はコンマ (,) で区切ります。</span><span class="sxs-lookup"><span data-stu-id="63062-118">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63062-119">例</span><span class="sxs-lookup"><span data-stu-id="63062-119">Example</span></span>  

 <span data-ttu-id="63062-120">次のコード例では、`Let` 句を使用して、製品に対して 10% の割引を計算します。</span><span class="sxs-lookup"><span data-stu-id="63062-120">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="63062-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="63062-121">See also</span></span>

- [<span data-ttu-id="63062-122">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="63062-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="63062-123">クエリ</span><span class="sxs-lookup"><span data-stu-id="63062-123">Queries</span></span>](index.md)
- [<span data-ttu-id="63062-124">Select 句</span><span class="sxs-lookup"><span data-stu-id="63062-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="63062-125">From 句</span><span class="sxs-lookup"><span data-stu-id="63062-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="63062-126">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="63062-126">Where Clause</span></span>](where-clause.md)
