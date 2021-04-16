---
title: 遅延式
description: F# の遅延式を使ってアプリとライブラリのパフォーマンスを向上させる方法について説明します。
ms.date: 08/15/2020
ms.openlocfilehash: 0b8496467295ce6793f80c341af88bb1819f4a47
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425504"
---
# <a name="lazy-expressions"></a><span data-ttu-id="61a62-103">遅延式</span><span class="sxs-lookup"><span data-stu-id="61a62-103">Lazy Expressions</span></span>

<span data-ttu-id="61a62-104">"*遅延式*" は、すぐには評価されず、結果が必要なときに評価される式です。</span><span class="sxs-lookup"><span data-stu-id="61a62-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="61a62-105">これは、コードのパフォーマンスを向上させるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="61a62-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="61a62-106">構文</span><span class="sxs-lookup"><span data-stu-id="61a62-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="61a62-107">解説</span><span class="sxs-lookup"><span data-stu-id="61a62-107">Remarks</span></span>

<span data-ttu-id="61a62-108">前の構文では、*expression* は結果が必要な場合にのみ評価されるコードであり、*identifier* は結果を格納する値です。</span><span class="sxs-lookup"><span data-stu-id="61a62-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="61a62-109">値は `Lazy<'T>` 型であり、`'T` に使用される実際の型は、式の結果から決定されます。</span><span class="sxs-lookup"><span data-stu-id="61a62-109">The value is of type `Lazy<'T>`, where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="61a62-110">遅延式を使用すると、式の実行を、結果が必要な場合のみに制限することで、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="61a62-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="61a62-111">式を強制的に実行するには、メソッド `Force` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="61a62-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="61a62-112">`Force` を使用すると、実行が一度だけ行われます。</span><span class="sxs-lookup"><span data-stu-id="61a62-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="61a62-113">その後で `Force` を呼び出すと、同じ結果が返されますが、コードは実行されません。</span><span class="sxs-lookup"><span data-stu-id="61a62-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="61a62-114">次のコードは、遅延式の使用方法と `Force` の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="61a62-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="61a62-115">このコードでは、`result` の型は `Lazy<int>` で、`Force` メソッドは `int` を返します。</span><span class="sxs-lookup"><span data-stu-id="61a62-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="61a62-116">`Lazy` 型ではない遅延評価は、シーケンスにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="61a62-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="61a62-117">詳細については、[シーケンス](sequences.md)にするページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="61a62-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="61a62-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="61a62-118">See also</span></span>

- [<span data-ttu-id="61a62-119">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="61a62-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="61a62-120">LazyExtensions モジュール</span><span class="sxs-lookup"><span data-stu-id="61a62-120">LazyExtensions module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
