---
description: '詳細情報: Option Infer ステートメント'
title: Option Infer ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: d0c3de7bdafb7e9b361da7a8538046e3d76b5ce7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741589"
---
# <a name="option-infer-statement"></a><span data-ttu-id="dccb8-103">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="dccb8-103">Option Infer Statement</span></span>

<span data-ttu-id="dccb8-104">変数の宣言でローカル型推論を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="dccb8-104">Enables the use of local type inference in declaring variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="dccb8-105">構文</span><span class="sxs-lookup"><span data-stu-id="dccb8-105">Syntax</span></span>

```vb
Option Infer { On | Off }
```

## <a name="parts"></a><span data-ttu-id="dccb8-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="dccb8-106">Parts</span></span>

|<span data-ttu-id="dccb8-107">用語</span><span class="sxs-lookup"><span data-stu-id="dccb8-107">Term</span></span>|<span data-ttu-id="dccb8-108">定義</span><span class="sxs-lookup"><span data-stu-id="dccb8-108">Definition</span></span>|
|---|---|
|`On`|<span data-ttu-id="dccb8-109">任意。</span><span class="sxs-lookup"><span data-stu-id="dccb8-109">Optional.</span></span> <span data-ttu-id="dccb8-110">ローカル型推論を有効にします。</span><span class="sxs-lookup"><span data-stu-id="dccb8-110">Enables local type inference.</span></span>|
|`Off`|<span data-ttu-id="dccb8-111">任意。</span><span class="sxs-lookup"><span data-stu-id="dccb8-111">Optional.</span></span> <span data-ttu-id="dccb8-112">ローカル型推論を無効にします。</span><span class="sxs-lookup"><span data-stu-id="dccb8-112">Disables local type inference.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dccb8-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="dccb8-113">Remarks</span></span>

<span data-ttu-id="dccb8-114">ファイルに `Option Infer` を設定するには、ファイルの先頭に他のソース コードよりも前に `Option Infer On` または `Option Infer Off` を入力します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-114">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="dccb8-115">ファイルの `Option Infer` に設定した値が IDE またはコマンド ラインに設定した値と競合した場合は、ファイルの値が優先されます。</span><span class="sxs-lookup"><span data-stu-id="dccb8-115">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="dccb8-116">`Option Infer` を `On` に設定すると、データ型を明示的に指定せずにローカル変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="dccb8-116">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="dccb8-117">コンパイラは、初期化式の型から変数のデータ型を推測します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-117">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>

<span data-ttu-id="dccb8-118">次の図では、`Option Infer` がオンになっています。</span><span class="sxs-lookup"><span data-stu-id="dccb8-118">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="dccb8-119">宣言 `Dim someVar = 2` 内の変数は、型の推定によって整数として宣言されています。</span><span class="sxs-lookup"><span data-stu-id="dccb8-119">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

<span data-ttu-id="dccb8-120">次のスクリーンショットは、Option Infer がオンの場合の IntelliSense を示しています。</span><span class="sxs-lookup"><span data-stu-id="dccb8-120">The following screenshot shows IntelliSense when Option Infer is on:</span></span>

![Option Infer がオンの場合の IntelliSense ビューを示すスクリーンショット。](./media/option-infer-statement/option-infer-as-integer-on.png)

<span data-ttu-id="dccb8-122">次の図では、`Option Infer` がオフになっています。</span><span class="sxs-lookup"><span data-stu-id="dccb8-122">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="dccb8-123">宣言 `Dim someVar = 2` 内の変数は、型の推定によって `Object` として宣言されています。</span><span class="sxs-lookup"><span data-stu-id="dccb8-123">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="dccb8-124">この例では、[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) で、**Option Strict** 設定が **オフ** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="dccb8-124">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="dccb8-125">次のスクリーンショットは、Option Infer がオフの場合の IntelliSense を示しています。</span><span class="sxs-lookup"><span data-stu-id="dccb8-125">The following screenshot shows IntelliSense when Option Infer is off:</span></span>

![Option Infer がオフの場合の IntelliSense ビューを示すスクリーンショット。](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> <span data-ttu-id="dccb8-127">変数を `Object` として宣言すると、プログラムの実行中にランタイム型が変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="dccb8-127">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="dccb8-128">Visual Basic では、*ボックス化* と *ボックス化解除* という操作を実行して `Object` と値型との間で変換を行いますが、このために実行速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-128">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="dccb8-129">ボックス化とボックス化解除の詳細については、[Visual Basic 言語の仕様](~/_vblang/spec/conversions.md#value-type-conversions)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccb8-129">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>

<span data-ttu-id="dccb8-130">型の推定は、プロシージャ レベルで適用され、クラス、構造体、モジュール、またはインターフェイスのプロシージャの外側には適用されません。</span><span class="sxs-lookup"><span data-stu-id="dccb8-130">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>

<span data-ttu-id="dccb8-131">詳細については、「[ローカル型の推論](../../programming-guide/language-features/variables/local-type-inference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccb8-131">For additional information, see [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="dccb8-132">Option Infer ステートメントが指定されていない場合</span><span class="sxs-lookup"><span data-stu-id="dccb8-132">When an Option Infer Statement Is Not Present</span></span>

<span data-ttu-id="dccb8-133">ソース コードに `Option Infer` ステートメントが含まれていない場合は、[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) の **Option Infer** 設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="dccb8-133">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="dccb8-134">コマンドライン コンパイラを使用している場合は、[-optioninfer](../../reference/command-line-compiler/optioninfer.md) コンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-134">If the command-line compiler is used, the [-optioninfer](../../reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>

#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="dccb8-135">IDE の Option Infer を設定するには</span><span class="sxs-lookup"><span data-stu-id="dccb8-135">To set Option Infer in the IDE</span></span>

1. <span data-ttu-id="dccb8-136">**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-136">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="dccb8-137">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dccb8-137">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="dccb8-138">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dccb8-138">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="dccb8-139">**[Option infer]** ボックスに値を設定します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-139">Set the value in the **Option infer** box.</span></span>

<span data-ttu-id="dccb8-140">新しいプロジェクトを作成すると、 **[コンパイル]** タブの **[Option Infer]** 設定が **[VISUAL BASIC の既定値]** ダイアログ ボックスの **[Option Infer]** 設定に設定されます。</span><span class="sxs-lookup"><span data-stu-id="dccb8-140">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="dccb8-141">**[VISUAL BASIC の既定値]** ダイアログ ボックスにアクセスするには、 **[ツール]** メニューで **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dccb8-141">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="dccb8-142">**[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、 **[VISUAL BASIC の既定値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dccb8-142">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="dccb8-143">**[VISUAL BASIC の既定値]** の初期の既定値は `On` です。</span><span class="sxs-lookup"><span data-stu-id="dccb8-143">The initial default setting in **VB Defaults** is `On`.</span></span>

#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="dccb8-144">コマンド ラインで Option Infer を設定するには</span><span class="sxs-lookup"><span data-stu-id="dccb8-144">To set Option Infer on the command line</span></span>

<span data-ttu-id="dccb8-145">**vbc** コマンドに [-optioninfer](../../reference/command-line-compiler/optioninfer.md) コンパイラ オプションを含めます。</span><span class="sxs-lookup"><span data-stu-id="dccb8-145">Include the [-optioninfer](../../reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>

## <a name="default-data-types-and-values"></a><span data-ttu-id="dccb8-146">既定のデータ型と値</span><span class="sxs-lookup"><span data-stu-id="dccb8-146">Default Data Types and Values</span></span>

<span data-ttu-id="dccb8-147">次の表では、`Dim` ステートメントのデータ型と初期化子を指定するさまざまな組み合わせの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-147">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="dccb8-148">データ型が指定されているか</span><span class="sxs-lookup"><span data-stu-id="dccb8-148">Data type specified?</span></span>|<span data-ttu-id="dccb8-149">初期化子が指定されているか</span><span class="sxs-lookup"><span data-stu-id="dccb8-149">Initializer specified?</span></span>|<span data-ttu-id="dccb8-150">例</span><span class="sxs-lookup"><span data-stu-id="dccb8-150">Example</span></span>|<span data-ttu-id="dccb8-151">結果</span><span class="sxs-lookup"><span data-stu-id="dccb8-151">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="dccb8-152">いいえ</span><span class="sxs-lookup"><span data-stu-id="dccb8-152">No</span></span>|<span data-ttu-id="dccb8-153">いいえ</span><span class="sxs-lookup"><span data-stu-id="dccb8-153">No</span></span>|`Dim qty`|<span data-ttu-id="dccb8-154">`Option Strict` がオフ (既定値) の場合、変数は `Nothing` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="dccb8-154">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="dccb8-155">`Option Strict` がオンの場合、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-155">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="dccb8-156">いいえ</span><span class="sxs-lookup"><span data-stu-id="dccb8-156">No</span></span>|<span data-ttu-id="dccb8-157">はい</span><span class="sxs-lookup"><span data-stu-id="dccb8-157">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="dccb8-158">`Option Infer` がオン (既定値) の場合、変数は初期化子のデータ型になります。</span><span class="sxs-lookup"><span data-stu-id="dccb8-158">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="dccb8-159">「[ローカル型の推論](../../programming-guide/language-features/variables/local-type-inference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccb8-159">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="dccb8-160">`Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。</span><span class="sxs-lookup"><span data-stu-id="dccb8-160">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="dccb8-161">`Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-161">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="dccb8-162">はい</span><span class="sxs-lookup"><span data-stu-id="dccb8-162">Yes</span></span>|<span data-ttu-id="dccb8-163">いいえ</span><span class="sxs-lookup"><span data-stu-id="dccb8-163">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="dccb8-164">変数は、データ型の既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="dccb8-164">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="dccb8-165">詳細については、「[Dim ステートメント](dim-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccb8-165">For more information, see [Dim Statement](dim-statement.md).</span></span>|
|<span data-ttu-id="dccb8-166">はい</span><span class="sxs-lookup"><span data-stu-id="dccb8-166">Yes</span></span>|<span data-ttu-id="dccb8-167">はい</span><span class="sxs-lookup"><span data-stu-id="dccb8-167">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="dccb8-168">初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-168">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

## <a name="example"></a><span data-ttu-id="dccb8-169">例</span><span class="sxs-lookup"><span data-stu-id="dccb8-169">Example</span></span>

<span data-ttu-id="dccb8-170">次の例では、`Option Infer` ステートメントがローカル型推論をどのように有効にするかを示します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-170">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a><span data-ttu-id="dccb8-171">例</span><span class="sxs-lookup"><span data-stu-id="dccb8-171">Example</span></span>

<span data-ttu-id="dccb8-172">次の例では、変数が `Object` として識別されたときに、ランタイム型が異なる場合があることを示します。</span><span class="sxs-lookup"><span data-stu-id="dccb8-172">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a><span data-ttu-id="dccb8-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="dccb8-173">See also</span></span>

- [<span data-ttu-id="dccb8-174">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="dccb8-174">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="dccb8-175">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="dccb8-175">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="dccb8-176">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="dccb8-176">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="dccb8-177">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="dccb8-177">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="dccb8-178">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="dccb8-178">Option Strict Statement</span></span>](option-strict-statement.md)
- <span data-ttu-id="dccb8-179">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="dccb8-179">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
- [<span data-ttu-id="dccb8-180">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="dccb8-180">-optioninfer</span></span>](../../reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="dccb8-181">ボックス化とボックス化解除</span><span class="sxs-lookup"><span data-stu-id="dccb8-181">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
