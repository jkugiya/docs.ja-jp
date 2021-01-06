---
title: '破壊的変更:CA2013: 値の型と共に ReferenceEquals を使用しないでください'
description: コード分析ルール CA2013 の有効化によって発生する .NET 5.0 での破壊的変更について学習します。
ms.date: 09/03/2020
ms.openlocfilehash: ca2b845427eff547b996b577394c6859e30f50bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759320"
---
# <a name="warning-ca2013-do-not-use-referenceequals-with-value-types"></a><span data-ttu-id="4c0f3-103">警告 CA2013:値の型と共に ReferenceEquals を使用しないでください</span><span class="sxs-lookup"><span data-stu-id="4c0f3-103">Warning CA2013: Do not use ReferenceEquals with value types</span></span>

<span data-ttu-id="4c0f3-104">.NET コード アナライザー ルール [CA2013](/visualstudio/code-quality/ca2013) は、.NET 5.0 以降では既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-104">.NET code analyzer rule [CA2013](/visualstudio/code-quality/ca2013) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="4c0f3-105"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> を使用して 1 つまたは複数の値の型の等価性を比較するコードについては、ビルド警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-105">It produces a build warning for any code where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span>

## <a name="change-description"></a><span data-ttu-id="4c0f3-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="4c0f3-106">Change description</span></span>

<span data-ttu-id="4c0f3-107">.NET 5.0 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="4c0f3-108">これらのルールのいくつかは、[CA2013](/visualstudio/code-quality/ca2013) を含め、既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-108">Several of these rules are enabled, by default, including [CA2013](/visualstudio/code-quality/ca2013).</span></span> <span data-ttu-id="4c0f3-109">このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="4c0f3-110"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> を使用して 1 または複数の値の型の等価性を比較するインスタンスが、ルール CA2013 によって検出されます。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-110">Rule CA2013 finds instances where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span> <span data-ttu-id="4c0f3-111">このように値の型の等価性を比較すると、値がボックス化されてから比較が行われるため、結果が不正確になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-111">Comparing value types for equality in this way can lead to incorrect results, because the values are boxed before they're compared.</span></span> <span data-ttu-id="4c0f3-112">比較した値が、同じ値の型のインスタンスを表す場合でも、<xref:System.Object.ReferenceEquals(System.Object,System.Object)> からは `false` が返されます。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-112"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> will return `false` even if the compared values represent the same instance of a value type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4c0f3-113">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="4c0f3-113">Version introduced</span></span>

<span data-ttu-id="4c0f3-114">5.0</span><span class="sxs-lookup"><span data-stu-id="4c0f3-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4c0f3-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="4c0f3-115">Recommended action</span></span>

- <span data-ttu-id="4c0f3-116">適切な等値演算子 (`==` など) を使用するようにコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-116">Change the code to use an appropriate equality operator, such as `==`.</span></span> <span data-ttu-id="4c0f3-117">この警告を抑制しないでください。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-117">You should not suppress this warning.</span></span>

- <span data-ttu-id="4c0f3-118">コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="4c0f3-119">詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c0f3-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4c0f3-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="4c0f3-120">Affected APIs</span></span>

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

### Category

Code analysis

-->