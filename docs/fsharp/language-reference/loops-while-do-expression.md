---
title: 'ループ: while...do 式'
description: while...do 式を使用して、指定したテスト条件が true の間に反復実行 (ループ) を行う方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 73526279358db101f8d07721a200920f1e87f119
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216636"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="3904b-103">ループ: while...do 式</span><span class="sxs-lookup"><span data-stu-id="3904b-103">Loops: while...do Expression</span></span>

<span data-ttu-id="3904b-104">`while...do` 式は、指定したテスト条件が true の間に反復実行 (ループ) を行う場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="3904b-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="3904b-105">構文</span><span class="sxs-lookup"><span data-stu-id="3904b-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="3904b-106">解説</span><span class="sxs-lookup"><span data-stu-id="3904b-106">Remarks</span></span>

<span data-ttu-id="3904b-107">*test-expression* が評価されます。それが `true` の場合、*body-expression* が実行され、テスト式が再評価されます。</span><span class="sxs-lookup"><span data-stu-id="3904b-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="3904b-108">*body-expression* には型 `unit` が必要です。</span><span class="sxs-lookup"><span data-stu-id="3904b-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="3904b-109">テスト式が `false` の場合、反復は終了します。</span><span class="sxs-lookup"><span data-stu-id="3904b-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="3904b-110">`while...do` 式の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3904b-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="3904b-111">前のコードの出力は、1 から 20 までのランダムな数値のストリームで、最後は 10 になります。</span><span class="sxs-lookup"><span data-stu-id="3904b-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```console
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> <span data-ttu-id="3904b-112">`while...do` は、シーケンス式やその他のコンピュテーション式で使用することができます。その場合は、`while...do` 式のカスタマイズされたバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="3904b-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="3904b-113">詳細については、「[シーケンス](sequences.md)」、「[非同期ワークフロー](asynchronous-workflows.md)」、「[コンピュテーション式](computation-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3904b-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3904b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3904b-114">See also</span></span>

- [<span data-ttu-id="3904b-115">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="3904b-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="3904b-116">ループ: `for...in` 式</span><span class="sxs-lookup"><span data-stu-id="3904b-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="3904b-117">ループ: `for...to` 式</span><span class="sxs-lookup"><span data-stu-id="3904b-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
