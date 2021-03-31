---
description: '詳細情報: URL からプロトコルとポート番号を抽出する方法'
title: '方法 : URL からプロトコルとポート番号を抽出する'
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
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
ms.openlocfilehash: 5240719f26b092053f1f8efa56cb464f77ce0154
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642787"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="73b83-103">方法 : URL からプロトコルとポート番号を抽出する</span><span class="sxs-lookup"><span data-stu-id="73b83-103">How to: Extract a Protocol and Port Number from a URL</span></span>

<span data-ttu-id="73b83-104">次の例では、URL からプロトコルとポート番号を抽出します。</span><span class="sxs-lookup"><span data-stu-id="73b83-104">The following example extracts a protocol and port number from a URL.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="73b83-105">例</span><span class="sxs-lookup"><span data-stu-id="73b83-105">Example</span></span>  

 <span data-ttu-id="73b83-106">例では <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> メソッドを使用して、後にコロンとポート番号が続くプロトコルを返します。</span><span class="sxs-lookup"><span data-stu-id="73b83-106">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="73b83-107">この正規表現パターン `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="73b83-107">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="73b83-108">Pattern</span><span class="sxs-lookup"><span data-stu-id="73b83-108">Pattern</span></span>|<span data-ttu-id="73b83-109">説明</span><span class="sxs-lookup"><span data-stu-id="73b83-109">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="73b83-110">文字列の先頭から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="73b83-110">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="73b83-111">1 つ以上の単語文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="73b83-111">Match one or more word characters.</span></span> <span data-ttu-id="73b83-112">このグループに `proto` と名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="73b83-112">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="73b83-113">後に 2 つのスラッシュ記号が続くコロンと一致します。</span><span class="sxs-lookup"><span data-stu-id="73b83-113">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="73b83-114">スラッシュ記号以外の任意の文字の 1 回以上の (ただし、可能な限り少ない) 出現と一致します。</span><span class="sxs-lookup"><span data-stu-id="73b83-114">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="73b83-115">後に 1 桁以上の文字が続くコロンの 0 回または 1 回の出現と一致します。</span><span class="sxs-lookup"><span data-stu-id="73b83-115">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="73b83-116">このグループに `port` と名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="73b83-116">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="73b83-117">スラッシュ記号に一致します。</span><span class="sxs-lookup"><span data-stu-id="73b83-117">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="73b83-118"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> メソッドは、正規表現パターンでキャプチャされた 2 つの名前付きグループの値を連結する、`${proto}${port}` 置換シーケンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="73b83-118">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="73b83-119">これは、<xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> プロパティによって返されたコレクション オブジェクトから取得した文字列を明示的に連結するための便利な代替です。</span><span class="sxs-lookup"><span data-stu-id="73b83-119">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="73b83-120">例では、<xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> メソッドを 2 つの置換 `${proto}` と `${port}` とともに使用して、キャプチャされたグループを出力文字列に含めます。</span><span class="sxs-lookup"><span data-stu-id="73b83-120">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="73b83-121">代わりに、次のコードに示されているように、一致の <xref:System.Text.RegularExpressions.GroupCollection> オブジェクトから、キャプチャされたグループを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="73b83-121">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="73b83-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="73b83-122">See also</span></span>

- [<span data-ttu-id="73b83-123">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="73b83-123">.NET Regular Expressions</span></span>](regular-expressions.md)
