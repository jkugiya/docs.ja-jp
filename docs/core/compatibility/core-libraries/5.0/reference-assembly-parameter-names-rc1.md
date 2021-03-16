---
title: 破壊的変更:RC2 でパラメーター名が変更された
description: Core .NET ライブラリにおける .NET 5 の破壊的変更について学習します。一部の参照アセンブリ パラメーター名が .NET 5.0 のプレビューとリリース候補バージョンから変更されました。
ms.date: 11/01/2020
ms.openlocfilehash: caca9055bda50174b40d5675c6d34679df61deba
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257194"
---
# <a name="parameter-names-changed-in-rc2"></a><span data-ttu-id="33b56-103">RC2 でパラメーター名が変更された</span><span class="sxs-lookup"><span data-stu-id="33b56-103">Parameter names changed in RC2</span></span>

<span data-ttu-id="33b56-104">一部の参照アセンブリ パラメーター名が、実装アセンブリ内のパラメーター名と一致するように変更されました。</span><span class="sxs-lookup"><span data-stu-id="33b56-104">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

## <a name="change-description"></a><span data-ttu-id="33b56-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="33b56-105">Change description</span></span>

<span data-ttu-id="33b56-106">以前の .NET 5 Preview および RC バージョンでは、一部の[参照アセンブリ](../../../../standard/assembly/reference-assemblies.md)のパラメーター名が、実装アセンブリ内にある対応するパラメーターのものとは異なっています。</span><span class="sxs-lookup"><span data-stu-id="33b56-106">In previous .NET 5 preview and RC versions, some [reference assembly](../../../../standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="33b56-107">これにより、名前付き引数とリフレクションの使用中に問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="33b56-107">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="33b56-108">.NET 5 RC2 では、参照アセンブリ内でこのような不一致のパラメーター名が更新され、実装アセンブリ内の対応するパラメーター名と完全に一致するようになりました。</span><span class="sxs-lookup"><span data-stu-id="33b56-108">In .NET 5 RC2, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="33b56-109">次の表に API と変更されたパラメーター名を示します。</span><span class="sxs-lookup"><span data-stu-id="33b56-109">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="33b56-110">API</span><span class="sxs-lookup"><span data-stu-id="33b56-110">API</span></span> | <span data-ttu-id="33b56-111">古いパラメーター名</span><span class="sxs-lookup"><span data-stu-id="33b56-111">Old parameter name</span></span> | <span data-ttu-id="33b56-112">新しいパラメーター名</span><span class="sxs-lookup"><span data-stu-id="33b56-112">New parameter name</span></span> |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

## <a name="reason-for-change"></a><span data-ttu-id="33b56-113">変更理由</span><span class="sxs-lookup"><span data-stu-id="33b56-113">Reason for change</span></span>

<span data-ttu-id="33b56-114">一貫性を保つため、および名前付き引数とリフレクションを使用するときにエラーが発生するのを回避するために、パラメーター名が変更されました。</span><span class="sxs-lookup"><span data-stu-id="33b56-114">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="33b56-115">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="33b56-115">Version introduced</span></span>

<span data-ttu-id="33b56-116">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="33b56-116">5.0 RC2</span></span>

## <a name="recommended-action"></a><span data-ttu-id="33b56-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="33b56-117">Recommended action</span></span>

<span data-ttu-id="33b56-118">パラメーター名の変更が原因で、コンパイラ エラーが発生する場合は、適宜パラメーター名を更新してください。</span><span class="sxs-lookup"><span data-stu-id="33b56-118">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="33b56-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="33b56-119">Affected APIs</span></span>

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
