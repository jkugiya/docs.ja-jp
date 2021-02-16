---
description: '詳細情報: Sub プロシージャ (Visual Basic)'
title: Sub プロシージャ
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: fe9d26fb2d18fbd29820af7aca96b826d7b45d0b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466511"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="7ea55-103">Sub プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ea55-103">Sub procedures (Visual Basic)</span></span>

<span data-ttu-id="7ea55-104">`Sub` プロシージャは、`Sub` ステートメントと `End Sub` ステートメントで囲まれた一連の Visual Basic ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7ea55-104">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="7ea55-105">`Sub` プロシージャはタスクを実行した後、呼び出し元のコードに制御を戻しますが、呼び出し元のコードに値は返しません。</span><span class="sxs-lookup"><span data-stu-id="7ea55-105">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>

<span data-ttu-id="7ea55-106">プロシージャが呼び出されるたびに、そのステートメントが実行されます。`Sub` ステートメントの後の実行可能な最初のステートメントから始まり、最初に出現した `End Sub`、`Exit Sub`、または `Return` ステートメントで終了します。</span><span class="sxs-lookup"><span data-stu-id="7ea55-106">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>

<span data-ttu-id="7ea55-107">`Sub` プロシージャは、モジュール、クラス、構造体で定義できます。</span><span class="sxs-lookup"><span data-stu-id="7ea55-107">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="7ea55-108">既定では `Public` であるため、プロシージャが定義されているモジュール、クラス、または構造体にアクセスできるアプリケーション内のどこからでも呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7ea55-108">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="7ea55-109">"*メソッド*" という用語は、プロシージャが定義されているモジュール、クラス、または構造体の外部からアクセスされる `Sub` または `Function` プロシージャを示します。</span><span class="sxs-lookup"><span data-stu-id="7ea55-109">The term *method* describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="7ea55-110">詳細については、「[プロシージャ](./index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ea55-110">For more information, see [Procedures](./index.md).</span></span>

<span data-ttu-id="7ea55-111">`Sub` プロシージャは、呼び出し元のコードから渡される定数、変数、式などの引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="7ea55-111">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="7ea55-112">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="7ea55-112">Declaration syntax</span></span>

<span data-ttu-id="7ea55-113">`Sub` プロシージャを宣言するための構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7ea55-113">The syntax for declaring a `Sub` procedure is as follows:</span></span>

```vb
[modifiers] Sub SubName[(parameterList)]
    ' Statements of the Sub procedure.
End Sub
```

<span data-ttu-id="7ea55-114">`modifiers` では、アクセス レベルと、オーバーロード、オーバーライド、共有、シャドウに関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7ea55-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="7ea55-115">詳細については、「[Sub Statement (Sub ステートメント)](../../../language-reference/statements/sub-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7ea55-115">For more information, see [Sub Statement](../../../language-reference/statements/sub-statement.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="7ea55-116">パラメーターの宣言</span><span class="sxs-lookup"><span data-stu-id="7ea55-116">Parameter declaration</span></span>

<span data-ttu-id="7ea55-117">変数を宣言する場合と同様に、パラメーター名とデータ型を指定して、プロシージャの各パラメーターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="7ea55-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="7ea55-118">引渡し方法、パラメーターが省略可能かどうか、パラメーターがパラメーター配列かどうかを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7ea55-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>

<span data-ttu-id="7ea55-119">パラメーター リストの各パラメーターの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7ea55-119">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] [ByVal | ByRef] [ParamArray] parameterName As DataType
```

<span data-ttu-id="7ea55-120">パラメーターが省略可能な場合は、宣言の一部として既定値も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ea55-120">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="7ea55-121">既定値を指定するための構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7ea55-121">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional [ByVal | ByRef]  parameterName As DataType = defaultValue
```

### <a name="parameters-as-local-variables"></a><span data-ttu-id="7ea55-122">ローカル変数としてのパラメーター</span><span class="sxs-lookup"><span data-stu-id="7ea55-122">Parameters as local variables</span></span>

<span data-ttu-id="7ea55-123">制御がプロシージャに渡されると、各パラメーターはローカル変数として扱われます。</span><span class="sxs-lookup"><span data-stu-id="7ea55-123">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="7ea55-124">つまり、パラメーターの有効期間はプロシージャの有効期間と同じであり、スコープはプロシージャ全体になります。</span><span class="sxs-lookup"><span data-stu-id="7ea55-124">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="7ea55-125">呼び出しの構文</span><span class="sxs-lookup"><span data-stu-id="7ea55-125">Calling syntax</span></span>

<span data-ttu-id="7ea55-126">`Sub` プロシージャは、スタンドアロンの呼び出しステートメントで明示的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7ea55-126">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="7ea55-127">式で名前を使用して呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="7ea55-127">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="7ea55-128">省略可能ではないすべての引数に値を指定する必要があり、引数リストをかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ea55-128">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="7ea55-129">引数を指定しない場合は、必要に応じてかっこを省略できます。</span><span class="sxs-lookup"><span data-stu-id="7ea55-129">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="7ea55-130">`Call` キーワードの使用は任意ですが、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ea55-130">The use of the `Call` keyword is optional but not recommended.</span></span>

<span data-ttu-id="7ea55-131">`Sub` プロシージャの呼び出しの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7ea55-131">The syntax for a call to a `Sub` procedure is as follows:</span></span>

```vb
[Call] SubName[(argumentlist)]
```

<span data-ttu-id="7ea55-132">`Sub` メソッドは、これを定義しているクラスの外部から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7ea55-132">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="7ea55-133">まず、`New` キーワードを使用してクラスのインスタンスを作成するか、クラスのインスタンスを返すメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ea55-133">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="7ea55-134">詳細については、「[New Operator (New 演算子)](../../../language-reference/operators/new-operator.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7ea55-134">For more information, see [New Operator](../../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="7ea55-135">次に、次の構文を使用して、インスタンス オブジェクトに対して `Sub` メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7ea55-135">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>

```vb
object.MethodName[(argumentList)]
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="7ea55-136">宣言と呼び出しの実例</span><span class="sxs-lookup"><span data-stu-id="7ea55-136">Illustration of declaration and call</span></span>

<span data-ttu-id="7ea55-137">次の `Sub` プロシージャは、アプリケーションが実行しようとしているタスクをコンピューターのオペレーターに通知し、タイム スタンプも表示します。</span><span class="sxs-lookup"><span data-stu-id="7ea55-137">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="7ea55-138">すべてのタスクの開始時にこのコードを複製するのではなく、アプリケーションはさまざまな場所から `tellOperator` 呼び出すだけです。</span><span class="sxs-lookup"><span data-stu-id="7ea55-138">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="7ea55-139">各呼び出しでは、開始されるタスクを識別する文字列を `task` 引数に渡します。</span><span class="sxs-lookup"><span data-stu-id="7ea55-139">Each call passes a string in the `task` argument that identifies the task being started.</span></span>

[!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]

<span data-ttu-id="7ea55-140">次の例は、`tellOperator` の一般的な呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="7ea55-140">The following example shows a typical call to `tellOperator`.</span></span>

[!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]

## <a name="see-also"></a><span data-ttu-id="7ea55-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ea55-141">See also</span></span>

- [<span data-ttu-id="7ea55-142">手順</span><span class="sxs-lookup"><span data-stu-id="7ea55-142">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7ea55-143">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="7ea55-143">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="7ea55-144">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="7ea55-144">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="7ea55-145">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="7ea55-145">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="7ea55-146">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="7ea55-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7ea55-147">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="7ea55-147">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="7ea55-148">方法: 値を返さないプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="7ea55-148">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="7ea55-149">方法: Visual Basic でイベント ハンドラーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="7ea55-149">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
