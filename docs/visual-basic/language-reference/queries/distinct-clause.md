---
description: '詳細情報: Distinct 句 (Visual Basic)'
title: Distinct 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: df1cdc58f7af406533e67a396a958a26b0c79635
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700651"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="7b6a8-103">Distinct 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b6a8-103">Distinct Clause (Visual Basic)</span></span>

<span data-ttu-id="7b6a8-104">現在の範囲変数の値を制限して、後続のクエリ結果内で重複する値を除去します。</span><span class="sxs-lookup"><span data-stu-id="7b6a8-104">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b6a8-105">構文</span><span class="sxs-lookup"><span data-stu-id="7b6a8-105">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="7b6a8-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="7b6a8-106">Remarks</span></span>  

 <span data-ttu-id="7b6a8-107">`Distinct` 句を使用して、一意の項目の一覧を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="7b6a8-107">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="7b6a8-108">`Distinct` 句によって、クエリで重複するクエリ結果を無視させます。</span><span class="sxs-lookup"><span data-stu-id="7b6a8-108">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="7b6a8-109">`Distinct` 句は、`Select` 句で指定されたすべての戻りフィールドの重複する値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7b6a8-109">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="7b6a8-110">`Select` 句が指定されていない場合、`Distinct` 句は `From` 句で識別されたクエリの範囲変数に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7b6a8-110">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="7b6a8-111">範囲変数が変更できない型である場合、クエリでは、その型のすべてのメンバーが既存のクエリの結果と一致する場合にのみ、クエリの結果が無視されます。</span><span class="sxs-lookup"><span data-stu-id="7b6a8-111">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b6a8-112">例</span><span class="sxs-lookup"><span data-stu-id="7b6a8-112">Example</span></span>  

 <span data-ttu-id="7b6a8-113">次のクエリ式では、顧客の一覧と顧客の注文の一覧が結合されます。</span><span class="sxs-lookup"><span data-stu-id="7b6a8-113">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="7b6a8-114">一意の顧客名と注文日の一覧を返すために、`Distinct` 句が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7b6a8-114">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="7b6a8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b6a8-115">See also</span></span>

- [<span data-ttu-id="7b6a8-116">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="7b6a8-116">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="7b6a8-117">クエリ</span><span class="sxs-lookup"><span data-stu-id="7b6a8-117">Queries</span></span>](index.md)
- [<span data-ttu-id="7b6a8-118">From 句</span><span class="sxs-lookup"><span data-stu-id="7b6a8-118">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="7b6a8-119">Select 句</span><span class="sxs-lookup"><span data-stu-id="7b6a8-119">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="7b6a8-120">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="7b6a8-120">Where Clause</span></span>](where-clause.md)
