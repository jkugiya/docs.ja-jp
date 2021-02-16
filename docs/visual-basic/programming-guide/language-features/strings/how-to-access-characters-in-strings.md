---
description: '詳細情報: 方法:Visual Basic で文字列の文字にアクセスする'
title: '方法: 文字列の文字にアクセスする'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 373005699483dbae92df3a6fe73cc9b6318a9c61
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476164"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="3ad03-103">方法: Visual Basic で文字列の文字にアクセスする</span><span class="sxs-lookup"><span data-stu-id="3ad03-103">How to: Access Characters in Strings in Visual Basic</span></span>

<span data-ttu-id="3ad03-104">この例では、<xref:System.String.Chars%2A> プロパティを使用して、文字列内の指定された位置にある文字にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3ad03-104">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ad03-105">例</span><span class="sxs-lookup"><span data-stu-id="3ad03-105">Example</span></span>  

 <span data-ttu-id="3ad03-106">文字列の文字と文字列内でのそれらの文字の位置に関するデータがあると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="3ad03-106">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="3ad03-107">文字列は文字 (`Char` インスタンス) の配列と考えることができます。<xref:System.String.Chars%2A> プロパティを使用して特定の文字のインデックスを参照することによって、その文字を取得できます。</span><span class="sxs-lookup"><span data-stu-id="3ad03-107">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="3ad03-108"><xref:System.String.Chars%2A> プロパティの `index` パラメーターは 0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="3ad03-108">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3ad03-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="3ad03-109">Robust Programming</span></span>  

 <span data-ttu-id="3ad03-110"><xref:System.String.Chars%2A> プロパティは、指定された位置の文字を返します。</span><span class="sxs-lookup"><span data-stu-id="3ad03-110">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="3ad03-111">ただし、一部の Unicode 文字は複数の文字で表すことができます。</span><span class="sxs-lookup"><span data-stu-id="3ad03-111">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="3ad03-112">Unicode 文字を操作する方法の詳細については、[文字列を文字の配列に変換する方法](how-to-convert-a-string-to-an-array-of-characters.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3ad03-112">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="3ad03-113"><xref:System.String.Chars%2A> プロパティは、`index` パラメーターが文字列の長さ以上である場合、またはゼロ未満の場合に、<xref:System.IndexOutOfRangeException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3ad03-113">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad03-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ad03-114">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="3ad03-115">方法: 文字列を文字の配列に変換する</span><span class="sxs-lookup"><span data-stu-id="3ad03-115">How to: Convert a String to an Array of Characters</span></span>](how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="3ad03-116">Visual Basic で、文字列型とその他のデータ型との変換を行う</span><span class="sxs-lookup"><span data-stu-id="3ad03-116">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="3ad03-117">文字列</span><span class="sxs-lookup"><span data-stu-id="3ad03-117">Strings</span></span>](index.md)
