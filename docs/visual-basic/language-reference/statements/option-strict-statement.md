---
description: '詳細情報: Option Strict Statement'
title: Option Strict Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
ms.openlocfilehash: a128aca1bdaa6ce8bd4c4cd8e63e05348f00e4d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741433"
---
# <a name="option-strict-statement"></a><span data-ttu-id="23eb9-103">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="23eb9-103">Option Strict Statement</span></span>

<span data-ttu-id="23eb9-104">暗黙的なデータ型変換を拡大変換のみに制限し、遅延バインディングを許可せず、`Object` 型になる暗黙的な型指定も許可しません。</span><span class="sxs-lookup"><span data-stu-id="23eb9-104">Restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23eb9-105">構文</span><span class="sxs-lookup"><span data-stu-id="23eb9-105">Syntax</span></span>  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="23eb9-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="23eb9-106">Parts</span></span>  
  
|<span data-ttu-id="23eb9-107">用語</span><span class="sxs-lookup"><span data-stu-id="23eb9-107">Term</span></span>|<span data-ttu-id="23eb9-108">定義</span><span class="sxs-lookup"><span data-stu-id="23eb9-108">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="23eb9-109">任意。</span><span class="sxs-lookup"><span data-stu-id="23eb9-109">Optional.</span></span> <span data-ttu-id="23eb9-110">`Option Strict` チェックを有効にします。</span><span class="sxs-lookup"><span data-stu-id="23eb9-110">Enables `Option Strict` checking.</span></span>|  
|`Off`|<span data-ttu-id="23eb9-111">任意。</span><span class="sxs-lookup"><span data-stu-id="23eb9-111">Optional.</span></span> <span data-ttu-id="23eb9-112">`Option Strict` チェックを無効にします。</span><span class="sxs-lookup"><span data-stu-id="23eb9-112">Disables `Option Strict` checking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23eb9-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="23eb9-113">Remarks</span></span>  

 <span data-ttu-id="23eb9-114">`Option Strict On` または `Option Strict` がファイルに存在すると、次の条件によりコンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-114">When `Option Strict On` or `Option Strict` appears in a file, the following conditions cause a compile-time error:</span></span>  
  
- <span data-ttu-id="23eb9-115">暗黙的な縮小変換</span><span class="sxs-lookup"><span data-stu-id="23eb9-115">Implicit narrowing conversions</span></span>  
  
- <span data-ttu-id="23eb9-116">遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="23eb9-116">Late binding</span></span>  
  
- <span data-ttu-id="23eb9-117">結果が `Object` 型となる暗黙の型指定</span><span class="sxs-lookup"><span data-stu-id="23eb9-117">Implicit typing that results in an `Object` type</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23eb9-118">[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) で設定できる警告の構成には、コンパイル時エラーが発生する 3 つの条件に相当する 3 つの設定があります。</span><span class="sxs-lookup"><span data-stu-id="23eb9-118">In the warning configurations that you can set on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), there are three settings that correspond to the three conditions that cause a compile-time error.</span></span> <span data-ttu-id="23eb9-119">これらの設定の使用方法については、このトピックで後述する「[IDE で警告の構成を設定するには](option-strict-statement.md#conditions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23eb9-119">For information about how to use these settings, see [To set warning configurations in the IDE](option-strict-statement.md#conditions) later in this topic.</span></span>  
  
 <span data-ttu-id="23eb9-120">関連付けられている IDE 設定でこれらのエラーまたは警告をオンにするように指定している場合でも、`Option Strict Off` ステートメントは、3 つの条件すべてについてエラーおよび警告チェックをオフにします。</span><span class="sxs-lookup"><span data-stu-id="23eb9-120">The `Option Strict Off` statement turns off error and warning checking for all three conditions, even if the associated IDE settings specify to turn on these errors or warnings.</span></span> <span data-ttu-id="23eb9-121">`Option Strict On` ステートメントは、関連する IDE 設定でこれらのエラーまたは警告をオフにするように指定している場合でも、3 つの条件すべてについてエラーおよび警告チェックをオンにします。</span><span class="sxs-lookup"><span data-stu-id="23eb9-121">The `Option Strict On` statement turns on error and warning checking for all three conditions, even if the associated IDE settings specify to turn off these errors or warnings.</span></span>  
  
 <span data-ttu-id="23eb9-122">使用する場合、`Option Strict` ステートメントは、ファイル内のどのソース ステートメントよりも前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23eb9-122">If used, the `Option Strict` statement must appear before any other code statements in a file.</span></span>  
  
 <span data-ttu-id="23eb9-123">`Option Strict` を `On` に設定すると、Visual Basic では、すべてのプログラミング要素にデータ型が指定されているかどうかがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-123">When you set `Option Strict` to `On`, Visual Basic checks that data types are specified for all programming elements.</span></span> <span data-ttu-id="23eb9-124">データ型は、明示的に指定することも、ローカル型推論を使用して指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-124">Data types can be specified explicitly, or specified by using local type inference.</span></span> <span data-ttu-id="23eb9-125">次の理由から、すべてのプログラミング要素にデータ型を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="23eb9-125">Specifying data types for all your programming elements is recommended, for the following reasons:</span></span>  
  
- <span data-ttu-id="23eb9-126">これにより、変数とパラメーターの IntelliSense サポートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="23eb9-126">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="23eb9-127">これにより、コードを入力しながら、プロパティとその他のメンバーを確認できます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-127">This enables you to see their properties and other members as you type code.</span></span>  
  
- <span data-ttu-id="23eb9-128">これにより、コンパイラは型チェックを実行できます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-128">It enables the compiler to perform type checking.</span></span> <span data-ttu-id="23eb9-129">型チェックを使用すると、型変換エラーのために実行時に失敗する可能性があるステートメントを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-129">Type checking helps you find statements that can fail at run time because of type conversion errors.</span></span> <span data-ttu-id="23eb9-130">また、これらのメソッドをサポートしていないオブジェクトに対するメソッドの呼び出しも識別します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-130">It also identifies calls to methods on objects that do not support those methods.</span></span>  
  
- <span data-ttu-id="23eb9-131">これにより、コードの実行速度が向上します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-131">It speeds up the execution of code.</span></span> <span data-ttu-id="23eb9-132">その理由の 1 つは、プログラミング要素のデータ型を指定しない場合、Visual Basic コンパイラによって `Object` 型に割り当てられることです。</span><span class="sxs-lookup"><span data-stu-id="23eb9-132">One reason for this is that if you do not specify a data type for a programming element, the Visual Basic compiler assigns it the `Object` type.</span></span> <span data-ttu-id="23eb9-133">コンパイルされたコードは、`Object` とその他のデータ型との間で変換を行う必要があり、これによりパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-133">Compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="implicit-narrowing-conversion-errors"></a><span data-ttu-id="23eb9-134">暗黙的な縮小変換エラー</span><span class="sxs-lookup"><span data-stu-id="23eb9-134">Implicit Narrowing Conversion Errors</span></span>  

 <span data-ttu-id="23eb9-135">縮小変換する暗黙的なデータ型変換がある場合は、暗黙的な縮小変換エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-135">Implicit narrowing conversion errors occur when there is an implicit data type conversion that is a narrowing conversion.</span></span>  
  
 <span data-ttu-id="23eb9-136">Visual Basic は、さまざまなデータ型を他のデータ型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-136">Visual Basic can convert many data types to other data types.</span></span> <span data-ttu-id="23eb9-137">あるデータ型の値を精度が低いデータ型または容量の小さいデータ型に変換すると、データ損失が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="23eb9-137">Data loss can occur when the value of one data type is converted to a data type that has less precision or a smaller capacity.</span></span> <span data-ttu-id="23eb9-138">このような縮小変換が失敗すると、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-138">A run-time error occurs if such a narrowing conversion fails.</span></span> <span data-ttu-id="23eb9-139">`Option Strict` を使用すると、このような縮小変換についてコンパイル時に通知が送信されるため、変換を回避できます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-139">`Option Strict` ensures compile-time notification of these narrowing conversions so that you can avoid them.</span></span> <span data-ttu-id="23eb9-140">詳細については、「[暗黙の型変換と明示的な型変換](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)」および「[拡大変換と縮小変換](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23eb9-140">For more information, see [Implicit and Explicit Conversions](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) and [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
 <span data-ttu-id="23eb9-141">エラーを発生させる可能性のある変換には、式で発生する暗黙的な変換が含まれます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-141">Conversions that can cause errors include implicit conversions that occur in expressions.</span></span> <span data-ttu-id="23eb9-142">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="23eb9-142">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="23eb9-143">+ 演算子</span><span class="sxs-lookup"><span data-stu-id="23eb9-143">+ Operator</span></span>](../operators/addition-operator.md)  
  
- [<span data-ttu-id="23eb9-144">+= 演算子</span><span class="sxs-lookup"><span data-stu-id="23eb9-144">+= Operator</span></span>](../operators/addition-assignment-operator.md)  
  
- [<span data-ttu-id="23eb9-145">\ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23eb9-145">\ Operator (Visual Basic)</span></span>](../operators/integer-division-operator.md)  
  
- [<span data-ttu-id="23eb9-146">/= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23eb9-146">/= Operator (Visual Basic)</span></span>](../operators/floating-point-division-assignment-operator.md)  
  
- [<span data-ttu-id="23eb9-147">Char データ型</span><span class="sxs-lookup"><span data-stu-id="23eb9-147">Char Data Type</span></span>](../data-types/char-data-type.md)  
  
 <span data-ttu-id="23eb9-148">[& 演算子](../operators/concatenation-operator.md)を使用して文字列を連結する場合、文字列へのすべての変換は拡大と見なされます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-148">When you concatenate strings by using the [& Operator](../operators/concatenation-operator.md), all conversions to the strings are considered to be widening.</span></span> <span data-ttu-id="23eb9-149">したがって、`Option Strict` がオンの場合でも、これらの変換では暗黙的な縮小変換エラーは生成されません。</span><span class="sxs-lookup"><span data-stu-id="23eb9-149">So these conversions do not generate an implicit narrowing conversion error, even if `Option Strict` is on.</span></span>  
  
 <span data-ttu-id="23eb9-150">対応するパラメーターとは異なるデータ型の引数を持つメソッドを呼び出すと、`Option Strict` がオンになっている場合は、縮小変換によってコンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-150">When you call a method that has an argument that has a data type different from the corresponding parameter, a narrowing conversion causes a compile-time error if `Option Strict` is on.</span></span> <span data-ttu-id="23eb9-151">拡大変換または明示的な変換を使用すると、コンパイル時エラーを回避できます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-151">You can avoid the compile-time error by using a widening conversion or an explicit conversion.</span></span>  
  
 <span data-ttu-id="23eb9-152">`For Each…Next` コレクション内の要素からループ制御変数への変換では、コンパイル時に暗黙的な縮小変換エラーが抑制されます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-152">Implicit narrowing conversion errors are suppressed at compile-time for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="23eb9-153">これは、`Option Strict` がオンになっている場合でも発生します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-153">This occurs even if `Option Strict` is on.</span></span> <span data-ttu-id="23eb9-154">詳細については、「[For Each...Next ステートメント](for-each-next-statement.md)」の縮小変換に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="23eb9-154">For more information, see the "Narrowing Conversions" section in [For Each...Next Statement](for-each-next-statement.md).</span></span>  
  
## <a name="late-binding-errors"></a><span data-ttu-id="23eb9-155">遅延バインディング エラー</span><span class="sxs-lookup"><span data-stu-id="23eb9-155">Late Binding Errors</span></span>  

 <span data-ttu-id="23eb9-156">`Object` 型として宣言された変数のプロパティまたはメソッドにオブジェクトを代入する場合は、そのオブジェクトは遅延バインディングされます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-156">An object is late bound when it is assigned to a property or method of a variable that is declared to be of type `Object`.</span></span> <span data-ttu-id="23eb9-157">詳細については、「[事前バインディングと遅延バインディング](../../programming-guide/language-features/early-late-binding/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23eb9-157">For more information, see [Early and Late Binding](../../programming-guide/language-features/early-late-binding/index.md).</span></span>  
  
## <a name="implicit-object-type-errors"></a><span data-ttu-id="23eb9-158">暗黙的なオブジェクトの型エラー</span><span class="sxs-lookup"><span data-stu-id="23eb9-158">Implicit Object Type Errors</span></span>  

 <span data-ttu-id="23eb9-159">適切な型が宣言された変数を推論できない場合は暗黙的なオブジェクトの型エラーが発生するため、`Object` の型が推論されます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-159">Implicit object type errors occur when an appropriate type cannot be inferred for a declared variable, so a type of `Object` is inferred.</span></span> <span data-ttu-id="23eb9-160">これは主に、`As` 句を使用せず、`Option Infer` をオフにして、`Dim` ステートメントを使用して変数を宣言した場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-160">This primarily occurs when you use a `Dim` statement to declare a variable without using an `As` clause, and `Option Infer` is off.</span></span> <span data-ttu-id="23eb9-161">詳細については、「[Option Infer ステートメント](option-infer-statement.md)」および「[Visual Basic 言語仕様](../../reference/language-specification/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23eb9-161">For more information, see [Option Infer Statement](option-infer-statement.md) and the [Visual Basic Language Specification](../../reference/language-specification/index.md).</span></span>  
  
 <span data-ttu-id="23eb9-162">メソッドのパラメーターで `Option Strict` がオフの場合、`As` 句は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="23eb9-162">For method parameters, the `As` clause is optional if `Option Strict` is off.</span></span> <span data-ttu-id="23eb9-163">ただし、いずれかのパラメーターが `As` 句を使用する場合は、すべてで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23eb9-163">However, if any one parameter uses an `As` clause, they all must use it.</span></span> <span data-ttu-id="23eb9-164">`Option Strict` がオンの場合は、すべてのパラメーター定義に対して `As` 句が必要です。</span><span class="sxs-lookup"><span data-stu-id="23eb9-164">If `Option Strict` is on, the `As` clause is required for every parameter definition.</span></span>  
  
 <span data-ttu-id="23eb9-165">`As` 句を使用せずに変数を宣言し、それを `Nothing` に設定すると、変数の型は `Object` になります。</span><span class="sxs-lookup"><span data-stu-id="23eb9-165">If you declare a variable without using an `As` clause and set it to `Nothing`, the variable has a type of `Object`.</span></span> <span data-ttu-id="23eb9-166">この場合、`Option Strict` がオンで `Option Infer` がオンの場合、コンパイル時エラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="23eb9-166">No compile-time error occurs in this case when `Option Strict` is on and `Option Infer` is on.</span></span> <span data-ttu-id="23eb9-167">この例が `Dim something = Nothing` です。</span><span class="sxs-lookup"><span data-stu-id="23eb9-167">An example of this is `Dim something = Nothing`.</span></span>  
  
### <a name="default-data-types-and-values"></a><span data-ttu-id="23eb9-168">既定のデータ型と値</span><span class="sxs-lookup"><span data-stu-id="23eb9-168">Default Data Types and Values</span></span>  

 <span data-ttu-id="23eb9-169">次の表では、[Dim ステートメント](dim-statement.md)のデータ型と初期化子を指定するさまざまな組み合わせの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-169">The following table describes the results of various combinations of specifying the data type and initializer in a [Dim Statement](dim-statement.md).</span></span>  
  
|<span data-ttu-id="23eb9-170">データ型が指定されているか</span><span class="sxs-lookup"><span data-stu-id="23eb9-170">Data type specified?</span></span>|<span data-ttu-id="23eb9-171">初期化子が指定されているか</span><span class="sxs-lookup"><span data-stu-id="23eb9-171">Initializer specified?</span></span>|<span data-ttu-id="23eb9-172">例</span><span class="sxs-lookup"><span data-stu-id="23eb9-172">Example</span></span>|<span data-ttu-id="23eb9-173">結果</span><span class="sxs-lookup"><span data-stu-id="23eb9-173">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="23eb9-174">いいえ</span><span class="sxs-lookup"><span data-stu-id="23eb9-174">No</span></span>|<span data-ttu-id="23eb9-175">いいえ</span><span class="sxs-lookup"><span data-stu-id="23eb9-175">No</span></span>|`Dim qty`|<span data-ttu-id="23eb9-176">`Option Strict` がオフ (既定値) の場合、変数は `Nothing` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-176">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="23eb9-177">`Option Strict` がオンの場合、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-177">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="23eb9-178">いいえ</span><span class="sxs-lookup"><span data-stu-id="23eb9-178">No</span></span>|<span data-ttu-id="23eb9-179">はい</span><span class="sxs-lookup"><span data-stu-id="23eb9-179">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="23eb9-180">`Option Infer` がオン (既定値) の場合、変数は初期化子のデータ型になります。</span><span class="sxs-lookup"><span data-stu-id="23eb9-180">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="23eb9-181">「[ローカル型の推論](../../programming-guide/language-features/variables/local-type-inference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23eb9-181">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="23eb9-182">`Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。</span><span class="sxs-lookup"><span data-stu-id="23eb9-182">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="23eb9-183">`Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-183">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="23eb9-184">はい</span><span class="sxs-lookup"><span data-stu-id="23eb9-184">Yes</span></span>|<span data-ttu-id="23eb9-185">いいえ</span><span class="sxs-lookup"><span data-stu-id="23eb9-185">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="23eb9-186">変数は、データ型の既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-186">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="23eb9-187">詳細については、「[Dim ステートメント](dim-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23eb9-187">For more information, see [Dim Statement](dim-statement.md).</span></span>|  
|<span data-ttu-id="23eb9-188">はい</span><span class="sxs-lookup"><span data-stu-id="23eb9-188">Yes</span></span>|<span data-ttu-id="23eb9-189">はい</span><span class="sxs-lookup"><span data-stu-id="23eb9-189">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="23eb9-190">初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-190">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a><span data-ttu-id="23eb9-191">Option Strict ステートメントが指定されていない場合</span><span class="sxs-lookup"><span data-stu-id="23eb9-191">When an Option Strict Statement Is Not Present</span></span>  

 <span data-ttu-id="23eb9-192">ソース コードに `Option Strict` ステートメントが含まれていない場合は、[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) の **[Option strict]** 設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-192">If the source code does not contain an `Option Strict` statement, the **Option strict** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="23eb9-193">**[コンパイル] ページ** には、エラーを生成する条件をさらに制御するための設定があります。</span><span class="sxs-lookup"><span data-stu-id="23eb9-193">The **Compile Page** has settings that provide additional control over the conditions that generate an error.</span></span>  
  
 <span data-ttu-id="23eb9-194">コマンドライン コンパイラを使用している場合は、[-optionstrict](../../reference/command-line-compiler/optionstrict.md) コンパイラ オプションを使用して `Option Strict` の設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-194">If you are using the command-line compiler, you can use the [-optionstrict](../../reference/command-line-compiler/optionstrict.md) compiler option to specify a setting for `Option Strict`.</span></span>  
  
### <a name="to-set-option-strict-in-the-ide"></a><span data-ttu-id="23eb9-195">IDE の Option Strict を設定するには</span><span class="sxs-lookup"><span data-stu-id="23eb9-195">To set Option Strict in the IDE</span></span>  

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. <span data-ttu-id="23eb9-196">**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-196">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="23eb9-197">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23eb9-197">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="23eb9-198">**[コンパイル]** タブで、 **[Option Strict]** ボックスの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-198">On the **Compile** tab, set the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-warning-configurations-in-the-ide"></a><a name="conditions"></a> <span data-ttu-id="23eb9-199">IDE で警告の構成を設定するには</span><span class="sxs-lookup"><span data-stu-id="23eb9-199">To set warning configurations in the IDE</span></span>  

 <span data-ttu-id="23eb9-200">`Option Strict` ステートメントの代わりに [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) を使用している場合は、エラーを生成する条件をさらに制御できます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-200">When you use the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) instead of an `Option Strict` statement, you have additional control over the conditions that generate errors.</span></span> <span data-ttu-id="23eb9-201">**[コンパイル]** ページの **[警告の構成]** セクションには、`Option Strict` がオンになっているときにコンパイル時エラーが発生する 3 つの条件に相当する設定があります。</span><span class="sxs-lookup"><span data-stu-id="23eb9-201">The **Warning configurations** section of the **Compile Page** has settings that correspond to the three conditions that cause a compile-time error when `Option Strict` is on.</span></span> <span data-ttu-id="23eb9-202">これらの設定を次に示します。</span><span class="sxs-lookup"><span data-stu-id="23eb9-202">Following are these settings:</span></span>  
  
- <span data-ttu-id="23eb9-203">**暗黙的な変換**</span><span class="sxs-lookup"><span data-stu-id="23eb9-203">**Implicit conversion**</span></span>  
  
- <span data-ttu-id="23eb9-204">**遅延バインディング、呼び出しが実行時に失敗する可能性があります**</span><span class="sxs-lookup"><span data-stu-id="23eb9-204">**Late binding; call could fail at run time**</span></span>  
  
- <span data-ttu-id="23eb9-205">**暗黙的な型、オブジェクトと見なされます**</span><span class="sxs-lookup"><span data-stu-id="23eb9-205">**Implicit type; object assumed**</span></span>  
  
 <span data-ttu-id="23eb9-206">**[Option Strict]** を **[オン]** に設定すると、これら 3 つの警告の構成設定のすべてが **[エラー]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-206">When you set **Option Strict** to **On**, all three of these warning configuration settings are set to **Error**.</span></span> <span data-ttu-id="23eb9-207">**[Option Strict]** を **[オフ]** に設定すると、3 つの設定すべてが **[なし]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-207">When you set **Option Strict** to **Off**, all three settings are set to **None**.</span></span>  
  
 <span data-ttu-id="23eb9-208">各警告の構成設定を個別に **[なし]** 、 **[警告]** 、または **[エラー]** に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-208">You can individually change each warning configuration setting to **None**, **Warning**, or **Error**.</span></span> <span data-ttu-id="23eb9-209">3 つの警告の構成設定がすべて **[エラー]** に設定されている場合、`Option strict` ボックスに `On` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-209">If all three warning configuration settings are set to **Error**, `On` appears in the `Option strict` box.</span></span> <span data-ttu-id="23eb9-210">3 つすべてが **[なし]** に設定されている場合、このボックスには `Off` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-210">If all three are set to **None**, `Off` appears in this box.</span></span> <span data-ttu-id="23eb9-211">これらの設定のその他の組み合わせに対しては、 **(カスタム)** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-211">For any other combination of these settings, **(custom)** appears.</span></span>  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a><span data-ttu-id="23eb9-212">新しいプロジェクトの Option Strict の既定の設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="23eb9-212">To set the Option Strict default setting for new projects</span></span>  

 <span data-ttu-id="23eb9-213">プロジェクトを作成するときに、 **[コンパイル]** タブの **[Option Strict]** 設定が **[オプション]** ダイアログ ボックスの **[Option Strict]** 設定に設定されます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-213">When you create a project, the **Option Strict** setting on the **Compile** tab is set to the **Option Strict** setting in the **Options** dialog box.</span></span>  
  
 <span data-ttu-id="23eb9-214">このダイアログ ボックスの `Option Strict` を設定するには、 **[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23eb9-214">To set `Option Strict` in this dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="23eb9-215">**[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、 **[VISUAL BASIC の既定値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23eb9-215">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="23eb9-216">**[VISUAL BASIC の既定値]** の初期の既定値は `Off` です。</span><span class="sxs-lookup"><span data-stu-id="23eb9-216">The initial default setting in **VB Defaults** is `Off`.</span></span>  
  
### <a name="to-set-option-strict-on-the-command-line"></a><span data-ttu-id="23eb9-217">コマンド ラインで Option Strict を設定するには</span><span class="sxs-lookup"><span data-stu-id="23eb9-217">To set Option Strict on the command line</span></span>  

 <span data-ttu-id="23eb9-218">**vbc** コマンドに [-optionstrict](../../reference/command-line-compiler/optionstrict.md) コンパイラ オプションを含めます。</span><span class="sxs-lookup"><span data-stu-id="23eb9-218">Include the [-optionstrict](../../reference/command-line-compiler/optionstrict.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23eb9-219">例</span><span class="sxs-lookup"><span data-stu-id="23eb9-219">Example</span></span>  

 <span data-ttu-id="23eb9-220">次の例は、縮小変換である暗黙の型変換によって発生するコンパイル時のエラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="23eb9-220">The following examples demonstrate compile-time errors caused by implicit type conversions that are narrowing conversions.</span></span> <span data-ttu-id="23eb9-221">このカテゴリのエラーは、 **[コンパイル] ページ** の **[暗黙的な変換]** 条件に対応しています。</span><span class="sxs-lookup"><span data-stu-id="23eb9-221">This category of errors corresponds to the **Implicit conversion** condition on the **Compile Page**.</span></span>  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a><span data-ttu-id="23eb9-222">例</span><span class="sxs-lookup"><span data-stu-id="23eb9-222">Example</span></span>  

 <span data-ttu-id="23eb9-223">次の例は、遅延バインディングによって発生したコンパイル時エラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="23eb9-223">The following example demonstrates a compile-time error caused by late binding.</span></span> <span data-ttu-id="23eb9-224">このカテゴリのエラーは、 **[コンパイル] ページ** の **[遅延バインディングです。呼び出しが実行時に失敗する可能性があります]** 条件に対応しています。</span><span class="sxs-lookup"><span data-stu-id="23eb9-224">This category of errors corresponds to the **Late binding; call could fail at run time** condition on the **Compile Page**.</span></span>  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a><span data-ttu-id="23eb9-225">例</span><span class="sxs-lookup"><span data-stu-id="23eb9-225">Example</span></span>  

 <span data-ttu-id="23eb9-226">次の例は、暗黙的な型の `Object` で宣言された変数によって発生するエラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="23eb9-226">The following examples demonstrate errors caused by variables that are declared with an implicit type of `Object`.</span></span> <span data-ttu-id="23eb9-227">このカテゴリのエラーは **[コンパイル] ページ** の **[暗黙的な型です。オブジェクトと見なされます]** 条件に対応しています。</span><span class="sxs-lookup"><span data-stu-id="23eb9-227">This category of errors corresponds to the **Implicit type; object assumed** condition on the **Compile Page**.</span></span>  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a><span data-ttu-id="23eb9-228">関連項目</span><span class="sxs-lookup"><span data-stu-id="23eb9-228">See also</span></span>

- [<span data-ttu-id="23eb9-229">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="23eb9-229">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="23eb9-230">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="23eb9-230">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- <span data-ttu-id="23eb9-231">[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="23eb9-231">[Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span></span>
- [<span data-ttu-id="23eb9-232">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="23eb9-232">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="23eb9-233">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="23eb9-233">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="23eb9-234">方法: オブジェクトのメンバーにアクセスする</span><span class="sxs-lookup"><span data-stu-id="23eb9-234">How to: Access Members of an Object</span></span>](../../programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [<span data-ttu-id="23eb9-235">XML での埋め込み式</span><span class="sxs-lookup"><span data-stu-id="23eb9-235">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="23eb9-236">厳密でないデリゲート変換</span><span class="sxs-lookup"><span data-stu-id="23eb9-236">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="23eb9-237">Office ソリューションの遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="23eb9-237">Late Binding in Office Solutions</span></span>](/visualstudio/vsto/late-binding-in-office-solutions)
- [<span data-ttu-id="23eb9-238">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="23eb9-238">-optionstrict</span></span>](../../reference/command-line-compiler/optionstrict.md)
- <span data-ttu-id="23eb9-239">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="23eb9-239">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
