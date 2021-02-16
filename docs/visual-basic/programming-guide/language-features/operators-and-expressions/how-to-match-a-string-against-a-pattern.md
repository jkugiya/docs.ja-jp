---
description: '詳細情報: 方法:文字列がパターンに一致するかどうかを調べる (Visual Basic)'
title: '方法: 文字列がパターンに一致するかを調べる'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: f3e3426f85d420726571f03c88546d181cdccf97
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461945"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="c0630-103">方法: 文字列がパターンに一致するかどうかを調べる (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0630-103">How to: Match a String against a Pattern (Visual Basic)</span></span>

<span data-ttu-id="c0630-104">[文字列データ型](../../../language-reference/data-types/string-data-type.md)の式がパターンを満たしているかどうかを確認するには、[Like 演算子](../../../language-reference/operators/like-operator.md)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0630-104">If you want to find out if an expression of the [String Data Type](../../../language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="c0630-105">`Like` は 2 つのオペランドを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c0630-105">`Like` takes two operands.</span></span> <span data-ttu-id="c0630-106">左オペランドは文字列式であり、右オペランドは照合に使用されるパターンを含む文字列です。</span><span class="sxs-lookup"><span data-stu-id="c0630-106">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="c0630-107">`Like` からは、文字列式がパターンを満たしているかどうかを示す `Boolean` 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="c0630-107">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>

<span data-ttu-id="c0630-108">文字列式の各文字を、特定の文字、ワイルドカード文字、文字リスト、または文字範囲と照合できます。</span><span class="sxs-lookup"><span data-stu-id="c0630-108">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="c0630-109">パターン文字列内の指定の位置は、文字列式で照合される文字の位置に対応しています。</span><span class="sxs-lookup"><span data-stu-id="c0630-109">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="c0630-110">文字列式の文字を特定の文字と照合するには</span><span class="sxs-lookup"><span data-stu-id="c0630-110">To match a character in the string expression against a specific character</span></span>

<span data-ttu-id="c0630-111">特定の文字をパターン文字列に直接含めます。</span><span class="sxs-lookup"><span data-stu-id="c0630-111">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="c0630-112">一部の特殊文字は角かっこ (`[ ]`) で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0630-112">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="c0630-113">詳細については、「[Like 演算子](../../../language-reference/operators/like-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0630-113">For more information, see [Like Operator](../../../language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="c0630-114">次の例では、`myString` が 1 つの文字 `H` で構成されているかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="c0630-114">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="c0630-115">文字列式の文字をワイルドカード文字と照合するには</span><span class="sxs-lookup"><span data-stu-id="c0630-115">To match a character in the string expression against a wildcard character</span></span>

<span data-ttu-id="c0630-116">パターン文字列に疑問符 (`?`) を含めます。</span><span class="sxs-lookup"><span data-stu-id="c0630-116">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="c0630-117">この位置にある任意の有効な文字が一致と見なされます。</span><span class="sxs-lookup"><span data-stu-id="c0630-117">Any valid character in this position makes a successful match.</span></span>

<span data-ttu-id="c0630-118">次の例では、`myString` が、1 つの文字 `W` と、それに続く任意の値のちょうど 2 つの文字で構成されているかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="c0630-118">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="c0630-119">文字列式の文字を文字のリストと照合するには</span><span class="sxs-lookup"><span data-stu-id="c0630-119">To match a character in the string expression against a list of characters</span></span>

<span data-ttu-id="c0630-120">角かっこ (`[ ]`) をパターン文字列に含め、角かっこの内側に文字のリストを含めます。</span><span class="sxs-lookup"><span data-stu-id="c0630-120">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="c0630-121">文字をコンマやその他の区切り記号で区切らないでください。</span><span class="sxs-lookup"><span data-stu-id="c0630-121">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="c0630-122">リスト内の任意の 1 文字が一致と見なされます。</span><span class="sxs-lookup"><span data-stu-id="c0630-122">Any single character in the list makes a successful match.</span></span>

<span data-ttu-id="c0630-123">次の例では、`myString` が、任意の有効な文字と、それに続く `A`、`C`、または `E` のいずれか 1 文字のみで構成されるかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="c0630-123">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

<span data-ttu-id="c0630-124">この照合では、大文字と小文字が区別されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c0630-124">Note that this match is case-sensitive.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="c0630-125">文字列式の文字を文字の範囲と照合するには</span><span class="sxs-lookup"><span data-stu-id="c0630-125">To match a character in the string expression against a range of characters</span></span>

<span data-ttu-id="c0630-126">パターン文字列に角かっこ (`[ ]`) を含め、角かっこ内にハイフン (`–`) で区切られた範囲内の最小文字と最大文字を含めます。</span><span class="sxs-lookup"><span data-stu-id="c0630-126">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="c0630-127">範囲内の任意の 1 文字が一致と見なされます。</span><span class="sxs-lookup"><span data-stu-id="c0630-127">Any single character within the range makes a successful match.</span></span>

<span data-ttu-id="c0630-128">次の例では、`myString` が、文字 `num` と、それに続く `i`、`j`、`k`、`l`、`m`、または `n` のいずれか 1 文字のみで構成されるかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="c0630-128">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

<span data-ttu-id="c0630-129">この照合では、大文字と小文字が区別されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c0630-129">Note that this match is case-sensitive.</span></span>

## <a name="matching-empty-strings"></a><span data-ttu-id="c0630-130">空の文字列の照合</span><span class="sxs-lookup"><span data-stu-id="c0630-130">Matching Empty Strings</span></span>

<span data-ttu-id="c0630-131">`Like` では、シーケンス `[]` は長さゼロの文字列 (`""`) として扱われます。</span><span class="sxs-lookup"><span data-stu-id="c0630-131">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="c0630-132">`[]` を使用して文字列式全体が空かどうかをテストできますが、文字列式の特定の位置が空であるかどうかをテストすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c0630-132">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="c0630-133">空の位置がテストする必要があるオプションの 1 つである場合は、`Like` を複数回使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0630-133">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="c0630-134">文字列式の文字を文字のリストまたは文字なしと照合するには</span><span class="sxs-lookup"><span data-stu-id="c0630-134">To match a character in the string expression against a list of characters or no character</span></span>

1. <span data-ttu-id="c0630-135">同じ文字列式で `Like` 演算子を 2 回呼び出し、2 つの呼び出しを [Or 演算子](../../../language-reference/operators/or-operator.md)または [OrElse 演算子](../../../language-reference/operators/orelse-operator.md)のいずれかを使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="c0630-135">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../language-reference/operators/or-operator.md) or the [OrElse Operator](../../../language-reference/operators/orelse-operator.md).</span></span>

2. <span data-ttu-id="c0630-136">1 つ目の `Like` 句のパターン文字列には、角かっこ (`[ ]`) で囲んだ文字リストを含めます。</span><span class="sxs-lookup"><span data-stu-id="c0630-136">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>

3. <span data-ttu-id="c0630-137">2 つ目の `Like` 句のパターン文字列には、対象の位置に文字を配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="c0630-137">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>

    <span data-ttu-id="c0630-138">次の例では、7 桁の電話番号 `phoneNum` (ちょうど 3 桁の数字、それに続くスペース、ハイフン (`–`)、ピリオド (`.`)、またはまったく文字なし、それに続くちょうど 4 桁の数字) をテストします。</span><span class="sxs-lookup"><span data-stu-id="c0630-138">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a><span data-ttu-id="c0630-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0630-139">See also</span></span>

- [<span data-ttu-id="c0630-140">比較演算子</span><span class="sxs-lookup"><span data-stu-id="c0630-140">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="c0630-141">演算子および式</span><span class="sxs-lookup"><span data-stu-id="c0630-141">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="c0630-142">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="c0630-142">Like Operator</span></span>](../../../language-reference/operators/like-operator.md)
- [<span data-ttu-id="c0630-143">String データ型</span><span class="sxs-lookup"><span data-stu-id="c0630-143">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
