---
title: インライン関数
description: 呼び出しコードに直接統合されている F# インライン関数を使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630682"
---
# <a name="inline-functions"></a><span data-ttu-id="0d9bf-103">インライン関数</span><span class="sxs-lookup"><span data-stu-id="0d9bf-103">Inline Functions</span></span>

<span data-ttu-id="0d9bf-104">"*インライン関数*" とは、呼び出しコードに直接統合されている関数です。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>

## <a name="using-inline-functions"></a><span data-ttu-id="0d9bf-105">インライン関数の使用</span><span class="sxs-lookup"><span data-stu-id="0d9bf-105">Using Inline Functions</span></span>

<span data-ttu-id="0d9bf-106">静的型パラメーターを使用する場合、型パラメーターによってパラメーター化される関数はインラインである必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="0d9bf-107">これにより、コンパイラでこれらの型パラメーターを解決できることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="0d9bf-108">通常のジェネリック型パラメーターを使用する場合、このような制限はありません。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="0d9bf-109">インライン関数は、メンバー制約の使用を有効にするだけでなく、コードの最適化にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="0d9bf-110">ただし、インライン関数を過剰に使用すると、コンパイラの最適化およびライブラリ関数の実装の変更に対してコードの抵抗力が低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="0d9bf-111">そのため、他のすべての最適化手法を試したのでない限り、最適化にインライン関数を使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="0d9bf-112">関数またはメソッドをインラインにするとパフォーマンスが向上する場合がありますが、常にそうであるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="0d9bf-113">したがって、特定の関数をインラインにすることに実際に好ましい効果があることを確認するために、パフォーマンス測定も使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="0d9bf-114">`inline` 修飾子は、クラスの最上位レベル、モジュール レベル、またはメソッド レベルの関数に適用できます。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="0d9bf-115">次のコード例は、最上位レベルのインライン関数、インライン インスタンス メソッド、インライン静的メソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="0d9bf-116">インライン関数と型の推定</span><span class="sxs-lookup"><span data-stu-id="0d9bf-116">Inline Functions and Type Inference</span></span>

<span data-ttu-id="0d9bf-117">`inline` があると型の推定に影響します。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="0d9bf-118">これは、インライン関数は静的に解決される型パラメーターを持つことができるのに対し、非インライン関数はそうできないためです。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="0d9bf-119">次のコード例は、静的に解決される型パラメーターを持つ関数 (`float` 変換演算子) を使用しているため、`inline` が役に立つケースを示しています。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="0d9bf-120">`inline` 修飾子を使用しない場合、型の推定により、特定の型が関数に強制されます (この場合は `int`)。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="0d9bf-121">しかし、`inline` 修飾子を使用すると、静的に解決される型パラメーターを持つものとして関数が推定されることにもなります。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="0d9bf-122">`inline` 修飾子を使用すると、型は次のように推定されます。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="0d9bf-123">これは、**float** への変換をサポートする任意の型を関数に指定できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0d9bf-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d9bf-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d9bf-124">See also</span></span>

- [<span data-ttu-id="0d9bf-125">関数</span><span class="sxs-lookup"><span data-stu-id="0d9bf-125">Functions</span></span>](index.md)
- [<span data-ttu-id="0d9bf-126">制約</span><span class="sxs-lookup"><span data-stu-id="0d9bf-126">Constraints</span></span>](../generics/constraints.md)
- [<span data-ttu-id="0d9bf-127">静的に解決される型パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d9bf-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
