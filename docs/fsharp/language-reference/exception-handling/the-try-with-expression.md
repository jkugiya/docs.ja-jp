---
title: '例外: try...with 式'
description: F# の 'try...with' 式を使用して例外処理を行う方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630252"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="62242-103">例外: try...with 式</span><span class="sxs-lookup"><span data-stu-id="62242-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="62242-104">このトピックでは、F# 言語での例外処理に使用される式である `try...with` 式について説明します。</span><span class="sxs-lookup"><span data-stu-id="62242-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="62242-105">構文</span><span class="sxs-lookup"><span data-stu-id="62242-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="62242-106">解説</span><span class="sxs-lookup"><span data-stu-id="62242-106">Remarks</span></span>

<span data-ttu-id="62242-107">`try...with` 式は、F# で例外を処理するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="62242-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="62242-108">これは、C# の `try...catch` ステートメントに似ています。</span><span class="sxs-lookup"><span data-stu-id="62242-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="62242-109">前の構文で、*expression1* のコードによって例外が生成されるとします。</span><span class="sxs-lookup"><span data-stu-id="62242-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="62242-110">`try...with` 式によって値が返されます。</span><span class="sxs-lookup"><span data-stu-id="62242-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="62242-111">例外がスローされない場合、式全体によって *expression1* の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="62242-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="62242-112">例外がスローされた場合、各 "*パターン*" がその例外と比較され、最初の一致パターンで、そのブランチに対応する "*式*" ("*例外ハンドラー*" と呼ばれる) が実行され、式全体により、その例外ハンドラーの式の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="62242-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="62242-113">一致するパターンがない場合、例外は、一致するハンドラーが見つかるまで呼び出し履歴をさかのぼります。</span><span class="sxs-lookup"><span data-stu-id="62242-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="62242-114">例外ハンドラー内の各式から返される値の型は、`try` ブロック内の式から返される型と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62242-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="62242-115">多くの場合、エラーが発生したということは、各例外ハンドラーの式から返される有効な値がないことも示します。</span><span class="sxs-lookup"><span data-stu-id="62242-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="62242-116">一般的なパターンは、式の型がオプション型になるというものです。</span><span class="sxs-lookup"><span data-stu-id="62242-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="62242-117">このパターンを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="62242-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="62242-118">例外は .NET 例外とすることも、F# 例外とすることもできます。</span><span class="sxs-lookup"><span data-stu-id="62242-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="62242-119">`exception` キーワードを使用して、F# 例外を定義できます。</span><span class="sxs-lookup"><span data-stu-id="62242-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="62242-120">さまざまなパターンを使用して、例外の種類やその他の条件を基にフィルター処理が行えます。次の表に、オプションの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="62242-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="62242-121">パターン</span><span class="sxs-lookup"><span data-stu-id="62242-121">Pattern</span></span>|<span data-ttu-id="62242-122">説明</span><span class="sxs-lookup"><span data-stu-id="62242-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="62242-123">:?</span><span class="sxs-lookup"><span data-stu-id="62242-123">:?</span></span> <span data-ttu-id="62242-124">*exception-type*</span><span class="sxs-lookup"><span data-stu-id="62242-124">*exception-type*</span></span>|<span data-ttu-id="62242-125">指定された .NET 例外の種類と一致します。</span><span class="sxs-lookup"><span data-stu-id="62242-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="62242-126">:?</span><span class="sxs-lookup"><span data-stu-id="62242-126">:?</span></span> <span data-ttu-id="62242-127">*exception-type* as *identifier*</span><span class="sxs-lookup"><span data-stu-id="62242-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="62242-128">指定された .NET 例外の種類と一致しますが、例外に名前付きの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="62242-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="62242-129">*exception-name*(*arguments*)</span><span class="sxs-lookup"><span data-stu-id="62242-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="62242-130">F# 例外の種類と一致し、引数をバインドします。</span><span class="sxs-lookup"><span data-stu-id="62242-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="62242-131">*identifier*</span><span class="sxs-lookup"><span data-stu-id="62242-131">*identifier*</span></span>|<span data-ttu-id="62242-132">任意の例外と一致し、その名前を例外オブジェクトにバインドします。</span><span class="sxs-lookup"><span data-stu-id="62242-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="62242-133">**:?System.Exception as**_identifier_ と同じです</span><span class="sxs-lookup"><span data-stu-id="62242-133">Equivalent to **:? System.Exception as**_identifier_</span></span>|
|<span data-ttu-id="62242-134">*identifier* when *condition*</span><span class="sxs-lookup"><span data-stu-id="62242-134">*identifier* when *condition*</span></span>|<span data-ttu-id="62242-135">条件が true の場合、すべての例外と一致します。</span><span class="sxs-lookup"><span data-stu-id="62242-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="62242-136">例</span><span class="sxs-lookup"><span data-stu-id="62242-136">Examples</span></span>

<span data-ttu-id="62242-137">次のコード例は、さまざまな例外ハンドラー パターンの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="62242-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> <span data-ttu-id="62242-138">`try...with` コンストラクトは、`try...finally` 式とは別の式です。</span><span class="sxs-lookup"><span data-stu-id="62242-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="62242-139">したがって、コードに `with` ブロックと `finally` ブロックの両方が必要な場合は、2 つの式を入れ子にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="62242-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="62242-140">`try...with` は、非同期ワークフローやその他のコンピュテーション式で使用することができます。その場合は、`try...with` 式のカスタマイズされたバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="62242-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="62242-141">詳細については、「[非同期ワークフロー](../asynchronous-workflows.md)」、「[コンピュテーション式](../computation-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62242-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62242-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="62242-142">See also</span></span>

- [<span data-ttu-id="62242-143">例外処理</span><span class="sxs-lookup"><span data-stu-id="62242-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="62242-144">例外の種類</span><span class="sxs-lookup"><span data-stu-id="62242-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="62242-145">例外: `try...finally` 式</span><span class="sxs-lookup"><span data-stu-id="62242-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
