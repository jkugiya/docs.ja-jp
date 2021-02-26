---
description: try-finally - C# リファレンス
title: try-finally - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 03e5fa46cef6b30a0af15c113ec6b141a61bee47
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639417"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="55339-103">try-finally (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="55339-103">try-finally (C# Reference)</span></span>

<span data-ttu-id="55339-104">`finally` ブロックを使用すると、[try](try-catch.md) ブロックで割り当てられたリソースをクリーンアップし、`try` ブロックで例外が発生してもコードを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="55339-104">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="55339-105">通常、制御が `finally` ステートメントを離れると、`try` ブロックのステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="55339-105">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="55339-106">制御の移動は、`break` ステートメント、`continue` ステートメント、`goto` ステートメント、`return` またはステートメントの正常な実行の結果や、`try` ステートメントで生じた例外の反映の結果として生じます。</span><span class="sxs-lookup"><span data-stu-id="55339-106">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="55339-107">ハンドルされている例外では、関連する `finally` ブロックの実行が保証されます。</span><span class="sxs-lookup"><span data-stu-id="55339-107">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="55339-108">ただし、例外がハンドルされていない場合、`finally` ブロックの実行は、例外のアンワインド操作のトリガー方法に依存します。</span><span class="sxs-lookup"><span data-stu-id="55339-108">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="55339-109">つまり、コンピューターの設定に依存するということでもあります。</span><span class="sxs-lookup"><span data-stu-id="55339-109">That, in turn, is dependent on how your computer is set up.</span></span> <span data-ttu-id="55339-110">`finally` 句が実行されないのは、プログラムが直ちに停止している場合のみです。</span><span class="sxs-lookup"><span data-stu-id="55339-110">The only cases where `finally` clauses don't run involve a program being immediately stopped.</span></span> <span data-ttu-id="55339-111">これの例は、IL ステートメントが壊れているために <xref:System.InvalidProgramException> がスローされる場合です。</span><span class="sxs-lookup"><span data-stu-id="55339-111">An example of this would be when <xref:System.InvalidProgramException> gets thrown because of the IL statements being corrupt.</span></span> <span data-ttu-id="55339-112">ほとんどのオペレーティング システムでは、プロセスの停止とアンロードの一環として、リソースの適切なクリーンアップが行われます。</span><span class="sxs-lookup"><span data-stu-id="55339-112">On most operating systems, reasonable resource cleanup will take place as part of stopping and unloading the process.</span></span>

<span data-ttu-id="55339-113">通常、ハンドルされていない例外によってアプリケーションが終了した場合、`finally` ブロックが実行されるかどうかは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="55339-113">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="55339-114">ただし、このような状況でも実行する必要のあるステートメントが `finally` ブロックにある場合は、`try`-`finally` ステートメントに `catch` ブロックを追加するという方法があります。</span><span class="sxs-lookup"><span data-stu-id="55339-114">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="55339-115">または、`try`-`finally` ステートメントの `try` ブロックでスローされた例外があれば、コール スタックの上の方でキャッチすることもできます。</span><span class="sxs-lookup"><span data-stu-id="55339-115">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="55339-116">つまり、`try`-`finally` ステートメントが含まれているメソッドを呼び出すメソッド内でも、そのメソッドを呼び出すメソッド内でも、コール スタック内の任意のメソッド内でも、例外をキャッチできるということです。</span><span class="sxs-lookup"><span data-stu-id="55339-116">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="55339-117">例外がキャッチされない場合、`finally` ブロックの実行は、例外のアンワインド操作がオペレーティング システムによってトリガーされるかどうかに依存します。</span><span class="sxs-lookup"><span data-stu-id="55339-117">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="55339-118">例</span><span class="sxs-lookup"><span data-stu-id="55339-118">Example</span></span>

<span data-ttu-id="55339-119">次の例では、無効な変換ステートメントによって `System.InvalidCastException` 例外が発生しています。</span><span class="sxs-lookup"><span data-stu-id="55339-119">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="55339-120">この例外はハンドルされていません。</span><span class="sxs-lookup"><span data-stu-id="55339-120">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="55339-121">次の例では、コール スタックのずっと上の方のメソッド内で `TryCast` メソッドからの例外がキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="55339-121">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="55339-122">`finally` の詳細については、「[try-catch-finally](try-catch-finally.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55339-122">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="55339-123">C# には、<xref:System.IDisposable> オブジェクトに対して同様の機能を便利な構文で提供する [using ステートメント](using-statement.md)も含まれています。</span><span class="sxs-lookup"><span data-stu-id="55339-123">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="55339-124">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="55339-124">C# language specification</span></span>

<span data-ttu-id="55339-125">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の「[try ステートメント](~/_csharplang/spec/statements.md#the-try-statement)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="55339-125">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55339-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="55339-126">See also</span></span>

- [<span data-ttu-id="55339-127">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="55339-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="55339-128">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="55339-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="55339-129">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="55339-129">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="55339-130">try、throw、catch ステートメント (C++)</span><span class="sxs-lookup"><span data-stu-id="55339-130">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="55339-131">throw</span><span class="sxs-lookup"><span data-stu-id="55339-131">throw</span></span>](throw.md)
- [<span data-ttu-id="55339-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="55339-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="55339-133">方法: 例外を明示的にスローする</span><span class="sxs-lookup"><span data-stu-id="55339-133">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
