---
title: 破壊的変更:Vector<T> が NotSupportedException をスローする
description: Core .NET ライブラリにおける .NET 5 の破壊的変更について学習します。Vector<T> によって、サポートされていない型パラメーターに対して常に例外がスローされます。
ms.date: 11/01/2020
ms.openlocfilehash: dccd39c01f4debd7d1432195e7f3cb14aeda5f65
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257012"
---
# <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a><span data-ttu-id="16778-103">Vector\<T> で、サポートされていない型に対して常に NotSupportedException がスローされる</span><span class="sxs-lookup"><span data-stu-id="16778-103">Vector\<T> always throws NotSupportedException for unsupported types</span></span>

<span data-ttu-id="16778-104"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> では、サポートされていない型パラメーターに対して常に <xref:System.NotSupportedException> がスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="16778-104"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> now always throws a <xref:System.NotSupportedException> for unsupported type parameters.</span></span>

## <a name="change-description"></a><span data-ttu-id="16778-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="16778-105">Change description</span></span>

<span data-ttu-id="16778-106">以前の <xref:System.Numerics.Vector%601> のメンバーでは、`T` が [サポートされていない型](#unsupported-types)だった場合に、常に <xref:System.NotSupportedException> がスローされるとは限りませんでした。</span><span class="sxs-lookup"><span data-stu-id="16778-106">Previously, members of <xref:System.Numerics.Vector%601> would not always throw a <xref:System.NotSupportedException> when `T` was an [unsupported type](#unsupported-types).</span></span> <span data-ttu-id="16778-107">例外が常にスローされなかったのは、ハードウェアの高速化をサポートしていたコード パスが原因でした。</span><span class="sxs-lookup"><span data-stu-id="16778-107">The exception wasn't always thrown because of code paths that supported hardware acceleration.</span></span> <span data-ttu-id="16778-108">たとえば、ハードウェアの高速化がないプラットフォーム (ARM32 など) で `Vector<bool> + Vector<bool>` を使用すると、例外をスローするのではなく `default` が返されました。</span><span class="sxs-lookup"><span data-stu-id="16778-108">For example, `Vector<bool> + Vector<bool>` returned `default` instead of throwing an exception on platforms that have no hardware acceleration, such as ARM32.</span></span> <span data-ttu-id="16778-109">サポートされていない型について、<xref:System.Numerics.Vector%601> のメンバーが示す動作には、異なるプラットフォームやハードウェア構成にわたる一貫性がありませんでした。</span><span class="sxs-lookup"><span data-stu-id="16778-109">For unsupported types, <xref:System.Numerics.Vector%601> members exhibited inconsistent behavior across different platforms and hardware configurations.</span></span>

<span data-ttu-id="16778-110">.NET 5 以降、<xref:System.Numerics.Vector%601> のメンバーでは、`T` がサポートされていない型である場合に、すべてのハードウェア構成で常に <xref:System.NotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="16778-110">Starting in .NET 5, <xref:System.Numerics.Vector%601> members always throw a <xref:System.NotSupportedException> on all hardware configurations when `T` is not a supported type.</span></span>

### <a name="unsupported-types"></a><span data-ttu-id="16778-111">サポートされていない型</span><span class="sxs-lookup"><span data-stu-id="16778-111">Unsupported types</span></span>

<span data-ttu-id="16778-112"><xref:System.Numerics.Vector%601> の型パラメーターでサポートされている型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="16778-112">The supported types for the type parameter of <xref:System.Numerics.Vector%601> are:</span></span>

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

<span data-ttu-id="16778-113">サポートされている型は変更されていませんが、将来変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16778-113">The supported types have not changed, however, they may change in the future.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="16778-114">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="16778-114">Version introduced</span></span>

<span data-ttu-id="16778-115">5.0</span><span class="sxs-lookup"><span data-stu-id="16778-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="16778-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="16778-116">Recommended action</span></span>

<span data-ttu-id="16778-117"><xref:System.Numerics.Vector%601> の型パラメーターにサポートされていない型を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="16778-117">Don't use an unsupported type for the type parameter of <xref:System.Numerics.Vector%601>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="16778-118">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="16778-118">Affected APIs</span></span>

- <span data-ttu-id="16778-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> およびそのすべてのメンバー</span><span class="sxs-lookup"><span data-stu-id="16778-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> and all its members</span></span>

<!--

#### Category

Core .NET libraries

### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
