---
title: .NET で文字列を比較する
description: .NET で文字列を比較する方法について確認します。 Compare、CompareOrdinal、CompareTo、StartsWith、EndsWith、Equals、IndexOf、LastIndexOf の各メソッドについて説明します。
ms.date: 03/30/2017
ms.topic: conceptual
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- value comparisons of strings
- LastIndexOf method
- CompareTo method
- IndexOf method
- Compare method
- strings [.NET], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
ms.openlocfilehash: ca2e89fa8c42807757f4ed004c8f8ddaaeafba3b
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693073"
---
# <a name="compare-strings-in-net"></a><span data-ttu-id="f3a85-104">.NET で文字列を比較する</span><span class="sxs-lookup"><span data-stu-id="f3a85-104">Compare strings in .NET</span></span>

<span data-ttu-id="f3a85-105">.NET は、文字列の値を比較するためのメソッドをいくつか提供します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-105">.NET provides several methods to compare the values of strings.</span></span> <span data-ttu-id="f3a85-106">これらの値の比較メソッドとその説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-106">The following table lists and describes the value-comparison methods.</span></span>

|<span data-ttu-id="f3a85-107">メソッド名</span><span class="sxs-lookup"><span data-stu-id="f3a85-107">Method name</span></span>|<span data-ttu-id="f3a85-108">使用</span><span class="sxs-lookup"><span data-stu-id="f3a85-108">Use</span></span>|
|-----------------|---------|
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|<span data-ttu-id="f3a85-109">2 つの文字列の値を比較します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-109">Compares the values of two strings.</span></span> <span data-ttu-id="f3a85-110">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-110">Returns an integer value.</span></span>|
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|<span data-ttu-id="f3a85-111">ローカル カルチャに関係なく、2 つの文字列を比較します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-111">Compares two strings without regard to local culture.</span></span> <span data-ttu-id="f3a85-112">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-112">Returns an integer value.</span></span>|
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|<span data-ttu-id="f3a85-113">現在の文字列オブジェクトを別の文字列と比較します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-113">Compares the current string object to another string.</span></span> <span data-ttu-id="f3a85-114">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-114">Returns an integer value.</span></span>|
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|<span data-ttu-id="f3a85-115">文字列が、渡された文字列で始まるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-115">Determines whether a string begins with the string passed.</span></span> <span data-ttu-id="f3a85-116">Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-116">Returns a Boolean value.</span></span>|
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|<span data-ttu-id="f3a85-117">文字列が、渡された文字列で終わるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-117">Determines whether a string ends with the string passed.</span></span> <span data-ttu-id="f3a85-118">Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-118">Returns a Boolean value.</span></span>|
|<xref:System.String.Contains%2A?displayProperty=nameWithType>|<span data-ttu-id="f3a85-119">文字または文字列が別の文字列内にあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-119">Determines whether a character or string occurs within another string.</span></span> <span data-ttu-id="f3a85-120">Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-120">Returns a Boolean value.</span></span>|
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|<span data-ttu-id="f3a85-121">2 つの文字列が等しいかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-121">Determines whether two strings are the same.</span></span> <span data-ttu-id="f3a85-122">Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-122">Returns a Boolean value.</span></span>|
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|<span data-ttu-id="f3a85-123">検索対象文字列の先頭から開始して、特定の文字または文字列が見つかったインデックス位置を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-123">Returns the index position of a character or string, starting from the beginning of the string you are examining.</span></span> <span data-ttu-id="f3a85-124">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-124">Returns an integer value.</span></span>|
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|<span data-ttu-id="f3a85-125">検索対象文字列の末尾から開始して、特定の文字または文字列が見つかったインデックス位置を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-125">Returns the index position of a character or string, starting from the end of the string you are examining.</span></span> <span data-ttu-id="f3a85-126">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-126">Returns an integer value.</span></span>|

## <a name="compare-method"></a><span data-ttu-id="f3a85-127">Compare メソッド</span><span class="sxs-lookup"><span data-stu-id="f3a85-127">Compare method</span></span>

<span data-ttu-id="f3a85-128">静的な <xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドは、2 つの文字列を詳細に比較する手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-128">The static <xref:System.String.Compare%2A?displayProperty=nameWithType> method provides a thorough way of comparing two strings.</span></span> <span data-ttu-id="f3a85-129">このメソッドはカルチャに対応しています。</span><span class="sxs-lookup"><span data-stu-id="f3a85-129">This method is culturally aware.</span></span> <span data-ttu-id="f3a85-130">この機能は、2 つの文字列、または 2 つの文字列の部分文字列を比較するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="f3a85-130">You can use this function to compare two strings or substrings of two strings.</span></span> <span data-ttu-id="f3a85-131">また、大文字と小文字の区別やカルチャの違いを考慮または無視するためのオーバーロードも用意されています。</span><span class="sxs-lookup"><span data-stu-id="f3a85-131">Additionally, overloads are provided that regard or disregard case and cultural variance.</span></span> <span data-ttu-id="f3a85-132">このメソッドによって返される可能性のある 3 つの整数値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-132">The following table shows the three integer values that this method might return.</span></span>

|<span data-ttu-id="f3a85-133">戻り値</span><span class="sxs-lookup"><span data-stu-id="f3a85-133">Return value</span></span>|<span data-ttu-id="f3a85-134">条件</span><span class="sxs-lookup"><span data-stu-id="f3a85-134">Condition</span></span>|
|------------------|---------------|
|<span data-ttu-id="f3a85-135">負の整数</span><span class="sxs-lookup"><span data-stu-id="f3a85-135">A negative integer</span></span>|<span data-ttu-id="f3a85-136">最初の文字列は、並べ替え順序が 2 番目の文字列の前に置かれます。</span><span class="sxs-lookup"><span data-stu-id="f3a85-136">The first string precedes the second string in the sort order.</span></span><br /><br /> <span data-ttu-id="f3a85-137">\- または -</span><span class="sxs-lookup"><span data-stu-id="f3a85-137">-or-</span></span><br /><br /> <span data-ttu-id="f3a85-138">最初の文字列は `null`です。</span><span class="sxs-lookup"><span data-stu-id="f3a85-138">The first string is `null`.</span></span>|
|<span data-ttu-id="f3a85-139">0</span><span class="sxs-lookup"><span data-stu-id="f3a85-139">0</span></span>|<span data-ttu-id="f3a85-140">最初の文字列と 2 番目の文字列は等価です。</span><span class="sxs-lookup"><span data-stu-id="f3a85-140">The first string and the second string are equal.</span></span><br /><br /> <span data-ttu-id="f3a85-141">\- または -</span><span class="sxs-lookup"><span data-stu-id="f3a85-141">-or-</span></span><br /><br /> <span data-ttu-id="f3a85-142">両方の文字列が `null`です。</span><span class="sxs-lookup"><span data-stu-id="f3a85-142">Both strings are `null`.</span></span>|
|<span data-ttu-id="f3a85-143">正の整数</span><span class="sxs-lookup"><span data-stu-id="f3a85-143">A positive integer</span></span><br /><br /> <span data-ttu-id="f3a85-144">\- または -</span><span class="sxs-lookup"><span data-stu-id="f3a85-144">-or-</span></span><br /><br /> <span data-ttu-id="f3a85-145">1</span><span class="sxs-lookup"><span data-stu-id="f3a85-145">1</span></span>|<span data-ttu-id="f3a85-146">最初の文字列は、並べ替え順序が 2 番目の文字列の後に続きます。</span><span class="sxs-lookup"><span data-stu-id="f3a85-146">The first string follows the second string in the sort order.</span></span><br /><br /> <span data-ttu-id="f3a85-147">\- または -</span><span class="sxs-lookup"><span data-stu-id="f3a85-147">-or-</span></span><br /><br /> <span data-ttu-id="f3a85-148">第 2 文字列は `null`です。</span><span class="sxs-lookup"><span data-stu-id="f3a85-148">The second string is `null`.</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="f3a85-149"><xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドは、主に文字列の並べ替えに使用するものです。</span><span class="sxs-lookup"><span data-stu-id="f3a85-149">The <xref:System.String.Compare%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="f3a85-150">等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、 <xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f3a85-150">You should not use the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="f3a85-151">2 つの文字列が等価かどうかを判断するには、 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="f3a85-151">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>

 <span data-ttu-id="f3a85-152"><xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドを使用して、2 つの文字列の相対値を確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-152">The following example uses the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to determine the relative values of two strings.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]

 <span data-ttu-id="f3a85-153">この例は、コンソールに `-1` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-153">This example displays `-1` to the console.</span></span>

 <span data-ttu-id="f3a85-154">既定では、上の例はカルチャによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f3a85-154">The preceding example is culture-sensitive by default.</span></span> <span data-ttu-id="f3a85-155">カルチャに依存しない文字列操作を実行するには、 <xref:System.String.Compare%2A?displayProperty=nameWithType> culture *パラメーターを指定することによって使用するカルチャを指定することを可能にする* メソッドのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-155">To perform a culture-insensitive string comparison, use an overload of the <xref:System.String.Compare%2A?displayProperty=nameWithType> method that allows you to specify the culture to use by supplying a *culture* parameter.</span></span> <span data-ttu-id="f3a85-156"><xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドを使用してカルチャに依存しない比較を実行する例については、[カルチャを認識しない文字列の比較](../globalization-localization/performing-culture-insensitive-string-comparisons.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3a85-156">For an example that demonstrates how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to perform a culture-insensitive comparison, see [Culture-insensitive string comparisons](../globalization-localization/performing-culture-insensitive-string-comparisons.md).</span></span>

## <a name="compareordinal-method"></a><span data-ttu-id="f3a85-157">CompareOrdinal メソッド</span><span class="sxs-lookup"><span data-stu-id="f3a85-157">CompareOrdinal method</span></span>

<span data-ttu-id="f3a85-158"><xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> メソッドは、ローカル カルチャを考慮せずに 2 つの文字列オブジェクトを比較します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-158">The <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method compares two string objects without considering the local culture.</span></span> <span data-ttu-id="f3a85-159">このメソッドの戻り値は、上の表で示した `Compare` メソッドによって返される値と同じです。</span><span class="sxs-lookup"><span data-stu-id="f3a85-159">The return values of this method are identical to the values returned by the `Compare` method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f3a85-160"><xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> メソッドは、主に文字列の並べ替えに使用するものです。</span><span class="sxs-lookup"><span data-stu-id="f3a85-160">The <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="f3a85-161">等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> メソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f3a85-161">You should not use the <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="f3a85-162">2 つの文字列が等価かどうかを判断するには、 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="f3a85-162">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>

 <span data-ttu-id="f3a85-163">`CompareOrdinal` メソッドを使用して、2 つの文字列の値を比較する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-163">The following example uses the `CompareOrdinal` method to compare the values of two strings.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]

 <span data-ttu-id="f3a85-164">この例は、コンソールに `-32` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-164">This example displays `-32` to the console.</span></span>

## <a name="compareto-method"></a><span data-ttu-id="f3a85-165">CompareTo メソッド</span><span class="sxs-lookup"><span data-stu-id="f3a85-165">CompareTo method</span></span>

<span data-ttu-id="f3a85-166"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドは、現在の文字列オブジェクトがカプセル化している文字列を別の文字列またはオブジェクトと比較します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-166">The <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method compares the string that the current string object encapsulates to another string or object.</span></span> <span data-ttu-id="f3a85-167">このメソッドの戻り値は、上の表で示した <xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドによって返される値と同じです。</span><span class="sxs-lookup"><span data-stu-id="f3a85-167">The return values of this method are identical to the values returned by the <xref:System.String.Compare%2A?displayProperty=nameWithType> method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f3a85-168"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドは、主に文字列の並べ替えに使用するものです。</span><span class="sxs-lookup"><span data-stu-id="f3a85-168">The <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="f3a85-169">等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f3a85-169">You should not use the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="f3a85-170">2 つの文字列が等価かどうかを判断するには、 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="f3a85-170">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>

 <span data-ttu-id="f3a85-171"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドを使用して、 `string1` オブジェクトを `string2` オブジェクトと比較する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-171">The following example uses the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method to compare the `string1` object to the `string2` object.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]

 <span data-ttu-id="f3a85-172">この例は、コンソールに `-1` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-172">This example displays `-1` to the console.</span></span>

 <span data-ttu-id="f3a85-173"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドのすべてのオーバーロードは、既定で、カルチャに依存して大文字小文字を区別する比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-173">All overloads of the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method perform culture-sensitive and case-sensitive comparisons by default.</span></span> <span data-ttu-id="f3a85-174">このメソッドのオーバーロードで、カルチャに依存しない比較を実行できるものはありません。</span><span class="sxs-lookup"><span data-stu-id="f3a85-174">No overloads of this method are provided that allow you to perform a culture-insensitive comparison.</span></span> <span data-ttu-id="f3a85-175">コードを理解しやすくするために、 `String.Compare` メソッドを使用することをお勧めします。その際、カルチャに依存する操作には <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> を指定し、カルチャに依存しない操作には <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-175">For code clarity, we recommend that you use the `String.Compare` method instead, specifying <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> for culture-sensitive operations or <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> for culture-insensitive operations.</span></span> <span data-ttu-id="f3a85-176">`String.Compare` メソッドを使用してカルチャに依存する比較とカルチャに依存しない比較の両方を実行する例については、「 [カルチャを認識しない文字列比較の実行](../globalization-localization/performing-culture-insensitive-string-comparisons.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3a85-176">For examples that demonstrate how to use the `String.Compare` method to perform both culture-sensitive and culture-insensitive comparisons, see [Performing Culture-Insensitive String Comparisons](../globalization-localization/performing-culture-insensitive-string-comparisons.md).</span></span>

## <a name="equals-method"></a><span data-ttu-id="f3a85-177">Equals メソッド</span><span class="sxs-lookup"><span data-stu-id="f3a85-177">Equals method</span></span>

<span data-ttu-id="f3a85-178"><xref:System.String.Equals%2A?displayProperty=nameWithType> メソッドを使用すると、2 つの文字列が等しいかどうかを簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="f3a85-178">The <xref:System.String.Equals%2A?displayProperty=nameWithType> method can easily determine if two strings are the same.</span></span> <span data-ttu-id="f3a85-179">このメソッドは大文字と小文字を区別し、`true` または `false` の Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-179">This case-sensitive method returns a `true` or `false` Boolean value.</span></span> <span data-ttu-id="f3a85-180">このメソッドは、次の例に示すように、既存のクラスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f3a85-180">It can be used from an existing class, as illustrated in the next example.</span></span> <span data-ttu-id="f3a85-181">`Equals` メソッドを使用して、文字列オブジェクトに "Hello World" という語句が含まれているかどうかを確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-181">The following example uses the `Equals` method to determine whether a string object contains the phrase "Hello World".</span></span>

 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]

 <span data-ttu-id="f3a85-182">この例は、コンソールに `True` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-182">This example displays `True` to the console.</span></span>

 <span data-ttu-id="f3a85-183">このメソッドは、静的メソッドとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="f3a85-183">This method can also be used as a static method.</span></span> <span data-ttu-id="f3a85-184">静的メソッドを使用して、2 つの文字列オブジェクトを比較する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-184">The following example compares two string objects using a static method.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]

 <span data-ttu-id="f3a85-185">この例は、コンソールに `True` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-185">This example displays `True` to the console.</span></span>

## <a name="startswith-and-endswith-methods"></a><span data-ttu-id="f3a85-186">StartsWith メソッドと EndsWith メソッド</span><span class="sxs-lookup"><span data-stu-id="f3a85-186">StartsWith and EndsWith methods</span></span>

<span data-ttu-id="f3a85-187"><xref:System.String.StartsWith%2A?displayProperty=nameWithType> メソッドを使用すると、文字列オブジェクトが、別の文字列を構成している文字と同じ文字で始まっているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f3a85-187">You can use the <xref:System.String.StartsWith%2A?displayProperty=nameWithType> method to determine whether a string object begins with the same characters that encompass another string.</span></span> <span data-ttu-id="f3a85-188">このメソッドは大文字と小文字を区別し、現在の文字列オブジェクトが、渡された文字列で始まる場合は `true`、それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-188">This case-sensitive method returns `true` if the current string object begins with the passed string and `false` if it does not.</span></span> <span data-ttu-id="f3a85-189">このメソッドを使用して、文字列オブジェクトが "Hello" で始まるかどうかを確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-189">The following example uses this method to determine if a string object begins with "Hello".</span></span>

 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]

 <span data-ttu-id="f3a85-190">この例は、コンソールに `True` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-190">This example displays `True` to the console.</span></span>

 <span data-ttu-id="f3a85-191"><xref:System.String.EndsWith%2A?displayProperty=nameWithType> メソッドは、渡された文字列を現在の文字列オブジェクトの末尾にある文字列と比較します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-191">The <xref:System.String.EndsWith%2A?displayProperty=nameWithType> method compares a passed string to the characters that exist at the end of the current string object.</span></span> <span data-ttu-id="f3a85-192">このメソッドも Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-192">It also returns a Boolean value.</span></span> <span data-ttu-id="f3a85-193">`EndsWith` メソッドを使用して、文字列の末尾を確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-193">The following example checks the end of a string using the `EndsWith` method.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]

 <span data-ttu-id="f3a85-194">この例は、コンソールに `False` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-194">This example displays `False` to the console.</span></span>

## <a name="indexof-and-lastindexof-methods"></a><span data-ttu-id="f3a85-195">IndexOf メソッドと LastIndexOf メソッド</span><span class="sxs-lookup"><span data-stu-id="f3a85-195">IndexOf and LastIndexOf methods</span></span>

<span data-ttu-id="f3a85-196"><xref:System.String.IndexOf%2A?displayProperty=nameWithType> メソッドを使用すると、特定の文字が文字列内で最初に出現する位置を確認できます。</span><span class="sxs-lookup"><span data-stu-id="f3a85-196">You can use the <xref:System.String.IndexOf%2A?displayProperty=nameWithType> method to determine the position of the first occurrence of a particular character within a string.</span></span> <span data-ttu-id="f3a85-197">このメソッドは大文字と小文字を区別し、文字列の先頭からカウントを開始し、0 から始まるインデックスを使用して、渡された文字が出現する位置を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-197">This case-sensitive method starts counting from the beginning of a string and returns the position of a passed character using a zero-based index.</span></span> <span data-ttu-id="f3a85-198">指定した文字が見つからない場合は、値 –1 を返します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-198">If the character cannot be found, a value of –1 is returned.</span></span>

<span data-ttu-id="f3a85-199">`IndexOf` メソッドを使用して、'`l`' という文字が文字列内で最初に出現する位置を検索する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-199">The following example uses the `IndexOf` method to search for the first occurrence of the '`l`' character in a string.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]

 <span data-ttu-id="f3a85-200">この例は、コンソールに `2` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-200">This example displays `2` to the console.</span></span>

 <span data-ttu-id="f3a85-201"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> メソッドは `String.IndexOf` メソッドに似ていますが、指定した文字列が文字列内で最後に出現する位置を返すという点が異なります。</span><span class="sxs-lookup"><span data-stu-id="f3a85-201">The <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> method is similar to the `String.IndexOf` method except that it returns the position of the last occurrence of a particular character within a string.</span></span> <span data-ttu-id="f3a85-202">このメソッドは大文字と小文字を区別し、0 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-202">It is case-sensitive and uses a zero-based index.</span></span>

 <span data-ttu-id="f3a85-203">`LastIndexOf` メソッドを使用して、'`l`' という文字が文字列内で最後に出現する位置を検索する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-203">The following example uses the `LastIndexOf` method to search for the last occurrence of the '`l`' character in a string.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]

 <span data-ttu-id="f3a85-204">この例は、コンソールに `9` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f3a85-204">This example displays `9` to the console.</span></span>

 <span data-ttu-id="f3a85-205">いずれのメソッドも、 <xref:System.String.Remove%2A?displayProperty=nameWithType> メソッドと組み合わせて使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="f3a85-205">Both methods are useful when used in conjunction with the <xref:System.String.Remove%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f3a85-206">`IndexOf` メソッドまたは `LastIndexOf` メソッドのいずれかを使用して文字の位置を取得し、その位置を `Remove` メソッドに渡すことによって、その文字またはその文字で始まる単語を削除できます。</span><span class="sxs-lookup"><span data-stu-id="f3a85-206">You can use either the `IndexOf` or `LastIndexOf` methods to retrieve the position of a character, and then supply that position to the `Remove` method in order to remove a character or a word that begins with that character.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3a85-207">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3a85-207">See also</span></span>

- [<span data-ttu-id="f3a85-208">.NET の文字列を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="f3a85-208">Best Practices for Using Strings in .NET</span></span>](best-practices-strings.md)
- [<span data-ttu-id="f3a85-209">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="f3a85-209">Basic String Operations</span></span>](basic-string-operations.md)
- [<span data-ttu-id="f3a85-210">カルチャを認識しない文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="f3a85-210">Performing Culture-Insensitive String Operations</span></span>](../globalization-localization/performing-culture-insensitive-string-operations.md)
- <span data-ttu-id="f3a85-211">[重みのテーブルの並べ替え](https://www.microsoft.com/download/details.aspx?id=10921) - Windows 上の .NET Framework と .NET Core 1.0 - 3.1 によって使用されます</span><span class="sxs-lookup"><span data-stu-id="f3a85-211">[Sorting Weight Tables](https://www.microsoft.com/download/details.aspx?id=10921) - used by .NET Framework and .NET Core 1.0-3.1 on Windows</span></span>
- <span data-ttu-id="f3a85-212">[デフォルト Unicode 照合基本テーブル](https://www.unicode.org/Public/UCA/latest/allkeys.txt) - すべてのプラットフォーム上の .NET 5 および Linux と macOS 上の .NET Core によって使用されます</span><span class="sxs-lookup"><span data-stu-id="f3a85-212">[Default Unicode Collation Element Table](https://www.unicode.org/Public/UCA/latest/allkeys.txt) - used by .NET 5 on all platforms, and by .NET Core on Linux and macOS</span></span>
