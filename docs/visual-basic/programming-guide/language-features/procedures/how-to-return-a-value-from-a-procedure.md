---
description: '詳細情報: 方法:プロシージャから値を返す (Visual Basic)'
title: '方法: プロシージャから値を返す'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: c158f15b1e6acb7334d78037d84145981822e177
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476177"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="88e66-103">方法: プロシージャから値を返す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88e66-103">How to: Return a Value from a Procedure (Visual Basic)</span></span>

<span data-ttu-id="88e66-104">`Function` プロシージャは、`Return` ステートメントを実行するか、`Exit Function` または `End Function` ステートメントを検出すると、呼び出し元のコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="88e66-104">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="88e66-105">Return ステートメントを使用して値を返すには</span><span class="sxs-lookup"><span data-stu-id="88e66-105">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="88e66-106">プロシージャのタスクが完了した位置に、`Return` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="88e66-106">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="88e66-107">`Return` キーワードの後に、呼び出し元のコードに返す値を生成する式を入力します。</span><span class="sxs-lookup"><span data-stu-id="88e66-107">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="88e66-108">同じプロシージャ内に複数の `Return` ステートメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="88e66-108">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="88e66-109">次の `Function` プロシージャは、直角三角形の最も長い辺 (斜辺) を計算して呼び出し元のコードに返します。</span><span class="sxs-lookup"><span data-stu-id="88e66-109">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="88e66-110">次の例は、戻り値を格納する `hypotenuse` の一般的な呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="88e66-110">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="88e66-111">Exit Function または End Function を使用して値を返すには</span><span class="sxs-lookup"><span data-stu-id="88e66-111">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="88e66-112">`Function` プロシージャ内の少なくとも 1 か所で、プロシージャの名前に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="88e66-112">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="88e66-113">`Exit Function` または `End Function` ステートメントを実行すると、Visual Basic はプロシージャの名前に最後に割り当てられた値を返します。</span><span class="sxs-lookup"><span data-stu-id="88e66-113">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="88e66-114">同じプロシージャ内に複数の `Exit Function` ステートメントを含めることができ、さらに同じプロシージャ内に `Return` ステートメントと `Exit Function` ステートメントを混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="88e66-114">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="88e66-115">`End Function` ステートメントは、`Function` プロシージャに 1 つだけ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="88e66-115">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="88e66-116">詳細と例については、「[Function Statement (Function ステートメント)](../../../language-reference/statements/function-statement.md)」の戻り値に関するセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="88e66-116">For more information and an example, see "Return Value" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e66-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="88e66-117">See also</span></span>

- [<span data-ttu-id="88e66-118">手順</span><span class="sxs-lookup"><span data-stu-id="88e66-118">Procedures</span></span>](./index.md)
- [<span data-ttu-id="88e66-119">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="88e66-119">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="88e66-120">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="88e66-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="88e66-121">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="88e66-121">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="88e66-122">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="88e66-122">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="88e66-123">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="88e66-123">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="88e66-124">Return ステートメント</span><span class="sxs-lookup"><span data-stu-id="88e66-124">Return Statement</span></span>](../../../language-reference/statements/return-statement.md)
- [<span data-ttu-id="88e66-125">方法: 値を返すプロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="88e66-125">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="88e66-126">方法: 値を返すプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="88e66-126">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
