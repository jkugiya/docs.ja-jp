---
title: '破壊的変更:CA2015: MemoryManager<T> から派生した型にはファイナライザーを定義しません'
description: コード分析ルール CA2015 の有効化によって発生する .NET 5 での破壊的変更について学習します。
ms.date: 09/03/2020
ms.openlocfilehash: 4333cec7657657f7e9ba864bcb9979609ad379e0
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257740"
---
# <a name="warning-ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a><span data-ttu-id="26376-103">警告 CA2015:MemoryManager\<T> から派生した型にはファイナライザーを定義しません</span><span class="sxs-lookup"><span data-stu-id="26376-103">Warning CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>

<span data-ttu-id="26376-104">.NET コード アナライザー ルール [CA2015](/visualstudio/code-quality/ca2015) は、.NET 5.0 以降では既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="26376-104">.NET code analyzer rule [CA2015](/visualstudio/code-quality/ca2015) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="26376-105">ファイナライザーを定義する <xref:System.Buffers.MemoryManager%601> から派生したすべての型に対して、ビルドの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="26376-105">It produces a build warning for any types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span>

## <a name="change-description"></a><span data-ttu-id="26376-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="26376-106">Change description</span></span>

<span data-ttu-id="26376-107">.NET 5 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="26376-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="26376-108">これらのルールのいくつかは、[CA2015](/visualstudio/code-quality/ca2015) を含め、既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="26376-108">Several of these rules are enabled, by default, including [CA2015](/visualstudio/code-quality/ca2015).</span></span> <span data-ttu-id="26376-109">このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="26376-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="26376-110">ルール CA2015 によって、ファイナライザーを定義する <xref:System.Buffers.MemoryManager%601> から派生した型にフラグが設定されます。</span><span class="sxs-lookup"><span data-stu-id="26376-110">Rule CA2015 flags types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span> <span data-ttu-id="26376-111"><xref:System.Buffers.MemoryManager%601> から派生した型にファイナライザーを追加すると、バグが示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="26376-111">Adding a finalizer to a type that derives from <xref:System.Buffers.MemoryManager%601> is likely an indication of a bug.</span></span> <span data-ttu-id="26376-112"><xref:System.Span%601> で取得されたネイティブ リソースはクリーンアップされている可能性がありますが、<xref:System.Span%601> によって引き続き使用されている可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="26376-112">It suggests that a native resource that could have been obtained in a <xref:System.Span%601> is getting cleaned up, potentially while it's still in use by the <xref:System.Span%601>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="26376-113">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="26376-113">Version introduced</span></span>

<span data-ttu-id="26376-114">5.0</span><span class="sxs-lookup"><span data-stu-id="26376-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="26376-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="26376-115">Recommended action</span></span>

- <span data-ttu-id="26376-116">ファイナライザーの定義を削除します。</span><span class="sxs-lookup"><span data-stu-id="26376-116">Remove the finalizer definition.</span></span> <span data-ttu-id="26376-117">詳細については、[CA2015](/visualstudio/code-quality/ca2015) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26376-117">For more information, see [CA2015](/visualstudio/code-quality/ca2015).</span></span>

- <span data-ttu-id="26376-118">コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="26376-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="26376-119">詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26376-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="26376-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="26376-120">Affected APIs</span></span>

<span data-ttu-id="26376-121">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="26376-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
