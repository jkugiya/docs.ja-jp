---
description: '詳細情報: 日付形式の変更に関する正規表現の例'
title: '正規表現の例: 日付形式の変更'
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET regular expressions, examples
- regular expressions [.NET], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
ms.openlocfilehash: 4617188e958042dce9709f8baf32f5b4e2930789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702939"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="f5312-103">正規表現の例: 日付形式の変更</span><span class="sxs-lookup"><span data-stu-id="f5312-103">Regular Expression Example: Changing Date Formats</span></span>

<span data-ttu-id="f5312-104">次のコード例では、<xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> メソッドを使用して、*mm*/*dd*/*yy* 形式の日付を *dd*-*mm*-*yy* 形式の日付に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f5312-104">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="f5312-105">例</span><span class="sxs-lookup"><span data-stu-id="f5312-105">Example</span></span>  

 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="f5312-106">次のコードは、アプリケーションで `MDYToDMY` メソッドを呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f5312-106">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="f5312-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f5312-107">Comments</span></span>  

 <span data-ttu-id="f5312-108">この正規表現パターン `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f5312-108">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="f5312-109">Pattern</span><span class="sxs-lookup"><span data-stu-id="f5312-109">Pattern</span></span>|<span data-ttu-id="f5312-110">説明</span><span class="sxs-lookup"><span data-stu-id="f5312-110">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="f5312-111">ワード境界から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="f5312-111">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="f5312-112">1 桁または 2 桁の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="f5312-112">Match one or two decimal digits.</span></span> <span data-ttu-id="f5312-113">これは、`month` キャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="f5312-113">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="f5312-114">スラッシュ マークと一致します。</span><span class="sxs-lookup"><span data-stu-id="f5312-114">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="f5312-115">1 桁または 2 桁の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="f5312-115">Match one or two decimal digits.</span></span> <span data-ttu-id="f5312-116">これは、`day` キャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="f5312-116">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="f5312-117">スラッシュ マークと一致します。</span><span class="sxs-lookup"><span data-stu-id="f5312-117">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="f5312-118">2 ～ 4 の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="f5312-118">Match from two to four decimal digits.</span></span> <span data-ttu-id="f5312-119">これは、`year` キャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="f5312-119">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="f5312-120">ワード境界で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="f5312-120">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="f5312-121">パターン `${day}-${month}-${year}` は、次の表に示すように置換文字列を定義します。</span><span class="sxs-lookup"><span data-stu-id="f5312-121">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="f5312-122">Pattern</span><span class="sxs-lookup"><span data-stu-id="f5312-122">Pattern</span></span>|<span data-ttu-id="f5312-123">説明</span><span class="sxs-lookup"><span data-stu-id="f5312-123">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="f5312-124">`day` キャプチャ グループによってキャプチャされた文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="f5312-124">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="f5312-125">ハイフンを追加します。</span><span class="sxs-lookup"><span data-stu-id="f5312-125">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="f5312-126">`month` キャプチャ グループによってキャプチャされた文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="f5312-126">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="f5312-127">ハイフンを追加します。</span><span class="sxs-lookup"><span data-stu-id="f5312-127">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="f5312-128">`year` キャプチャ グループによってキャプチャされた文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="f5312-128">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5312-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5312-129">See also</span></span>

- [<span data-ttu-id="f5312-130">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="f5312-130">.NET Regular Expressions</span></span>](regular-expressions.md)
