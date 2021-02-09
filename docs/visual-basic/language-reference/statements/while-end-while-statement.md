---
description: '詳細情報: While...End While ステートメント (Visual Basic)'
title: While...End While ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: ab452e2d9446c9c44b952c6ebf026f7a6f9080cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787579"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="63eb8-103">While...End While ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63eb8-103">While...End While Statement (Visual Basic)</span></span>

<span data-ttu-id="63eb8-104">指定された条件が `True` である限り、一連のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="63eb8-104">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63eb8-105">構文</span><span class="sxs-lookup"><span data-stu-id="63eb8-105">Syntax</span></span>  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="63eb8-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="63eb8-106">Parts</span></span>  
  
|<span data-ttu-id="63eb8-107">用語</span><span class="sxs-lookup"><span data-stu-id="63eb8-107">Term</span></span>|<span data-ttu-id="63eb8-108">定義</span><span class="sxs-lookup"><span data-stu-id="63eb8-108">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="63eb8-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="63eb8-109">Required.</span></span> <span data-ttu-id="63eb8-110">`Boolean` 式。</span><span class="sxs-lookup"><span data-stu-id="63eb8-110">`Boolean` expression.</span></span> <span data-ttu-id="63eb8-111">`condition` が `Nothing` の場合、Visual Basic ではそれを `False` として扱います。</span><span class="sxs-lookup"><span data-stu-id="63eb8-111">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="63eb8-112">任意。</span><span class="sxs-lookup"><span data-stu-id="63eb8-112">Optional.</span></span> <span data-ttu-id="63eb8-113">`While` の後の 1 つ以上のステートメント。`condition` が `True` であるたびに実行されます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-113">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="63eb8-114">任意。</span><span class="sxs-lookup"><span data-stu-id="63eb8-114">Optional.</span></span> <span data-ttu-id="63eb8-115">`While` ブロックの次の反復に制御を渡します。</span><span class="sxs-lookup"><span data-stu-id="63eb8-115">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="63eb8-116">任意。</span><span class="sxs-lookup"><span data-stu-id="63eb8-116">Optional.</span></span> <span data-ttu-id="63eb8-117">`While` ブロックから制御を渡します。</span><span class="sxs-lookup"><span data-stu-id="63eb8-117">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="63eb8-118">必須です。</span><span class="sxs-lookup"><span data-stu-id="63eb8-118">Required.</span></span> <span data-ttu-id="63eb8-119">`While` ブロックの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="63eb8-119">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63eb8-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="63eb8-120">Remarks</span></span>  

 <span data-ttu-id="63eb8-121">条件が `True` のままである限り、一連のステートメントを無限に繰り返す場合は、`While...End While` 構造体を使用します。</span><span class="sxs-lookup"><span data-stu-id="63eb8-121">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="63eb8-122">条件をテストする場所またはテストで求める結果に関してより柔軟性を必要とする場合は、[Do...Loop ステートメント](do-loop-statement.md)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="63eb8-122">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](do-loop-statement.md).</span></span> <span data-ttu-id="63eb8-123">設定した回数だけステートメントを繰り返す場合は、通常、[For...Next ステートメント](for-next-statement.md)の方が適しています。</span><span class="sxs-lookup"><span data-stu-id="63eb8-123">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63eb8-124">`While` キーワードは、[Do...Loop ステートメント](do-loop-statement.md)、[Skip While 句](../queries/skip-while-clause.md)、および [Take While 句](../queries/take-while-clause.md)でも使用します。</span><span class="sxs-lookup"><span data-stu-id="63eb8-124">The `While` keyword is also used in the [Do...Loop Statement](do-loop-statement.md), the [Skip While Clause](../queries/skip-while-clause.md) and the [Take While Clause](../queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="63eb8-125">`condition` が `True` である場合、`End While` ステートメントが検出されるまで、すべての `statements` が実行されます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-125">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="63eb8-126">その後、制御が `While` ステートメントに戻り、`condition` が再度チェックされます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-126">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="63eb8-127">`condition` がまだ `True` である場合は、プロセスが繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-127">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="63eb8-128">`False` である場合は、制御が `End While` ステートメントの後のステートメントに渡されます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-128">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="63eb8-129">`While` ステートメントでは、ループを開始する前に常に条件がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-129">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="63eb8-130">ループは、条件が `True` のままである間続行されます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-130">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="63eb8-131">最初にループに入ったときに `condition` が `False` である場合は、1 回も実行されません。</span><span class="sxs-lookup"><span data-stu-id="63eb8-131">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="63eb8-132">通常、`condition` は 2 つの値の比較の結果になりますが、[ブール データ型](../data-types/boolean-data-type.md)の値 (`True` または `False`) に評価される任意の式を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-132">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="63eb8-133">この式には、`Boolean` に変換された別のデータ型 (数値型など) の値を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-133">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="63eb8-134">`While` ループを入れ子にするには、別のループ内にループを配置します。</span><span class="sxs-lookup"><span data-stu-id="63eb8-134">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="63eb8-135">また、さまざまな種類の制御構造を相互に入れ子にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-135">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="63eb8-136">詳細については、「[入れ子になった制御構造](../../programming-guide/language-features/control-flow/nested-control-structures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63eb8-136">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="63eb8-137">Exit While</span><span class="sxs-lookup"><span data-stu-id="63eb8-137">Exit While</span></span>  

 <span data-ttu-id="63eb8-138">[Exit While](exit-statement.md) ステートメントでは、`While` ループを終了する別の方法を提供できます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-138">The [Exit While](exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="63eb8-139">`Exit While` では `End While` ステートメントの次のステートメントに制御が直ちに渡されます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-139">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="63eb8-140">`Exit While` は一般に、何らかの条件を評価した (`If...Then...Else` ストラクチャなどで) 後に使用します。</span><span class="sxs-lookup"><span data-stu-id="63eb8-140">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="63eb8-141">誤った値や終了要求など、反復処理を続行することが不要になるか、不可能になる状況を検出した場合に、ループを終了させたいことがあります。</span><span class="sxs-lookup"><span data-stu-id="63eb8-141">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="63eb8-142">`Exit While` は、*無限ループ* を引き起こす可能性がある条件をテストする場合に使用できます。無限ループは、膨大な回数または無限に実行する可能性があるループです。</span><span class="sxs-lookup"><span data-stu-id="63eb8-142">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="63eb8-143">そこで、`Exit While` を使用すると、ループから抜け出すことができます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-143">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="63eb8-144">`While` ループ内の任意の場所に、任意の数の `Exit While` ステートメントを配置できます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-144">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="63eb8-145">入れ子になった `While` ループ内で使用した場合、`Exit While` では最も内側のループから次の上位レベルの入れ子に制御が渡されます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-145">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="63eb8-146">`Continue While` ステートメントでは、ループの次の反復に直ちに制御が渡されます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-146">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="63eb8-147">詳細については、「[Continue ステートメント](continue-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63eb8-147">For more information, see [Continue Statement](continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63eb8-148">例</span><span class="sxs-lookup"><span data-stu-id="63eb8-148">Example</span></span>  

 <span data-ttu-id="63eb8-149">次の例では、ループ内のステートメントは `index` 変数が 10 を超えるまで実行されます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="63eb8-150">例</span><span class="sxs-lookup"><span data-stu-id="63eb8-150">Example</span></span>  

 <span data-ttu-id="63eb8-151">次の例では、`Continue While` および `Exit While` ステートメントの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="63eb8-151">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="63eb8-152">例</span><span class="sxs-lookup"><span data-stu-id="63eb8-152">Example</span></span>  

 <span data-ttu-id="63eb8-153">次の例では、テキスト ファイル内のすべての行を読み取っています。</span><span class="sxs-lookup"><span data-stu-id="63eb8-153">The following example reads all lines in a text file.</span></span> <span data-ttu-id="63eb8-154"><xref:System.IO.File.OpenText%2A> メソッドでは、ファイルを開いて、文字を読み取る <xref:System.IO.StreamReader> が返されます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-154">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="63eb8-155">`While` 条件では、`StreamReader` の <xref:System.IO.StreamReader.Peek%2A> メソッドによって、ファイルに追加の文字が含まれるかどうかが判断されます。</span><span class="sxs-lookup"><span data-stu-id="63eb8-155">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="63eb8-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="63eb8-156">See also</span></span>

- [<span data-ttu-id="63eb8-157">ループ構造</span><span class="sxs-lookup"><span data-stu-id="63eb8-157">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="63eb8-158">Do...Loop ステートメント</span><span class="sxs-lookup"><span data-stu-id="63eb8-158">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="63eb8-159">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="63eb8-159">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="63eb8-160">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="63eb8-160">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="63eb8-161">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="63eb8-161">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="63eb8-162">Exit ステートメント</span><span class="sxs-lookup"><span data-stu-id="63eb8-162">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="63eb8-163">Continue ステートメント</span><span class="sxs-lookup"><span data-stu-id="63eb8-163">Continue Statement</span></span>](continue-statement.md)
