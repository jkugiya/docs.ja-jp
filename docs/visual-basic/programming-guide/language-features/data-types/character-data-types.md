---
description: '詳細情報: 文字データ型 (Visual Basic)'
title: 文字データ型
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 2197c0210cb0c2287baff9856889334f5f95bd4d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466394"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="1423a-103">文字データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1423a-103">Character Data Types (Visual Basic)</span></span>

<span data-ttu-id="1423a-104">Visual Basic には、印刷や表示が可能な文字を処理するための "*文字データ型*" が用意されています。</span><span class="sxs-lookup"><span data-stu-id="1423a-104">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="1423a-105">どちらも Unicode 文字を処理しますが、`Char` は 1 つの文字を保持するのに対し、`String` は不特定数の文字を含みます。</span><span class="sxs-lookup"><span data-stu-id="1423a-105">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="1423a-106">Visual Basic データ型を並べて比較している表を、[データ型](../../../language-reference/data-types/index.md)に関するページで参照してください。</span><span class="sxs-lookup"><span data-stu-id="1423a-106">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="1423a-107">Char 型</span><span class="sxs-lookup"><span data-stu-id="1423a-107">Char Type</span></span>  

 <span data-ttu-id="1423a-108">`Char` データ型は、1 つの 2 バイト (16 ビット) Unicode 文字です。</span><span class="sxs-lookup"><span data-stu-id="1423a-108">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="1423a-109">常に変数が厳密に 1 つの文字を格納する場合は、`Char` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="1423a-109">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="1423a-110">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1423a-110">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="1423a-111">`Char` または `String` 変数に含めることができる値は、"*コード ポイント*"、つまり Unicode 文字セットの文字コードです。</span><span class="sxs-lookup"><span data-stu-id="1423a-111">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="1423a-112">Unicode 文字には、基本的な ASCII 文字セット、その他のさまざまなアルファベット文字、アクセント記号、通貨記号、分数、分音記号、数学記号、および技術用記号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1423a-112">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1423a-113">Unicode 文字セットでは、"*サロゲート ペア*" (1 つのコード ポイントを表すために 2 つの 16 ビット値を必要とする) のためにコード ポイント D800 から DFFF (10 進数では 55296 から 55551) が予約されています。</span><span class="sxs-lookup"><span data-stu-id="1423a-113">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="1423a-114">`Char` 変数はサロゲート ペアを保持できません。`String` は 2 つの位置を使用してこのようなペアを保持します。</span><span class="sxs-lookup"><span data-stu-id="1423a-114">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="1423a-115">詳細については、「[文字型 (Char)](../../../language-reference/data-types/char-data-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1423a-115">For more information, see [Char Data Type](../../../language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="1423a-116">文字列の種類</span><span class="sxs-lookup"><span data-stu-id="1423a-116">String Type</span></span>  

 <span data-ttu-id="1423a-117">`String` データ型は、0 個以上の 2 バイト (16 ビット) Unicode 文字のシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="1423a-117">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="1423a-118">変数が不特定数の文字を含む可能性がある場合は、`String` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="1423a-118">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="1423a-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1423a-119">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="1423a-120">詳細については、「[文字列型 (String)](../../../language-reference/data-types/string-data-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1423a-120">For more information, see [String Data Type](../../../language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1423a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="1423a-121">See also</span></span>

- [<span data-ttu-id="1423a-122">基本データ型</span><span class="sxs-lookup"><span data-stu-id="1423a-122">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="1423a-123">複合データ型</span><span class="sxs-lookup"><span data-stu-id="1423a-123">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="1423a-124">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1423a-124">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="1423a-125">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="1423a-125">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="1423a-126">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="1423a-126">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="1423a-127">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="1423a-127">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="1423a-128">型文字</span><span class="sxs-lookup"><span data-stu-id="1423a-128">Type Characters</span></span>](type-characters.md)
