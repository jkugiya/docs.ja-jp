---
description: '詳細情報: Sorted コレクション型'
title: Sorted コレクション型
ms.date: 04/30/2020
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
ms.openlocfilehash: b57d767457b5de8d38100db104dde3e7ad2e540a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676132"
---
# <a name="sorted-collection-types"></a><span data-ttu-id="c76db-103">Sorted コレクション型</span><span class="sxs-lookup"><span data-stu-id="c76db-103">Sorted Collection Types</span></span>

<span data-ttu-id="c76db-104"><xref:System.Collections.SortedList?displayProperty=nameWithType> クラス、<xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> ジェネリック クラス、および <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> ジェネリック クラスは、<xref:System.Collections.IDictionary> インターフェイスを実装する点において <xref:System.Collections.Hashtable> クラスと <xref:System.Collections.Generic.Dictionary%602> ジェネリック クラスに似ていますが、キーによる並べ替え順序で自身の要素を維持し、ハッシュ テーブルの O(1) 挿入と取得の特性はありません。</span><span class="sxs-lookup"><span data-stu-id="c76db-104">The <xref:System.Collections.SortedList?displayProperty=nameWithType> class, the <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> generic class, and the <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> generic class are similar to the <xref:System.Collections.Hashtable> class and the <xref:System.Collections.Generic.Dictionary%602> generic class in that they implement the <xref:System.Collections.IDictionary> interface, but they maintain their elements in sort order by key, and they do not have the O(1) insertion and retrieval characteristic of hash tables.</span></span> <span data-ttu-id="c76db-105">これら 3 つのクラスには、次のような共通の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="c76db-105">The three classes have several features in common:</span></span>

- <span data-ttu-id="c76db-106">この 3 つのクラスはすべて、<xref:System.Collections.IDictionary?displayProperty=nameWithType> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="c76db-106">All three classes implement the <xref:System.Collections.IDictionary?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="c76db-107">2 つのジェネリック クラスも <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> ジェネリック インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="c76db-107">The two generic classes also implement the <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> generic interface.</span></span>

- <span data-ttu-id="c76db-108">各要素は、列挙で使用できるようにキーと値のペアになっています。</span><span class="sxs-lookup"><span data-stu-id="c76db-108">Each element is a key/value pair for enumeration purposes.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c76db-109"><xref:System.Collections.SortedList> 非ジェネリック クラスは列挙されると <xref:System.Collections.DictionaryEntry> オブジェクトを返しますが、2 つのジェネリック型のクラスは <xref:System.Collections.Generic.KeyValuePair%602> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="c76db-109">The nongeneric <xref:System.Collections.SortedList> class returns <xref:System.Collections.DictionaryEntry> objects when enumerated, although the two generic types return <xref:System.Collections.Generic.KeyValuePair%602> objects.</span></span>

- <span data-ttu-id="c76db-110">要素の並べ替えは <xref:System.Collections.IComparer?displayProperty=nameWithType> の実装 (非ジェネリック クラス <xref:System.Collections.SortedList> の場合) または <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 実装 (2 つのジェネリック クラスの場合) に基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="c76db-110">Elements are sorted according to a <xref:System.Collections.IComparer?displayProperty=nameWithType> implementation (for nongeneric <xref:System.Collections.SortedList>) or a <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation (for the two generic classes).</span></span>

- <span data-ttu-id="c76db-111">各クラスが提供するプロパティは、キーのみまたは値のみを含むコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="c76db-111">Each class provides properties that return collections containing only the keys or only the values.</span></span>

<span data-ttu-id="c76db-112">次の表に、2 つの並べ替えられたリスト クラスと <xref:System.Collections.Generic.SortedDictionary%602> クラスの違いをいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="c76db-112">The following table lists some of the differences between the two sorted list classes and the <xref:System.Collections.Generic.SortedDictionary%602> class.</span></span>

| <span data-ttu-id="c76db-113"><xref:System.Collections.SortedList>非ジェネリック クラスと <xref:System.Collections.Generic.SortedList%602> ジェネリック クラス</span><span class="sxs-lookup"><span data-stu-id="c76db-113"><xref:System.Collections.SortedList> nongeneric class and <xref:System.Collections.Generic.SortedList%602> generic class</span></span> | <span data-ttu-id="c76db-114"><xref:System.Collections.Generic.SortedDictionary%602> ジェネリック クラス</span><span class="sxs-lookup"><span data-stu-id="c76db-114"><xref:System.Collections.Generic.SortedDictionary%602> generic class</span></span> |
|--|--|
| <span data-ttu-id="c76db-115">キーと値を返すプロパティにはインデックスが付けられるため、インデックスを使用して効率的に取得できます。</span><span class="sxs-lookup"><span data-stu-id="c76db-115">The properties that return keys and values are indexed, allowing efficient indexed retrieval.</span></span> | <span data-ttu-id="c76db-116">インデックスを使用して取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="c76db-116">No indexed retrieval.</span></span> |
| <span data-ttu-id="c76db-117">取得は O(log `n`) です。</span><span class="sxs-lookup"><span data-stu-id="c76db-117">Retrieval is O(log `n`).</span></span> | <span data-ttu-id="c76db-118">取得は O(log `n`) です。</span><span class="sxs-lookup"><span data-stu-id="c76db-118">Retrieval is O(log `n`).</span></span> |
| <span data-ttu-id="c76db-119">挿入と削除は一般に O(`n`) ですが、既に並べ替えられているデータの挿入は O(log `n`) であるため、各要素はリストの最後に追加されます。</span><span class="sxs-lookup"><span data-stu-id="c76db-119">Insertion and removal are generally O(`n`); however, insertion is O(log `n`) for data that are already in sort order, so that each element is added to the end of the list.</span></span> <span data-ttu-id="c76db-120">(これは、サイズの変更が不要であることを前提としています。)</span><span class="sxs-lookup"><span data-stu-id="c76db-120">(This assumes that a resize is not required.)</span></span> | <span data-ttu-id="c76db-121">挿入と削除は O(log `n`) です。</span><span class="sxs-lookup"><span data-stu-id="c76db-121">Insertion and removal are O(log `n`).</span></span> |
| <span data-ttu-id="c76db-122">使用するメモリは <xref:System.Collections.Generic.SortedDictionary%602> より少なくなります。</span><span class="sxs-lookup"><span data-stu-id="c76db-122">Uses less memory than a <xref:System.Collections.Generic.SortedDictionary%602>.</span></span> | <span data-ttu-id="c76db-123"><xref:System.Collections.SortedList> 非ジェネリック クラスと <xref:System.Collections.Generic.SortedList%602> ジェネリック クラスより多くのメモリを使用します。</span><span class="sxs-lookup"><span data-stu-id="c76db-123">Uses more memory than the <xref:System.Collections.SortedList> nongeneric class and the <xref:System.Collections.Generic.SortedList%602> generic class.</span></span> |

<span data-ttu-id="c76db-124">並べ替えられたリストや辞書に複数のスレッドから同時にアクセスできる必要がある場合、<xref:System.Collections.Concurrent.ConcurrentDictionary%602> から派生するクラスに並べ替えロジックを追加できます。</span><span class="sxs-lookup"><span data-stu-id="c76db-124">For sorted lists or dictionaries that must be accessible concurrently from multiple threads, you can add sorting logic to a class that derives from <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span></span> <span data-ttu-id="c76db-125">不変にしたい場合は、<xref:System.Collections.Immutable.ImmutableSortedSet%601> と <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> の対応する不変型に同様の並べ替えセマンティクスがあります。</span><span class="sxs-lookup"><span data-stu-id="c76db-125">When considering immutability, the following corresponding immutable types follow similar sorting semantics: <xref:System.Collections.Immutable.ImmutableSortedSet%601> and <xref:System.Collections.Immutable.ImmutableSortedDictionary%602>.</span></span>

> [!NOTE]
> <span data-ttu-id="c76db-126">独自のキーを含む値 (従業員 ID 番号を含む従業員レコードなど) では、<xref:System.Collections.ObjectModel.KeyedCollection%602> ジェネリック クラスから派生することによってリストの特性と辞書の特性を合わせ持つキー付きのコレクションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c76db-126">For values that contain their own keys (for example, employee records that contain an employee ID number), you can create a keyed collection that has some characteristics of a list and some characteristics of a dictionary by deriving from the <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class.</span></span>

<span data-ttu-id="c76db-127">.NET Framework 4 以降の <xref:System.Collections.Generic.SortedSet%601> クラスのツリーは、挿入、削除、検索後、自らバランスを取り、順序を並べ替えデータを保持します。</span><span class="sxs-lookup"><span data-stu-id="c76db-127">Starting with .NET Framework 4, the <xref:System.Collections.Generic.SortedSet%601> class provides a self-balancing tree that maintains data in sorted order after insertions, deletions, and searches.</span></span> <span data-ttu-id="c76db-128">このクラスと <xref:System.Collections.Generic.HashSet%601> クラスは、<xref:System.Collections.Generic.ISet%601> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="c76db-128">This class and the <xref:System.Collections.Generic.HashSet%601> class implement the <xref:System.Collections.Generic.ISet%601> interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="c76db-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c76db-129">See also</span></span>

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [<span data-ttu-id="c76db-130"> 一般的に使用されるコレクション型</span><span class="sxs-lookup"><span data-stu-id="c76db-130">Commonly Used Collection Types</span></span>](commonly-used-collection-types.md)
