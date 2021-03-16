---
title: 破壊的変更:CA2247:TaskCompletionSource コンストラクターの引数は、TaskCreationOptions 値にする必要があります
description: .NET 5 での破壊的変更について学習します。これは、コード分析ルール CA2247 の有効化によって発生します。
ms.date: 09/03/2020
ms.openlocfilehash: 6c7accaad312352a1448406f2bbf4189f3df1ee5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257701"
---
# <a name="warning-ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a><span data-ttu-id="68398-103">警告 CA2247:TaskCompletionSource コンストラクターの引数は、TaskCreationOptions 値にする必要があります</span><span class="sxs-lookup"><span data-stu-id="68398-103">Warning CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>

<span data-ttu-id="68398-104">.NET コード アナライザー ルール [CA2247](/visualstudio/code-quality/ca2247) は、.NET 5.0 以降では既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="68398-104">.NET code analyzer rule [CA2247](/visualstudio/code-quality/ca2247) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="68398-105"><xref:System.Threading.Tasks.TaskContinuationOptions> 型の引数を渡す <xref:System.Threading.Tasks.TaskCompletionSource%601> コンストラクターへの呼び出しに対して、ビルドの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="68398-105">It produces a build warning for calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span>

## <a name="change-description"></a><span data-ttu-id="68398-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="68398-106">Change description</span></span>

<span data-ttu-id="68398-107">.NET 5 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="68398-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="68398-108">これらのルールのいくつかは、[CA2247](/visualstudio/code-quality/ca2247) を含め、既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="68398-108">Several of these rules are enabled, by default, including [CA2247](/visualstudio/code-quality/ca2247).</span></span> <span data-ttu-id="68398-109">このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68398-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="68398-110">ルール CA2247 によって、<xref:System.Threading.Tasks.TaskContinuationOptions> 型の引数を渡す <xref:System.Threading.Tasks.TaskCompletionSource%601> コンストラクターへの呼び出しが検索されます。</span><span class="sxs-lookup"><span data-stu-id="68398-110">Rule CA2247 finds calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span> <span data-ttu-id="68398-111"><xref:System.Threading.Tasks.TaskCompletionSource%601> 型には、<xref:System.Threading.Tasks.TaskCreationOptions> 値を受け入れるコンストラクターと、<xref:System.Object> を受け入れる別のコンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="68398-111">The <xref:System.Threading.Tasks.TaskCompletionSource%601> type has a constructor that accepts a <xref:System.Threading.Tasks.TaskCreationOptions> value, and another constructor that accepts an <xref:System.Object>.</span></span> <span data-ttu-id="68398-112"><xref:System.Threading.Tasks.TaskCreationOptions> 値ではなく <xref:System.Threading.Tasks.TaskContinuationOptions> 値を誤って渡した場合、<xref:System.Object> パラメーターを持つコンストラクターが実行時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="68398-112">If you accidentally pass a <xref:System.Threading.Tasks.TaskContinuationOptions> value instead of a <xref:System.Threading.Tasks.TaskCreationOptions> value, the constructor with the <xref:System.Object> parameter is called at run time.</span></span> <span data-ttu-id="68398-113">コードは、コンパイルされ、実行されますが、意図した動作を含みません。</span><span class="sxs-lookup"><span data-stu-id="68398-113">Your code will compile and run but won't have the intended behavior.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="68398-114">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="68398-114">Version introduced</span></span>

<span data-ttu-id="68398-115">5.0</span><span class="sxs-lookup"><span data-stu-id="68398-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="68398-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="68398-116">Recommended action</span></span>

- <span data-ttu-id="68398-117"><xref:System.Threading.Tasks.TaskContinuationOptions> 引数を、対応する <xref:System.Threading.Tasks.TaskCreationOptions> 値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="68398-117">Replace the <xref:System.Threading.Tasks.TaskContinuationOptions> argument with the corresponding <xref:System.Threading.Tasks.TaskCreationOptions> value.</span></span> <span data-ttu-id="68398-118">ほぼ常にコード内のバグが強調表示されるため、この警告を表示しないでください。</span><span class="sxs-lookup"><span data-stu-id="68398-118">Do not suppress this warning, since it almost always highlights a bug in your code.</span></span> <span data-ttu-id="68398-119">詳細については、[CA2247](/visualstudio/code-quality/ca2247) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68398-119">For more information, see [CA2247](/visualstudio/code-quality/ca2247).</span></span>

- <span data-ttu-id="68398-120">コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="68398-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="68398-121">詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68398-121">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="68398-122">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="68398-122">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

### Category

Code analysis

-->
