---
description: '詳細情報: 方法:方法: char 値の配列から文字列を作成する (Visual Basic)'
title: '方法: Char 値の配列から文字列を作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 67b675f5f02c92b785e374b99f49248d43d12fb4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429833"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="11494-103">方法: 方法: char 値の配列から文字列を作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11494-103">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>

<span data-ttu-id="11494-104">この例では、個々の文字から文字列 "abcd" を作成します。</span><span class="sxs-lookup"><span data-stu-id="11494-104">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11494-105">例</span><span class="sxs-lookup"><span data-stu-id="11494-105">Example</span></span>  

 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="11494-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="11494-106">Compile the code</span></span>  

 <span data-ttu-id="11494-107">このメソッドには特別な要件はありません。</span><span class="sxs-lookup"><span data-stu-id="11494-107">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="11494-108">引用符で囲まれた単一の文字の後に単一の `c` が続く構文 `"a"c` を使用して、文字リテラルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="11494-108">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="11494-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="11494-109">Robust Programming</span></span>  

 <span data-ttu-id="11494-110">文字列に null 文字 (`Chr(0)` に相当) が含まれていると、文字列を使用したときに予期しない結果が生じます。</span><span class="sxs-lookup"><span data-stu-id="11494-110">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="11494-111">文字列に nulll 文字を含めることはできますが、状況によっては、nulll 文字に続く文字が表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="11494-111">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11494-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="11494-112">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="11494-113">Char データ型</span><span class="sxs-lookup"><span data-stu-id="11494-113">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="11494-114">データの種類</span><span class="sxs-lookup"><span data-stu-id="11494-114">Data Types</span></span>](../data-types/index.md)
