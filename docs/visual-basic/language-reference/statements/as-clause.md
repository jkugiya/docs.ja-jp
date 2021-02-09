---
description: '詳細情報: As 句 (Visual Basic)'
title: As 句
ms.date: 07/20/2015
f1_keywords:
- vb.as
helpviewer_keywords:
- constraints, Visual Basic generic types
- As keyword [Visual Basic], statement syntax
- As keyword [Visual Basic]
ms.assetid: b4281ec8-2be5-49f7-aae8-ae0a96265b0d
ms.openlocfilehash: a8c7a3d9bcc43c817910aa330b81ffaf98980699
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674065"
---
# <a name="as-clause-visual-basic"></a><span data-ttu-id="36ae2-103">As 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36ae2-103">As Clause (Visual Basic)</span></span>

<span data-ttu-id="36ae2-104">宣言ステートメントのデータ型またはジェネリック型パラメーターの制約リストを識別する `As` 句について紹介します。</span><span class="sxs-lookup"><span data-stu-id="36ae2-104">Introduces an `As` clause, which identifies a data type in a declaration statement or a constraint list on a generic type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36ae2-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="36ae2-105">Remarks</span></span>  

 <span data-ttu-id="36ae2-106">キーワード `As` は次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="36ae2-106">The `As` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="36ae2-107">Aggregate 句</span><span class="sxs-lookup"><span data-stu-id="36ae2-107">Aggregate Clause</span></span>](../queries/aggregate-clause.md)  
  
 [<span data-ttu-id="36ae2-108">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-108">Class Statement</span></span>](class-statement.md)  
  
 [<span data-ttu-id="36ae2-109">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-109">Const Statement</span></span>](const-statement.md)  
  
 [<span data-ttu-id="36ae2-110">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-110">Declare Statement</span></span>](declare-statement.md)  
  
 [<span data-ttu-id="36ae2-111">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-111">Delegate Statement</span></span>](delegate-statement.md)  
  
 [<span data-ttu-id="36ae2-112">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-112">Dim Statement</span></span>](dim-statement.md)  
  
 [<span data-ttu-id="36ae2-113">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-113">Enum Statement</span></span>](enum-statement.md)  
  
 [<span data-ttu-id="36ae2-114">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-114">Event Statement</span></span>](event-statement.md)  
  
 [<span data-ttu-id="36ae2-115">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-115">For...Next Statements</span></span>](for-next-statement.md)  
  
 [<span data-ttu-id="36ae2-116">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-116">For Each...Next Statements</span></span>](for-each-next-statement.md)  
  
 [<span data-ttu-id="36ae2-117">From 句</span><span class="sxs-lookup"><span data-stu-id="36ae2-117">From Clause</span></span>](../queries/from-clause.md)  
  
 [<span data-ttu-id="36ae2-118">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-118">Function Statement</span></span>](function-statement.md)  
  
 [<span data-ttu-id="36ae2-119">Group Join 句</span><span class="sxs-lookup"><span data-stu-id="36ae2-119">Group Join Clause</span></span>](../queries/group-join-clause.md)  
  
 [<span data-ttu-id="36ae2-120">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-120">Interface Statement</span></span>](interface-statement.md)  
  
 [<span data-ttu-id="36ae2-121">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-121">Operator Statement</span></span>](operator-statement.md)  
  
 [<span data-ttu-id="36ae2-122">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-122">Property Statement</span></span>](property-statement.md)  
  
 [<span data-ttu-id="36ae2-123">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-123">Structure Statement</span></span>](structure-statement.md)  
  
 [<span data-ttu-id="36ae2-124">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-124">Sub Statement</span></span>](sub-statement.md)  
  
 [<span data-ttu-id="36ae2-125">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="36ae2-125">Try...Catch...Finally Statements</span></span>](try-catch-finally-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="36ae2-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="36ae2-126">See also</span></span>

- [<span data-ttu-id="36ae2-127">方法: 新しい変数を作成する</span><span class="sxs-lookup"><span data-stu-id="36ae2-127">How to: Create a New Variable</span></span>](../../programming-guide/language-features/variables/how-to-create-a-new-variable.md)
- [<span data-ttu-id="36ae2-128">データの種類</span><span class="sxs-lookup"><span data-stu-id="36ae2-128">Data Types</span></span>](../../programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="36ae2-129">変数宣言</span><span class="sxs-lookup"><span data-stu-id="36ae2-129">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="36ae2-130">型リスト</span><span class="sxs-lookup"><span data-stu-id="36ae2-130">Type List</span></span>](type-list.md)
- [<span data-ttu-id="36ae2-131">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36ae2-131">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="36ae2-132">キーワード</span><span class="sxs-lookup"><span data-stu-id="36ae2-132">Keywords</span></span>](../keywords/index.md)
