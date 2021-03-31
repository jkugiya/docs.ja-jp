---
title: System.Text.Json でサポートされているコレクション型
description: System.Text.Json 名前空間の API によるシリアル化がサポートされているコレクション型について説明します。
ms.date: 02/01/2021
no-loc:
- System.Text.Json
ms.topic: reference
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 5a5016c70e86124510a4778aafb9fb14b1890add
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2021
ms.locfileid: "99547656"
---
# <a name="supported-collection-types-in-systemtextjson"></a><span data-ttu-id="6a7b5-103">System.Text.Json でサポートされているコレクション型</span><span class="sxs-lookup"><span data-stu-id="6a7b5-103">Supported collection types in System.Text.Json</span></span>

<span data-ttu-id="6a7b5-104">この記事では、どのコレクションでシリアル化および逆シリアル化がサポートされているかを概説します。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-104">This article gives an overview of which collections are supported for serialization and deserialization.</span></span> <span data-ttu-id="6a7b5-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> では、次の場合にシリアル化用のコレクション型をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> supports a collection type for serialization if it:</span></span>

* <span data-ttu-id="6a7b5-106"><xref:System.Collections.IEnumerable>から派生します。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-106">Derives from <xref:System.Collections.IEnumerable>.</span></span>
* <span data-ttu-id="6a7b5-107">シリアル化可能な要素が含まれている。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-107">Contains elements that are serializable.</span></span>

<span data-ttu-id="6a7b5-108">シリアライザーが <xref:System.Collections.IEnumerable.GetEnumerator> メソッドを呼び出し、その要素を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-108">The serializer calls the <xref:System.Collections.IEnumerable.GetEnumerator> method, and writes the elements.</span></span>

<span data-ttu-id="6a7b5-109">逆シリアル化はこれよりも複雑であり、一部のコレクション型ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-109">Deserialization is more complicated and is not supported for some collection types.</span></span>

<span data-ttu-id="6a7b5-110">次のセクションでは、名前空間ごとに、シリアル化と逆シリアル化がサポートされている型を示します。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-110">The following sections are organized by namespace and show which types are supported for serialization and deserialization.</span></span>

## <a name="systemarray-namespace"></a><span data-ttu-id="6a7b5-111">System.Array 名前空間</span><span class="sxs-lookup"><span data-stu-id="6a7b5-111">System.Array namespace</span></span>

| <span data-ttu-id="6a7b5-112">種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-112">Type</span></span>                                                                                            | <span data-ttu-id="6a7b5-113">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-113">Serialization</span></span> | <span data-ttu-id="6a7b5-114">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-114">Deserialization</span></span> |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| [<span data-ttu-id="6a7b5-115">1 次元配列</span><span class="sxs-lookup"><span data-stu-id="6a7b5-115">Single-dimensional arrays</span></span>](../../csharp/programming-guide/arrays/single-dimensional-arrays.md) | <span data-ttu-id="6a7b5-116">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-116">✔️</span></span>           | <span data-ttu-id="6a7b5-117">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-117">✔️</span></span>              |
| [<span data-ttu-id="6a7b5-118">多次元配列</span><span class="sxs-lookup"><span data-stu-id="6a7b5-118">Multi-dimensional arrays</span></span>](../../csharp/programming-guide/arrays/multidimensional-arrays.md)    | ❌           | ❌              |
| [<span data-ttu-id="6a7b5-119">ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="6a7b5-119">Jagged arrays</span></span>](../../csharp/programming-guide/arrays/jagged-arrays.md)                         | <span data-ttu-id="6a7b5-120">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-120">✔️</span></span>           | <span data-ttu-id="6a7b5-121">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-121">✔️</span></span>              |

## <a name="systemcollections-namespace"></a><span data-ttu-id="6a7b5-122">System.Collections 名前空間</span><span class="sxs-lookup"><span data-stu-id="6a7b5-122">System.Collections namespace</span></span>

| <span data-ttu-id="6a7b5-123">種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-123">Type</span></span>                                      | <span data-ttu-id="6a7b5-124">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-124">Serialization</span></span> | <span data-ttu-id="6a7b5-125">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-125">Deserialization</span></span> |
|-------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ArrayList>       | <span data-ttu-id="6a7b5-126">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-126">✔️</span></span>           | <span data-ttu-id="6a7b5-127">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-127">✔️</span></span>              |
| <xref:System.Collections.BitArray>        | <span data-ttu-id="6a7b5-128">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-128">✔️</span></span>           | ❌              |
| <xref:System.Collections.DictionaryEntry> | <span data-ttu-id="6a7b5-129">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-129">✔️</span></span>           | <span data-ttu-id="6a7b5-130">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-130">✔️</span></span>              |
| <xref:System.Collections.Hashtable>       | <span data-ttu-id="6a7b5-131">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-131">✔️</span></span>           | <span data-ttu-id="6a7b5-132">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-132">✔️</span></span>              |
| <xref:System.Collections.Queue>           | <span data-ttu-id="6a7b5-133">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-133">✔️</span></span>           | <span data-ttu-id="6a7b5-134">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-134">✔️</span></span>              |
| <xref:System.Collections.SortedList>      | <span data-ttu-id="6a7b5-135">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-135">✔️</span></span>           | <span data-ttu-id="6a7b5-136">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-136">✔️</span></span>              |
| <xref:System.Collections.Stack>           | <span data-ttu-id="6a7b5-137">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-137">✔️</span></span>           | <span data-ttu-id="6a7b5-138">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-138">✔️</span></span>              |
| <xref:System.Collections.ICollection>     | <span data-ttu-id="6a7b5-139">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-139">✔️</span></span>           | <span data-ttu-id="6a7b5-140">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-140">✔️</span></span>              |
| <xref:System.Collections.IDictionary>     | <span data-ttu-id="6a7b5-141">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-141">✔️</span></span>           | <span data-ttu-id="6a7b5-142">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-142">✔️</span></span>              |
| <xref:System.Collections.IEnumerable>     | <span data-ttu-id="6a7b5-143">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-143">✔️</span></span>           | <span data-ttu-id="6a7b5-144">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-144">✔️</span></span>              |
| <xref:System.Collections.IList>           | <span data-ttu-id="6a7b5-145">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-145">✔️</span></span>           | <span data-ttu-id="6a7b5-146">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-146">✔️</span></span>              |

## <a name="systemcollectionsgeneric-namespace"></a><span data-ttu-id="6a7b5-147">System.Collections.Generic 名前空間</span><span class="sxs-lookup"><span data-stu-id="6a7b5-147">System.Collections.Generic namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="6a7b5-148">種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-148">Type</span></span>                                                      | <span data-ttu-id="6a7b5-149">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-149">Serialization</span></span> | <span data-ttu-id="6a7b5-150">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-150">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="6a7b5-151"><xref:System.Collections.Generic.Dictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-151"><xref:System.Collections.Generic.Dictionary%602> \*</span></span>       | <span data-ttu-id="6a7b5-152">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-152">✔️</span></span>           | <span data-ttu-id="6a7b5-153">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-153">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>             | <span data-ttu-id="6a7b5-154">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-154">✔️</span></span>           | <span data-ttu-id="6a7b5-155">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-155">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>        | <span data-ttu-id="6a7b5-156">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-156">✔️</span></span>           | <span data-ttu-id="6a7b5-157">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-157">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>          | <span data-ttu-id="6a7b5-158">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-158">✔️</span></span>           | <span data-ttu-id="6a7b5-159">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-159">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>      | <span data-ttu-id="6a7b5-160">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-160">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                | <span data-ttu-id="6a7b5-161">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-161">✔️</span></span>           | <span data-ttu-id="6a7b5-162">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-162">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>               | <span data-ttu-id="6a7b5-163">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-163">✔️</span></span>           | <span data-ttu-id="6a7b5-164">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-164">✔️</span></span>              |
| <span data-ttu-id="6a7b5-165"><xref:System.Collections.Generic.SortedDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-165"><xref:System.Collections.Generic.SortedDictionary%602> \*</span></span> | <span data-ttu-id="6a7b5-166">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-166">✔️</span></span>           | <span data-ttu-id="6a7b5-167">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-167">✔️</span></span>              |
| <span data-ttu-id="6a7b5-168"><xref:System.Collections.Generic.SortedList%602> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-168"><xref:System.Collections.Generic.SortedList%602> \*</span></span>       | <span data-ttu-id="6a7b5-169">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-169">✔️</span></span>           | <span data-ttu-id="6a7b5-170">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-170">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>           | <span data-ttu-id="6a7b5-171">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-171">✔️</span></span>           | <span data-ttu-id="6a7b5-172">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-172">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>               | <span data-ttu-id="6a7b5-173">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-173">✔️</span></span>           | <span data-ttu-id="6a7b5-174">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-174">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>    | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>         | <span data-ttu-id="6a7b5-175">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-175">✔️</span></span>           | <span data-ttu-id="6a7b5-176">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-176">✔️</span></span>              |
| <span data-ttu-id="6a7b5-177"><xref:System.Collections.Generic.IDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-177"><xref:System.Collections.Generic.IDictionary%602> \*</span></span>      | <span data-ttu-id="6a7b5-178">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-178">✔️</span></span>           | <span data-ttu-id="6a7b5-179">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-179">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>         | <span data-ttu-id="6a7b5-180">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-180">✔️</span></span>           | <span data-ttu-id="6a7b5-181">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-181">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>               | <span data-ttu-id="6a7b5-182">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-182">✔️</span></span>           | <span data-ttu-id="6a7b5-183">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-183">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601> | <span data-ttu-id="6a7b5-184">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-184">✔️</span></span>           | <span data-ttu-id="6a7b5-185">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-185">✔️</span></span>              |
| <span data-ttu-id="6a7b5-186"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-186"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span></span> | <span data-ttu-id="6a7b5-187">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-187">✔️</span></span>        | <span data-ttu-id="6a7b5-188">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-188">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>       | <span data-ttu-id="6a7b5-189">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-189">✔️</span></span>           | <span data-ttu-id="6a7b5-190">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-190">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                | <span data-ttu-id="6a7b5-191">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-191">✔️</span></span>           | <span data-ttu-id="6a7b5-192">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-192">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="6a7b5-193">種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-193">Type</span></span>                                                                                            | <span data-ttu-id="6a7b5-194">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-194">Serialization</span></span> | <span data-ttu-id="6a7b5-195">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-195">Deserialization</span></span> |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="6a7b5-196">[Dictionary\<string, TValue>](xref:System.Collections.Generic.Dictionary%602) \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-196">[Dictionary\<string, TValue>](xref:System.Collections.Generic.Dictionary%602) \*</span></span>                | <span data-ttu-id="6a7b5-197">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-197">✔️</span></span>           | <span data-ttu-id="6a7b5-198">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-198">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>                                                   | <span data-ttu-id="6a7b5-199">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-199">✔️</span></span>           | <span data-ttu-id="6a7b5-200">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-200">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>                                              | <span data-ttu-id="6a7b5-201">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-201">✔️</span></span>           | <span data-ttu-id="6a7b5-202">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-202">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>                                                | <span data-ttu-id="6a7b5-203">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-203">✔️</span></span>           | <span data-ttu-id="6a7b5-204">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-204">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>                                            | <span data-ttu-id="6a7b5-205">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-205">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                                                      | <span data-ttu-id="6a7b5-206">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-206">✔️</span></span>           | <span data-ttu-id="6a7b5-207">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-207">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>                                                     | <span data-ttu-id="6a7b5-208">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-208">✔️</span></span>           | <span data-ttu-id="6a7b5-209">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-209">✔️</span></span>              |
| <span data-ttu-id="6a7b5-210">[SortedDictionary\<string, TValue>](xref:System.Collections.Generic.SortedDictionary%602) \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-210">[SortedDictionary\<string, TValue>](xref:System.Collections.Generic.SortedDictionary%602) \*</span></span>    | <span data-ttu-id="6a7b5-211">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-211">✔️</span></span>           | <span data-ttu-id="6a7b5-212">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-212">✔️</span></span>              |
| <span data-ttu-id="6a7b5-213">[SortedList\<string, TValue>](xref:System.Collections.Generic.SortedList%602) \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-213">[SortedList\<string, TValue>](xref:System.Collections.Generic.SortedList%602) \*</span></span>                | <span data-ttu-id="6a7b5-214">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-214">✔️</span></span>           | <span data-ttu-id="6a7b5-215">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-215">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>                                                 | <span data-ttu-id="6a7b5-216">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-216">✔️</span></span>           | <span data-ttu-id="6a7b5-217">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-217">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>                                                     | <span data-ttu-id="6a7b5-218">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-218">✔️</span></span>           | <span data-ttu-id="6a7b5-219">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-219">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>                                          | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>                                               | <span data-ttu-id="6a7b5-220">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-220">✔️</span></span>           | <span data-ttu-id="6a7b5-221">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-221">✔️</span></span>              |
| <span data-ttu-id="6a7b5-222">[IDictionary\<string, TValue> ](xref:System.Collections.Generic.IDictionary%602) \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-222">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*</span></span>              | <span data-ttu-id="6a7b5-223">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-223">✔️</span></span>           | <span data-ttu-id="6a7b5-224">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-224">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>                                               | <span data-ttu-id="6a7b5-225">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-225">✔️</span></span>           | <span data-ttu-id="6a7b5-226">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-226">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>                                                     | <span data-ttu-id="6a7b5-227">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-227">✔️</span></span>           | <span data-ttu-id="6a7b5-228">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-228">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601>                                       | <span data-ttu-id="6a7b5-229">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-229">✔️</span></span>           | <span data-ttu-id="6a7b5-230">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-230">✔️</span></span>              |
| <span data-ttu-id="6a7b5-231">[IReadOnlyDictionary\<string, TValue>](xref:System.Collections.Generic.IReadOnlyDictionary%602) \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-231">[IReadOnlyDictionary\<string, TValue>](xref:System.Collections.Generic.IReadOnlyDictionary%602) \*</span></span> | <span data-ttu-id="6a7b5-232">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-232">✔️</span></span>        | <span data-ttu-id="6a7b5-233">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-233">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>                                             | <span data-ttu-id="6a7b5-234">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-234">✔️</span></span>           | <span data-ttu-id="6a7b5-235">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-235">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                                                      | <span data-ttu-id="6a7b5-236">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-236">✔️</span></span>           | <span data-ttu-id="6a7b5-237">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-237">✔️</span></span>              |

::: zone-end

<span data-ttu-id="6a7b5-238">\* 「[サポートされているキーの種類](#supported-key-types)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-238">\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsimmutable-namespace"></a><span data-ttu-id="6a7b5-239">System.Collections.Immutable 名前空間</span><span class="sxs-lookup"><span data-stu-id="6a7b5-239">System.Collections.Immutable namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="6a7b5-240">種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-240">Type</span></span>                                                              | <span data-ttu-id="6a7b5-241">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-241">Serialization</span></span> | <span data-ttu-id="6a7b5-242">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-242">Deserialization</span></span> |
|-------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>            | <span data-ttu-id="6a7b5-243">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-243">✔️</span></span>           | <span data-ttu-id="6a7b5-244">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-244">✔️</span></span>              |
| <span data-ttu-id="6a7b5-245"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-245"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span></span>  | <span data-ttu-id="6a7b5-246">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-246">✔️</span></span>           | <span data-ttu-id="6a7b5-247">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-247">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>          | <span data-ttu-id="6a7b5-248">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-248">✔️</span></span>           | <span data-ttu-id="6a7b5-249">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-249">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="6a7b5-250">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-250">✔️</span></span>           | <span data-ttu-id="6a7b5-251">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-251">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>            | <span data-ttu-id="6a7b5-252">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-252">✔️</span></span>           | <span data-ttu-id="6a7b5-253">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-253">✔️</span></span>              |
| <span data-ttu-id="6a7b5-254"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-254"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span></span> | <span data-ttu-id="6a7b5-255">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-255">✔️</span></span>      | <span data-ttu-id="6a7b5-256">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-256">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>        | <span data-ttu-id="6a7b5-257">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-257">✔️</span></span>           | <span data-ttu-id="6a7b5-258">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-258">✔️</span></span>              |
| <span data-ttu-id="6a7b5-259"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-259"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>         | <span data-ttu-id="6a7b5-260">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-260">✔️</span></span>           | <span data-ttu-id="6a7b5-261">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-261">✔️</span></span>              |
| <span data-ttu-id="6a7b5-262"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-262"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span></span> | <span data-ttu-id="6a7b5-263">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-263">✔️</span></span>           | <span data-ttu-id="6a7b5-264">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-264">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="6a7b5-265">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-265">✔️</span></span>           | <span data-ttu-id="6a7b5-266">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-266">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>           | <span data-ttu-id="6a7b5-267">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-267">✔️</span></span>           | <span data-ttu-id="6a7b5-268">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-268">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>             | <span data-ttu-id="6a7b5-269">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-269">✔️</span></span>           | <span data-ttu-id="6a7b5-270">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-270">✔️</span></span>              |
| <span data-ttu-id="6a7b5-271"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-271"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>        | <span data-ttu-id="6a7b5-272">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-272">✔️</span></span>           | <span data-ttu-id="6a7b5-273">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-273">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="6a7b5-274">種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-274">Type</span></span>                                                                                                          | <span data-ttu-id="6a7b5-275">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-275">Serialization</span></span> | <span data-ttu-id="6a7b5-276">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-276">Deserialization</span></span> |
|---------------------------------------------------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>                                                        | <span data-ttu-id="6a7b5-277">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-277">✔️</span></span>           | <span data-ttu-id="6a7b5-278">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-278">✔️</span></span>              |
| <span data-ttu-id="6a7b5-279">[ImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableDictionary%602) \*\*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-279">[ImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableDictionary%602) \*\*</span></span>        | <span data-ttu-id="6a7b5-280">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-280">✔️</span></span>           | <span data-ttu-id="6a7b5-281">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-281">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>                                                      | <span data-ttu-id="6a7b5-282">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-282">✔️</span></span>           | <span data-ttu-id="6a7b5-283">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-283">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="6a7b5-284">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-284">✔️</span></span>           | <span data-ttu-id="6a7b5-285">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-285">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>                                                        | <span data-ttu-id="6a7b5-286">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-286">✔️</span></span>           | <span data-ttu-id="6a7b5-287">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-287">✔️</span></span>              |
| <span data-ttu-id="6a7b5-288">[ImmutableSortedDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableSortedDictionary%602) \*\*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-288">[ImmutableSortedDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableSortedDictionary%602) \*\*</span></span>| <span data-ttu-id="6a7b5-289">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-289">✔️</span></span>       | <span data-ttu-id="6a7b5-290">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-290">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>                                                    | <span data-ttu-id="6a7b5-291">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-291">✔️</span></span>           | <span data-ttu-id="6a7b5-292">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-292">✔️</span></span>              |
| <span data-ttu-id="6a7b5-293"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-293"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>                                                     | <span data-ttu-id="6a7b5-294">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-294">✔️</span></span>           | <span data-ttu-id="6a7b5-295">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-295">✔️</span></span>              |
| <span data-ttu-id="6a7b5-296">[IImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.IImmutableDictionary%602) \*\*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-296">[IImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.IImmutableDictionary%602) \*\*</span></span>      | <span data-ttu-id="6a7b5-297">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-297">✔️</span></span>           | <span data-ttu-id="6a7b5-298">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-298">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="6a7b5-299">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-299">✔️</span></span>           | <span data-ttu-id="6a7b5-300">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-300">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>                                                       | <span data-ttu-id="6a7b5-301">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-301">✔️</span></span>           | <span data-ttu-id="6a7b5-302">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-302">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>                                                         | <span data-ttu-id="6a7b5-303">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-303">✔️</span></span>           | <span data-ttu-id="6a7b5-304">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-304">✔️</span></span>              |
| <span data-ttu-id="6a7b5-305"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-305"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>                                                    | <span data-ttu-id="6a7b5-306">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-306">✔️</span></span>           | <span data-ttu-id="6a7b5-307">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-307">✔️</span></span>              |

::: zone-end

<span data-ttu-id="6a7b5-308">\* 「[Stack\<T> のラウンド トリップをサポートする](system-text-json-converters-how-to.md#support-round-trip-for-stackt)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-308">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="6a7b5-309">\* 「\*サポートされているキーの種類[」を参照してください](#supported-key-types)。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-309">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsspecialized-namespace"></a><span data-ttu-id="6a7b5-310">System.Collections.Specialized 名前空間</span><span class="sxs-lookup"><span data-stu-id="6a7b5-310">System.Collections.Specialized namespace</span></span>

| <span data-ttu-id="6a7b5-311">種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-311">Type</span></span>                                                      | <span data-ttu-id="6a7b5-312">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-312">Serialization</span></span> | <span data-ttu-id="6a7b5-313">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-313">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Specialized.BitVector32>         | <span data-ttu-id="6a7b5-314">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-314">✔️</span></span>           | ❌\*            |
| <xref:System.Collections.Specialized.HybridDictionary>    | <span data-ttu-id="6a7b5-315">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-315">✔️</span></span>           | <span data-ttu-id="6a7b5-316">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-316">✔️</span></span>              |
| <xref:System.Collections.Specialized.IOrderedDictionary>  | <span data-ttu-id="6a7b5-317">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-317">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.ListDictionary>      | <span data-ttu-id="6a7b5-318">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-318">✔️</span></span>           | <span data-ttu-id="6a7b5-319">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-319">✔️</span></span>              |
| <xref:System.Collections.Specialized.StringCollection>    | <span data-ttu-id="6a7b5-320">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-320">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.StringDictionary>    | <span data-ttu-id="6a7b5-321">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-321">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.NameValueCollection> | <span data-ttu-id="6a7b5-322">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-322">✔️</span></span>           | ❌              |

<span data-ttu-id="6a7b5-323">\* <xref:System.Collections.Specialized.BitVector32> が逆シリアル化されると、パブリック セッターがないため、<xref:System.Collections.Specialized.BitVector32.Data> はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-323">\* When <xref:System.Collections.Specialized.BitVector32> is deserialized, the <xref:System.Collections.Specialized.BitVector32.Data> property is skipped because it doesn't have a public setter.</span></span> <span data-ttu-id="6a7b5-324">例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-324">No exception is thrown.</span></span>

## <a name="systemcollectionsconcurrent-namespace"></a><span data-ttu-id="6a7b5-325">System.Collections.Concurrent 名前空間</span><span class="sxs-lookup"><span data-stu-id="6a7b5-325">System.Collections.Concurrent namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="6a7b5-326">種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-326">Type</span></span>                                                          | <span data-ttu-id="6a7b5-327">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-327">Serialization</span></span> | <span data-ttu-id="6a7b5-328">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-328">Deserialization</span></span> |
|---------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601>   | <span data-ttu-id="6a7b5-329">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-329">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>        | <span data-ttu-id="6a7b5-330">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-330">✔️</span></span>           | ❌              |
| <span data-ttu-id="6a7b5-331"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-331"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span></span> | <span data-ttu-id="6a7b5-332">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-332">✔️</span></span>      | <span data-ttu-id="6a7b5-333">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-333">✔️</span></span>              |
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>      | <span data-ttu-id="6a7b5-334">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-334">✔️</span></span>           | <span data-ttu-id="6a7b5-335">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-335">✔️</span></span>              |
| <span data-ttu-id="6a7b5-336"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-336"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>   | <span data-ttu-id="6a7b5-337">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-337">✔️</span></span>           | <span data-ttu-id="6a7b5-338">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-338">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="6a7b5-339">種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-339">Type</span></span>                                                        | <span data-ttu-id="6a7b5-340">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-340">Serialization</span></span> | <span data-ttu-id="6a7b5-341">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-341">Deserialization</span></span> |
|-------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601> | <span data-ttu-id="6a7b5-342">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-342">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>      | <span data-ttu-id="6a7b5-343">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-343">✔️</span></span>           | ❌              |
| <span data-ttu-id="6a7b5-344">[ConcurrentDictionary\<string, TValue>](xref:System.Collections.Concurrent.ConcurrentDictionary%602) \*\*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-344">[ConcurrentDictionary\<string, TValue>](xref:System.Collections.Concurrent.ConcurrentDictionary%602) \*\*</span></span> |<span data-ttu-id="6a7b5-345">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-345">✔️</span></span>|<span data-ttu-id="6a7b5-346">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-346">✔️</span></span>|
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>    | <span data-ttu-id="6a7b5-347">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-347">✔️</span></span>           | <span data-ttu-id="6a7b5-348">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-348">✔️</span></span>              |
| <span data-ttu-id="6a7b5-349"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-349"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span> | <span data-ttu-id="6a7b5-350">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-350">✔️</span></span>           | <span data-ttu-id="6a7b5-351">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-351">✔️</span></span>              |

::: zone-end

<span data-ttu-id="6a7b5-352">\* 「[Stack\<T> のラウンド トリップをサポートする](system-text-json-converters-how-to.md#support-round-trip-for-stackt)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-352">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="6a7b5-353">\* 「\*サポートされているキーの種類[」を参照してください](#supported-key-types)。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-353">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsobjectmodel-namespace"></a><span data-ttu-id="6a7b5-354">System.Collections.ObjectModel 名前空間</span><span class="sxs-lookup"><span data-stu-id="6a7b5-354">System.Collections.ObjectModel namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="6a7b5-355">種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-355">Type</span></span>                                                           | <span data-ttu-id="6a7b5-356">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-356">Serialization</span></span> | <span data-ttu-id="6a7b5-357">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-357">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="6a7b5-358">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-358">✔️</span></span>            | <span data-ttu-id="6a7b5-359">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-359">✔️</span></span>             |
| <span data-ttu-id="6a7b5-360">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-360">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="6a7b5-361">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-361">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="6a7b5-362">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-362">✔️</span></span>            | <span data-ttu-id="6a7b5-363">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-363">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="6a7b5-364">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-364">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602>   | <span data-ttu-id="6a7b5-365">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-365">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601> | <span data-ttu-id="6a7b5-366">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-366">✔️</span></span>    | ❌             |

<span data-ttu-id="6a7b5-367">\* `string` ではないキーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-367">\* Non-`string` keys are not supported.</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="6a7b5-368">種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-368">Type</span></span>                                                           | <span data-ttu-id="6a7b5-369">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-369">Serialization</span></span> | <span data-ttu-id="6a7b5-370">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-370">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="6a7b5-371">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-371">✔️</span></span>            | <span data-ttu-id="6a7b5-372">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-372">✔️</span></span>             |
| <span data-ttu-id="6a7b5-373">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-373">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="6a7b5-374">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-374">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="6a7b5-375">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-375">✔️</span></span>            | <span data-ttu-id="6a7b5-376">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-376">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="6a7b5-377">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-377">✔️</span></span>            | ❌             |
| <span data-ttu-id="6a7b5-378">[ReadOnlyDictionary\<string, TValue>](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602) \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-378">[ReadOnlyDictionary\<string, TValue>](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602) \*</span></span> |<span data-ttu-id="6a7b5-379">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-379">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601>| <span data-ttu-id="6a7b5-380">✔️</span><span class="sxs-lookup"><span data-stu-id="6a7b5-380">✔️</span></span>     | ❌             |

<span data-ttu-id="6a7b5-381">\* 「[サポートされているキーの種類](#supported-key-types)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-381">\* See [Supported key types](#supported-key-types).</span></span>

::: zone-end

## <a name="custom-collections"></a><span data-ttu-id="6a7b5-382">カスタム コレクション</span><span class="sxs-lookup"><span data-stu-id="6a7b5-382">Custom collections</span></span>

<span data-ttu-id="6a7b5-383">上記のいずれの名前空間にも含まれないコレクション型は、カスタム コレクションと見なされます。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-383">Any collection type that isn't in one of the preceding namespaces is considered a custom collection.</span></span> <span data-ttu-id="6a7b5-384">このような型には、ユーザー定義型と ASP.NET Core で定義されている型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-384">Such types include user-defined types and types defined by ASP.NET Core.</span></span> <span data-ttu-id="6a7b5-385">たとえば、このグループには <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> があります。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-385">For example, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> is in this group.</span></span>

<span data-ttu-id="6a7b5-386">すべてのカスタム コレクション (`IEnumerable` から派生するすべてのもの) は、その要素の型がサポートされている限り、シリアル化でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-386">All custom collections (everything that derives from `IEnumerable`) are supported for serialization, as long as their element types are supported.</span></span>

### <a name="custom-collections-with-deserialization-support"></a><span data-ttu-id="6a7b5-387">逆シリアル化がサポートされているカスタム コレクション</span><span class="sxs-lookup"><span data-stu-id="6a7b5-387">Custom collections with deserialization support</span></span>

<span data-ttu-id="6a7b5-388">次の場合、逆シリアル化にカスタム コレクションがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-388">A custom collection is supported for deserialization if it:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="6a7b5-389">インターフェイスでも抽象でもない場合。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-389">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="6a7b5-390">パラメーターのないコンストラクターがある場合。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-390">Has a parameterless constructor.</span></span>
* <span data-ttu-id="6a7b5-391"><xref:System.Text.Json.JsonSerializer> によってサポートされる要素型が含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-391">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="6a7b5-392">次のインターフェイスまたはクラスを 1 つ以上実装または継承している場合。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-392">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="6a7b5-393"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-393"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="6a7b5-394"><xref:System.Collections.Generic.IDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-394"><xref:System.Collections.Generic.IDictionary%602> \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="6a7b5-395"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-395"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="6a7b5-396"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-396"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="6a7b5-397">インターフェイスでも抽象でもない場合。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-397">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="6a7b5-398">パラメーターのないコンストラクターがある場合。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-398">Has a parameterless constructor.</span></span>
* <span data-ttu-id="6a7b5-399"><xref:System.Text.Json.JsonSerializer> によってサポートされる要素型が含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-399">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="6a7b5-400">次のインターフェイスまたはクラスを 1 つ以上実装または継承している場合。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-400">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="6a7b5-401"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-401"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="6a7b5-402">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \* \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-402">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="6a7b5-403"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-403"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="6a7b5-404"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="6a7b5-404"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

  <span data-ttu-id="6a7b5-405">\* 「[Stack\<T> のラウンド トリップをサポートする](system-text-json-converters-how-to.md#support-round-trip-for-stackt)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-405">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

  <span data-ttu-id="6a7b5-406">\* 「\*サポートされているキーの種類[」を参照してください](#supported-key-types)。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-406">\*\* See [Supported key types](#supported-key-types).</span></span>

### <a name="custom-collections-with-known-issues"></a><span data-ttu-id="6a7b5-407">既知の問題があるカスタム コレクション</span><span class="sxs-lookup"><span data-stu-id="6a7b5-407">Custom collections with known issues</span></span>

<span data-ttu-id="6a7b5-408">次のカスタム コレクションには既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-408">There are known issues with the following custom collections:</span></span>

- <span data-ttu-id="6a7b5-409"><xref:System.Dynamic.ExpandoObject>: [dotnet/runtime#29690](https://github.com/dotnet/runtime/issues/29690) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-409"><xref:System.Dynamic.ExpandoObject>: See [dotnet/runtime#29690](https://github.com/dotnet/runtime/issues/29690).</span></span>
- <span data-ttu-id="6a7b5-410"><xref:System.Dynamic.DynamicObject>: [dotnet/runtime#1808](https://github.com/dotnet/runtime/issues/1808) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-410"><xref:System.Dynamic.DynamicObject>: See [dotnet/runtime#1808](https://github.com/dotnet/runtime/issues/1808).</span></span>
- <span data-ttu-id="6a7b5-411"><xref:System.Data.DataTable>: [dotnet/docs#21366](https://github.com/dotnet/docs/issues/21366) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-411"><xref:System.Data.DataTable>: See [dotnet/docs#21366](https://github.com/dotnet/docs/issues/21366).</span></span>
- <span data-ttu-id="6a7b5-412"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-412"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>
- <span data-ttu-id="6a7b5-413"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-413"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>

<span data-ttu-id="6a7b5-414">既知の問題の詳細については、[System.Text.Json のオープンのイシュー](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-414">For more information about known issues, see the [open issues in System.Text.Json](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json).</span></span>

## <a name="supported-key-types"></a><span data-ttu-id="6a7b5-415">サポートされているキーの種類</span><span class="sxs-lookup"><span data-stu-id="6a7b5-415">Supported key types</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="6a7b5-416">`Dictionary` および `SortedList` 型のキーには、次の型がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-416">Supported types for the keys of `Dictionary` and `SortedList` types include the following:</span></span>

* `Boolean`
* `Byte`
* `DateTime`
* `DateTimeOffset`
* `Decimal`
* `Double`
* `Enum`
* `Guid`
* `Int16`
* `Int32`
* `Int64`
* <span data-ttu-id="6a7b5-417">`Object` (シリアル化と、ランタイム型がこの一覧でサポートされている型のいずれかである場合のみ)。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-417">`Object` (Only on serialization and if the runtime type is one of the supported types in this list.)</span></span>
* `SByte`
* `Single`
* `String`
* `UInt16`
* `UInt32`
* `UInt64`

::: zone-end

::: zone pivot="dotnet-core-3-1"

<span data-ttu-id="6a7b5-418">\*\* .NET Core 3.1 では、`Dictionary` および `SortedList` 型に `string` ではないキーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-418">\*\* Non-`string` keys for `Dictionary` and `SortedList` types are not supported in .NET Core 3.1.</span></span>

::: zone-end

## <a name="see-also"></a><span data-ttu-id="6a7b5-419">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a7b5-419">See also</span></span>

* [<span data-ttu-id="6a7b5-420">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="6a7b5-420">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="6a7b5-421">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="6a7b5-421">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="6a7b5-422">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="6a7b5-422">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="6a7b5-423">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="6a7b5-423">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="6a7b5-424">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="6a7b5-424">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="6a7b5-425">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="6a7b5-425">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="6a7b5-426">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="6a7b5-426">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="6a7b5-427">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="6a7b5-427">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="6a7b5-428">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="6a7b5-428">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="6a7b5-429">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="6a7b5-429">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="6a7b5-430">Newtonsoft.Json から System.Text.Json に移行する方法</span><span class="sxs-lookup"><span data-stu-id="6a7b5-430">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="6a7b5-431">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="6a7b5-431">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="6a7b5-432">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="6a7b5-432">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="6a7b5-433">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="6a7b5-433">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="6a7b5-434">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="6a7b5-434">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="6a7b5-435">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="6a7b5-435">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="6a7b5-436">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="6a7b5-436">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
