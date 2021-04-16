---
title: アサーション
description: F# プログラミング言語で式をテストするためのデバッグ機能として 'assert' 式を使用する方法について説明します。
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799059"
---
# <a name="assertions"></a><span data-ttu-id="9321e-103">アサーション</span><span class="sxs-lookup"><span data-stu-id="9321e-103">Assertions</span></span>

<span data-ttu-id="9321e-104">`assert` 式は、式のテストに使用できるデバッグ機能です。</span><span class="sxs-lookup"><span data-stu-id="9321e-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="9321e-105">デバッグ モードでエラーが発生すると、アサーションによってシステム エラーのダイアログ ボックスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9321e-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="9321e-106">構文</span><span class="sxs-lookup"><span data-stu-id="9321e-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="9321e-107">解説</span><span class="sxs-lookup"><span data-stu-id="9321e-107">Remarks</span></span>

<span data-ttu-id="9321e-108">`assert` 式の型は `bool -> unit` です。</span><span class="sxs-lookup"><span data-stu-id="9321e-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="9321e-109">`assert` 関数は <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> に解決されます。</span><span class="sxs-lookup"><span data-stu-id="9321e-109">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9321e-110">これは、その動作が <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> を直接呼び出した場合と同じであることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9321e-110">This means its behavior is identical to having called <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="9321e-111">アサーション チェックは、デバッグ モードでコンパイルした場合にのみ有効になります。つまり、定数 `DEBUG` が定義されている場合です。</span><span class="sxs-lookup"><span data-stu-id="9321e-111">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="9321e-112">プロジェクト システムでは、既定で、デバッグ構成の場合に `DEBUG` 定数が定義されますが、リリース構成の場合には定義されません。</span><span class="sxs-lookup"><span data-stu-id="9321e-112">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="9321e-113">F# 例外処理を使用してアサーション エラーをキャッチすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9321e-113">The assertion failure error cannot be caught by using F# exception handling.</span></span>

## <a name="example"></a><span data-ttu-id="9321e-114">例</span><span class="sxs-lookup"><span data-stu-id="9321e-114">Example</span></span>

<span data-ttu-id="9321e-115">次のコードは、`assert` 式の使用例を示しています。</span><span class="sxs-lookup"><span data-stu-id="9321e-115">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="9321e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9321e-116">See also</span></span>

- [<span data-ttu-id="9321e-117">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="9321e-117">F# Language Reference</span></span>](index.md)
