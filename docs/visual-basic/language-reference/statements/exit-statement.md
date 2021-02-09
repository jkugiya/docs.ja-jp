---
description: '詳細情報: Exit ステートメント (Visual Basic)'
title: Exit ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 54af7fbf908dbad829cf6f08bf442dfe85e35610
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769127"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="802bf-103">Exit ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="802bf-103">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="802bf-104">プロシージャまたはブロックを終了し、プロシージャ呼び出しまたはブロック定義の次のステートメントに直ちに制御を移します。</span><span class="sxs-lookup"><span data-stu-id="802bf-104">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="802bf-105">構文</span><span class="sxs-lookup"><span data-stu-id="802bf-105">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="802bf-106">ステートメント</span><span class="sxs-lookup"><span data-stu-id="802bf-106">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="802bf-107">これが存在する `Do` ループを直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="802bf-107">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="802bf-108">実行は、`Loop` ステートメントの次のステートメントを使用して続行されます。</span><span class="sxs-lookup"><span data-stu-id="802bf-108">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="802bf-109">`Exit Do` は `Do` ループ内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="802bf-109">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="802bf-110">入れ子になった `Do` ループ内で使用すると、`Exit Do` は、最も内側のループを終了し、次に高い入れ子レベルに制御を移します。</span><span class="sxs-lookup"><span data-stu-id="802bf-110">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="802bf-111">これが存在する `For` ループを直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="802bf-111">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="802bf-112">実行は、`Next` ステートメントの次のステートメントを使用して続行されます。</span><span class="sxs-lookup"><span data-stu-id="802bf-112">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="802bf-113">`Exit For` は、`For`...`Next` または `For Each`...`Next` ループ内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="802bf-113">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="802bf-114">入れ子になった `For` ループ内で使用すると、`Exit For` は、最も内側のループを終了し、次に高い入れ子レベルに制御を移します。</span><span class="sxs-lookup"><span data-stu-id="802bf-114">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="802bf-115">これが存在する `Function` プロシージャを直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="802bf-115">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="802bf-116">実行は、`Function` プロシージャを呼び出したステートメントの次のステートメントを使用して続行されます。</span><span class="sxs-lookup"><span data-stu-id="802bf-116">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="802bf-117">`Exit Function` は `Function` プロシージャ内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="802bf-117">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="802bf-118">戻り値を指定するには、`Exit Function` ステートメントの前にある行の関数名に値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="802bf-118">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="802bf-119">1 つのステートメントで戻り値を割り当てて関数を終了するには、代わりに [Return ステートメント](return-statement.md)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="802bf-119">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="802bf-120">これが存在する `Property` プロシージャを直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="802bf-120">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="802bf-121">実行は、`Property` プロシージャを呼び出したステートメント、つまり、プロパティの値を要求または設定するステートメントを使用して続行されます。</span><span class="sxs-lookup"><span data-stu-id="802bf-121">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="802bf-122">`Exit Property` は、プロパティの `Get` または `Set` プロシージャ内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="802bf-122">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="802bf-123">`Get` プロシージャで戻り値を指定するには、`Exit Property` ステートメントの前にある行の関数名に値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="802bf-123">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="802bf-124">1 つのステートメントで戻り値を割り当てて `Get` プロシージャを終了するには、代わりに `Return` ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="802bf-124">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="802bf-125">`Set` プロシージャでは、`Exit Property` ステートメントは `Return` ステートメントと同じです。</span><span class="sxs-lookup"><span data-stu-id="802bf-125">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="802bf-126">これが存在する `Select Case` ブロックを直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="802bf-126">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="802bf-127">実行は、`End Select` ステートメントの次のステートメントを使用して続行されます。</span><span class="sxs-lookup"><span data-stu-id="802bf-127">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="802bf-128">`Exit Select` は `Select Case` ステートメント内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="802bf-128">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="802bf-129">これが存在する `Sub` プロシージャを直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="802bf-129">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="802bf-130">実行は、`Sub` プロシージャを呼び出したステートメントの次のステートメントを使用して続行されます。</span><span class="sxs-lookup"><span data-stu-id="802bf-130">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="802bf-131">`Exit Sub` は `Sub` プロシージャ内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="802bf-131">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="802bf-132">`Sub` プロシージャでは、`Exit Sub` ステートメントは `Return` ステートメントと同じです。</span><span class="sxs-lookup"><span data-stu-id="802bf-132">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="802bf-133">これが存在する `Try` または `Catch` ブロックを直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="802bf-133">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="802bf-134">実行は、存在する場合は `Finally` ブロックを使用して続行されます。それ以外の場合は、`End Try` ステートメントの次のステートメントを使用して続行されます。</span><span class="sxs-lookup"><span data-stu-id="802bf-134">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="802bf-135">`Exit Try` は、`Finally` ブロック内ではなく、`Try` または `Catch` ブロック内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="802bf-135">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="802bf-136">これが存在する `While` ループを直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="802bf-136">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="802bf-137">実行は、`End While` ステートメントの次のステートメントを使用して続行されます。</span><span class="sxs-lookup"><span data-stu-id="802bf-137">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="802bf-138">`Exit While` は `While` ループ内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="802bf-138">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="802bf-139">入れ子になった `While` ループ内で使用される場合、`Exit While` は `Exit While` が出現するループの 1 つ上の入れ子レベルであるループに制御を移します。</span><span class="sxs-lookup"><span data-stu-id="802bf-139">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="802bf-140">Remarks</span><span class="sxs-lookup"><span data-stu-id="802bf-140">Remarks</span></span>

<span data-ttu-id="802bf-141">`Exit` ステートメントを `End` ステートメントと混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="802bf-141">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="802bf-142">`Exit` は、ステートメントの末尾を定義しません。</span><span class="sxs-lookup"><span data-stu-id="802bf-142">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="802bf-143">例</span><span class="sxs-lookup"><span data-stu-id="802bf-143">Example</span></span>

<span data-ttu-id="802bf-144">次の例では、`index` 変数が 100 より大きい場合、ループ条件によってループが停止します。</span><span class="sxs-lookup"><span data-stu-id="802bf-144">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="802bf-145">ただし、ループ内の `If` ステートメントでは、インデックス変数が 10 より大きい場合、`Exit Do` ステートメントによってループが停止されます。</span><span class="sxs-lookup"><span data-stu-id="802bf-145">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="802bf-146">例</span><span class="sxs-lookup"><span data-stu-id="802bf-146">Example</span></span>

<span data-ttu-id="802bf-147">次の例では、関数名 `myFunction` に戻り値を割り当ててから、`Exit Function` を使用して関数から返します。</span><span class="sxs-lookup"><span data-stu-id="802bf-147">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="802bf-148">例</span><span class="sxs-lookup"><span data-stu-id="802bf-148">Example</span></span>

<span data-ttu-id="802bf-149">次の例では、[Return ステートメント](return-statement.md)を使用して戻り値を割り当て、関数を終了します。</span><span class="sxs-lookup"><span data-stu-id="802bf-149">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="802bf-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="802bf-150">See also</span></span>

- [<span data-ttu-id="802bf-151">Continue ステートメント</span><span class="sxs-lookup"><span data-stu-id="802bf-151">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="802bf-152">Do...Loop ステートメント</span><span class="sxs-lookup"><span data-stu-id="802bf-152">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="802bf-153">End ステートメント</span><span class="sxs-lookup"><span data-stu-id="802bf-153">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="802bf-154">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="802bf-154">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="802bf-155">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="802bf-155">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="802bf-156">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="802bf-156">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="802bf-157">Return ステートメント</span><span class="sxs-lookup"><span data-stu-id="802bf-157">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="802bf-158">Stop ステートメント</span><span class="sxs-lookup"><span data-stu-id="802bf-158">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="802bf-159">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="802bf-159">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="802bf-160">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="802bf-160">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
