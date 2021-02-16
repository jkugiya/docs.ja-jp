---
description: '詳細情報: 方法:ラムダ式を作成する (Visual Basic)'
title: '方法: ラムダ式を作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 386d40c1e2021c9b02b2f785300c4e978b4da87d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472567"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="249aa-103">方法: ラムダ式を作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="249aa-103">How to: Create a Lambda Expression (Visual Basic)</span></span>

<span data-ttu-id="249aa-104">"*ラムダ式*" は、名前のない関数またはサブルーチンです。</span><span class="sxs-lookup"><span data-stu-id="249aa-104">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="249aa-105">ラムダ式は、デリゲート型が有効であれば使用できます。</span><span class="sxs-lookup"><span data-stu-id="249aa-105">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="249aa-106">単一行のラムダ式関数を作成するには</span><span class="sxs-lookup"><span data-stu-id="249aa-106">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="249aa-107">デリゲート型を使用できる場合、次の例に示すように、キーワード `Function` を入力します。</span><span class="sxs-lookup"><span data-stu-id="249aa-107">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="249aa-108">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="249aa-108">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="249aa-109">`Function` の直後のかっこ内に、関数のパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="249aa-109">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="249aa-110">`Function` の後に名前を指定しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="249aa-110">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="249aa-111">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="249aa-111">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="249aa-112">パラメーター リストの後に、関数の本体として単一の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="249aa-112">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="249aa-113">式が評価される値は、関数によって返される値です。</span><span class="sxs-lookup"><span data-stu-id="249aa-113">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="249aa-114">`As` 句を使用して戻り値の型は指定しません。</span><span class="sxs-lookup"><span data-stu-id="249aa-114">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="249aa-115">整数引数を渡してラムダ式を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="249aa-115">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="249aa-116">代わりに、次の例でも同じ結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="249aa-116">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="249aa-117">単一行のラムダ式サブルーチンを作成するには</span><span class="sxs-lookup"><span data-stu-id="249aa-117">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="249aa-118">デリゲート型を使用できる場合、次の例に示すように、キーワード `Sub` を入力します。</span><span class="sxs-lookup"><span data-stu-id="249aa-118">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="249aa-119">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="249aa-119">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="249aa-120">`Sub` の直後のかっこ内に、サブルーチンのパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="249aa-120">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="249aa-121">`Sub` の後に名前を指定しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="249aa-121">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="249aa-122">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="249aa-122">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="249aa-123">パラメーター リストの後に、サブルーチンの本体として単一のステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="249aa-123">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="249aa-124">文字列引数を渡してラムダ式を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="249aa-124">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="249aa-125">複数行のラムダ式関数を作成するには</span><span class="sxs-lookup"><span data-stu-id="249aa-125">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="249aa-126">デリゲート型を使用できる場合、次の例に示すように、キーワード `Function` を入力します。</span><span class="sxs-lookup"><span data-stu-id="249aa-126">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="249aa-127">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="249aa-127">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="249aa-128">`Function` の直後のかっこ内に、関数のパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="249aa-128">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="249aa-129">`Function` の後に名前を指定しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="249aa-129">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="249aa-130">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="249aa-130">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="249aa-131">ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="249aa-131">Press ENTER.</span></span> <span data-ttu-id="249aa-132">`End Function` ステートメントが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="249aa-132">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="249aa-133">関数の本体内に、次のコードを追加して式を作成し、値を返します。</span><span class="sxs-lookup"><span data-stu-id="249aa-133">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="249aa-134">`As` 句を使用して戻り値の型は指定しません。</span><span class="sxs-lookup"><span data-stu-id="249aa-134">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="249aa-135">整数引数を渡してラムダ式を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="249aa-135">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="249aa-136">複数行のラムダ式サブルーチンを作成するには</span><span class="sxs-lookup"><span data-stu-id="249aa-136">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="249aa-137">デリゲート型を使用できる場合、次の例に示すように、キーワード `Sub` を入力します。</span><span class="sxs-lookup"><span data-stu-id="249aa-137">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="249aa-138">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="249aa-138">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="249aa-139">`Sub` の直後のかっこ内に、サブルーチンのパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="249aa-139">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="249aa-140">`Sub` の後に名前を指定しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="249aa-140">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="249aa-141">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="249aa-141">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="249aa-142">ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="249aa-142">Press ENTER.</span></span> <span data-ttu-id="249aa-143">`End Sub` ステートメントが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="249aa-143">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="249aa-144">関数の本体内に、サブルーチンが呼び出されたときに実行する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="249aa-144">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="249aa-145">文字列引数を渡してラムダ式を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="249aa-145">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="249aa-146">例</span><span class="sxs-lookup"><span data-stu-id="249aa-146">Example</span></span>  

 <span data-ttu-id="249aa-147">ラムダ式の一般的な用途は、型が `Delegate` のパラメーターの引数として渡すことができる関数を定義することです。</span><span class="sxs-lookup"><span data-stu-id="249aa-147">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="249aa-148">次の例では、<xref:System.Diagnostics.Process.GetProcesses%2A> メソッドはローカルコンピューターで実行されているプロセスの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="249aa-148">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="249aa-149"><xref:System.Linq.Enumerable> クラスの <xref:System.Linq.Enumerable.Where%2A> メソッドには、引数として `Boolean` デリゲートが必要です。</span><span class="sxs-lookup"><span data-stu-id="249aa-149">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="249aa-150">この例のラムダ式は、そのために使用されています。</span><span class="sxs-lookup"><span data-stu-id="249aa-150">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="249aa-151">スレッドが 1 つしかないプロセスごとに `True` が返されます。それらは `filteredList` で選択されています。</span><span class="sxs-lookup"><span data-stu-id="249aa-151">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="249aa-152">前の例は、統合言語クエリ (LINQ) 構文で記述された次のコードに相当します。</span><span class="sxs-lookup"><span data-stu-id="249aa-152">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="249aa-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="249aa-153">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="249aa-154">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="249aa-154">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="249aa-155">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="249aa-155">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="249aa-156">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="249aa-156">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="249aa-157">デリゲート</span><span class="sxs-lookup"><span data-stu-id="249aa-157">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="249aa-158">方法: Visual Basic でプロシージャを別のプロシージャに渡す</span><span class="sxs-lookup"><span data-stu-id="249aa-158">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="249aa-159">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="249aa-159">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="249aa-160">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="249aa-160">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
