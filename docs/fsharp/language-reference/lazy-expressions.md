---
title: 遅延式
description: 'F # のレイジー式を使用して、アプリとライブラリのパフォーマンスを向上させる方法について説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: 0b8496467295ce6793f80c341af88bb1819f4a47
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425504"
---
# <a name="lazy-expressions"></a><span data-ttu-id="6fd6b-103">遅延式</span><span class="sxs-lookup"><span data-stu-id="6fd6b-103">Lazy Expressions</span></span>

<span data-ttu-id="6fd6b-104">*レイジー式* は、すぐに評価されるのではなく、結果が必要になったときに評価される式です。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="6fd6b-105">これは、コードのパフォーマンスを向上させるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="6fd6b-106">構文</span><span class="sxs-lookup"><span data-stu-id="6fd6b-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="6fd6b-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="6fd6b-107">Remarks</span></span>

<span data-ttu-id="6fd6b-108">前の構文では、 *expression* は結果が必要な場合にのみ評価されるコードであり、 *identifier* は結果を格納する値です。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="6fd6b-109">値は型であり `Lazy<'T>` 、に使用される実際の型 `'T` は、式の結果から決定されます。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-109">The value is of type `Lazy<'T>`, where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="6fd6b-110">レイジー式を使用すると、式の実行を、結果が必要な状況のみに制限することで、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="6fd6b-111">式を強制的に実行するには、メソッドを呼び出し `Force` ます。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="6fd6b-112">`Force` 実行を1回だけ実行します。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="6fd6b-113">後続のを呼び出すと、 `Force` 同じ結果が返されますが、コードは実行されません。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="6fd6b-114">次のコードは、レイジー式の使用方法との使用方法を示してい `Force` ます。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="6fd6b-115">このコードでは、の型 `result` は `Lazy<int>` で、メソッドはを `Force` 返し `int` ます。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="6fd6b-116">遅延評価は、型ではなく、 `Lazy` シーケンスにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="6fd6b-117">詳細については、「 [シーケンス](sequences.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6fd6b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fd6b-118">See also</span></span>

- [<span data-ttu-id="6fd6b-119">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="6fd6b-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="6fd6b-120">LazyExtensions モジュール</span><span class="sxs-lookup"><span data-stu-id="6fd6b-120">LazyExtensions module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
