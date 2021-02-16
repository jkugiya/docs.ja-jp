---
description: '詳細情報: Visual Basic におけるステートメント'
title: ステートメント
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: 9da27c77c858075e413580047b7ed688b328c87f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436891"
---
# <a name="statements-in-visual-basic"></a><span data-ttu-id="6982f-103">Visual Basic におけるステートメント</span><span class="sxs-lookup"><span data-stu-id="6982f-103">Statements in Visual Basic</span></span>

<span data-ttu-id="6982f-104">Visual Basic におけるステートメントは完全な命令です。</span><span class="sxs-lookup"><span data-stu-id="6982f-104">A statement in Visual Basic is a complete instruction.</span></span> <span data-ttu-id="6982f-105">キーワード、演算子、変数、定数、および式を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6982f-105">It can contain keywords, operators, variables, constants, and expressions.</span></span> <span data-ttu-id="6982f-106">各ステートメントは、次のいずれかのカテゴリに属します。</span><span class="sxs-lookup"><span data-stu-id="6982f-106">Each statement belongs to one of the following categories:</span></span>

- <span data-ttu-id="6982f-107">**宣言ステートメント**。変数、定数、またはプロシージャの名前を指定します。データ型を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="6982f-107">**Declaration Statements**, which name a variable, constant, or procedure, and can also specify a data type.</span></span>

- <span data-ttu-id="6982f-108">**実行可能なステートメント**。アクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="6982f-108">**Executable Statements**, which initiate actions.</span></span> <span data-ttu-id="6982f-109">これらのステートメントでは、メソッドまたは関数を呼び出すことができ、コードのブロックをループまたは分岐できます。</span><span class="sxs-lookup"><span data-stu-id="6982f-109">These statements can call a method or function, and they can loop or branch through blocks of code.</span></span> <span data-ttu-id="6982f-110">実行可能なステートメントには、変数または定数に値または式を代入する、**代入ステートメント** が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6982f-110">Executable statements include **Assignment Statements**, which assign a value or expression to a variable or constant.</span></span>

<span data-ttu-id="6982f-111">このトピックでは、各カテゴリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6982f-111">This topic describes each category.</span></span> <span data-ttu-id="6982f-112">また、このトピックでは、複数のステートメントを 1 行に結合する方法と、複数の行にわたってステートメントを続ける方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6982f-112">Also, this topic describes how to combine multiple statements on a single line and how to continue a statement over multiple lines.</span></span>

## <a name="declaration-statements"></a><span data-ttu-id="6982f-113">宣言ステートメント</span><span class="sxs-lookup"><span data-stu-id="6982f-113">Declaration statements</span></span>

<span data-ttu-id="6982f-114">宣言ステートメントを使用して、プロシージャ、変数、プロパティ、配列、および定数の名前を指定して定義します。</span><span class="sxs-lookup"><span data-stu-id="6982f-114">You use declaration statements to name and define procedures, variables, properties, arrays, and constants.</span></span> <span data-ttu-id="6982f-115">プログラミング要素を宣言するときに、そのデータ型、アクセス レベル、およびスコープを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="6982f-115">When you declare a programming element, you can also define its data type, access level, and scope.</span></span> <span data-ttu-id="6982f-116">詳細については、「[宣言された要素の特性](./declared-elements/declared-element-characteristics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-116">For more information, see [Declared Element Characteristics](./declared-elements/declared-element-characteristics.md).</span></span>

<span data-ttu-id="6982f-117">次の例には 3 つの宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6982f-117">The following example contains three declarations.</span></span>

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

<span data-ttu-id="6982f-118">最初の宣言は、`Sub` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="6982f-118">The first declaration is the `Sub` statement.</span></span> <span data-ttu-id="6982f-119">それに対応する `End Sub` ステートメントと共に、`applyFormat` という名前のプロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="6982f-119">Together with its matching `End Sub` statement, it declares a procedure named `applyFormat`.</span></span> <span data-ttu-id="6982f-120">また、`applyFormat` が `Public` であることを示します。これは、それを参照できるすべてのコードでそれを呼び出せることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6982f-120">It also specifies that `applyFormat` is `Public`, which means that any code that can refer to it can call it.</span></span>

<span data-ttu-id="6982f-121">2 番目の宣言は `Const` ステートメントであり、`Integer` データ型と 33 の値を指定して、定数 `limit` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="6982f-121">The second declaration is the `Const` statement, which declares the constant `limit`, specifying the `Integer` data type and a value of 33.</span></span>

<span data-ttu-id="6982f-122">3 番目の宣言は、変数 `thisWidget` を宣言する、`Dim` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="6982f-122">The third declaration is the `Dim` statement, which declares the variable `thisWidget`.</span></span> <span data-ttu-id="6982f-123">データ型は特定のオブジェクト、つまり、`Widget` クラスから作成されるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="6982f-123">The data type is a specific object, namely an object created from the `Widget` class.</span></span> <span data-ttu-id="6982f-124">任意の基本データ型、または使用しているアプリケーションで公開される任意のオブジェクト型の変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="6982f-124">You can declare a variable to be of any elementary data type or of any object type that is exposed in the application you are using.</span></span>

### <a name="initial-values"></a><span data-ttu-id="6982f-125">初期値</span><span class="sxs-lookup"><span data-stu-id="6982f-125">Initial Values</span></span>

<span data-ttu-id="6982f-126">宣言ステートメントを含むコードが実行されると、Visual Basic で、宣言された要素に必要なメモリが予約されます。</span><span class="sxs-lookup"><span data-stu-id="6982f-126">When the code containing a declaration statement runs, Visual Basic reserves the memory required for the declared element.</span></span> <span data-ttu-id="6982f-127">要素に値が保持されている場合、Visual Basic によって、そのデータ型の既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="6982f-127">If the element holds a value, Visual Basic initializes it to the default value for its data type.</span></span> <span data-ttu-id="6982f-128">詳細については、「[Dim ステートメント](../../language-reference/statements/dim-statement.md)」の "動作" に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-128">For more information, see "Behavior" in [Dim Statement](../../language-reference/statements/dim-statement.md).</span></span>

<span data-ttu-id="6982f-129">次の例に示すように、変数には、その宣言の一部として初期値を代入することができます。</span><span class="sxs-lookup"><span data-stu-id="6982f-129">You can assign an initial value to a variable as part of its declaration, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

<span data-ttu-id="6982f-130">変数がオブジェクト変数である場合は、次の例に示すように、[New 演算子](../../language-reference/operators/new-operator.md)キーワードを使用して宣言するときに、そのクラスのインスタンスを明示的に作成できます。</span><span class="sxs-lookup"><span data-stu-id="6982f-130">If a variable is an object variable, you can explicitly create an instance of its class when you declare it by using the [New Operator](../../language-reference/operators/new-operator.md) keyword, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

<span data-ttu-id="6982f-131">宣言ステートメントで指定する初期値は、実行がその宣言ステートメントに到達するまで変数に代入されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-131">Note that the initial value you specify in a declaration statement is not assigned to a variable until execution reaches its declaration statement.</span></span> <span data-ttu-id="6982f-132">それまでは、変数にそのデータ型の既定値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6982f-132">Until that time, the variable contains the default value for its data type.</span></span>

## <a name="executable-statements"></a><span data-ttu-id="6982f-133">実行可能なステートメント</span><span class="sxs-lookup"><span data-stu-id="6982f-133">Executable statements</span></span>

<span data-ttu-id="6982f-134">実行可能なステートメントでアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6982f-134">An executable statement performs an action.</span></span> <span data-ttu-id="6982f-135">プロシージャを呼び出したり、コード内の別の場所に分岐したり、複数のステートメントをループしたり、式を評価したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="6982f-135">It can call a procedure, branch to another place in the code, loop through several statements, or evaluate an expression.</span></span> <span data-ttu-id="6982f-136">代入ステートメントは、実行可能なステートメントの特殊なケースです。</span><span class="sxs-lookup"><span data-stu-id="6982f-136">An assignment statement is a special case of an executable statement.</span></span>

<span data-ttu-id="6982f-137">次の例では、`If...Then...Else` 制御構造を使用して、変数の値に基づいてさまざまなコード ブロックを実行します。</span><span class="sxs-lookup"><span data-stu-id="6982f-137">The following example uses an `If...Then...Else` control structure to run different blocks of code based on the value of a variable.</span></span> <span data-ttu-id="6982f-138">各コード ブロック内では、`For...Next` ループが指定された回数だけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="6982f-138">Within each block of code, a `For...Next` loop runs a specified number of times.</span></span>

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

<span data-ttu-id="6982f-139">前の例の `If` ステートメントでは、パラメーター `clockwise` の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="6982f-139">The `If` statement in the preceding example checks the value of the parameter `clockwise`.</span></span> <span data-ttu-id="6982f-140">値が `True` である場合は、`aWidget` の `spinClockwise` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6982f-140">If the value is `True`, it calls the `spinClockwise` method of `aWidget`.</span></span> <span data-ttu-id="6982f-141">値が `False` である場合は、`aWidget` の `spinCounterClockwise` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6982f-141">If the value is `False`, it calls the `spinCounterClockwise` method of `aWidget`.</span></span> <span data-ttu-id="6982f-142">`If...Then...Else` 制御構造は、`End If` で終わります。</span><span class="sxs-lookup"><span data-stu-id="6982f-142">The `If...Then...Else` control structure ends with `End If`.</span></span>

<span data-ttu-id="6982f-143">各ブロック内の `For...Next` ループでは、`revolutions` パラメーターの値と等しい回数だけ、適切なメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6982f-143">The `For...Next` loop within each block calls the appropriate method a number of times equal to the value of the `revolutions` parameter.</span></span>

## <a name="assignment-statements"></a><span data-ttu-id="6982f-144">代入ステートメント</span><span class="sxs-lookup"><span data-stu-id="6982f-144">Assignment statements</span></span>

<span data-ttu-id="6982f-145">代入ステートメントでは、次の例のように、代入演算子 (`=`) の右辺の値を取り、左側の要素に格納することで構成される代入演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="6982f-145">Assignment statements carry out assignment operations, which consist of taking the value on the right side of the assignment operator (`=`) and storing it in the element on the left, as in the following example.</span></span>

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

<span data-ttu-id="6982f-146">前の例の代入ステートメントでは、リテラル値 42 が変数 `v` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="6982f-146">In the preceding example, the assignment statement stores the literal value 42 in the variable `v`.</span></span>

### <a name="eligible-programming-elements"></a><span data-ttu-id="6982f-147">対象となるプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="6982f-147">Eligible programming elements</span></span>

<span data-ttu-id="6982f-148">代入演算子の左辺のプログラミング要素では、値を受け入れて格納できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6982f-148">The programming element on the left side of the assignment operator must be able to accept and store a value.</span></span> <span data-ttu-id="6982f-149">これは、[ReadOnly](../../language-reference/modifiers/readonly.md) ではない変数またはプロパティである必要があるか、あるいは配列要素である必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6982f-149">This means it must be a variable or property that is not [ReadOnly](../../language-reference/modifiers/readonly.md), or it must be an array element.</span></span> <span data-ttu-id="6982f-150">代入ステートメントのコンテキストでは、このような要素は、"左辺値" の場合、*lvalue* と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="6982f-150">In the context of an assignment statement, such an element is sometimes called an *lvalue*, for "left value."</span></span>

<span data-ttu-id="6982f-151">代入演算子の右辺の値は、式によって生成されます。これは、リテラル、定数、変数、プロパティ、配列要素、その他の式、または関数呼び出しの任意の組み合わせで構成できます。</span><span class="sxs-lookup"><span data-stu-id="6982f-151">The value on the right side of the assignment operator is generated by an expression, which can consist of any combination of literals, constants, variables, properties, array elements, other expressions, or function calls.</span></span> <span data-ttu-id="6982f-152">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-152">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

<span data-ttu-id="6982f-153">前の例では、変数 `y` に保持されている値を、変数 `z` に保持されている値に追加してから、関数 `findResult` への呼び出しによって返される値を追加します。</span><span class="sxs-lookup"><span data-stu-id="6982f-153">The preceding example adds the value held in variable `y` to the value held in variable `z`, and then adds the value returned by the call to function `findResult`.</span></span> <span data-ttu-id="6982f-154">その後、この式の合計値は、変数 `x` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="6982f-154">The total value of this expression is then stored in variable `x`.</span></span>

### <a name="data-types-in-assignment-statements"></a><span data-ttu-id="6982f-155">代入ステートメントのデータ型</span><span class="sxs-lookup"><span data-stu-id="6982f-155">Data types in assignment statements</span></span>

<span data-ttu-id="6982f-156">次の例に示すように、代入演算子では、数値に加え、`String` 値も代入することができます。</span><span class="sxs-lookup"><span data-stu-id="6982f-156">In addition to numeric values, the assignment operator can also assign `String` values, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

<span data-ttu-id="6982f-157">次の例に示すように、`Boolean` リテラルまたは `Boolean` 式を使用して、`Boolean` 値を代入することもできます。</span><span class="sxs-lookup"><span data-stu-id="6982f-157">You can also assign `Boolean` values, using either a `Boolean` literal or a `Boolean` expression, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

<span data-ttu-id="6982f-158">同様に、`Char`、`Date`、または `Object` データ型のプログラミング要素に適切な値を代入することができます。</span><span class="sxs-lookup"><span data-stu-id="6982f-158">Similarly, you can assign appropriate values to programming elements of the `Char`, `Date`, or `Object` data type.</span></span> <span data-ttu-id="6982f-159">また、インスタンスの作成元のクラスとして宣言された要素に、オブジェクト インスタンスを代入することができます。</span><span class="sxs-lookup"><span data-stu-id="6982f-159">You can also assign an object instance to an element declared to be of the class from which that instance is created.</span></span>

### <a name="compound-assignment-statements"></a><span data-ttu-id="6982f-160">複合代入ステートメント</span><span class="sxs-lookup"><span data-stu-id="6982f-160">Compound assignment statements</span></span>

<span data-ttu-id="6982f-161">"*複合代入ステートメント*" では、最初に式で演算を行ってから、プログラミング要素に代入します。</span><span class="sxs-lookup"><span data-stu-id="6982f-161">*Compound assignment statements* first perform an operation on an expression before assigning it to a programming element.</span></span> <span data-ttu-id="6982f-162">次の例では、演算子の左辺の変数値を、右側の式の値でインクリメントする、これらの `+=` の演算子を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-162">The following example illustrates one of these operators, `+=`, which increments the value of the variable on the left side of the operator by the value of the expression on the right.</span></span>

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

<span data-ttu-id="6982f-163">前の例では、`n` の値に 1 を加算してから、その新しい値を `n` に格納します。</span><span class="sxs-lookup"><span data-stu-id="6982f-163">The preceding example adds 1 to the value of `n`, and then stores that new value in `n`.</span></span> <span data-ttu-id="6982f-164">これは、次のステートメントに相当する短縮形です。</span><span class="sxs-lookup"><span data-stu-id="6982f-164">It is a shorthand equivalent of the following statement:</span></span>

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

<span data-ttu-id="6982f-165">この型の演算子を使用することで、さまざまな複合代入演算を実行できます。</span><span class="sxs-lookup"><span data-stu-id="6982f-165">A variety of compound assignment operations can be performed using operators of this type.</span></span> <span data-ttu-id="6982f-166">これらの演算子の一覧と詳細については、「[代入演算子](../../language-reference/operators/assignment-operators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-166">For a list of these operators and more information about them, see [Assignment Operators](../../language-reference/operators/assignment-operators.md).</span></span>

<span data-ttu-id="6982f-167">連結代入演算子 (`&=`) は、次の例に示すように、既存の文字列の末尾に文字列を追加する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="6982f-167">The concatenation assignment operator (`&=`) is useful for adding a string to the end of already existing strings, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a><span data-ttu-id="6982f-168">代入ステートメントでの型変換</span><span class="sxs-lookup"><span data-stu-id="6982f-168">Type Conversions in Assignment Statements</span></span>

<span data-ttu-id="6982f-169">変数、プロパティ、または配列要素に代入する値は、そのターゲット要素に適したデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6982f-169">The value you assign to a variable, property, or array element must be of a data type appropriate to that destination element.</span></span> <span data-ttu-id="6982f-170">一般には、ターゲット要素と同じデータ型の値の生成を試みることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6982f-170">In general, you should try to generate a value of the same data type as that of the destination element.</span></span> <span data-ttu-id="6982f-171">しかし、代入時に他の型に変換できる型もあります。</span><span class="sxs-lookup"><span data-stu-id="6982f-171">However, some types can be converted to other types during assignment.</span></span>

<span data-ttu-id="6982f-172">データ型間の変換については、「[Visual Basic における型変換](./data-types/type-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-172">For information on converting between data types, see [Type Conversions in Visual Basic](./data-types/type-conversions.md).</span></span> <span data-ttu-id="6982f-173">簡単に言えば、Visual Basic では、指定された型の値を、拡大変換される他の型に自動的に変換します。</span><span class="sxs-lookup"><span data-stu-id="6982f-173">In brief, Visual Basic automatically converts a value of a given type to any other type to which it widens.</span></span> <span data-ttu-id="6982f-174">"*拡大変換*" は、実行時に常に成功し、データが失われないものです。</span><span class="sxs-lookup"><span data-stu-id="6982f-174">A *widening conversion* is one in that always succeeds at run time and does not lose any data.</span></span> <span data-ttu-id="6982f-175">たとえば、Visual Basic では、必要に応じて、`Integer` 値を `Double` に変換します。これは、`Integer` が `Double` に拡大変換されるためです。</span><span class="sxs-lookup"><span data-stu-id="6982f-175">For example, Visual Basic converts an `Integer` value to `Double` when appropriate, because `Integer` widens to `Double`.</span></span> <span data-ttu-id="6982f-176">詳細については、「 [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-176">For more information, see [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="6982f-177">*縮小変換* (拡大しないもの) は、実行時の失敗、あるいはデータ損失のリスクを伴います。</span><span class="sxs-lookup"><span data-stu-id="6982f-177">*Narrowing conversions* (those that are not widening) carry a risk of failure at run time, or of data loss.</span></span> <span data-ttu-id="6982f-178">型変換関数を使用して、縮小変換を明示的に実行することも、`Option Strict Off` を設定して、暗黙的にすべての変換を実行するようにコンパイラに指示することもできます。</span><span class="sxs-lookup"><span data-stu-id="6982f-178">You can perform a narrowing conversion explicitly by using a type conversion function, or you can direct the compiler to perform all conversions implicitly by setting `Option Strict Off`.</span></span> <span data-ttu-id="6982f-179">詳細については、「[暗黙の型変換と明示的な型変換](./data-types/implicit-and-explicit-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-179">For more information, see [Implicit and Explicit Conversions](./data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="putting-multiple-statements-on-one-line"></a><span data-ttu-id="6982f-180">1 行に複数のステートメントを配置する</span><span class="sxs-lookup"><span data-stu-id="6982f-180">Putting multiple statements on one line</span></span>

<span data-ttu-id="6982f-181">1 行に複数のステートメントを配置し、コロン (`:`) 文字で区切ることができます。</span><span class="sxs-lookup"><span data-stu-id="6982f-181">You can have multiple statements on a single line separated by the colon (`:`) character.</span></span> <span data-ttu-id="6982f-182">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-182">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

<span data-ttu-id="6982f-183">この形式の構文は、便利な場合もありますが、コードを読んだり、保持することが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="6982f-183">Though occasionally convenient, this form of syntax makes your code hard to read and maintain.</span></span> <span data-ttu-id="6982f-184">したがって、1 つのステートメントを 1 行に収めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6982f-184">Thus, it is recommended that you keep one statement to a line.</span></span>

## <a name="continuing-a-statement-over-multiple-lines"></a><span data-ttu-id="6982f-185">複数行にわたってステートメントを続ける</span><span class="sxs-lookup"><span data-stu-id="6982f-185">Continuing a statement over multiple lines</span></span>

<span data-ttu-id="6982f-186">ステートメントは通常、1 行に収まりますが、長すぎる場合は、行連結シーケンスを使用して、次の行に続けることができます。これは、スペース、その後に続くアンダースコア文字 (`_`)、さらにその後に続く復帰で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6982f-186">A statement usually fits on one line, but when it is too long, you can continue it onto the next line using a line-continuation sequence, which consists of a space followed by an underscore character (`_`) followed by a carriage return.</span></span> <span data-ttu-id="6982f-187">次の例では、`MsgBox` の実行可能なステートメントは 2 行にわたって続きます。</span><span class="sxs-lookup"><span data-stu-id="6982f-187">In the following example, the `MsgBox` executable statement is continued over two lines.</span></span>

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a><span data-ttu-id="6982f-188">暗黙的な行連結</span><span class="sxs-lookup"><span data-stu-id="6982f-188">Implicit line continuation</span></span>

<span data-ttu-id="6982f-189">多くの場合、アンダースコア文字 (`_`) を使用せずに、次の連続する行にステートメントを続けることができます。</span><span class="sxs-lookup"><span data-stu-id="6982f-189">In many cases, you can continue a statement on the next consecutive line without using the underscore character (`_`).</span></span> <span data-ttu-id="6982f-190">以下の構文要素では、暗黙的にステートメントを次のコード行に続けます。</span><span class="sxs-lookup"><span data-stu-id="6982f-190">The following syntax elements implicitly continue the statement on the next line of code.</span></span>

- <span data-ttu-id="6982f-191">コンマ (`,`) の後。</span><span class="sxs-lookup"><span data-stu-id="6982f-191">After a comma (`,`).</span></span> <span data-ttu-id="6982f-192">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-192">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- <span data-ttu-id="6982f-193">開きかっこ (`(`) の後、または閉じかっこ (`)`) の前。</span><span class="sxs-lookup"><span data-stu-id="6982f-193">After an open parenthesis (`(`) or before a closing parenthesis (`)`).</span></span> <span data-ttu-id="6982f-194">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-194">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- <span data-ttu-id="6982f-195">左中かっこ (`{`) の後、または右中かっこ (`}`) の前。</span><span class="sxs-lookup"><span data-stu-id="6982f-195">After an open curly brace (`{`) or before a closing curly brace (`}`).</span></span> <span data-ttu-id="6982f-196">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-196">For example:</span></span>

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    <span data-ttu-id="6982f-197">詳細については、「[オブジェクト初期化子: 名前付きの型と匿名型](./objects-and-classes/object-initializers-named-and-anonymous-types.md)」または「[コレクション初期化子](./collection-initializers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-197">For more information, see [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md) or [Collection Initializers](./collection-initializers/index.md).</span></span>

- <span data-ttu-id="6982f-198">XML リテラル内の開始埋め込み式 (`<%=`) の後、または埋め込み式の終了 (`%>`) の前。</span><span class="sxs-lookup"><span data-stu-id="6982f-198">After an open embedded expression (`<%=`) or before the close of an embedded expression (`%>`) within an XML literal.</span></span> <span data-ttu-id="6982f-199">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-199">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   <span data-ttu-id="6982f-200">詳細については、「[XML での埋め込み式](./xml/embedded-expressions-in-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-200">For more information, see [Embedded Expressions in XML](./xml/embedded-expressions-in-xml.md).</span></span>

- <span data-ttu-id="6982f-201">連結演算子 (`&`) の後。</span><span class="sxs-lookup"><span data-stu-id="6982f-201">After the concatenation operator (`&`).</span></span> <span data-ttu-id="6982f-202">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-202">For example:</span></span>

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   <span data-ttu-id="6982f-203">詳細については、「[機能別の演算子一覧](../../language-reference/operators/operators-listed-by-functionality.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-203">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="6982f-204">代入演算子 (`=`、`&=`、`:=`、`+=`、`-=`、`*=`、`/=`、`\=`、`^=`、`<<=`、`>>=`) の後。</span><span class="sxs-lookup"><span data-stu-id="6982f-204">After assignment operators (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).</span></span> <span data-ttu-id="6982f-205">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-205">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="6982f-206">詳細については、「[機能別の演算子一覧](../../language-reference/operators/operators-listed-by-functionality.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-206">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="6982f-207">式内の 2 項演算子 (`+`、`-`、`/`、`*`、`Mod`、`<>`、`<`、`>`、`<=`、`>=`、`^`、`>>`、`<<`、`And`、`AndAlso`、`Or`、`OrElse`、`Like`、`Xor`) の後。</span><span class="sxs-lookup"><span data-stu-id="6982f-207">After binary operators (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) within an expression.</span></span> <span data-ttu-id="6982f-208">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-208">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   <span data-ttu-id="6982f-209">詳細については、「[機能別の演算子一覧](../../language-reference/operators/operators-listed-by-functionality.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-209">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="6982f-210">`Is` および `IsNot` 演算子の後。</span><span class="sxs-lookup"><span data-stu-id="6982f-210">After the `Is` and `IsNot` operators.</span></span> <span data-ttu-id="6982f-211">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-211">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   <span data-ttu-id="6982f-212">詳細については、「[機能別の演算子一覧](../../language-reference/operators/operators-listed-by-functionality.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-212">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="6982f-213">メンバー修飾子文字 (`.`) の後、およびメンバー名の前。</span><span class="sxs-lookup"><span data-stu-id="6982f-213">After a member qualifier character (`.`) and before the member name.</span></span> <span data-ttu-id="6982f-214">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-214">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="6982f-215">しかし、`With` ステートメントを使用する場合、または型の初期化一覧に値を指定する場合は、メンバー修飾子文字の後に行連結文字 (`_`) を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="6982f-215">However, you must include a line-continuation character (`_`) following a member qualifier character when you are using the `With` statement or supplying values in the initialization list for a type.</span></span> <span data-ttu-id="6982f-216">`With` ステートメントまたはオブジェクト初期化一覧を使用する場合は、代入演算子 (`=` など) の後で改行することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-216">Consider breaking the line after the assignment operator (for example, `=`) when you are using `With` statements or object initialization lists.</span></span> <span data-ttu-id="6982f-217">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-217">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   <span data-ttu-id="6982f-218">詳細については、「[With...End With ステートメント](../../language-reference/statements/with-end-with-statement.md)」または「[オブジェクト初期化子: 名前付きの型と匿名型](./objects-and-classes/object-initializers-named-and-anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-218">For more information, see [With...End With Statement](../../language-reference/statements/with-end-with-statement.md) or [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

- <span data-ttu-id="6982f-219">XML 軸プロパティの修飾子 (`.`、`.@` または `...`) の後。</span><span class="sxs-lookup"><span data-stu-id="6982f-219">After an XML axis property qualifier (`.` or `.@` or `...`).</span></span> <span data-ttu-id="6982f-220">しかし、`With` キーワードを使用する場合は、メンバー修飾子を指定するときに行連結文字 (`_`) を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="6982f-220">However, you must include a line-continuation character (`_`) when you specify a member qualifier when you are using the `With` keyword.</span></span> <span data-ttu-id="6982f-221">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-221">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   <span data-ttu-id="6982f-222">詳細については、「[XML 軸プロパティ](../../language-reference/xml-axis/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-222">For more information, see [XML Axis Properties](../../language-reference/xml-axis/index.md).</span></span>

- <span data-ttu-id="6982f-223">属性を指定する場合は、小なり記号 (<) の後、または大なり記号 (`>`) の前。</span><span class="sxs-lookup"><span data-stu-id="6982f-223">After a less-than sign (<) or before a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="6982f-224">また、属性を指定する場合は、大なり記号 (`>`) の後。</span><span class="sxs-lookup"><span data-stu-id="6982f-224">Also after a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="6982f-225">しかし、アセンブリ レベルまたはモジュール レベルの属性を指定する場合は、行連結文字 (`_`) を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="6982f-225">However, you must include a line-continuation character (`_`) when you specify assembly-level or module-level attributes.</span></span> <span data-ttu-id="6982f-226">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-226">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   <span data-ttu-id="6982f-227">詳細については、「[属性の概要](../concepts/attributes/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-227">For more information, see [Attributes overview](../concepts/attributes/index.md).</span></span>

- <span data-ttu-id="6982f-228">クエリ演算子 (`Aggregate`、`Distinct`、`From`、`Group By`、`Group Join`、`Join`、`Let`、`Order By`、`Select`、`Skip`、`Skip While`、`Take`、`Take While`、`Where`、`In`、`Into`、`On`、`Ascending`、および `Descending`) の前か後。</span><span class="sxs-lookup"><span data-stu-id="6982f-228">Before and after query operators (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, and `Descending`).</span></span> <span data-ttu-id="6982f-229">複数のキーワードで構成されているクエリ演算子 (`Order By`、`Group Join`、`Take While`、および `Skip While`) のキーワードの間で改行することはできません。</span><span class="sxs-lookup"><span data-stu-id="6982f-229">You cannot break a line between the keywords of query operators that are made up of multiple keywords (`Order By`, `Group Join`, `Take While`, and `Skip While`).</span></span> <span data-ttu-id="6982f-230">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-230">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   <span data-ttu-id="6982f-231">詳細については、「[クエリ](../../language-reference/queries/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-231">For more information, see [Queries](../../language-reference/queries/index.md).</span></span>

- <span data-ttu-id="6982f-232">`For Each` ステートメント内の `In` キーワードの後。</span><span class="sxs-lookup"><span data-stu-id="6982f-232">After the `In` keyword in a `For Each` statement.</span></span> <span data-ttu-id="6982f-233">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-233">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   <span data-ttu-id="6982f-234">詳細については、[For Each...Next ステートメント](../../language-reference/statements/for-each-next-statement.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-234">For more information, see [For Each...Next Statement](../../language-reference/statements/for-each-next-statement.md).</span></span>

- <span data-ttu-id="6982f-235">コレクション初期化子内の `From` キーワードの後。</span><span class="sxs-lookup"><span data-stu-id="6982f-235">After the `From` keyword in a collection initializer.</span></span> <span data-ttu-id="6982f-236">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-236">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   <span data-ttu-id="6982f-237">詳細については、「[コレクション初期化子](collection-initializers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6982f-237">For more information, see [Collection Initializers](collection-initializers/index.md).</span></span>

## <a name="adding-comments"></a><span data-ttu-id="6982f-238">コメントの追加</span><span class="sxs-lookup"><span data-stu-id="6982f-238">Adding comments</span></span>

<span data-ttu-id="6982f-239">ソース コードは、それを記述したプログラマであっても、見ればすぐわかるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="6982f-239">Source code is not always self-explanatory, even to the programmer who wrote it.</span></span> <span data-ttu-id="6982f-240">そのため、コードの文書化に役立つように、ほとんどのプログラマは埋め込みコメントを十分に利用します。</span><span class="sxs-lookup"><span data-stu-id="6982f-240">To help document their code, therefore, most programmers make liberal use of embedded comments.</span></span> <span data-ttu-id="6982f-241">コード内のコメントでは、後でそれを読んだり、操作を行うすべてのユーザーに対して、プロシージャまたは特定の命令について説明することができます。</span><span class="sxs-lookup"><span data-stu-id="6982f-241">Comments in code can explain a procedure or a particular instruction to anyone reading or working with it later.</span></span> <span data-ttu-id="6982f-242">Visual Basic では、コンパイル時にコメントが無視され、コンパイルされたコードには影響しません。</span><span class="sxs-lookup"><span data-stu-id="6982f-242">Visual Basic ignores comments during compilation, and they do not affect the compiled code.</span></span>

<span data-ttu-id="6982f-243">コメント行はアポストロフィ (`'`) または `REM` で始まり、その後にスペースが続きます。</span><span class="sxs-lookup"><span data-stu-id="6982f-243">Comment lines begin with an apostrophe (`'`) or `REM` followed by a space.</span></span> <span data-ttu-id="6982f-244">文字列内の場合を除き、コード内の任意の場所に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="6982f-244">They can be added anywhere in code, except within a string.</span></span> <span data-ttu-id="6982f-245">ステートメントにコメントを追加するには、ステートメントの後にアポストロフィまたは `REM` を挿入し、その後にコメントを続けます。</span><span class="sxs-lookup"><span data-stu-id="6982f-245">To append a comment to a statement, insert an apostrophe or `REM` after the statement, followed by the comment.</span></span> <span data-ttu-id="6982f-246">コメントを独自の行に続けることもできます。</span><span class="sxs-lookup"><span data-stu-id="6982f-246">Comments can also go on their own separate line.</span></span> <span data-ttu-id="6982f-247">これらの考えられる例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-247">The following example demonstrates these possibilities.</span></span>

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a><span data-ttu-id="6982f-248">コンパイル エラーの確認</span><span class="sxs-lookup"><span data-stu-id="6982f-248">Checking compilation errors</span></span>

<span data-ttu-id="6982f-249">コード行を入力した後、その行の下に青い破線が表示されている場合 (エラー メッセージも表示される場合があります)、ステートメントに構文エラーがあります。</span><span class="sxs-lookup"><span data-stu-id="6982f-249">If, after you type a line of code, the line is displayed with a wavy blue underline (an error message may appear as well), there is a syntax error in the statement.</span></span> <span data-ttu-id="6982f-250">ステートメントの問題を確認し (タスク一覧を調べるか、マウス ポインターでエラーをポイントしてエラー メッセージを読んで)、修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6982f-250">You must find out what is wrong with the statement (by looking in the task list, or hovering over the error with the mouse pointer and reading the error message) and correct it.</span></span> <span data-ttu-id="6982f-251">コード内の構文エラーをすべて修正するまで、プログラムでは正しくコンパイルできません。</span><span class="sxs-lookup"><span data-stu-id="6982f-251">Until you have fixed all syntax errors in your code, your program will fail to compile correctly.</span></span>

## <a name="related-sections"></a><span data-ttu-id="6982f-252">関連項目</span><span class="sxs-lookup"><span data-stu-id="6982f-252">Related sections</span></span>

|<span data-ttu-id="6982f-253">用語</span><span class="sxs-lookup"><span data-stu-id="6982f-253">Term</span></span>|<span data-ttu-id="6982f-254">定義</span><span class="sxs-lookup"><span data-stu-id="6982f-254">Definition</span></span>|
|---|---|
|[<span data-ttu-id="6982f-255">代入演算子</span><span class="sxs-lookup"><span data-stu-id="6982f-255">Assignment Operators</span></span>](../../language-reference/operators/assignment-operators.md)|<span data-ttu-id="6982f-256">`=`、`*=`、`&=` などの代入演算子に関する言語リファレンス ページへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="6982f-256">Provides links to language reference pages covering assignment operators such as `=`, `*=`, and `&=`.</span></span>|
|[<span data-ttu-id="6982f-257">演算子および式</span><span class="sxs-lookup"><span data-stu-id="6982f-257">Operators and Expressions</span></span>](./operators-and-expressions/index.md)|<span data-ttu-id="6982f-258">要素を演算子と組み合わせて新しい値を生成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-258">Shows how to combine elements with operators to yield new values.</span></span>|
|[<span data-ttu-id="6982f-259">方法: コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="6982f-259">How to: Break and Combine Statements in Code</span></span>](../program-structure/how-to-break-and-combine-statements-in-code.md)|<span data-ttu-id="6982f-260">1 つのステートメントを複数の行に分割する方法と、複数のステートメントを同じ行に配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-260">Shows how to break a single statement into multiple lines and how to place multiple statements on the same line.</span></span>|
|[<span data-ttu-id="6982f-261">方法: ステートメントへのラベル付け</span><span class="sxs-lookup"><span data-stu-id="6982f-261">How to: Label Statements</span></span>](../program-structure/how-to-label-statements.md)|<span data-ttu-id="6982f-262">コード行にラベルを付ける方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6982f-262">Shows how to label a line of code.</span></span>|
