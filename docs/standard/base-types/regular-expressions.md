---
title: .NET の正規表現
description: 正規表現を使用して、特定の文字パターンの検索、テキストの検証、テキスト部分文字列の処理、抽出した文字列の .NET のコレクションへの追加を行います。
ms.topic: conceptual
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pattern-matching with regular expressions, about pattern-matching
- substrings
- searching with regular expressions, about regular expressions
- pattern-matching with regular expressions
- searching with regular expressions
- parsing text with regular expressions
- regular expressions [.NET], about regular expressions
- regular expressions [.NET]
- .NET regular expressions, about
- characters [.NET], regular expressions
- parsing text with regular expressions, overview
- .NET regular expressions
- strings [.NET], regular expressions
ms.assetid: 521b3f6d-f869-42e1-93e5-158c54a6895d
ms.openlocfilehash: ea6b16909b79236245b35238ad43d778eec3051a
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692774"
---
# <a name="net-regular-expressions"></a><span data-ttu-id="a81a9-103">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="a81a9-103">.NET regular expressions</span></span>

<span data-ttu-id="a81a9-104">正規表現を使用すると、強力、柔軟、そして効率的な方法でテキストを処理できます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-104">Regular expressions provide a powerful, flexible, and efficient method for processing text.</span></span> <span data-ttu-id="a81a9-105">正規表現によるパターン一致の広範な表記法を使用すると、大量のテキストをすばやく解析し、次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-105">The extensive pattern-matching notation of regular expressions enables you to quickly parse large amounts of text to:</span></span>

- <span data-ttu-id="a81a9-106">特定の文字パターンを検索する</span><span class="sxs-lookup"><span data-stu-id="a81a9-106">Find specific character patterns.</span></span>
- <span data-ttu-id="a81a9-107">テキストを検証して、定義済みのパターン (電子メール アドレスなど) と一致することを確実にする</span><span class="sxs-lookup"><span data-stu-id="a81a9-107">Validate text to ensure that it matches a predefined pattern (such as an email address).</span></span>
- <span data-ttu-id="a81a9-108">テキスト部分文字列の抽出、編集、置換、または削除を行う</span><span class="sxs-lookup"><span data-stu-id="a81a9-108">Extract, edit, replace, or delete text substrings.</span></span>
- <span data-ttu-id="a81a9-109">抽出された文字列をコレクションに追加して、レポートを生成する</span><span class="sxs-lookup"><span data-stu-id="a81a9-109">Add extracted strings to a collection in order to generate a report.</span></span>

<span data-ttu-id="a81a9-110">文字列処理や大量のテキストを解析する多くのアプリケーションにとって、正規表現は欠くことのできないツールです。</span><span class="sxs-lookup"><span data-stu-id="a81a9-110">For many applications that deal with strings or that parse large blocks of text, regular expressions are an indispensable tool.</span></span>  
  
## <a name="how-regular-expressions-work"></a><span data-ttu-id="a81a9-111">正規表現のしくみ</span><span class="sxs-lookup"><span data-stu-id="a81a9-111">How regular expressions work</span></span>

 <span data-ttu-id="a81a9-112">正規表現を使ったテキスト処理の最も重要な部分は、.NET の <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> オブジェクトによって表される正規表現エンジンです。</span><span class="sxs-lookup"><span data-stu-id="a81a9-112">The centerpiece of text processing with regular expressions is the regular expression engine, which is represented by the <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> object in .NET.</span></span> <span data-ttu-id="a81a9-113">正規表現を使ったテキスト処理では、正規表現エンジンに対し、最低でも次の 2 つの情報を与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="a81a9-113">At a minimum, processing text using regular expressions requires that the regular expression engine be provided with the following two items of information:</span></span>  
  
- <span data-ttu-id="a81a9-114">テキストを識別する正規表現パターン。</span><span class="sxs-lookup"><span data-stu-id="a81a9-114">The regular expression pattern to identify in the text.</span></span>  
  
     <span data-ttu-id="a81a9-115">.NET では、正規表現のパターンが特殊な構文または言語で定義されます。この構文または言語には、Perl 5 の正規表現と互換性があるほか、右から左への一致処理など、いくつかの機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="a81a9-115">In .NET, regular expression patterns are defined by a special syntax or language, which is compatible with Perl 5 regular expressions and adds some additional features such as right-to-left matching.</span></span> <span data-ttu-id="a81a9-116">詳細については、「[正規表現言語 - クイック リファレンス](regular-expression-language-quick-reference.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a81a9-116">For more information, see [Regular Expression Language - Quick Reference](regular-expression-language-quick-reference.md).</span></span>  
  
- <span data-ttu-id="a81a9-117">正規表現パターンの解析対象となるテキスト。</span><span class="sxs-lookup"><span data-stu-id="a81a9-117">The text to parse for the regular expression pattern.</span></span>  
  
<span data-ttu-id="a81a9-118"><xref:System.Text.RegularExpressions.Regex> クラスのメソッドを使用すると、次のような処理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-118">The methods of the <xref:System.Text.RegularExpressions.Regex> class let you perform the following operations:</span></span>  
  
- <span data-ttu-id="a81a9-119">入力されたテキストに特定の正規表現パターンが出現するかどうかを調べるには、<xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-119">Determine whether the regular expression pattern occurs in the input text by calling the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a81a9-120"><xref:System.Text.RegularExpressions.Regex.IsMatch%2A> メソッドを使用してテキストを検証する例については、「[方法:文字列が有効な電子メール形式であるかどうかを検証する](how-to-verify-that-strings-are-in-valid-email-format.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a81a9-120">For an example that uses the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method for validating text, see [How to: Verify that Strings Are in Valid Email Format](how-to-verify-that-strings-are-in-valid-email-format.md).</span></span>  
  
- <span data-ttu-id="a81a9-121">正規表現パターンと一致したテキストを 1 つまたは全部取得するには、<xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-121">Retrieve one or all occurrences of text that matches the regular expression pattern by calling the <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a81a9-122">前者は、一致したテキストの情報を保持する <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-122">The former method returns a <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> object that provides information about the matching text.</span></span> <span data-ttu-id="a81a9-123">後者は、解析対象のテキストに見つかった各一致につき 1 つの <xref:System.Text.RegularExpressions.MatchCollection> オブジェクトを含む <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-123">The latter returns a <xref:System.Text.RegularExpressions.MatchCollection> object that contains one <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> object for each match found in the parsed text.</span></span>  
  
- <span data-ttu-id="a81a9-124">正規表現パターンと一致したテキストを置換するには、<xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-124">Replace text that matches the regular expression pattern by calling the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a81a9-125"><xref:System.Text.RegularExpressions.Regex.Replace%2A> メソッドを使用して日付形式を変更したり文字列から無効な文字を削除したりする例については、「[方法:文字列から無効な文字を取り除く](how-to-strip-invalid-characters-from-a-string.md)」と「[例:日付形式の変更](regular-expression-example-changing-date-formats.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a81a9-125">For examples that use the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method to change date formats and remove invalid characters from a string, see [How to: Strip Invalid Characters from a String](how-to-strip-invalid-characters-from-a-string.md) and [Example: Changing Date Formats](regular-expression-example-changing-date-formats.md).</span></span>  
  
<span data-ttu-id="a81a9-126">正規表現のオブジェクト モデルの概要については、「[正規表現のオブジェクト モデル](the-regular-expression-object-model.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a81a9-126">For an overview of the regular expression object model, see [The Regular Expression Object Model](the-regular-expression-object-model.md).</span></span>  
  
<span data-ttu-id="a81a9-127">正規表現の言語について詳しくは、「[正規表現言語 - クイック リファレンス](regular-expression-language-quick-reference.md)」を参照するか、次の資料のいずれかをダウンロードして印刷してください。</span><span class="sxs-lookup"><span data-stu-id="a81a9-127">For more information about the regular expression language, see [Regular Expression Language - Quick Reference](regular-expression-language-quick-reference.md) or download and print one of these brochures:</span></span>  
  
- [<span data-ttu-id="a81a9-128">Word (.docx) 形式のクイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="a81a9-128">Quick Reference in Word (.docx) format</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [<span data-ttu-id="a81a9-129">PDF (.pdf) 形式のクイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="a81a9-129">Quick Reference in PDF (.pdf) format</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a><span data-ttu-id="a81a9-130">正規表現の例</span><span class="sxs-lookup"><span data-stu-id="a81a9-130">Regular expression examples</span></span>

<span data-ttu-id="a81a9-131"><xref:System.String> クラスには、文字列内のリテラル文字列を検索する際に使用できる文字列の検索メソッドと置換メソッドが数多く含まれています。</span><span class="sxs-lookup"><span data-stu-id="a81a9-131">The <xref:System.String> class includes a number of string search and replacement methods that you can use when you want to locate literal strings in a larger string.</span></span> <span data-ttu-id="a81a9-132">正規表現は、次の例に示すように、文字列内の部分文字列のいずれかを検索する場合、または文字列内のパターンを識別する場合に最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-132">Regular expressions are most useful either when you want to locate one of several substrings in a larger string, or when you want to identify patterns in a string, as the following examples illustrate.</span></span>

[!INCLUDE [regex](../../../includes/regex.md)]

> [!TIP]
> <span data-ttu-id="a81a9-133"><xref:System.Web.RegularExpressions> 名前空間には、正規表現オブジェクトがたくさん含まれています。このオブジェクトは、HTML、XML、ASP.NET 文書の文字列を解析する事前定義済み正規表現パターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-133">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="a81a9-134">たとえば、<xref:System.Web.RegularExpressions.TagRegex> クラスは文字列の開始タグを識別します。<xref:System.Web.RegularExpressions.CommentRegex> クラスは文字列の ASP.NET コメントを識別します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-134">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>

### <a name="example-1-replace-substrings"></a><span data-ttu-id="a81a9-135">例 1: 部分文字列の置換</span><span class="sxs-lookup"><span data-stu-id="a81a9-135">Example 1: Replace substrings</span></span>  

 <span data-ttu-id="a81a9-136">氏名に敬称 (Mr.、Mrs.、Miss、または Ms.) が付いている場合がある名前が、宛先リストに含まれるとします。</span><span class="sxs-lookup"><span data-stu-id="a81a9-136">Assume that a mailing list contains names that sometimes include a title (Mr., Mrs., Miss, or Ms.) along with a first and last name.</span></span> <span data-ttu-id="a81a9-137">そのリストから封筒のラベルを生成する場合に敬称が含まれないようにするには、次の例に示すように、正規表現を使用して敬称を削除します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-137">If you do not want to include the titles when you generate envelope labels from the list, you can use a regular expression to remove the titles, as the following example illustrates.</span></span>  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 <span data-ttu-id="a81a9-138">正規表現パターン `(Mr\.? |Mrs\.? |Miss |Ms\.? )` は、"Mr "、"Mr. "、"Mrs "、"Mrs. "、"Miss "、"Ms"、または "Ms. " の出現と一致します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-138">The regular expression pattern `(Mr\.? |Mrs\.? |Miss |Ms\.? )` matches any occurrence of "Mr ", "Mr. ", "Mrs ", "Mrs. ", "Miss ", "Ms or "Ms. ".</span></span> <span data-ttu-id="a81a9-139"><xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> メソッドを呼び出すと、一致する文字列が <xref:System.String.Empty?displayProperty=nameWithType> に置き換えられます。つまり、元の文字列から削除されます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-139">The call to the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method replaces the matched string with <xref:System.String.Empty?displayProperty=nameWithType>; in other words, it removes it from the original string.</span></span>  
  
### <a name="example-2-identify-duplicated-words"></a><span data-ttu-id="a81a9-140">例 2:重複する単語の識別</span><span class="sxs-lookup"><span data-stu-id="a81a9-140">Example 2: Identify duplicated words</span></span>  

 <span data-ttu-id="a81a9-141">記述者が単語を誤って重複入力するというエラーがよくあります。</span><span class="sxs-lookup"><span data-stu-id="a81a9-141">Accidentally duplicating words is a common error that writers make.</span></span> <span data-ttu-id="a81a9-142">次の例に示すように、正規表現を使用して重複する単語を識別できます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-142">A regular expression can be used to identify duplicated words, as the following example shows.</span></span>  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 <span data-ttu-id="a81a9-143">正規表現パターン `\b(\w+?)\s\1\b` は、次のように解釈できます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-143">The regular expression pattern `\b(\w+?)\s\1\b` can be interpreted as follows:</span></span>  
  
> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="a81a9-144">パターン</span><span class="sxs-lookup"><span data-stu-id="a81a9-144">Pattern</span></span>|<span data-ttu-id="a81a9-145">解釈</span><span class="sxs-lookup"><span data-stu-id="a81a9-145">Interpretation</span></span>|  
> |-|-|
> |`\b`|<span data-ttu-id="a81a9-146">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-146">Start at a word boundary.</span></span>|  
> |`(\w+?)`|<span data-ttu-id="a81a9-147">1 つ以上 (ただし、できるだけ少ない文字数) の単語文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-147">Match one or more word characters, but as few characters as possible.</span></span> <span data-ttu-id="a81a9-148">同時に、`\1` というグループを形成します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-148">Together, they form a group that can be referred to as `\1`.</span></span>|  
> |`\s`|<span data-ttu-id="a81a9-149">空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-149">Match a white-space character.</span></span>|  
> |`\1`|<span data-ttu-id="a81a9-150">`\1` という名前のグループと等しい部分文字列と一致します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-150">Match the substring that is equal to the group named `\1`.</span></span>|  
> |`\b`|<span data-ttu-id="a81a9-151">ワード境界に一致します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-151">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="a81a9-152"><xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> メソッドは、正規表現オプションを <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> に設定して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-152">The <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> method is called with regular expression options set to <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a81a9-153">したがって、照合操作では大文字と小文字が区別されず、この例では部分文字列 "This this" が重複として識別されます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-153">Therefore, the match operation is case-insensitive, and the example identifies the substring "This this" as a duplication.</span></span>  
  
 <span data-ttu-id="a81a9-154">入力文字列には部分文字列 "this?</span><span class="sxs-lookup"><span data-stu-id="a81a9-154">The input string includes the substring "this?</span></span> <span data-ttu-id="a81a9-155">This" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a81a9-155">This".</span></span> <span data-ttu-id="a81a9-156">ただし、句読点が介在するので、重複として識別されません。</span><span class="sxs-lookup"><span data-stu-id="a81a9-156">However, because of the intervening punctuation mark, it is not identified as a duplication.</span></span>  
  
### <a name="example-3-dynamically-build-a-culture-sensitive-regular-expression"></a><span data-ttu-id="a81a9-157">例 3:カルチャに依存した正規表現の動的な構築</span><span class="sxs-lookup"><span data-stu-id="a81a9-157">Example 3: Dynamically build a culture-sensitive regular expression</span></span>  

 <span data-ttu-id="a81a9-158">ここでは、正規表現による強力なテキスト処理と、.NET の柔軟なグローバリゼーション機能を組み合わせて使用する例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-158">The following example illustrates the power of regular expressions combined with the flexibility offered by .NET's globalization features.</span></span> <span data-ttu-id="a81a9-159">この例では、システムの現在のカルチャで用いられている通貨値の形式を調べるために、<xref:System.Globalization.NumberFormatInfo> オブジェクトが使用されています。</span><span class="sxs-lookup"><span data-stu-id="a81a9-159">It uses the <xref:System.Globalization.NumberFormatInfo> object to determine the format of currency values in the system's current culture.</span></span> <span data-ttu-id="a81a9-160">さらに、その情報を基に、テキストから通貨値を抽出する正規表現を動的に構築します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-160">It then uses that information to dynamically construct a regular expression that extracts currency values from the text.</span></span> <span data-ttu-id="a81a9-161">検出された一致ごとに、数値文字列のみを含んだサブグループを抽出し、<xref:System.Decimal> 値に変換して、通算の合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-161">For each match, it extracts the subgroup that contains the numeric string only, converts it to a <xref:System.Decimal> value, and calculates a running total.</span></span>  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 <span data-ttu-id="a81a9-162">現在 "英語 - 米国" (en-US) カルチャが使用されているコンピューターでは、`\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` という正規表現が動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-162">On a computer whose current culture is English - United States (en-US), the example dynamically builds the regular expression `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`.</span></span> <span data-ttu-id="a81a9-163">この正規表現パターンは、次のように解釈できます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-163">This regular expression pattern can be interpreted as follows:</span></span>  

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="a81a9-164">パターン</span><span class="sxs-lookup"><span data-stu-id="a81a9-164">Pattern</span></span>|<span data-ttu-id="a81a9-165">解釈</span><span class="sxs-lookup"><span data-stu-id="a81a9-165">Interpretation</span></span>|  
> |-|-|  
> |`\$`|<span data-ttu-id="a81a9-166">入力文字列に含まれる単一のドル記号 (`$`) を検索します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-166">Look for a single occurrence of the dollar symbol (`$`) in the input string.</span></span> <span data-ttu-id="a81a9-167">この正規表現パターン文字列に使用されている円記号は、ドル記号を正規表現のアンカーではなく、文字として扱うことを意味します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-167">The regular expression pattern string includes a backslash to indicate that the dollar symbol is to be interpreted literally rather than as a regular expression anchor.</span></span> <span data-ttu-id="a81a9-168">(`$` 記号のみの場合、正規表現エンジンが文字列の最後で一致の開始を試みる必要があることを示します。)現在のカルチャの通貨記号が正規表現記号として解釈されるのを防ぐため、例では、<xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> メソッドを呼び出して文字をエスケープしています。</span><span class="sxs-lookup"><span data-stu-id="a81a9-168">(The `$` symbol alone would indicate that the regular expression engine should try to begin its match at the end of a string.) To ensure that the current culture's currency symbol is not misinterpreted as a regular expression symbol, the example calls the <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> method to escape the character.</span></span>|  
> |`\s*`|<span data-ttu-id="a81a9-169">空白文字の 0 回以上の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-169">Look for zero or more occurrences of a white-space character.</span></span>|  
> |`[-+]?`|<span data-ttu-id="a81a9-170">正の符号または負の符号の 0 回または 1 回の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-170">Look for zero or one occurrence of either a positive sign or a negative sign.</span></span>|  
> |`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|<span data-ttu-id="a81a9-171">外側の丸かっこで囲まれている表現は、キャプチャ グループまたは部分式として定義されます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-171">The outer parentheses around this expression define it as a capturing group or a subexpression.</span></span> <span data-ttu-id="a81a9-172">一致が見つかった場合、その一致した文字列の、この部分に関する情報が、<xref:System.Text.RegularExpressions.Group> プロパティから返された <xref:System.Text.RegularExpressions.GroupCollection> オブジェクトの 2 つ目の <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> オブジェクトから取得できます</span><span class="sxs-lookup"><span data-stu-id="a81a9-172">If a match is found, information about this part of the matching string can be retrieved from the second <xref:System.Text.RegularExpressions.Group> object in the <xref:System.Text.RegularExpressions.GroupCollection> object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a81a9-173">(コレクションの 1 つ目の要素は、一致した文字列全体を表します)。</span><span class="sxs-lookup"><span data-stu-id="a81a9-173">(The first element in the collection represents the entire match.)</span></span>|  
> |`[0-9]{0,3}`|<span data-ttu-id="a81a9-174">10 進数字 (0 ～ 9) の 0 回以上、3 回以下の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-174">Look for zero to three occurrences of the decimal digits 0 through 9.</span></span>|  
> |`(,[0-9]{3})*`|<span data-ttu-id="a81a9-175">桁区切り記号と 3 桁の 10 進数字の 0 回以上の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-175">Look for zero or more occurrences of a group separator followed by three decimal digits.</span></span>|  
> |`\.`|<span data-ttu-id="a81a9-176">単一の小数点を検索します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-176">Look for a single occurrence of the decimal separator.</span></span>|  
> |`[0-9]+`|<span data-ttu-id="a81a9-177">10 進数字の 1 回以上の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-177">Look for one or more decimal digits.</span></span>|  
> |`(\.[0-9]+)?`|<span data-ttu-id="a81a9-178">小数点と 1 桁以上の数字の 0 回または 1 回の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-178">Look for zero or one occurrence of the decimal separator followed by at least one decimal digit.</span></span>|  
  
 <span data-ttu-id="a81a9-179">以上の各サブパターンが入力文字列内に見つかると一致と判断され、その一致に関する情報を含んだ <xref:System.Text.RegularExpressions.Match> オブジェクトが <xref:System.Text.RegularExpressions.MatchCollection> オブジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a81a9-179">If each of these subpatterns is found in the input string, the match succeeds, and a <xref:System.Text.RegularExpressions.Match> object that contains information about the match is added to the <xref:System.Text.RegularExpressions.MatchCollection> object.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="a81a9-180">関連トピック</span><span class="sxs-lookup"><span data-stu-id="a81a9-180">Related topics</span></span>  
  
|<span data-ttu-id="a81a9-181">Title</span><span class="sxs-lookup"><span data-stu-id="a81a9-181">Title</span></span>|<span data-ttu-id="a81a9-182">説明</span><span class="sxs-lookup"><span data-stu-id="a81a9-182">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a81a9-183">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="a81a9-183">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)|<span data-ttu-id="a81a9-184">正規表現を定義するために使う一連の文字、演算子、および構成体について説明します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-184">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>|  
|[<span data-ttu-id="a81a9-185">正規表現のオブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="a81a9-185">The Regular Expression Object Model</span></span>](the-regular-expression-object-model.md)|<span data-ttu-id="a81a9-186">正規表現クラスの使用方法について詳しく説明し、コード例を示します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-186">Provides information and code examples that illustrate how to use the regular expression classes.</span></span>|  
|[<span data-ttu-id="a81a9-187">正規表現の動作の詳細</span><span class="sxs-lookup"><span data-stu-id="a81a9-187">Details of Regular Expression Behavior</span></span>](details-of-regular-expression-behavior.md)|<span data-ttu-id="a81a9-188">.NET の正規表現の機能と動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="a81a9-188">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>|
|[<span data-ttu-id="a81a9-189">Visual Studio での正規表現の使用</span><span class="sxs-lookup"><span data-stu-id="a81a9-189">Use regular expressions in Visual Studio</span></span>](/visualstudio/ide/using-regular-expressions-in-visual-studio)||
  
## <a name="reference"></a><span data-ttu-id="a81a9-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="a81a9-190">Reference</span></span>  

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
- [<span data-ttu-id="a81a9-191">正規表現 - クイック リファレンス (Word 形式でダウンロード)</span><span class="sxs-lookup"><span data-stu-id="a81a9-191">Regular Expressions - Quick Reference (download in Word format)</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [<span data-ttu-id="a81a9-192">正規表現 - クイック リファレンス (PDF 形式でダウンロード)</span><span class="sxs-lookup"><span data-stu-id="a81a9-192">Regular Expressions - Quick Reference (download in PDF format)</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
