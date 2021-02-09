---
description: '詳細情報: Like 演算子 (Visual Basic)'
title: Like 演算子
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: f1be174010b7acae5bface4fc0a2d0e606a90fca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665589"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="6c0c6-103">Like 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c0c6-103">Like Operator (Visual Basic)</span></span>

<span data-ttu-id="6c0c6-104">文字列をパターンと比較します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-104">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="6c0c6-105">`Like` 演算子は、現在、.NET Core および .NET Standard のプロジェクトではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-105">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="6c0c6-106">構文</span><span class="sxs-lookup"><span data-stu-id="6c0c6-106">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="6c0c6-107">指定項目</span><span class="sxs-lookup"><span data-stu-id="6c0c6-107">Parts</span></span>  

 `result`  
 <span data-ttu-id="6c0c6-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-108">Required.</span></span> <span data-ttu-id="6c0c6-109">任意の `Boolean` 変数。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-109">Any `Boolean` variable.</span></span> <span data-ttu-id="6c0c6-110">結果は、`string` が `pattern` を満たすかどうか示す `Boolean` 値です。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-110">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="6c0c6-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-111">Required.</span></span> <span data-ttu-id="6c0c6-112">任意のブール型 ( `String` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-112">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="6c0c6-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-113">Required.</span></span> <span data-ttu-id="6c0c6-114">「解説」で説明されているパターン マッチング規則に準拠した `String` 式を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-114">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c0c6-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="6c0c6-115">Remarks</span></span>  

 <span data-ttu-id="6c0c6-116">`string` の値が `pattern` に格納されているパターンを満たす場合、`result` は `True` になります。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-116">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="6c0c6-117">文字列がパターンを満たさない場合、`result` は `False` になります。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-117">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="6c0c6-118">`string` と `pattern` の両方が空の文字列の場合、結果は `True` になります。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-118">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="6c0c6-119">比較方法</span><span class="sxs-lookup"><span data-stu-id="6c0c6-119">Comparison Method</span></span>  

 <span data-ttu-id="6c0c6-120">`Like` 演算子の動作は、[Option Compare ステートメント](../statements/option-compare-statement.md)に基づきます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-120">The behavior of the `Like` operator depends on the [Option Compare Statement](../statements/option-compare-statement.md).</span></span> <span data-ttu-id="6c0c6-121">各ソース ファイルの既定の文字列比較方法は `Option Compare Binary` です。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-121">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="6c0c6-122">パターンのオプション</span><span class="sxs-lookup"><span data-stu-id="6c0c6-122">Pattern Options</span></span>  

 <span data-ttu-id="6c0c6-123">組み込みのパターン マッチングでは、文字列比較に使用できるさまざまなツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-123">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="6c0c6-124">パターン マッチング機能を使用すると、`string` 内の各文字を、特定の文字、ワイルドカード文字、文字リスト、または文字範囲と一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-124">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="6c0c6-125">次の表に、`pattern` で使用できる文字と、それらが何に一致するかを示します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-125">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="6c0c6-126">`pattern` 内の文字</span><span class="sxs-lookup"><span data-stu-id="6c0c6-126">Characters in `pattern`</span></span>|<span data-ttu-id="6c0c6-127">`string` 内の以下に一致</span><span class="sxs-lookup"><span data-stu-id="6c0c6-127">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="6c0c6-128">任意の 1 文字</span><span class="sxs-lookup"><span data-stu-id="6c0c6-128">Any single character</span></span>|  
|`*`|<span data-ttu-id="6c0c6-129">0 個以上の文字</span><span class="sxs-lookup"><span data-stu-id="6c0c6-129">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="6c0c6-130">任意の 1 つの数字 (0 ～ 9)</span><span class="sxs-lookup"><span data-stu-id="6c0c6-130">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="6c0c6-131">`charlist` 内の任意の 1 文字</span><span class="sxs-lookup"><span data-stu-id="6c0c6-131">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="6c0c6-132">`charlist` 内にない任意の 1 文字</span><span class="sxs-lookup"><span data-stu-id="6c0c6-132">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="6c0c6-133">文字リスト</span><span class="sxs-lookup"><span data-stu-id="6c0c6-133">Character Lists</span></span>  

 <span data-ttu-id="6c0c6-134">角かっこ (`[ ]`) で囲まれた 1 つ以上の文字のグループ (`charlist`) と、`string` 内の任意の 1 文字を一致させることができます。このグループには、数字を含むほぼすべての文字コードを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-134">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="6c0c6-135">`charlist` の先頭にある感嘆符 (`!`) は、`charlist` 内の文字を除く任意の文字が `string` で見つかった場合に一致することを意味します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-135">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="6c0c6-136">感嘆符を角かっこの外側で使用すると、感嘆符自体を照合できます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-136">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="6c0c6-137">特殊文字</span><span class="sxs-lookup"><span data-stu-id="6c0c6-137">Special Characters</span></span>  

 <span data-ttu-id="6c0c6-138">特殊文字の左角かっこ (`[`)、疑問符 (`?`)、番号記号 (`#`)、およびアスタリスク (`*`) を一致させるには、これらを角かっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-138">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="6c0c6-139">右角かっこ (`]`) は、グループ内でそれ自体を一致させるために使用できませんが、グループの外側で個別の文字として使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-139">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="6c0c6-140">文字シーケンス `[]` は、長さが 0 の文字列 (`""`) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-140">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="6c0c6-141">ただし、これを角かっこで囲まれた文字リストの一部にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-141">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="6c0c6-142">`Like` を 2 回使用すると、`string` 内のある場所に、文字グループのいずれかの文字が含まれているか、または文字がまったく含まれていないか確認できます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-142">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="6c0c6-143">例については、「[方法: 文字列がパターンに一致するかを調べる](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-143">For an example, see [How to: Match a String against a Pattern](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="6c0c6-144">文字範囲</span><span class="sxs-lookup"><span data-stu-id="6c0c6-144">Character Ranges</span></span>  

 <span data-ttu-id="6c0c6-145">ハイフン (`–`) を使用して範囲の下限と上限を区切ることにより、`charlist` で文字の範囲を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-145">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="6c0c6-146">たとえば、`string` 内の対応する文字位置に、`A`–`Z` の範囲の任意の文字が含まれている場合、`[A–Z]` は一致と見なされます。また、対応する文字位置に `H`–`L` の範囲外の文字が含まれている場合、`[!H–L]` は一致と見なされます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-146">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="6c0c6-147">文字の範囲を指定する場合、昇順の並べ替え順序、つまり、最小から最大の順序で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-147">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="6c0c6-148">したがって、`[A–Z]` は有効なパターンですが、`[Z–A]` は有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-148">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="6c0c6-149">複数の文字範囲</span><span class="sxs-lookup"><span data-stu-id="6c0c6-149">Multiple Character Ranges</span></span>  

 <span data-ttu-id="6c0c6-150">同じ文字位置の複数の範囲を指定するには、区切り記号を使用せずに同じ角かっこ内にそれらの範囲を配置します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-150">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="6c0c6-151">たとえば、`string` 内の対応する文字位置に範囲 `A`–`C` または範囲 `X`–`Z` 内の文字が含まれる場合、`[A–CX–Z]` は一致と見なされます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-151">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="6c0c6-152">ハイフンの使用</span><span class="sxs-lookup"><span data-stu-id="6c0c6-152">Usage of the Hyphen</span></span>  

 <span data-ttu-id="6c0c6-153">ハイフン (`–`) を `charlist` の先頭 (感嘆符がある場合はその後)、または末尾に配置することで、ハイフン自体と一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-153">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="6c0c6-154">その他の場所では、ハイフンは、ハイフンの両側の文字によって定められた文字の範囲を示します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-154">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="6c0c6-155">照合順序</span><span class="sxs-lookup"><span data-stu-id="6c0c6-155">Collating Sequence</span></span>  

 <span data-ttu-id="6c0c6-156">指定した範囲の意味は、実行時の文字の順序によって異なります。`Option Compare` と、コードが実行されるシステムのロケール設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-156">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="6c0c6-157">`Option Compare Binary` を使用すると、範囲 `[A–E]` は `A`、`B`、`C`、`D`、および `E` と一致します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-157">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="6c0c6-158">`Option Compare Text` を使用すると、`[A–E]` は `A`、`a`、`À`、`à`、`B`、`b`、`C`、`c`、`D`、`d`、`E`、および `e` と一致します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-158">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="6c0c6-159">この範囲は `Ê` および `ê` とは一致しません。これは、並べ替え順序で、アクセント記号付き文字がアクセント記号なし文字の後になるためです。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-159">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="6c0c6-160">digraph 文字</span><span class="sxs-lookup"><span data-stu-id="6c0c6-160">Digraph Characters</span></span>  

 <span data-ttu-id="6c0c6-161">言語によっては、2 つの個別の文字を表すアルファベット文字があります。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-161">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="6c0c6-162">たとえば、いくつかの言語では、文字 `æ` を使用して文字 `a` と文字 `e` (これらが一緒に現れる場合) を表します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-162">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="6c0c6-163">`Like` 演算子は、1 つの digraph 文字と 2 つの個別文字が同等であると認識します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-163">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="6c0c6-164">digraph 文字を使用する言語がシステムのロケール設定で指定されている場合、`pattern` または `string` に 1 つの digraph 文字があると、その digraph 文字は他の文字列内の同等の連続する 2 文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-164">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="6c0c6-165">同様に、角かっこ (それ自体、リスト内、または範囲内) で囲まれた `pattern` 内の digraph 文字は、`string` 内の同等の連続する 2 文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-165">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="6c0c6-166">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="6c0c6-166">Overloading</span></span>  

 <span data-ttu-id="6c0c6-167">`Like` 演算子は "*オーバーロード*" できます。つまり、オペランドの型がクラスまたは構造体であるとき、そのクラスまたは構造体で、演算子の動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-167">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="6c0c6-168">コードで、そのようなクラスまたは構造体に対してこの演算子が使用される場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-168">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="6c0c6-169">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-169">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c0c6-170">例</span><span class="sxs-lookup"><span data-stu-id="6c0c6-170">Example</span></span>  

 <span data-ttu-id="6c0c6-171">この例では、`Like` 演算子を使用して、文字列をさまざまなパターンと比較します。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-171">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="6c0c6-172">結果は、各文字列がパターンを満たすかどうかを示す `Boolean` 変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="6c0c6-172">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="6c0c6-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c0c6-173">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="6c0c6-174">比較演算子</span><span class="sxs-lookup"><span data-stu-id="6c0c6-174">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="6c0c6-175">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="6c0c6-175">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="6c0c6-176">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="6c0c6-176">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="6c0c6-177">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c0c6-177">Option Compare Statement</span></span>](../statements/option-compare-statement.md)
- [<span data-ttu-id="6c0c6-178">演算子および式</span><span class="sxs-lookup"><span data-stu-id="6c0c6-178">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="6c0c6-179">方法: 文字列がパターンに一致するかを調べる</span><span class="sxs-lookup"><span data-stu-id="6c0c6-179">How to: Match a String against a Pattern</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
