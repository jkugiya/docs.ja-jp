---
title: '破壊的変更:CA2014: stackalloc はループ内で使用しないでください。'
description: コード分析ルール CA2014 の有効化によって発生する .NET 5.0 での破壊的変更について学習します。
ms.date: 09/03/2020
ms.openlocfilehash: 7ad6203c0edd930bbbe43cdb8df0413cba833d8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759319"
---
# <a name="warning-ca2014-do-not-use-stackalloc-in-loops"></a><span data-ttu-id="77ab2-103">警告 CA2014:stackalloc はループ内で使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="77ab2-103">Warning CA2014: Do not use stackalloc in loops</span></span>

<span data-ttu-id="77ab2-104">.NET コード アナライザー ルール [CA2014](/visualstudio/code-quality/ca2014) は、.NET 5.0 以降では既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="77ab2-104">.NET code analyzer rule [CA2014](/visualstudio/code-quality/ca2014) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="77ab2-105">[stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) 式がループ内で使用される C# コードに対して、ビルドの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="77ab2-105">It produces a build warning for any C# code where a [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) expression is used inside a loop.</span></span>

## <a name="change-description"></a><span data-ttu-id="77ab2-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="77ab2-106">Change description</span></span>

<span data-ttu-id="77ab2-107">.NET 5.0 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="77ab2-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="77ab2-108">これらのルールのいくつかは、[CA2014](/visualstudio/code-quality/ca2014) を含め、既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="77ab2-108">Several of these rules are enabled, by default, including [CA2014](/visualstudio/code-quality/ca2014).</span></span> <span data-ttu-id="77ab2-109">このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="77ab2-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="77ab2-110">[stackalloc 式](../../../../csharp/language-reference/operators/stackalloc.md)がループ内で使用されるルール CA2014 によって、C# コードが検索されます。</span><span class="sxs-lookup"><span data-stu-id="77ab2-110">Rule CA2014 looks for C# code where a [stackalloc expression](../../../../csharp/language-reference/operators/stackalloc.md) is used inside a loop.</span></span> <span data-ttu-id="77ab2-111">[stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) によって、現在のスタック フレームからメモリが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="77ab2-111">[stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) allocates memory from the current stack frame.</span></span> <span data-ttu-id="77ab2-112">現在のメソッド呼び出しが戻るまでメモリは解放されません。これにより、スタック オーバーフローにつながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="77ab2-112">The memory isn't released until the current method call returns, which can lead to stack overflows.</span></span> <span data-ttu-id="77ab2-113">スタック オーバーフローの例外をキャッチできないため、スタック オーバーフローが発生した場合はアプリが終了します。</span><span class="sxs-lookup"><span data-stu-id="77ab2-113">Because you can't catch stack overflow exceptions, the app will terminate in case of stack overflow.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="77ab2-114">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="77ab2-114">Version introduced</span></span>

<span data-ttu-id="77ab2-115">5.0</span><span class="sxs-lookup"><span data-stu-id="77ab2-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="77ab2-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="77ab2-116">Recommended action</span></span>

- <span data-ttu-id="77ab2-117">ループ内での [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) の使用を避けます。</span><span class="sxs-lookup"><span data-stu-id="77ab2-117">Avoid using [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) inside loops.</span></span> <span data-ttu-id="77ab2-118">ループの外側でメモリ ブロックを割り当て、それをループ内で再利用してください。</span><span class="sxs-lookup"><span data-stu-id="77ab2-118">Allocate the memory block outside the loop and reuse it inside the loop.</span></span> <span data-ttu-id="77ab2-119">詳細については、[CA2014](/visualstudio/code-quality/ca2014) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77ab2-119">For more information, see [CA2014](/visualstudio/code-quality/ca2014).</span></span>

- <span data-ttu-id="77ab2-120">コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="77ab2-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="77ab2-121">詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77ab2-121">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="77ab2-122">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="77ab2-122">Affected APIs</span></span>

<span data-ttu-id="77ab2-123">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="77ab2-123">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->