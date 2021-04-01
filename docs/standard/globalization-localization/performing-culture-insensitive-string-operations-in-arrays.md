---
description: '詳細情報: カルチャを認識しない配列の操作の実行'
title: カルチャを認識しない配列の操作の実行
ms.date: 03/30/2017
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
ms.openlocfilehash: 35c9ceea3c8de45cc37ff14cf14704268c848a5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675729"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="927eb-103">カルチャを認識しない配列の操作の実行</span><span class="sxs-lookup"><span data-stu-id="927eb-103">Performing Culture-Insensitive String Operations in Arrays</span></span>

<span data-ttu-id="927eb-104"><xref:System.Array.Sort%2A?displayProperty=nameWithType> メソッドと <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> メソッドのオーバーロードは、<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> プロパティを使用して、カルチャを認識する並べ替えを既定で実行します。</span><span class="sxs-lookup"><span data-stu-id="927eb-104">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="927eb-105">これらのメソッドで返されたカルチャを認識した結果は、並べ替え順序の違いに起因し、カルチャによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="927eb-105">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="927eb-106">カルチャを認識した動作を回避するには、`comparer` パラメーターを受け入れる、このメソッドのいずれかのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="927eb-106">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="927eb-107">`comparer` パラメーターによって、配列の要素を比較するときに使用する <xref:System.Collections.IComparer> 実装が指定されます。</span><span class="sxs-lookup"><span data-stu-id="927eb-107">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="927eb-108">このパラメーターには、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> を使用するカスタム invariant comparer クラスを指定してください。</span><span class="sxs-lookup"><span data-stu-id="927eb-108">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="927eb-109">カスタム invariant comparer クラスの例は、「[カルチャを認識しないコレクションの操作の実行](performing-culture-insensitive-string-operations-in-collections.md)」トピックのサブトピック「SortedList クラスの使用」にあります。</span><span class="sxs-lookup"><span data-stu-id="927eb-109">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="927eb-110">**CultureInfo.InvariantCulture** を比較メソッドに渡すと、カルチャを認識しない比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="927eb-110">Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="927eb-111">ただし、これによって、ファイル パス、レジストリ キー、環境変数などで、非言語的な比較が行われることはありません。</span><span class="sxs-lookup"><span data-stu-id="927eb-111">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="927eb-112">また、比較結果に基づいたセキュリティに関する決定もサポートされません。</span><span class="sxs-lookup"><span data-stu-id="927eb-112">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="927eb-113">非言語的な比較や、結果に基づくセキュリティに関する決定については、アプリケーションは <xref:System.StringComparison> 値を受け入れる比較メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="927eb-113">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="927eb-114">アプリケーションは <xref:System.StringComparison.Ordinal> を渡します。</span><span class="sxs-lookup"><span data-stu-id="927eb-114">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>

## <a name="see-also"></a><span data-ttu-id="927eb-115">参照</span><span class="sxs-lookup"><span data-stu-id="927eb-115">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="927eb-116">カルチャを認識しない文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="927eb-116">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)
