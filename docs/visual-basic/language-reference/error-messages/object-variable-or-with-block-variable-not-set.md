---
description: '詳細情報: オブジェクト変数または With ブロック変数が設定されていません。'
title: オブジェクト変数または With ブロック変数が設定されていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: a20655c2219aa5b90015e025a38ea9dd02894a6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795574"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="8eedf-103">オブジェクト変数または With ブロック変数が設定されていません。</span><span class="sxs-lookup"><span data-stu-id="8eedf-103">Object variable or With block variable not set</span></span>

<span data-ttu-id="8eedf-104">無効なオブジェクト変数が参照されています。</span><span class="sxs-lookup"><span data-stu-id="8eedf-104">An invalid object variable is being referenced.</span></span> <span data-ttu-id="8eedf-105">このエラーが発生する原因は複数あります。</span><span class="sxs-lookup"><span data-stu-id="8eedf-105">This error can occur for several reasons:</span></span>

- <span data-ttu-id="8eedf-106">型を指定せずに変数が宣言されました。</span><span class="sxs-lookup"><span data-stu-id="8eedf-106">A variable was declared without specifying a type.</span></span> <span data-ttu-id="8eedf-107">型を指定せずに変数が宣言されている場合、既定で `Object` 型になります。</span><span class="sxs-lookup"><span data-stu-id="8eedf-107">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="8eedf-108">たとえば、`Dim x` で宣言された変数は、`Object;` 型になり、`Dim x As String` で宣言された変数は、`String` 型になります。</span><span class="sxs-lookup"><span data-stu-id="8eedf-108">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="8eedf-109">`Option Strict` ステートメントでは、結果が `Object` 型となる暗黙の型指定が許可されません。</span><span class="sxs-lookup"><span data-stu-id="8eedf-109">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="8eedf-110">型を省略すると、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="8eedf-110">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="8eedf-111">「[Option Strict ステートメント](../statements/option-strict-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8eedf-111">See [Option Strict Statement](../statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="8eedf-112">`Nothing` に設定されているオブジェクトを参照しようとしています。</span><span class="sxs-lookup"><span data-stu-id="8eedf-112">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="8eedf-113">正しく宣言されていない配列変数の要素にアクセスしようとしています。</span><span class="sxs-lookup"><span data-stu-id="8eedf-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="8eedf-114">たとえば、`products() As String` として宣言された配列では、配列 `products(3) = "Widget"` の要素を参照しようとした場合に、エラーがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="8eedf-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="8eedf-115">配列には要素がなく、オブジェクトとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="8eedf-115">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="8eedf-116">ブロックが初期化される前に、`With...End With` ブロック内のコードにアクセスしようとしています。</span><span class="sxs-lookup"><span data-stu-id="8eedf-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="8eedf-117">`With` ステートメントのエントリ ポイントを実行して、`With...End With` ブロックを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8eedf-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="8eedf-118">Visual Basic または VBA の以前のバージョンでは、このエラーは、`Set` キーワードを使用せずに変数に値を代入する (`Set x = "name"` ではなく `x = "name"`) ことによってもトリガーされていました。</span><span class="sxs-lookup"><span data-stu-id="8eedf-118">In earlier versions of Visual Basic or VBA, this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="8eedf-119">`Set` キーワードは、Visual Basic .Net では無効になりました。</span><span class="sxs-lookup"><span data-stu-id="8eedf-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8eedf-120">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8eedf-120">To correct this error</span></span>

1. <span data-ttu-id="8eedf-121">ファイルの先頭に次のコードを追加して、`Option Strict` を `On` に設定します。</span><span class="sxs-lookup"><span data-stu-id="8eedf-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="8eedf-122">プロジェクトを実行すると、**エラー一覧** に、型を使用せずに指定された任意の変数についてのコンパイラ エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8eedf-122">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="8eedf-123">`Option Strict` を有効にしない場合、コードで、型を使用せずに指定されたすべての変数 (`Dim x As String` ではなく `Dim x`) を検索し、目的の型を宣言に追加します。</span><span class="sxs-lookup"><span data-stu-id="8eedf-123">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="8eedf-124">`Nothing` に設定されているオブジェクト変数を参照していないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8eedf-124">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="8eedf-125">コードでキーワード `Nothing` を検索し、オブジェクトを参照した後までオブジェクトが `Nothing` に設定されないように、コードを修正します。</span><span class="sxs-lookup"><span data-stu-id="8eedf-125">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="8eedf-126">配列変数にアクセスする前に、それらの次元が設定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8eedf-126">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="8eedf-127">最初に配列を作成するときに次元を割り当てる (`Dim x() As String` ではなく `Dim x(5) As String`) か、または配列に最初にアクセスする前に、`ReDim` キーワードを使用して、その次元を設定できます。</span><span class="sxs-lookup"><span data-stu-id="8eedf-127">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="8eedf-128">`With` ステートメントのエントリ ポイントを実行して、`With` ブロックが初期化されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8eedf-128">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="8eedf-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="8eedf-129">See also</span></span>

- [<span data-ttu-id="8eedf-130">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="8eedf-130">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="8eedf-131">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="8eedf-131">ReDim Statement</span></span>](../statements/redim-statement.md)
- [<span data-ttu-id="8eedf-132">With...End With ステートメント</span><span class="sxs-lookup"><span data-stu-id="8eedf-132">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
