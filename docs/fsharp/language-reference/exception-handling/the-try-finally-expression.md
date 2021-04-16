---
title: '例外: try...finally 式'
description: F# の 'try...finally' 式を使用して、コードのブロックで例外がスローされた場合でもクリーンアップ コードを実行できるようにする方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 0ddb64ac13b307404864ec5b54f26fd8a7a3d7d8
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083004"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="40659-103">例外: try...finally 式</span><span class="sxs-lookup"><span data-stu-id="40659-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="40659-104">`try...finally` 式を使用すると、コードのブロックで例外がスローされた場合でもクリーンアップ コードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="40659-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="40659-105">構文</span><span class="sxs-lookup"><span data-stu-id="40659-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="40659-106">解説</span><span class="sxs-lookup"><span data-stu-id="40659-106">Remarks</span></span>

<span data-ttu-id="40659-107">`try...finally` 式を使用すると、上記の構文で *expression1* の実行中に例外が生成されたかどうかに関係なく、*expression2* のコードを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="40659-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="40659-108">*expression2* の型は、式全体の値には影響しません。例外が発生しなかったときに返される型は、*expression1* の最後の値です。</span><span class="sxs-lookup"><span data-stu-id="40659-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="40659-109">例外が発生した場合、値は返されず、制御のフローは、コール スタックの上位にある次の一致する例外ハンドラーに移ります。</span><span class="sxs-lookup"><span data-stu-id="40659-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="40659-110">例外ハンドラーが見つからない場合、プログラムは終了します。</span><span class="sxs-lookup"><span data-stu-id="40659-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="40659-111">一致するハンドラー内のコードが実行される前、またはプログラムが終了する前に、`finally` 分岐内のコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="40659-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="40659-112">`try...finally` 式を使用したコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40659-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="40659-113">コンソールへの出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="40659-113">The output to the console is as follows.</span></span>

```console
Closing stream
Exception handled.
```

<span data-ttu-id="40659-114">出力からわかるように、外側の例外が処理される前にストリームが閉じられています。また、ファイル `test.txt` にテキスト `test1` が含まれているということは、例外によって制御が外側の例外ハンドラーに移ったにもかかわらず、バッファーがフラッシュされてディスクに書き込まれたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="40659-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="40659-115">`try...with` コンストラクトは、`try...finally` コンストラクトとは別のコンストラクトであることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="40659-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="40659-116">したがって、コードに `with` ブロックと `finally` ブロックの両方が必要な場合は、次のコード例に示すように、2 つのコンストラクトを入れ子にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="40659-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="40659-117">コンピュテーション式のコンテキスト (シーケンス式と非同期ワークフローを含む) では、**try...finally** 式にカスタム実装を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="40659-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="40659-118">詳細については、「[コンピュテーション式](../computation-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="40659-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40659-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="40659-119">See also</span></span>

- [<span data-ttu-id="40659-120">例外処理</span><span class="sxs-lookup"><span data-stu-id="40659-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="40659-121">例外: `try...with` 式</span><span class="sxs-lookup"><span data-stu-id="40659-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
