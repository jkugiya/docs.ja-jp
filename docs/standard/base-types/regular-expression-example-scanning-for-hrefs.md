---
title: '正規表現の例: HREF のスキャン'
description: .NET での正規表現の例を確認します。 この例では、入力文字列を検索して、すべての href 属性値とその場所を表示します。
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
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
ms.openlocfilehash: 659ba966ab18f2c5db13af3ac687af57dea7b126
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513212"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a><span data-ttu-id="c26d0-104">正規表現の例: HREF のスキャン</span><span class="sxs-lookup"><span data-stu-id="c26d0-104">Regular Expression Example: Scanning for HREFs</span></span>

<span data-ttu-id="c26d0-105">次の例では、入力文字列を検索して、文字列中のすべての href="…" 値とその場所を表示します。</span><span class="sxs-lookup"><span data-stu-id="c26d0-105">The following example searches an input string and displays all the href="…" values and their locations in the string.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="the-regex-object"></a><span data-ttu-id="c26d0-106">Regex オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c26d0-106">The Regex Object</span></span>

 <span data-ttu-id="c26d0-107">`DumpHRefs` メソッドは、ユーザー コードから複数回呼び出される可能性があるため、`static` (Visual Basic の場合は `Shared`) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c26d0-107">Because the `DumpHRefs` method can be called multiple times from user code, it uses the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c26d0-108">これにより、正規表現エンジンが正規表現をキャッシュできるようになり、メソッドを呼び出すたびに新しい <xref:System.Text.RegularExpressions.Regex> オブジェクトをインスタンス化するオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="c26d0-108">This enables the regular expression engine to cache the regular expression and avoids the overhead of instantiating a new <xref:System.Text.RegularExpressions.Regex> object each time the method is called.</span></span> <span data-ttu-id="c26d0-109"><xref:System.Text.RegularExpressions.Match> オブジェクトは、文字列内のすべての一致を反復処理するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c26d0-109">A <xref:System.Text.RegularExpressions.Match> object is then used to iterate through all matches in the string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 <span data-ttu-id="c26d0-110">`DumpHRefs` メソッドを呼び出す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c26d0-110">The following example then illustrates a call to the `DumpHRefs` method.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 <span data-ttu-id="c26d0-111">この正規表現パターン `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c26d0-111">The regular expression pattern `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="c26d0-112">パターン</span><span class="sxs-lookup"><span data-stu-id="c26d0-112">Pattern</span></span>|<span data-ttu-id="c26d0-113">説明</span><span class="sxs-lookup"><span data-stu-id="c26d0-113">Description</span></span>|  
|-------------|-----------------|  
|`href`|<span data-ttu-id="c26d0-114">リテラル文字列 "href" と一致します。</span><span class="sxs-lookup"><span data-stu-id="c26d0-114">Match the literal string "href".</span></span> <span data-ttu-id="c26d0-115">一致では、大文字と小文字を区別しません。</span><span class="sxs-lookup"><span data-stu-id="c26d0-115">The match is case-insensitive.</span></span>|  
|`\s*`|<span data-ttu-id="c26d0-116">0 個以上の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="c26d0-116">Match zero or more white-space characters.</span></span>|  
|`=`|<span data-ttu-id="c26d0-117">等号と一致します。</span><span class="sxs-lookup"><span data-stu-id="c26d0-117">Match the equals sign.</span></span>|  
|`\s*`|<span data-ttu-id="c26d0-118">0 個以上の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="c26d0-118">Match zero or more white-space characters.</span></span>|  
|`(?:\["'\](?<1>\[^"'\]*)["']\|(?<1>\S+))`|<span data-ttu-id="c26d0-119">次のいずれかと一致し、キャプチャ グループに結果を代入しません。</span><span class="sxs-lookup"><span data-stu-id="c26d0-119">Match one of the following without assigning the result to a captured group:</span></span><br /> <ul><li><p><span data-ttu-id="c26d0-120">\- 引用符またはアポストロフィ、引用符またはアポストロフィ以外の任意の文字の 0 回以上の繰り返し、引用符またはアポストロフィの順に続く文字列。</span><span class="sxs-lookup"><span data-stu-id="c26d0-120">A quotation mark or apostrophe, followed by zero or more occurrences of any character other than a quotation mark or apostrophe, followed by a quotation mark or apostrophe.</span></span> <span data-ttu-id="c26d0-121">このパターンには `1` という名前のグループが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c26d0-121">The group named `1` is included in this pattern.</span></span></p></li><li><p><span data-ttu-id="c26d0-122">\- 1 個以上の空白以外の文字。</span><span class="sxs-lookup"><span data-stu-id="c26d0-122">One or more non-white-space characters.</span></span> <span data-ttu-id="c26d0-123">このパターンには `1` という名前のグループが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c26d0-123">The group named `1` is included in this pattern.</span></span></p></li></ul>|  
|`(?<1>[^"']*)`|<span data-ttu-id="c26d0-124">引用符またはアポストロフィ以外の任意の文字の 0 回以上の繰り返しを `1` という名前のキャプチャ グループに代入します。</span><span class="sxs-lookup"><span data-stu-id="c26d0-124">Assign zero or more occurrences of any character other than a quotation mark or apostrophe to the capturing group named `1`.</span></span>|  
|`(?<1>\S+)`|<span data-ttu-id="c26d0-125">1 個以上の空白以外の文字を `1` という名前のキャプチャ グループに代入します。</span><span class="sxs-lookup"><span data-stu-id="c26d0-125">Assign one or more non-white-space characters to the capturing group named `1`.</span></span>|  
  
## <a name="match-result-class"></a><span data-ttu-id="c26d0-126">Match 結果クラス</span><span class="sxs-lookup"><span data-stu-id="c26d0-126">Match Result Class</span></span>  

 <span data-ttu-id="c26d0-127">検索結果は <xref:System.Text.RegularExpressions.Match> クラス内に格納されます。これにより、検索処理によって抽出されたすべての部分文字列にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c26d0-127">The results of a search are stored in the <xref:System.Text.RegularExpressions.Match> class, which provides access to all the substrings extracted by the search.</span></span> <span data-ttu-id="c26d0-128">このクラスは、検索対象となった文字列や、使用された正規表現も記憶しているため、<xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> メソッドを呼び出して、最後の検索が終了した位置から別の検索を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="c26d0-128">It also remembers the string being searched and the regular expression being used, so it can call the <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> method to perform another search starting where the last one ended.</span></span>  
  
## <a name="explicitly-named-captures"></a><span data-ttu-id="c26d0-129">明示的に指定したキャプチャ</span><span class="sxs-lookup"><span data-stu-id="c26d0-129">Explicitly Named Captures</span></span>  

 <span data-ttu-id="c26d0-130">従来の正規表現では、キャプチャするかっこに自動的に連番が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c26d0-130">In traditional regular expressions, capturing parentheses are automatically numbered sequentially.</span></span> <span data-ttu-id="c26d0-131">その結果、2 つの問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="c26d0-131">This leads to two problems.</span></span> <span data-ttu-id="c26d0-132">1 つ目の問題は、かっこのペアの挿入や削除を行って正規表現が修正されると、新しい番号を反映するために、番号付きのキャプチャを参照するコードをすべて書き直す必要があることです。</span><span class="sxs-lookup"><span data-stu-id="c26d0-132">First, if a regular expression is modified by inserting or removing a set of parentheses, all code that refers to the numbered captures must be rewritten to reflect the new numbering.</span></span> <span data-ttu-id="c26d0-133">2 つ目の問題は、ある文字列の検索用に 2 つの代替表現を指定する際、異なるかっこのペアを使用することが多いため、実際にどちらの代替表現から結果が返されたのかを判断するのが難しい場合があることです。</span><span class="sxs-lookup"><span data-stu-id="c26d0-133">Second, because different sets of parentheses often are used to provide two alternative expressions for an acceptable match, it might be difficult to determine which of the two expressions actually returned a result.</span></span>  
  
 <span data-ttu-id="c26d0-134">これらの問題に対処するために、<xref:System.Text.RegularExpressions.Regex> クラスでは指定されたスロットに一致文字列をキャプチャするための構文 `(?<name>…)` をサポートしています (スロットには、文字列または整数の名前を付けることができます。整数の名前を付けた方が、よりすばやく再呼び出しできます)。</span><span class="sxs-lookup"><span data-stu-id="c26d0-134">To address these problems, the <xref:System.Text.RegularExpressions.Regex> class supports the syntax `(?<name>…)` for capturing a match into a specified slot (the slot can be named using a string or an integer; integers can be recalled more quickly).</span></span> <span data-ttu-id="c26d0-135">これにより、同じ文字列に対する代替表現の一致結果をすべて同じ場所に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="c26d0-135">Thus, alternative matches for the same string all can be directed to the same place.</span></span> <span data-ttu-id="c26d0-136">競合が発生する場合は、スロットにキャプチャされた最後の一致文字列が、適切な一致であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="c26d0-136">In case of a conflict, the last match dropped into a slot is the successful match.</span></span> <span data-ttu-id="c26d0-137">(ただし、1 つのスロットで複数の一致文字列の完全なリストを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c26d0-137">(However, a complete list of multiple matches for a single slot is available.</span></span> <span data-ttu-id="c26d0-138">詳細については、<xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> コレクションを参照してください。)</span><span class="sxs-lookup"><span data-stu-id="c26d0-138">See the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> collection for details.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26d0-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="c26d0-139">See also</span></span>

- [<span data-ttu-id="c26d0-140">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="c26d0-140">.NET Regular Expressions</span></span>](regular-expressions.md)
