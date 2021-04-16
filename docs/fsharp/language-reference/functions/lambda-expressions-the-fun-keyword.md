---
title: 'ラムダ式: fun キーワード'
description: F# の "fun" キーワードを使用して、匿名関数であるラムダ式を定義する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630661"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="229bd-103">ラムダ式: fun キーワード (F#)</span><span class="sxs-lookup"><span data-stu-id="229bd-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="229bd-104">`fun` キーワードは、ラムダ式、つまり匿名関数を定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="229bd-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="229bd-105">構文</span><span class="sxs-lookup"><span data-stu-id="229bd-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="229bd-106">解説</span><span class="sxs-lookup"><span data-stu-id="229bd-106">Remarks</span></span>

<span data-ttu-id="229bd-107">*parameter-list* は、通常、名前と、必要に応じてパラメーターの型で構成されます。</span><span class="sxs-lookup"><span data-stu-id="229bd-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="229bd-108">より一般的には、*parameter-list* は任意の F# パターンで構成できます。</span><span class="sxs-lookup"><span data-stu-id="229bd-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="229bd-109">使用可能なパターンの完全な一覧については、「[パターン マッチ](../pattern-matching.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="229bd-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="229bd-110">有効なパラメーターの一覧を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="229bd-110">Lists of valid parameters include the following examples.</span></span>

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

<span data-ttu-id="229bd-111">*expression* は関数の本体であり、その最後の式で戻り値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="229bd-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="229bd-112">有効なラムダ式の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="229bd-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="229bd-113">ラムダ式の使用</span><span class="sxs-lookup"><span data-stu-id="229bd-113">Using Lambda Expressions</span></span>

<span data-ttu-id="229bd-114">ラムダ式は、リストまたは他のコレクションに対して操作を実行する必要があり、関数を定義する余分な作業を避ける必要がある場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="229bd-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="229bd-115">多くの F# ライブラリ関数は、引数として関数の値を受け取ります。このような場合は、ラムダ式を使用すると特に便利です。</span><span class="sxs-lookup"><span data-stu-id="229bd-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="229bd-116">次のコードは、リストの要素にラムダ式を適用します。</span><span class="sxs-lookup"><span data-stu-id="229bd-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="229bd-117">この場合、匿名関数により、リストのすべての要素に 1 が加算されます。</span><span class="sxs-lookup"><span data-stu-id="229bd-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="229bd-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="229bd-118">See also</span></span>

- [<span data-ttu-id="229bd-119">関数</span><span class="sxs-lookup"><span data-stu-id="229bd-119">Functions</span></span>](index.md)
