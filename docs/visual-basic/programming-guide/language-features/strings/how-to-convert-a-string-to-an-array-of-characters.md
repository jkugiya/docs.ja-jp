---
description: '詳細情報: 方法:Visual Basic で文字列を文字の配列に変換する'
title: '方法: 文字列を文字の配列に変換する'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: f85b0801cf013e207eacd70a256a3ed0a8dc7887
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476151"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="edef3-103">方法: Visual Basic で文字列を文字の配列に変換する</span><span class="sxs-lookup"><span data-stu-id="edef3-103">How to: Convert a String to an Array of Characters in Visual Basic</span></span>

<span data-ttu-id="edef3-104">文字列を解析する場合など、文字列の文字と文字列内でのそれらの文字の位置に関するデータがあると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="edef3-104">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="edef3-105">この例では、文字列の <xref:System.String.ToCharArray%2A> メソッドを呼び出して、文字列の文字の配列を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="edef3-105">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edef3-106">例</span><span class="sxs-lookup"><span data-stu-id="edef3-106">Example</span></span>  

 <span data-ttu-id="edef3-107">この例は、文字列を `Char` 配列に分割する方法と、文字列を Unicode テキスト文字の `String` 配列に分割する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="edef3-107">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="edef3-108">この区別の理由は、Unicode テキスト文字は 2つ以上の `Char` 文字 (サロゲート ペアや結合文字シーケンスなど) で構成できるからです。</span><span class="sxs-lookup"><span data-stu-id="edef3-108">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="edef3-109">詳細については、<xref:System.Globalization.TextElementEnumerator> に関する記事、および「[The Unicode Standard (Unicode 標準)](https://www.unicode.org/standard/standard.html)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="edef3-109">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a><span data-ttu-id="edef3-110">例</span><span class="sxs-lookup"><span data-stu-id="edef3-110">Example</span></span>  

 <span data-ttu-id="edef3-111">文字列を Unicode テキスト文字に分割する方が難しいですが、文字列の視覚的な表現に関する情報が必要な場合に、これが必要となります。</span><span class="sxs-lookup"><span data-stu-id="edef3-111">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="edef3-112">この例では、<xref:System.Globalization.StringInfo.SubstringByTextElements%2A> メソッドを使用して、文字列を構成する Unicode テキスト文字に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="edef3-112">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a><span data-ttu-id="edef3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="edef3-113">See also</span></span>

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="edef3-114">方法: 文字列の文字にアクセスする</span><span class="sxs-lookup"><span data-stu-id="edef3-114">How to: Access Characters in Strings</span></span>](how-to-access-characters-in-strings.md)
- [<span data-ttu-id="edef3-115">Visual Basic で、文字列型とその他のデータ型との変換を行う</span><span class="sxs-lookup"><span data-stu-id="edef3-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="edef3-116">文字列</span><span class="sxs-lookup"><span data-stu-id="edef3-116">Strings</span></span>](index.md)
