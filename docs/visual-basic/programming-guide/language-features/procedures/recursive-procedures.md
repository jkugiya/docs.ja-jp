---
description: '詳細情報: 再帰プロシージャ (Visual Basic)'
title: 再帰プロシージャ
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: 378b279a6664cd494fb2e26ff3276afcea56cc16
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466563"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="2190a-103">再帰プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2190a-103">Recursive Procedures (Visual Basic)</span></span>

<span data-ttu-id="2190a-104">"*再帰*" プロシージャとは、自身を呼び出すプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2190a-104">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="2190a-105">一般に、これは Visual Basic コードを記述する最も効果的な方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="2190a-105">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="2190a-106">次のプロシージャでは、再帰を使用して元の引数の階乗を計算します。</span><span class="sxs-lookup"><span data-stu-id="2190a-106">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="2190a-107">再帰プロシージャに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="2190a-107">Considerations with Recursive Procedures</span></span>

 <span data-ttu-id="2190a-108">**制限条件**。</span><span class="sxs-lookup"><span data-stu-id="2190a-108">**Limiting Conditions**.</span></span> <span data-ttu-id="2190a-109">再帰を終了できる条件を少なくとも 1 つはテストするように、再帰プロシージャを設計する必要があります。また、妥当な回数の再帰呼び出しでそのような条件が満たされない場合の処理も必要となります。</span><span class="sxs-lookup"><span data-stu-id="2190a-109">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="2190a-110">必ず満たすことができる条件が少なくとも 1 つはないと、プロシージャが無限ループで実行されるリスクが高くなります。</span><span class="sxs-lookup"><span data-stu-id="2190a-110">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>

 <span data-ttu-id="2190a-111">**メモリ使用状況**。</span><span class="sxs-lookup"><span data-stu-id="2190a-111">**Memory Usage**.</span></span> <span data-ttu-id="2190a-112">アプリケーションがローカル変数に使用できる領域は限られています。</span><span class="sxs-lookup"><span data-stu-id="2190a-112">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="2190a-113">プロシージャが自身を呼び出すたびに、ローカル変数のコピーが追加され、その領域が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2190a-113">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="2190a-114">このプロセスが無期限に続行されると、最終的に <xref:System.StackOverflowException> エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="2190a-114">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>

 <span data-ttu-id="2190a-115">**効率**。</span><span class="sxs-lookup"><span data-stu-id="2190a-115">**Efficiency**.</span></span> <span data-ttu-id="2190a-116">ほとんどの場合、再帰の代わりにループを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2190a-116">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="2190a-117">ループには、引数を渡し、追加のストレージを初期化して、値を返すというオーバーヘッドはありません。</span><span class="sxs-lookup"><span data-stu-id="2190a-117">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="2190a-118">再帰呼び出しがない場合、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="2190a-118">Your performance can be much better without recursive calls.</span></span>

 <span data-ttu-id="2190a-119">**相互再帰**。</span><span class="sxs-lookup"><span data-stu-id="2190a-119">**Mutual Recursion**.</span></span> <span data-ttu-id="2190a-120">2 つのプロシージャが相互に呼び出し合うと、パフォーマンスが大幅に低下したり、無限ループが発生したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2190a-120">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="2190a-121">このような設計では、単一の再帰プロシージャと同じ問題が発生しますが、検出とデバッグがより困難になることがあります。</span><span class="sxs-lookup"><span data-stu-id="2190a-121">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>

 <span data-ttu-id="2190a-122">**かっこを使用した呼び出し**。</span><span class="sxs-lookup"><span data-stu-id="2190a-122">**Calling with Parentheses**.</span></span> <span data-ttu-id="2190a-123">`Function` プロシージャが自身を再帰的に呼び出すときには、引数リストがない場合でも、プロシージャ名の後にかっこを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2190a-123">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="2190a-124">そうしないと、関数名が関数の戻り値を表していると見なされます。</span><span class="sxs-lookup"><span data-stu-id="2190a-124">Otherwise, the function name is taken as representing the return value of the function.</span></span>

 <span data-ttu-id="2190a-125">**テスト**。</span><span class="sxs-lookup"><span data-stu-id="2190a-125">**Testing**.</span></span> <span data-ttu-id="2190a-126">再帰プロシージャを作成した場合は、慎重にテストして、何らかの制限条件を常に満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2190a-126">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="2190a-127">また、再帰呼び出しが多すぎるためにメモリ不足にならないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2190a-127">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="2190a-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="2190a-128">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="2190a-129">手順</span><span class="sxs-lookup"><span data-stu-id="2190a-129">Procedures</span></span>](index.md)
- [<span data-ttu-id="2190a-130">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2190a-130">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="2190a-131">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2190a-131">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="2190a-132">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2190a-132">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="2190a-133">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2190a-133">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="2190a-134">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="2190a-134">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2190a-135">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="2190a-135">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="2190a-136">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2190a-136">Troubleshooting Procedures</span></span>](troubleshooting-procedures.md)
- [<span data-ttu-id="2190a-137">ループ構造</span><span class="sxs-lookup"><span data-stu-id="2190a-137">Loop Structures</span></span>](../control-flow/loop-structures.md)
