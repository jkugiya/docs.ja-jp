---
description: '詳細情報: Function プロシージャ (Visual Basic)'
title: Function プロシージャ
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 4997059fc33fb5d438519356b2c9fdd9e6a27cce
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436150"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="9cd3a-103">Function プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cd3a-103">Function procedures (Visual Basic)</span></span>

<span data-ttu-id="9cd3a-104">`Function` プロシージャは、`Function` ステートメントと `End Function` ステートメントで囲まれた一連の Visual Basic ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-104">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="9cd3a-105">`Function` プロシージャはタスクを実行した後、呼び出し元のコードに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-105">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="9cd3a-106">制御を戻すときに、呼び出し元のコードに値も返します。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-106">When it returns control, it also returns a value to the calling code.</span></span>

<span data-ttu-id="9cd3a-107">プロシージャが呼び出されるたびに、そのステートメントが実行されます。`Function` ステートメントの後の実行可能な最初のステートメントから始まり、最初に出現した `End Function`、`Exit Function`、または `Return` ステートメントで終了します。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-107">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>

<span data-ttu-id="9cd3a-108">`Function` プロシージャは、モジュール、クラス、または構造体で定義できます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-108">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="9cd3a-109">既定では `Public` であるため、プロシージャが定義されているモジュール、クラス、または構造体にアクセスできるアプリケーション内のどこからでも呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-109">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>

<span data-ttu-id="9cd3a-110">`Function` プロシージャは、呼び出し元のコードから渡される定数、変数、式などの引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-110">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="9cd3a-111">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="9cd3a-111">Declaration syntax</span></span>

<span data-ttu-id="9cd3a-112">`Function` プロシージャを宣言するための構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-112">The syntax for declaring a `Function` procedure is as follows:</span></span>

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

<span data-ttu-id="9cd3a-113">"*修飾子*" では、アクセス レベルと、オーバーロード、オーバーライド、共有、シャドウに関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-113">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="9cd3a-114">詳細については、「[Function Statement (Function ステートメント)](../../../language-reference/statements/function-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-114">For more information, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

<span data-ttu-id="9cd3a-115">各パラメーターは、[Sub プロシージャ](./sub-procedures.md)の場合と同様に宣言します。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-115">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="9cd3a-116">データの種類</span><span class="sxs-lookup"><span data-stu-id="9cd3a-116">Data type</span></span>

<span data-ttu-id="9cd3a-117">すべての変数と同様に、すべての `Function` プロシージャにもデータ型があります。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-117">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="9cd3a-118">このデータ型は、`Function` ステートメントの `As` 句で指定され、関数が呼び出し元のコードに返す値のデータ型が決定されます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-118">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="9cd3a-119">次の宣言のサンプルはこれを示しています。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-119">The following sample declarations illustrate this.</span></span>

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

<span data-ttu-id="9cd3a-120">詳細については、「[Function Statement (Function ステートメント)](../../../language-reference/statements/function-statement.md)」の「Parts (要素)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-120">For more information, see "Parts" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

### <a name="returning-values"></a><span data-ttu-id="9cd3a-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="9cd3a-121">Returning values</span></span>

<span data-ttu-id="9cd3a-122">`Function` プロシージャが呼び出し元のコードに返す値は戻り値と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-122">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="9cd3a-123">プロシージャは、次の 2 つの方法のいずれかでこの値を返します。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-123">The procedure returns this value in one of two ways:</span></span>

- <span data-ttu-id="9cd3a-124">`Return` ステートメントを使用して戻り値を指定し、呼び出し元のプログラムに制御をすぐに戻します。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-124">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="9cd3a-125">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-125">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- <span data-ttu-id="9cd3a-126">プロシージャの 1 つ以上のステートメントで、独自の関数名に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-126">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="9cd3a-127">`Exit Function` または `End Function` ステートメントが実行されるまで、呼び出し元のプログラムに制御は戻りません。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-127">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="9cd3a-128">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-128">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

<span data-ttu-id="9cd3a-129">戻り値を関数名に割り当てる利点は、`Exit Function` または `End Function` ステートメントが出現するまで、プロシージャから制御が戻されないことです。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-129">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="9cd3a-130">これにより、暫定値を割り当て、必要に応じて後で調整できます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-130">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>

<span data-ttu-id="9cd3a-131">戻り値の詳細については、「[Function Statement (Function ステートメント)](../../../language-reference/statements/function-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-131">For more information about returning values, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="9cd3a-132">配列を返す方法については、[配列](../arrays/index.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-132">For information about returning arrays, see [Arrays](../arrays/index.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="9cd3a-133">呼び出しの構文</span><span class="sxs-lookup"><span data-stu-id="9cd3a-133">Calling syntax</span></span>

<span data-ttu-id="9cd3a-134">`Function` プロシージャを呼び出すには、その名前と引数を代入ステートメントの右辺または式に含めます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-134">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="9cd3a-135">省略可能ではないすべての引数に値を指定する必要があり、引数リストをかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-135">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="9cd3a-136">引数を指定しない場合は、必要に応じてかっこを省略できます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-136">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="9cd3a-137">`Function` プロシージャの呼び出しの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-137">The syntax for a call to a `Function` procedure is as follows.</span></span>

<span data-ttu-id="9cd3a-138">*lvalue*  `=`  *関数名* `[(` *引数リスト* `)]`</span><span class="sxs-lookup"><span data-stu-id="9cd3a-138">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>

<span data-ttu-id="9cd3a-139">`If ((` *関数名* `[(` *引数リスト* `)] / 3) <=`  *式* `) Then`</span><span class="sxs-lookup"><span data-stu-id="9cd3a-139">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>

<span data-ttu-id="9cd3a-140">`Function` プロシージャを呼び出すときに、その戻り値を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-140">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="9cd3a-141">使用しない場合、関数のすべてのアクションが実行されますが、戻り値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-141">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="9cd3a-142">多くの場合、<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> はこの方法で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-142"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="9cd3a-143">宣言と呼び出しの実例</span><span class="sxs-lookup"><span data-stu-id="9cd3a-143">Illustration of declaration and call</span></span>

<span data-ttu-id="9cd3a-144">次の `Function` プロシージャは、他の 2 つの辺の値を指定して、直角三角形の最も長い辺 (斜辺) を計算します。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-144">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

<span data-ttu-id="9cd3a-145">次の例は、`hypotenuse` の一般的な呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-145">The following example shows a typical call to `hypotenuse`.</span></span>

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a><span data-ttu-id="9cd3a-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cd3a-146">See also</span></span>

- [<span data-ttu-id="9cd3a-147">手順</span><span class="sxs-lookup"><span data-stu-id="9cd3a-147">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9cd3a-148">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="9cd3a-148">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="9cd3a-149">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="9cd3a-149">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="9cd3a-150">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="9cd3a-150">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="9cd3a-151">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="9cd3a-151">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9cd3a-152">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="9cd3a-152">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="9cd3a-153">方法: 値を返すプロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="9cd3a-153">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="9cd3a-154">方法: プロシージャから値を返す</span><span class="sxs-lookup"><span data-stu-id="9cd3a-154">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="9cd3a-155">方法: 値を返すプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="9cd3a-155">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
