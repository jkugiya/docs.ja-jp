---
title: '例外: raise 関数'
description: F# 'raise' 関数を使用して、エラーまたは例外条件が発生したことを示す方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630290"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="fad20-103">例外: raise 関数</span><span class="sxs-lookup"><span data-stu-id="fad20-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="fad20-104">`raise` 関数は、エラーまたは例外条件が発生したことを示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="fad20-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="fad20-105">エラーに関する情報は、例外オブジェクトでキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="fad20-105">Information about the error is captured in an exception object.</span></span>

## <a name="syntax"></a><span data-ttu-id="fad20-106">構文</span><span class="sxs-lookup"><span data-stu-id="fad20-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="fad20-107">解説</span><span class="sxs-lookup"><span data-stu-id="fad20-107">Remarks</span></span>

<span data-ttu-id="fad20-108">`raise` 関数は、例外オブジェクトを生成し、スタックのアンワインド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="fad20-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="fad20-109">スタックのアンワインド プロセスは共通言語ランタイム (CLR) によって管理されているため、このプロセスの動作は他のすべての .NET 言語と同じになります。</span><span class="sxs-lookup"><span data-stu-id="fad20-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="fad20-110">スタックのアンワインド プロセスでは、生成された例外に一致する例外ハンドラーを検索します。</span><span class="sxs-lookup"><span data-stu-id="fad20-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="fad20-111">検索は、現在の `try...with` 式 (存在する場合) で開始されます。</span><span class="sxs-lookup"><span data-stu-id="fad20-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="fad20-112">`with` ブロック内の各パターンが順番に確認されます。</span><span class="sxs-lookup"><span data-stu-id="fad20-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="fad20-113">一致する例外ハンドラーが見つかった場合、例外は処理済みと見なされます。それ以外の場合、スタックはアンワインドされ、一致するハンドラーが見つかるまで呼び出しチェーンの上部にある `with` ブロックが確認されます。</span><span class="sxs-lookup"><span data-stu-id="fad20-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="fad20-114">呼び出しチェーンで見つかった `finally` ブロックも、スタックのアンワインドと同様に順番に実行されます。</span><span class="sxs-lookup"><span data-stu-id="fad20-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="fad20-115">`raise` 関数は、C# または C++ の `throw` に相当します。</span><span class="sxs-lookup"><span data-stu-id="fad20-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="fad20-116">catch ハンドラーで `reraise` を使用して、同じ例外を呼び出しチェーンの上部に伝達します。</span><span class="sxs-lookup"><span data-stu-id="fad20-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="fad20-117">次のコード例は、`raise` 関数を使用して例外を生成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="fad20-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="fad20-118">`raise` 関数は、次の例に示すように、.NET の例外を発生させるためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="fad20-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a><span data-ttu-id="fad20-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fad20-119">See also</span></span>

- [<span data-ttu-id="fad20-120">例外処理</span><span class="sxs-lookup"><span data-stu-id="fad20-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="fad20-121">例外の種類</span><span class="sxs-lookup"><span data-stu-id="fad20-121">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="fad20-122">例外: `try...with` 式</span><span class="sxs-lookup"><span data-stu-id="fad20-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
- [<span data-ttu-id="fad20-123">例外: `try...finally` 式</span><span class="sxs-lookup"><span data-stu-id="fad20-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
- [<span data-ttu-id="fad20-124">例外: `failwith` 関数</span><span class="sxs-lookup"><span data-stu-id="fad20-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)
- [<span data-ttu-id="fad20-125">例外: `invalidArg` 関数</span><span class="sxs-lookup"><span data-stu-id="fad20-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
