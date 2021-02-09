---
description: '詳細情報: Take While 句 (Visual Basic)'
title: Take While 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: a413223d4a85670c66f71e24addb92ae4d38a4a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719709"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="25098-103">Take While 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25098-103">Take While Clause (Visual Basic)</span></span>

<span data-ttu-id="25098-104">指定された条件が `true` である限り、コレクションの要素を含むようにし、残りの要素をバイパスします。</span><span class="sxs-lookup"><span data-stu-id="25098-104">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25098-105">構文</span><span class="sxs-lookup"><span data-stu-id="25098-105">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="25098-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="25098-106">Parts</span></span>  
  
|<span data-ttu-id="25098-107">用語</span><span class="sxs-lookup"><span data-stu-id="25098-107">Term</span></span>|<span data-ttu-id="25098-108">定義</span><span class="sxs-lookup"><span data-stu-id="25098-108">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="25098-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="25098-109">Required.</span></span> <span data-ttu-id="25098-110">次の要素をテストするための条件を表す式。</span><span class="sxs-lookup"><span data-stu-id="25098-110">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="25098-111">式は、`Boolean` 値または同等の機能 (`Boolean` として評価される `Integer` など) を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="25098-111">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25098-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="25098-112">Remarks</span></span>  

 <span data-ttu-id="25098-113">`Take While` 句には、クエリ結果の先頭から、指定された `expression` で `false` が返されるまでの要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="25098-113">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="25098-114">`expression` が `false` を返すと、クエリでは残りのすべての要素がバイパスされます。</span><span class="sxs-lookup"><span data-stu-id="25098-114">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="25098-115">残りの結果に対して、`expression` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="25098-115">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="25098-116">`Take While` 句は、`Where` 句を使用して、特定の条件を満たすクエリからのすべての要素を含めることができるという点で、`Where` 句と異なります。</span><span class="sxs-lookup"><span data-stu-id="25098-116">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="25098-117">`Take While` 句には、初めて条件が満たされなくなったときまでの要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="25098-117">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="25098-118">`Take While` 句は、順序付けされたクエリ結果を操作する場合に最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="25098-118">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25098-119">例</span><span class="sxs-lookup"><span data-stu-id="25098-119">Example</span></span>  

 <span data-ttu-id="25098-120">次のコード例では、`Take While` 句を使用して、注文がない最初の顧客が見つかるまで結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="25098-120">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="25098-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="25098-121">See also</span></span>

- [<span data-ttu-id="25098-122">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="25098-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="25098-123">クエリ</span><span class="sxs-lookup"><span data-stu-id="25098-123">Queries</span></span>](index.md)
- [<span data-ttu-id="25098-124">Select 句</span><span class="sxs-lookup"><span data-stu-id="25098-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="25098-125">From 句</span><span class="sxs-lookup"><span data-stu-id="25098-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="25098-126">Take 句</span><span class="sxs-lookup"><span data-stu-id="25098-126">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="25098-127">Skip While 句</span><span class="sxs-lookup"><span data-stu-id="25098-127">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="25098-128">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="25098-128">Where Clause</span></span>](where-clause.md)
