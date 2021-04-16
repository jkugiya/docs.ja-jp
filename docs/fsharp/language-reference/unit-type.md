---
title: Unit 型
description: 値が不要な場合や目的の値がない場合に、言語の構文で値が必要とされる場所を保持するために、どのようにして F# の 'unit' 型がよく使用されるかについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: a5960fb05af50486a78345d10a5ad913e65729e3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424024"
---
# <a name="unit-type"></a><span data-ttu-id="be611-103">Unit 型</span><span class="sxs-lookup"><span data-stu-id="be611-103">Unit Type</span></span>

<span data-ttu-id="be611-104">`unit` 型は、特定の値を持たないことを示す型です。`unit` 型には値が 1 つだけあり、他の値が存在しない場合や不要な場合のプレースホルダーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="be611-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="be611-105">構文</span><span class="sxs-lookup"><span data-stu-id="be611-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="be611-106">解説</span><span class="sxs-lookup"><span data-stu-id="be611-106">Remarks</span></span>

<span data-ttu-id="be611-107">すべての F# 式は、値に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="be611-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="be611-108">目的の値を生成しない式の場合は、型 `unit` の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="be611-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="be611-109">`unit` 型は、C# や C++ などの言語の `void` 型に似ています。</span><span class="sxs-lookup"><span data-stu-id="be611-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="be611-110">`unit` 型には単一の値があり、その値はトークン `()` によって示されます。</span><span class="sxs-lookup"><span data-stu-id="be611-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="be611-111">F# プログラミングで `unit` 型の値は、言語の構文によって値が必要とされてはいるものの、何ら値が必要なく、望ましくもない場合に、場所を保持する目的でよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="be611-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="be611-112">例として、`printf` 関数の戻り値が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="be611-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="be611-113">`printf` 操作の重要なアクションは関数内で発生するため、関数は実際の値を返す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="be611-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="be611-114">そのため、戻り値の型は `unit` となります。</span><span class="sxs-lookup"><span data-stu-id="be611-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="be611-115">一部のコンストラクトでは `unit` の値が想定されています。</span><span class="sxs-lookup"><span data-stu-id="be611-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="be611-116">たとえば、モジュールの最上位レベルの `do` バインドまたはコードは、`unit` の値に評価されると想定されます。</span><span class="sxs-lookup"><span data-stu-id="be611-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="be611-117">コンパイラでは、次の例に示すように、モジュールの最上位レベルの `do` バインドまたはコードが、使用されていない `unit` の値以外の結果を生成した場合に警告を報告します。</span><span class="sxs-lookup"><span data-stu-id="be611-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="be611-118">この警告は、関数型プログラミングの特性です。他の .NET プログラミング言語では表示されません。</span><span class="sxs-lookup"><span data-stu-id="be611-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="be611-119">関数に副作用がない純粋な関数型プログラムでは、最終的な戻り値は関数呼び出しの唯一の結果となります。</span><span class="sxs-lookup"><span data-stu-id="be611-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="be611-120">そのため、結果が無視された場合は、プログラミング エラーを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="be611-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="be611-121">F# は純粋な関数型プログラミング言語ではありませんが、できる限り関数型プログラミング スタイルに従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="be611-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="be611-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="be611-122">See also</span></span>

- [<span data-ttu-id="be611-123">プリミティブ</span><span class="sxs-lookup"><span data-stu-id="be611-123">Primitive</span></span>](basic-types.md)
- [<span data-ttu-id="be611-124">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="be611-124">F# Language Reference</span></span>](index.md)
