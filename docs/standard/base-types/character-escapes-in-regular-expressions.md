---
title: .NET 正規表現での文字のエスケープ
description: .NET 正規表現での特殊文字とエスケープ文字について説明します。
ms.date: 03/30/2017
ms.topic: conceptual
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unescaped characters
- replacement patterns
- characters, escapes
- regular expressions, character escapes
- escape characters
- .NET regular expressions, character escapes
- constructs, character escapes
ms.assetid: f49cc9cc-db7d-4058-8b8a-422bc08b29b0
ms.openlocfilehash: 44c297b7cc897ee08d3434dfcb18df0024b44e6f
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693099"
---
# <a name="character-escapes-in-regular-expressions"></a><span data-ttu-id="8160f-103">正規表現での文字のエスケープ</span><span class="sxs-lookup"><span data-stu-id="8160f-103">Character Escapes in Regular Expressions</span></span>

<span data-ttu-id="8160f-104">正規表現の円記号 (\\) は、次のいずれかを示します。</span><span class="sxs-lookup"><span data-stu-id="8160f-104">The backslash (\\) in a regular expression indicates one of the following:</span></span>  
  
- <span data-ttu-id="8160f-105">後に続く文字が、次のセクションの表に示す特殊文字であること。</span><span class="sxs-lookup"><span data-stu-id="8160f-105">The character that follows it is a special character, as shown in the table in the following section.</span></span> <span data-ttu-id="8160f-106">たとえば、`\b` は、正規表現の一致がワード境界から開始する必要があることを示すアンカーであり、`\t` はタブを表します。`\x020` は空白を表します。</span><span class="sxs-lookup"><span data-stu-id="8160f-106">For example, `\b` is an anchor that indicates that a regular expression match should begin on a word boundary, `\t` represents a tab, and `\x020` represents a space.</span></span>  
  
- <span data-ttu-id="8160f-107">エスケープされていない言語構成要素として解釈される文字は、文字どおりに解釈する必要があること。</span><span class="sxs-lookup"><span data-stu-id="8160f-107">A character that otherwise would be interpreted as an unescaped language construct should be interpreted literally.</span></span> <span data-ttu-id="8160f-108">たとえば、中かっこ (`{`) は量指定子の定義を開始しますが、円記号とそれに続く中かっこ (`\{`) は、正規表現エンジンで中かっこに一致させる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="8160f-108">For example, a brace (`{`) begins the definition of a quantifier, but a backslash followed by a brace (`\{`) indicates that the regular expression engine should match the brace.</span></span> <span data-ttu-id="8160f-109">同様に、1 つの円記号はエスケープされた言語構成要素の開始を示しますが、2 つの円記号 (`\\`) は、正規表現エンジンで円記号に一致させる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="8160f-109">Similarly, a single backslash marks the beginning of an escaped language construct, but two backslashes (`\\`) indicate that the regular expression engine should match the backslash.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8160f-110">文字エスケープは、正規表現では認識されますが、置換パターンでは認識されません。</span><span class="sxs-lookup"><span data-stu-id="8160f-110">Character escapes are recognized in regular expression patterns but not in replacement patterns.</span></span>  
  
## <a name="character-escapes-in-net"></a><span data-ttu-id="8160f-111">.NET での文字のエスケープ</span><span class="sxs-lookup"><span data-stu-id="8160f-111">Character Escapes in .NET</span></span>  

 <span data-ttu-id="8160f-112">次の表は、.NET の正規表現でサポートされている文字エスケープの一覧です。</span><span class="sxs-lookup"><span data-stu-id="8160f-112">The following table lists the character escapes supported by regular expressions in .NET.</span></span>  
  
|<span data-ttu-id="8160f-113">文字または文字シーケンス</span><span class="sxs-lookup"><span data-stu-id="8160f-113">Character or sequence</span></span>|<span data-ttu-id="8160f-114">説明</span><span class="sxs-lookup"><span data-stu-id="8160f-114">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="8160f-115">次の文字を除くすべての文字:</span><span class="sxs-lookup"><span data-stu-id="8160f-115">All characters except for the following:</span></span><br /><br /> <span data-ttu-id="8160f-116">.</span><span class="sxs-lookup"><span data-stu-id="8160f-116">.</span></span> <span data-ttu-id="8160f-117">$ ^ { [ ( &#124; ) \* + ?</span><span class="sxs-lookup"><span data-stu-id="8160f-117">$ ^ { [ ( &#124; ) \* + ?</span></span> \ |<span data-ttu-id="8160f-118">。**文字またはシーケンス** の列にリストされているもの以外の文字は、正規表現で特別な意味を持ちません。それらは、その文字自体と一致します。</span><span class="sxs-lookup"><span data-stu-id="8160f-118">Characters other than those listed in the **Character or sequence** column have no special meaning in regular expressions; they match themselves.</span></span><br /><br /> <span data-ttu-id="8160f-119">**文字またはシーケンス** の列に含まれる文字は、特殊な正規表現言語要素です。</span><span class="sxs-lookup"><span data-stu-id="8160f-119">The characters included in the **Character or sequence** column are special regular expression language elements.</span></span> <span data-ttu-id="8160f-120">正規表現でそれらの文字と一致するためには、エスケープするか、[正の文字グループ](character-classes-in-regular-expressions.md)に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="8160f-120">To match them in a regular expression, they must be escaped or included in a [positive character group](character-classes-in-regular-expressions.md).</span></span> <span data-ttu-id="8160f-121">たとえば、正規表現の `\$\d+` または `[$]\d+`は「$1200」と一致します。</span><span class="sxs-lookup"><span data-stu-id="8160f-121">For example, the regular expression `\$\d+` or `[$]\d+` matches "$1200".</span></span>|  
|`\a`|<span data-ttu-id="8160f-122">ビープ音 (アラーム) 文字の `\u0007`。</span><span class="sxs-lookup"><span data-stu-id="8160f-122">Matches a bell (alarm) character, `\u0007`.</span></span>|  
|`\b`|<span data-ttu-id="8160f-123">`[`*character_group*`]` 文字クラスでバックスペースの `\u0008` と一致します</span><span class="sxs-lookup"><span data-stu-id="8160f-123">In a `[`*character_group*`]` character class, matches a backspace, `\u0008`.</span></span>  <span data-ttu-id="8160f-124">(「[文字クラス](character-classes-in-regular-expressions.md)」を参照してください)。文字クラスの外部では、`\b` はワード境界と一致するアンカーです</span><span class="sxs-lookup"><span data-stu-id="8160f-124">(See [Character Classes](character-classes-in-regular-expressions.md).) Outside a character class, `\b` is an anchor that matches a word boundary.</span></span> <span data-ttu-id="8160f-125">(「[アンカー](anchors-in-regular-expressions.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8160f-125">(See [Anchors](anchors-in-regular-expressions.md).)</span></span>|  
|`\t`|<span data-ttu-id="8160f-126">タブの `\u0009`。</span><span class="sxs-lookup"><span data-stu-id="8160f-126">Matches a tab, `\u0009`.</span></span>|  
|`\r`|<span data-ttu-id="8160f-127">キャリッジ リターンの `\u000D`。</span><span class="sxs-lookup"><span data-stu-id="8160f-127">Matches a carriage return, `\u000D`.</span></span> <span data-ttu-id="8160f-128">`\r` の機能は `\n` という改行文字と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="8160f-128">Note that `\r` is not equivalent to the newline character, `\n`.</span></span>|  
|`\v`|<span data-ttu-id="8160f-129">垂直タブの `\u000B`。</span><span class="sxs-lookup"><span data-stu-id="8160f-129">Matches a vertical tab, `\u000B`.</span></span>|  
|`\f`|<span data-ttu-id="8160f-130">フォーム フィードの `\u000C`。</span><span class="sxs-lookup"><span data-stu-id="8160f-130">Matches a form feed, `\u000C`.</span></span>|  
|`\n`|<span data-ttu-id="8160f-131">改行文字の `\u000A`。</span><span class="sxs-lookup"><span data-stu-id="8160f-131">Matches a new line, `\u000A`.</span></span>|  
|`\e`|<span data-ttu-id="8160f-132">エスケープ文字の `\u001B`。</span><span class="sxs-lookup"><span data-stu-id="8160f-132">Matches an escape, `\u001B`.</span></span>|  
|<span data-ttu-id="8160f-133">`\` *nnn*</span><span class="sxs-lookup"><span data-stu-id="8160f-133">`\` *nnn*</span></span>|<span data-ttu-id="8160f-134">ASCII 文字と一致します。*nnn* は、8 進文字コードを表す 2 桁または 3 桁で構成されます。</span><span class="sxs-lookup"><span data-stu-id="8160f-134">Matches an ASCII character, where *nnn* consists of two or three digits that represent the octal character code.</span></span> <span data-ttu-id="8160f-135">たとえば、`\040` は、空白文字を表します。</span><span class="sxs-lookup"><span data-stu-id="8160f-135">For example, `\040` represents a space character.</span></span> <span data-ttu-id="8160f-136">この構成体は、1 桁のみの場合 (`\2` など)、またはキャプチャ グループの番号に対応する場合には前方参照として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="8160f-136">This construct is interpreted as a backreference if it has only one digit (for example, `\2`) or if it corresponds to the number of a capturing group.</span></span> <span data-ttu-id="8160f-137">(「[前方参照構成体](backreference-constructs-in-regular-expressions.md)」を参照してください。)</span><span class="sxs-lookup"><span data-stu-id="8160f-137">(See [Backreference Constructs](backreference-constructs-in-regular-expressions.md).)</span></span>|  
|<span data-ttu-id="8160f-138">`\x` *nn*</span><span class="sxs-lookup"><span data-stu-id="8160f-138">`\x` *nn*</span></span>|<span data-ttu-id="8160f-139">ASCII 文字と一致します。*nn* は 2 桁の 16 進文字コードです。</span><span class="sxs-lookup"><span data-stu-id="8160f-139">Matches an ASCII character, where *nn* is a two-digit hexadecimal character code.</span></span>|  
|<span data-ttu-id="8160f-140">`\c` *X*</span><span class="sxs-lookup"><span data-stu-id="8160f-140">`\c` *X*</span></span>|<span data-ttu-id="8160f-141">ASCII の制御文字と一致します。X は制御文字です。</span><span class="sxs-lookup"><span data-stu-id="8160f-141">Matches an ASCII control character, where X is the letter of the control character.</span></span> <span data-ttu-id="8160f-142">たとえば、`\cC` は CTRL-C です。</span><span class="sxs-lookup"><span data-stu-id="8160f-142">For example, `\cC` is CTRL-C.</span></span>|  
|<span data-ttu-id="8160f-143">`\u` *nnnn*</span><span class="sxs-lookup"><span data-stu-id="8160f-143">`\u` *nnnn*</span></span>|<span data-ttu-id="8160f-144">値が *nnnn* の 16 進数である UTF-16 コード単位と一致します。</span><span class="sxs-lookup"><span data-stu-id="8160f-144">Matches a UTF-16 code unit whose value is *nnnn* hexadecimal.</span></span> <span data-ttu-id="8160f-145">**注:** .NET では、Unicode を指定するために使用する Perl5 の文字エスケープはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8160f-145">**Note:**  The Perl 5 character escape that is used to specify Unicode is not supported by .NET.</span></span> <span data-ttu-id="8160f-146">Perl 5 の文字エスケープは `\x{` *####* `…}` の形式です。ここで、 *####* `…` は一連の 16 進数です。</span><span class="sxs-lookup"><span data-stu-id="8160f-146">The Perl 5 character escape has the form `\x{`*####*`…}`, where *####*`…` is a series of hexadecimal digits.</span></span> <span data-ttu-id="8160f-147">代わりに、`\u`*nnnn* を使用します。</span><span class="sxs-lookup"><span data-stu-id="8160f-147">Instead, use `\u`*nnnn*.</span></span>|  
|`\`|<span data-ttu-id="8160f-148">エスケープ文字として認識されない文字が後ろに付いている場合は、その文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="8160f-148">When followed by a character that is not recognized as an escaped character, matches that character.</span></span> <span data-ttu-id="8160f-149">たとえば、`\*` はアスタリスク (\*) と一致し、`\x2A` と同じです。</span><span class="sxs-lookup"><span data-stu-id="8160f-149">For example, `\*` matches an asterisk (\*) and is the same as `\x2A`.</span></span>|  
  
## <a name="an-example"></a><span data-ttu-id="8160f-150">例</span><span class="sxs-lookup"><span data-stu-id="8160f-150">An Example</span></span>  

 <span data-ttu-id="8160f-151">正規表現の文字エスケープの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8160f-151">The following example illustrates the use of character escapes in a regular expression.</span></span> <span data-ttu-id="8160f-152">2009 年の世界最大規模の都市の名前と人口を含む文字列を解析します。</span><span class="sxs-lookup"><span data-stu-id="8160f-152">It parses a string that contains the names of the world's largest cities and their populations in 2009.</span></span> <span data-ttu-id="8160f-153">各都市名は、タブ (`\t`) または縦棒 (&#124; または `\u007c`) で区切られます。</span><span class="sxs-lookup"><span data-stu-id="8160f-153">Each city name is separated from its population by a tab (`\t`) or a vertical bar (&#124; or `\u007c`).</span></span> <span data-ttu-id="8160f-154">個々の都市とその人口は、復帰とライン フィードで互いに区切られています。</span><span class="sxs-lookup"><span data-stu-id="8160f-154">Individual cities and their populations are separated from each other by a carriage return and line feed.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 <span data-ttu-id="8160f-155">この正規表現 `\G(.+)[\t\u007c](.+)\r?\n` の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="8160f-155">The regular expression `\G(.+)[\t\u007c](.+)\r?\n` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="8160f-156">パターン</span><span class="sxs-lookup"><span data-stu-id="8160f-156">Pattern</span></span>|<span data-ttu-id="8160f-157">説明</span><span class="sxs-lookup"><span data-stu-id="8160f-157">Description</span></span>|  
|-------------|-----------------|  
|`\G`|<span data-ttu-id="8160f-158">最後の一致の終了位置から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="8160f-158">Begin the match where the last match ended.</span></span>|  
|`(.+)`|<span data-ttu-id="8160f-159">任意の文字と 1 回以上、一致します。</span><span class="sxs-lookup"><span data-stu-id="8160f-159">Match any character one or more times.</span></span> <span data-ttu-id="8160f-160">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="8160f-160">This is the first capturing group.</span></span>|  
|`[\t\u007c]`|<span data-ttu-id="8160f-161">タブ (`\t`) または縦棒 (&#124;) と一致します。</span><span class="sxs-lookup"><span data-stu-id="8160f-161">Match a tab (`\t`) or a vertical bar (&#124;).</span></span>|  
|`(.+)`|<span data-ttu-id="8160f-162">任意の文字と 1 回以上、一致します。</span><span class="sxs-lookup"><span data-stu-id="8160f-162">Match any character one or more times.</span></span> <span data-ttu-id="8160f-163">これが 2 番目のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="8160f-163">This is the second capturing group.</span></span>|  
|`\r?\n`|<span data-ttu-id="8160f-164">復帰とそれに続く改行に、0 回または 1 回一致します。</span><span class="sxs-lookup"><span data-stu-id="8160f-164">Match zero or one occurrence of a carriage return followed by a new line.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8160f-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="8160f-165">See also</span></span>

- [<span data-ttu-id="8160f-166">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="8160f-166">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
