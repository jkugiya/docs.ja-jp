---
description: '詳細情報: 方法:日付または時刻を表す文字列を検証する (Visual Basic)'
title: '方法: 日付または時刻を表す文字列を検証する'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 4e9255717d1711d8e9839c218a78b359549d9eef
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424256"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="9f673-103">方法: 日付または時刻を表す文字列を検証する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f673-103">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>

<span data-ttu-id="9f673-104">次のコード例では、文字列が有効な日付または時刻を表しているかどうかを示す `Boolean` 値を設定します。</span><span class="sxs-lookup"><span data-stu-id="9f673-104">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f673-105">例</span><span class="sxs-lookup"><span data-stu-id="9f673-105">Example</span></span>  

 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="9f673-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="9f673-106">Compile the code</span></span>  

 <span data-ttu-id="9f673-107">`("01/01/03")` と `"9:30 PM"` を、検証する日付と時刻に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9f673-107">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="9f673-108">文字列は、ハードコーディングされた別の文字列、`String` 変数、または文字列を返すメソッド (`InputBox` など) に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="9f673-108">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9f673-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="9f673-109">Robust Programming</span></span>  

 <span data-ttu-id="9f673-110">`String` から `DateTime` 変数への変換を試みる前に、このメソッドを使用して文字列を検証します。</span><span class="sxs-lookup"><span data-stu-id="9f673-110">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="9f673-111">日付または時刻を最初にチェックしておくことで、実行時に例外が生成されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="9f673-111">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f673-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f673-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="9f673-113">Visual Basic における文字列の検証</span><span class="sxs-lookup"><span data-stu-id="9f673-113">Validating Strings in Visual Basic</span></span>](validating-strings.md)
