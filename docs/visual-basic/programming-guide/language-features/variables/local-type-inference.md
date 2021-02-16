---
description: '詳細情報: ローカル型の推論 (Visual Basic)'
title: ローカル型の推論
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: 50be8544229360287d2aef27f31360d7140640ac
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481702"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="bc502-103">ローカル型の推論 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc502-103">Local Type Inference (Visual Basic)</span></span>

<span data-ttu-id="bc502-104">Visual Basic コンパイラは、"*型推論*" を使用し、`As` 句を使用しないで宣言されたローカル変数のデータ型を判定します。</span><span class="sxs-lookup"><span data-stu-id="bc502-104">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="bc502-105">コンパイラは、初期化式の型から変数の型を推論します。</span><span class="sxs-lookup"><span data-stu-id="bc502-105">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="bc502-106">これにより、次の例で示すように、明示的に型を指定せずに変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="bc502-106">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="bc502-107">この宣言の結果として、`num1` と `num2` の両方が整数として厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="bc502-107">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="bc502-108">前の例の `num2` を `Integer` として型指定しない場合は、`Dim num3 As Object = 3` や `Dim num4 As Double = 3` などの宣言を使用して別の型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bc502-108">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>

> [!NOTE]
> <span data-ttu-id="bc502-109">型推論は、非静的なローカル変数に対してのみ使用できます。クラス フィールド、プロパティ、または関数の型を判定するために使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="bc502-109">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>

<span data-ttu-id="bc502-110">ローカル型推論は、プロシージャ レベルで適用されます。</span><span class="sxs-lookup"><span data-stu-id="bc502-110">Local type inference applies at procedure level.</span></span> <span data-ttu-id="bc502-111">モジュール レベル (プロシージャまたはブロック内ではなく、クラス、構造体、モジュール、またはインターフェイス内) での変数の宣言に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="bc502-111">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="bc502-112">前述の例の `num2` が、プロシージャ内のローカル変数ではなくクラスのフィールドである場合、`Option Strict` が on に設定されている場合は宣言でエラーが発生し、`Option Strict` が off に設定されている場合は `num2` が `Object` として分類されます。</span><span class="sxs-lookup"><span data-stu-id="bc502-112">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="bc502-113">同様に、ローカル型推論は、`Static` として宣言されたプロシージャ レベルの変数に適用されません。</span><span class="sxs-lookup"><span data-stu-id="bc502-113">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>

## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="bc502-114">型推論と遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="bc502-114">Type Inference vs. Late Binding</span></span>

<span data-ttu-id="bc502-115">型推論を使用するコードは、遅延バインディングに依存するコードに似ています。</span><span class="sxs-lookup"><span data-stu-id="bc502-115">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="bc502-116">ただし、型推論では、変数は `Object` のままではなく、厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="bc502-116">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="bc502-117">コンパイラは、コンパイル時に変数の初期化子を使用して変数の型を判定し、事前バインド コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="bc502-117">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="bc502-118">前述の例では、`num2` は、`num1` と同様、`Integer` として型指定されます。</span><span class="sxs-lookup"><span data-stu-id="bc502-118">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>

<span data-ttu-id="bc502-119">事前バインド変数の動作は、型が実行時にしか認識されない遅延バインド変数の動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="bc502-119">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="bc502-120">型が早期に認識されることにより、コンパイラは、実行前に問題を特定し、メモリを正確に割り当て、その他の最適化も行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bc502-120">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="bc502-121">また、事前バインディングにより、Visual Basic 統合開発環境 (IDE) では、オブジェクトのメンバーに関する IntelliSense ヘルプを提供できます。</span><span class="sxs-lookup"><span data-stu-id="bc502-121">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="bc502-122">事前バインディングは、パフォーマンスのためにも推奨されます。</span><span class="sxs-lookup"><span data-stu-id="bc502-122">Early binding is also preferred for performance.</span></span> <span data-ttu-id="bc502-123">遅延バインド変数に格納されるデータはすべて `Object` 型としてラップする必要があり、実行時にその型のメンバーにアクセスすると、プログラムの速度が低下するためです。</span><span class="sxs-lookup"><span data-stu-id="bc502-123">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>

## <a name="examples"></a><span data-ttu-id="bc502-124">使用例</span><span class="sxs-lookup"><span data-stu-id="bc502-124">Examples</span></span>

<span data-ttu-id="bc502-125">型推論は、ローカル変数が `As` 句を使用しないで宣言され、初期化されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="bc502-125">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="bc502-126">コンパイラは、割り当てられた初期値の型を変数の型として使用します。</span><span class="sxs-lookup"><span data-stu-id="bc502-126">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="bc502-127">たとえば、次のコード行はそれぞれ、`String` 型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="bc502-127">For example, each of the following lines of code declares a variable of type `String`.</span></span>

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

<span data-ttu-id="bc502-128">次のコードは、同じ整数の配列を作成する 2 通りの同等の方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc502-128">The following code demonstrates two equivalent ways to create an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

<span data-ttu-id="bc502-129">ループ制御変数の型を判定するには、型推論を使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="bc502-129">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="bc502-130">次のコードでは、前述の例の `someNumbers2` が整数の配列であるため、コンパイラは、`number` が `Integer` であると推論します。</span><span class="sxs-lookup"><span data-stu-id="bc502-130">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

<span data-ttu-id="bc502-131">次の例で示すように、ローカル型推論を `Using` ステートメントで使用して、リソース名の型を確定することができます。</span><span class="sxs-lookup"><span data-stu-id="bc502-131">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

<span data-ttu-id="bc502-132">次の例で示すように、変数の型を関数の戻り値から推論することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc502-132">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="bc502-133">`Process.GetProcesses` はプロセスの配列を返すため、`pList1` と `pList2` は両方ともプロセスの配列です。</span><span class="sxs-lookup"><span data-stu-id="bc502-133">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a><span data-ttu-id="bc502-134">Option Infer</span><span class="sxs-lookup"><span data-stu-id="bc502-134">Option Infer</span></span>

<span data-ttu-id="bc502-135">`Option Infer` を使用すると、特定のファイルでローカル型推論を許可するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bc502-135">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="bc502-136">このオプションを有効化またはブロックするには、次のステートメントのいずれかをファイルの先頭に入力します。</span><span class="sxs-lookup"><span data-stu-id="bc502-136">To enable or to block the option, type one of the following statements at the start of the file.</span></span>

`Option Infer On`

`Option Infer Off`

<span data-ttu-id="bc502-137">コードで `Option Infer` の値を指定しない場合、コンパイラの既定値は、`Option Infer On` です。</span><span class="sxs-lookup"><span data-stu-id="bc502-137">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span>

<span data-ttu-id="bc502-138">ファイルの `Option Infer` に設定した値が IDE またはコマンド ラインに設定した値と競合した場合は、ファイルの値が優先されます。</span><span class="sxs-lookup"><span data-stu-id="bc502-138">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="bc502-139">詳細については、「[Option Infer ステートメント](../../../language-reference/statements/option-infer-statement.md)」および「[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc502-139">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc502-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc502-140">See also</span></span>

- [<span data-ttu-id="bc502-141">匿名型</span><span class="sxs-lookup"><span data-stu-id="bc502-141">Anonymous Types</span></span>](../objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="bc502-142">事前バインディングと遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="bc502-142">Early and Late Binding</span></span>](../early-late-binding/index.md)
- [<span data-ttu-id="bc502-143">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc502-143">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="bc502-144">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc502-144">For...Next Statement</span></span>](../../../language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="bc502-145">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc502-145">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="bc502-146">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="bc502-146">-optioninfer</span></span>](../../../reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="bc502-147">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="bc502-147">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
