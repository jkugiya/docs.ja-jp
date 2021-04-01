---
description: '詳細情報: カルチャを認識しない文字列操作の実行'
title: カルチャを認識しない文字列操作の実行
ms.date: 08/22/2018
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
ms.openlocfilehash: 77365eae18c91b9e803f184258787d81e690ffc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675638"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="4af52-103">カルチャを認識しない文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="4af52-103">Performing culture-insensitive string operations</span></span>

<span data-ttu-id="4af52-104">カルチャを認識する文字列操作を既定で実行するほとんどの .NET メソッドには、<xref:System.Globalization.CultureInfo> パラメーターを渡すことによって使用するカルチャを明示的に指定できるメソッド オーバーロードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4af52-104">Most .NET methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="4af52-105">これらのオーバーロードによって、大文字小文字のマップおよび並べ替え規則のカルチャによる違いを排除し、カルチャを認識しない結果を確保できます。</span><span class="sxs-lookup"><span data-stu-id="4af52-105">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="4af52-106">このセクションの次の記事では、既定ではカルチャを認識する .NET のメソッドを使用し、カルチャを認識しない文字列操作を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4af52-106">This section provides the following articles to demonstrate how to perform culture-insensitive string operations using .NET methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4af52-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4af52-107">In this section</span></span>  

 [<span data-ttu-id="4af52-108">カルチャを認識しない文字列比較の実行</span><span class="sxs-lookup"><span data-stu-id="4af52-108">Performing Culture-Insensitive String Comparisons</span></span>](performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="4af52-109"><xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドと <xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドを使用してカルチャを認識しない文字列比較を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4af52-109">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="4af52-110">カルチャを認識しない大文字と小文字の変更の実行</span><span class="sxs-lookup"><span data-stu-id="4af52-110">Performing Culture-Insensitive Case Changes</span></span>](performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="4af52-111"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>、<xref:System.String.ToLower%2A?displayProperty=nameWithType>、<xref:System.Char.ToUpper%2A?displayProperty=nameWithType>、<xref:System.Char.ToLower%2A?displayProperty=nameWithType> の各メソッドを使用してカルチャを認識しない大文字と小文字の変換を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4af52-111">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="4af52-112">カルチャを認識しないコレクションの操作の実行</span><span class="sxs-lookup"><span data-stu-id="4af52-112">Performing Culture-Insensitive String Operations in Collections</span></span>](performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="4af52-113"><xref:System.Collections.CaseInsensitiveComparer>、<xref:System.Collections.CaseInsensitiveHashCodeProvider> クラス、<xref:System.Collections.SortedList>、<xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>、<xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> を使用して、コレクションでカルチャを認識しない操作を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4af52-113">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="4af52-114">カルチャを認識しない配列の操作の実行</span><span class="sxs-lookup"><span data-stu-id="4af52-114">Performing Culture-Insensitive String Operations in Arrays</span></span>](performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="4af52-115"><xref:System.Array.Sort%2A?displayProperty=nameWithType> メソッドと <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> メソッドを使用してカルチャを認識しない配列の操作を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4af52-115">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4af52-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4af52-116">Related sections</span></span>  

 [<span data-ttu-id="4af52-117">カルチャを認識しない文字列操作</span><span class="sxs-lookup"><span data-stu-id="4af52-117">Culture-Insensitive String Operations</span></span>](culture-insensitive-string-operations.md)  
 <span data-ttu-id="4af52-118">文字列操作を実行する際にカルチャに注意する理由について説明し、カルチャを認識する操作を実行するときとカルチャを認識しない操作を実行するときのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="4af52-118">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="4af52-119">参照</span><span class="sxs-lookup"><span data-stu-id="4af52-119">See also</span></span>

- [<span data-ttu-id="4af52-120">並べ替え重みテーブル (Windows システム上の .NET 用)</span><span class="sxs-lookup"><span data-stu-id="4af52-120">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="4af52-121">デフォルト Unicode 照合基本テーブル (Linux と macOS 上の .NET Core 用)</span><span class="sxs-lookup"><span data-stu-id="4af52-121">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
