---
description: '詳細情報: 方法:Visual Basic でプロシージャを別のプロシージャに渡す'
title: '方法: プロシージャを別のプロシージャに渡す'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: dfd75d1f58519365bfb6ac59892238b5322743f3
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434447"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="b871a-103">方法: Visual Basic でプロシージャを別のプロシージャに渡す</span><span class="sxs-lookup"><span data-stu-id="b871a-103">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>

<span data-ttu-id="b871a-104">この例では、デリゲートを使用してプロシージャを別のプロシージャに渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b871a-104">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="b871a-105">デリゲートは、Visual Basic で他の型と同じように使用できる型です。</span><span class="sxs-lookup"><span data-stu-id="b871a-105">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="b871a-106">`AddressOf` 演算子は、プロシージャ名に適用されるときにデリゲート オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="b871a-106">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="b871a-107">この例は、プロシージャと、`AddressOf` 演算子で取得した別のプロシージャへの参照を取ることができるデリゲート パラメーターを示しています。</span><span class="sxs-lookup"><span data-stu-id="b871a-107">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="b871a-108">デリゲートおよび一致するプロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="b871a-108">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="b871a-109">`MathOperator` という名前のデリゲートを作成します。</span><span class="sxs-lookup"><span data-stu-id="b871a-109">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="b871a-110">`MathOperator` のパラメーターと一致するパラメーターと戻り値を持つ、`AddNumbers` という名前のプロシージャを作成します。これによりシグネチャが一致します。</span><span class="sxs-lookup"><span data-stu-id="b871a-110">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. <span data-ttu-id="b871a-111">`MathOperator` と一致するシグネチャを持つ `SubtractNumbers` という名前のプロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="b871a-111">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. <span data-ttu-id="b871a-112">デリゲートをパラメーターとして取る `DelegateTest` という名前のプロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="b871a-112">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="b871a-113">このプロシージャは `AddNumbers` または `SubtractNumbers` への参照を受け入れることができます。なぜなら、そのシグネチャが `MathOperator` シグネチャと一致するためです。</span><span class="sxs-lookup"><span data-stu-id="b871a-113">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. <span data-ttu-id="b871a-114">`Test` という名前のプロシージャを作成します。このプロシージャは、`DelegateTest` を、`AddNumbers` のデリゲートでパラメーターとして 1 回呼び出し、`SubtractNumbers` のデリゲートでパラメーターとしてもう 1 回呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b871a-114">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     <span data-ttu-id="b871a-115">`Test` が呼び出されると、最初は `5` および `3` で動作している `AddNumbers` の結果である 8 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b871a-115">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="b871a-116">次に、`9` と `3` で動作している `SubtractNumbers` の結果である 6 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b871a-116">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b871a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b871a-117">See also</span></span>

- [<span data-ttu-id="b871a-118">デリゲート</span><span class="sxs-lookup"><span data-stu-id="b871a-118">Delegates</span></span>](index.md)
- [<span data-ttu-id="b871a-119">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="b871a-119">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="b871a-120">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="b871a-120">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="b871a-121">方法: デリゲート メソッドを呼び出す</span><span class="sxs-lookup"><span data-stu-id="b871a-121">How to: Invoke a Delegate Method</span></span>](how-to-invoke-a-delegate-method.md)
