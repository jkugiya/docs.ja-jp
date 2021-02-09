---
description: '詳細情報: Do...Loop ステートメント (Visual Basic)'
title: Do...Loop ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: d170074c44d1692517f6b51abd4a6b3d005941c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795184"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="bcfb1-103">Do...Loop ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcfb1-103">Do...Loop Statement (Visual Basic)</span></span>

<span data-ttu-id="bcfb1-104">`Boolean` 条件が `True` の場合、または条件が `True` になるまで、ステートメントのブロックを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-104">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcfb1-105">構文</span><span class="sxs-lookup"><span data-stu-id="bcfb1-105">Syntax</span></span>  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="bcfb1-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="bcfb1-106">Parts</span></span>  
  
|<span data-ttu-id="bcfb1-107">用語</span><span class="sxs-lookup"><span data-stu-id="bcfb1-107">Term</span></span>|<span data-ttu-id="bcfb1-108">定義</span><span class="sxs-lookup"><span data-stu-id="bcfb1-108">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="bcfb1-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-109">Required.</span></span> <span data-ttu-id="bcfb1-110">`Do` ループの定義を開始します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-110">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="bcfb1-111">`Until` を使用しない場合に、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-111">Required unless `Until` is used.</span></span> <span data-ttu-id="bcfb1-112">`condition` が `False` になるまでループを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-112">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="bcfb1-113">`While` を使用しない場合に、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-113">Required unless `While` is used.</span></span> <span data-ttu-id="bcfb1-114">`condition` が `True` になるまでループを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-114">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="bcfb1-115">任意。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-115">Optional.</span></span> <span data-ttu-id="bcfb1-116">`Boolean` 式。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-116">`Boolean` expression.</span></span> <span data-ttu-id="bcfb1-117">`condition` が `Nothing` の場合、Visual Basic ではそれを `False` として扱います。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-117">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="bcfb1-118">任意。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-118">Optional.</span></span> <span data-ttu-id="bcfb1-119">`condition` が `True` である間、またはその状態になるまで繰り返される、1 つまたは複数のステートメント。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-119">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="bcfb1-120">任意。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-120">Optional.</span></span> <span data-ttu-id="bcfb1-121">`Do` ループの次の反復に制御を渡します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-121">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="bcfb1-122">任意。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-122">Optional.</span></span> <span data-ttu-id="bcfb1-123">`Do` ループから制御を移します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-123">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="bcfb1-124">必須です。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-124">Required.</span></span> <span data-ttu-id="bcfb1-125">`Do` ループの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-125">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcfb1-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="bcfb1-126">Remarks</span></span>  

 <span data-ttu-id="bcfb1-127">条件が満たされるまで、一連のステートメントを無限に繰り返す場合は、`Do...Loop` 構造体を使用します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-127">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="bcfb1-128">ステートメントを設定した回数だけ繰り返す場合は、通常、[For...Next ステートメント](for-next-statement.md)のほうが適しています。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-128">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="bcfb1-129">`While` または `Until` のいずれかを使用して `condition` を指定できますが、両方を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-129">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="bcfb1-130">`condition` は、ループの開始時または終了時に 1 回だけテストできます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-130">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="bcfb1-131">ループの開始時に (`Do` ステートメントで) `condition` をテストする場合、ループは 1 回も実行されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-131">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="bcfb1-132">ループの最後に (`Loop` ステートメントで) テストする場合、ループは少なくとも 1 回は必ず実行されます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-132">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="bcfb1-133">通常、条件は 2 つの値を比較することによって判断されますが、[ブール データ型](../data-types/boolean-data-type.md)の値 (`True` または `False`) に評価される任意の式を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-133">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="bcfb1-134">これには、`Boolean` に変換されたその他のデータ型 (数値型など) の値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-134">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="bcfb1-135">`Do` ループを入れ子にするには、別のループ内にループを配置します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-135">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="bcfb1-136">また、さまざまな種類の制御構造を相互に入れ子にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-136">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="bcfb1-137">詳細については、「[入れ子になった制御構造](../../programming-guide/language-features/control-flow/nested-control-structures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-137">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcfb1-138">`Do...Loop` 構造は、[While...End While ステートメント](while-end-while-statement.md)よりも柔軟性があります。`condition` が `True` でなくなったとき、または初めて `True` になったときに、ループを終了するかどうかを判断できるためです。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-138">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="bcfb1-139">ループの開始時または終了時に `condition` をテストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-139">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="bcfb1-140">Exit Do</span><span class="sxs-lookup"><span data-stu-id="bcfb1-140">Exit Do</span></span>  

 <span data-ttu-id="bcfb1-141">[Exit Do](exit-statement.md) ステートメントを使用すると、別の方法で `Do…Loop` を終了させることができます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-141">The [Exit Do](exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="bcfb1-142">`Exit Do` は `Loop` ステートメントの次のステートメントに制御を直ちに渡します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-142">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="bcfb1-143">`Exit Do` は、何らかの条件を評価した (`If...Then...Else` 構造など) 後によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-143">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="bcfb1-144">誤った値や終了要求など、反復処理を続行することが不要であるか、不可能である状況が検出された場合に、ループを終了させることができます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-144">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="bcfb1-145">`Exit Do` の用途の 1 つとしては、*無限ループ* を引き起こす可能性がある条件をテストすることがあります。無限ループは、膨大な回数または無限に実行されるループです。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-145">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="bcfb1-146">`Exit Do` を使用すると、ループを終了できます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-146">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="bcfb1-147">`Do…Loop` 内の任意の場所に、任意の数の `Exit Do` ステートメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-147">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="bcfb1-148">入れ子になった `Do` ループ内で使用した場合、`Exit Do` は最も内側のループから次の上位レベルの入れ子に制御を渡します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-148">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcfb1-149">例</span><span class="sxs-lookup"><span data-stu-id="bcfb1-149">Example</span></span>  

 <span data-ttu-id="bcfb1-150">次の例では、ループ内のステートメントは `index` 変数が 10 を超えるまで実行されます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-150">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="bcfb1-151">`Until` 句はループの最後にあります。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-151">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="bcfb1-152">例</span><span class="sxs-lookup"><span data-stu-id="bcfb1-152">Example</span></span>  

 <span data-ttu-id="bcfb1-153">次の例では、`Until` 句ではなく `While` 句が使用されています。`condition` はループの終了時ではなく開始時にテストされます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-153">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="bcfb1-154">例</span><span class="sxs-lookup"><span data-stu-id="bcfb1-154">Example</span></span>  

 <span data-ttu-id="bcfb1-155">次の例では、`index` 変数が 100 を超えた場合、`condition` によってループが停止します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-155">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="bcfb1-156">ただし、ループ内の `If` ステートメントでは、インデックス変数が 10 より大きい場合、`Exit Do` ステートメントによってループが停止します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-156">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="bcfb1-157">例</span><span class="sxs-lookup"><span data-stu-id="bcfb1-157">Example</span></span>  

 <span data-ttu-id="bcfb1-158">次の例では、テキスト ファイル内のすべての行を読み取っています。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-158">The following example reads all lines in a text file.</span></span> <span data-ttu-id="bcfb1-159"><xref:System.IO.File.OpenText%2A> メソッドは、ファイルを開いて、文字を読み取る <xref:System.IO.StreamReader> を返します。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-159">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="bcfb1-160">`Do...Loop` 条件では、`StreamReader` の <xref:System.IO.StreamReader.Peek%2A> メソッドによって、追加の文字があるかどうかが判別されます。</span><span class="sxs-lookup"><span data-stu-id="bcfb1-160">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="bcfb1-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcfb1-161">See also</span></span>

- [<span data-ttu-id="bcfb1-162">ループ構造</span><span class="sxs-lookup"><span data-stu-id="bcfb1-162">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="bcfb1-163">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="bcfb1-163">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="bcfb1-164">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="bcfb1-164">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="bcfb1-165">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="bcfb1-165">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="bcfb1-166">Exit ステートメント</span><span class="sxs-lookup"><span data-stu-id="bcfb1-166">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="bcfb1-167">While...End While ステートメント</span><span class="sxs-lookup"><span data-stu-id="bcfb1-167">While...End While Statement</span></span>](while-end-while-statement.md)
