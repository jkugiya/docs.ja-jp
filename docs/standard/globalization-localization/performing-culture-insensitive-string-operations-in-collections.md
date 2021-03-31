---
description: '詳細情報: カルチャを認識しないコレクションの操作の実行'
title: カルチャを認識しないコレクションの操作の実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
ms.openlocfilehash: 38628474a20359be84780c2d90ac2470a9a66730
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675703"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="078b4-103">カルチャを認識しないコレクションの操作の実行</span><span class="sxs-lookup"><span data-stu-id="078b4-103">Performing Culture-Insensitive String Operations in Collections</span></span>

<span data-ttu-id="078b4-104">既定ではカルチャを認識する動作を提供するクラスとメンバーは <xref:System.Collections> 名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="078b4-104">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="078b4-105"><xref:System.Collections.CaseInsensitiveComparer> クラスおよび <xref:System.Collections.CaseInsensitiveHashCodeProvider> クラスのパラメーターなしのコンストラクターは、<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> プロパティを使用して新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="078b4-105">The parameterless constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="078b4-106"><xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> メソッドのすべてのオーバーロードは、既定で `Thread.CurrentCulture` プロパティを使用して、<xref:System.Collections.Hashtable> クラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="078b4-106">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="078b4-107"><xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> メソッドのオーバーロードは、`Thread.CurrentCulture` を使用して既定でカルチャを認識した並べ替えを実行します。</span><span class="sxs-lookup"><span data-stu-id="078b4-107">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="078b4-108"><xref:System.Collections.SortedList> での並べ替えと検索は、文字列がキーとして使用されるときに、`Thread.CurrentCulture` によって影響を受けることがあります。</span><span class="sxs-lookup"><span data-stu-id="078b4-108">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="078b4-109">このセクションで説明する推奨使用方法に従うと、`Collections` 名前空間のこれらのクラスとメソッドでカルチャを認識しない結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="078b4-109">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="078b4-110"><xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> を比較メソッドに渡すと、カルチャを認識しない比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="078b4-110">Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="078b4-111">ただし、これによって、ファイル パス、レジストリ キー、環境変数などで、非言語的な比較が行われることはありません。</span><span class="sxs-lookup"><span data-stu-id="078b4-111">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="078b4-112">また、比較結果に基づいたセキュリティに関する決定もサポートされません。</span><span class="sxs-lookup"><span data-stu-id="078b4-112">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="078b4-113">非言語的な比較や、結果に基づくセキュリティに関する決定については、アプリケーションは <xref:System.StringComparison> 値を受け入れる比較メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="078b4-113">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="078b4-114">アプリケーションは <xref:System.StringComparison> を渡します。</span><span class="sxs-lookup"><span data-stu-id="078b4-114">The application should then pass <xref:System.StringComparison>.</span></span>

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="078b4-115">CaseInsensitiveComparer クラスおよび CaseInsensitiveHashCodeProvider クラスの使用</span><span class="sxs-lookup"><span data-stu-id="078b4-115">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>

<span data-ttu-id="078b4-116">`CaseInsensitiveHashCodeProvider` および `CaseInsensitiveComparer` のパラメーターなしのコンストラクターは、`Thread.CurrentCulture` を使用してクラスの新しいインスタンスを初期化し、その結果としてカルチャを認識した動作が行われます。</span><span class="sxs-lookup"><span data-stu-id="078b4-116">The parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="078b4-117">次のコード例は `Hashtable` を示します。これがカルチャを認識するのは、`CaseInsensitiveHashCodeProvider` と `CaseInsensitiveComparer` のパラメーターなしのコンストラクターを使用するためです。</span><span class="sxs-lookup"><span data-stu-id="078b4-117">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

<span data-ttu-id="078b4-118">`CaseInsensitiveComparer` クラスと `CaseInsensitiveHashCodeProvider` クラスを使用してカルチャを認識しない `Hashtable` を作成したい場合は、`culture` パラメーターを受け取るコンストラクターを使用してこれらのクラスの新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="078b4-118">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="078b4-119">`culture` パラメーターに <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> を指定してください。</span><span class="sxs-lookup"><span data-stu-id="078b4-119">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="078b4-120">カルチャを認識しない `Hashtable` を次のコード例で示します。</span><span class="sxs-lookup"><span data-stu-id="078b4-120">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="078b4-121">CollectionsUtil.CreateCaseInsensitiveHashTable メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="078b4-121">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>

<span data-ttu-id="078b4-122">`CollectionsUtil.CreateCaseInsensitiveHashTable` メソッドは、文字列の大文字と小文字を無視する `Hashtable` クラスの新しいインスタンスを手早く作成する便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="078b4-122">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="078b4-123">ただし、`CollectionsUtil.CreateCaseInsensitiveHashTable` メソッドのすべてのオーバーロードは、`Thread.CurrentCulture` プロパティを使用するためカルチャを認識します。</span><span class="sxs-lookup"><span data-stu-id="078b4-123">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="078b4-124">このメソッドを使用して、カルチャを認識しない `Hashtable` を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="078b4-124">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="078b4-125">カルチャを認識しない `Hashtable` を作成するには、`culture`パラメーターを受け取る `Hashtable` コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="078b4-125">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="078b4-126">`culture` パラメーターに `CultureInfo.InvariantCulture` を指定してください。</span><span class="sxs-lookup"><span data-stu-id="078b4-126">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="078b4-127">カルチャを認識しない `Hashtable` を次のコード例で示します。</span><span class="sxs-lookup"><span data-stu-id="078b4-127">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>

## <a name="using-the-sortedlist-class"></a><span data-ttu-id="078b4-128">SortedList クラスの使用</span><span class="sxs-lookup"><span data-stu-id="078b4-128">Using the SortedList Class</span></span>

<span data-ttu-id="078b4-129">`SortedList`は、キーによって並べ替えられ、キーとインデックスを使ってアクセスできる、キーと値のペアのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="078b4-129">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="078b4-130">文字列がキーであるときに `SortedList` を使用すると、並べ替えと検索が `Thread.CurrentCulture` プロパティの影響を受けることがあります。</span><span class="sxs-lookup"><span data-stu-id="078b4-130">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="078b4-131">`SortedList` でカルチャを認識しない動作を実行するには、`comparer` パラメーターを受け取るコンストラクターの 1 つを使用して `SortedList` を作成します。</span><span class="sxs-lookup"><span data-stu-id="078b4-131">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="078b4-132">`comparer` パラメーターは、キーの比較に使用される <xref:System.Collections.IComparer> の実装を指定します。</span><span class="sxs-lookup"><span data-stu-id="078b4-132">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="078b4-133">このパラメーターには、キーを比較するために `CultureInfo.InvariantCulture` を使用するカスタム comparer クラスを指定してください。</span><span class="sxs-lookup"><span data-stu-id="078b4-133">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="078b4-134">次の例は、カルチャを認識しないカスタム comparer クラスです。これは `SortedList`コンストラクターの `comparer` パラメーターとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="078b4-134">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>

```vb
Imports System.Collections
Imports System.Globalization

Friend Class InvariantComparer
    Implements IComparer
    Private m_compareInfo As CompareInfo
    Friend Shared [Default] As New InvariantComparer()

    Friend Sub New()
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo
    End Sub

    Public Function Compare(a As Object, b As Object) As Integer _
            Implements IComparer.Compare
        Dim sa As String = CType(a, String)
        Dim sb As String = CType(b, String)
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then
            Return m_compareInfo.Compare(sa, sb)
        Else
            Return Comparer.Default.Compare(a, b)
        End If
    End Function
End Class
```

```csharp
using System;
using System.Collections;
using System.Globalization;

internal class InvariantComparer : IComparer
{
    private CompareInfo m_compareInfo;
    internal static readonly InvariantComparer Default = new
        InvariantComparer();

    internal InvariantComparer()
    {
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;
    }

    public int Compare(Object a, Object b)
    {
        String sa = a as String;
        String sb = b as String;
        if (sa != null && sb != null)
            return m_compareInfo.Compare(sa, sb);
        else
            return Comparer.Default.Compare(a,b);
    }
}
```

<span data-ttu-id="078b4-135">一般に、`SortedList` を文字列に対して使用する際にカスタム invariant comparer を指定しないと、リストにデータが設定された後で、`Thread.CurrentCulture` に対する変更によってリストが無効になることがあります。</span><span class="sxs-lookup"><span data-stu-id="078b4-135">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>

## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="078b4-136">ArrayList.Sort メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="078b4-136">Using the ArrayList.Sort Method</span></span>

<span data-ttu-id="078b4-137">`ArrayList.Sort` メソッドのオーバーロードは、`Thread.CurrentCulture`プロパティを使用して、カルチャを認識する並べ替えを既定で実行します。</span><span class="sxs-lookup"><span data-stu-id="078b4-137">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="078b4-138">結果は、さまざまな並べ替え順序のためカルチャによって変わることがあります。</span><span class="sxs-lookup"><span data-stu-id="078b4-138">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="078b4-139">カルチャを認識した動作を回避するには、`IComparer`実装を受け入れるこのメソッドのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="078b4-139">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="078b4-140">`comparer` パラメーターには、`CultureInfo.InvariantCulture` を使用するカスタム invariant comparer クラスを指定してください。</span><span class="sxs-lookup"><span data-stu-id="078b4-140">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="078b4-141">カスタム invariant comparer クラスの例は、「[SortedList クラスの使用](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1)」のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="078b4-141">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="078b4-142">参照</span><span class="sxs-lookup"><span data-stu-id="078b4-142">See also</span></span>

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="078b4-143">カルチャを認識しない文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="078b4-143">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
