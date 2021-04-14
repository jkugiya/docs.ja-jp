---
description: '詳細情報: 現在の FieldWidths を使用して、行 <number> を解析できません'
title: 現在の FieldWidth を使用して、行 <number> を解析できません。
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_MalFormedFixedWidthLine
ms.assetid: 84e14245-dfdf-4b62-8b84-e83a31608899
ms.openlocfilehash: 58a4da34c33c952c60d65c6cfbaeaa86e902238c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430171"
---
# <a name="line-number-cannot-be-parsed-using-the-current-fieldwidths"></a><span data-ttu-id="c53e7-103">現在の FieldWidth を使用して、行 \<number> を解析できません。</span><span class="sxs-lookup"><span data-stu-id="c53e7-103">Line \<number> cannot be parsed using the current FieldWidths</span></span>

<span data-ttu-id="c53e7-104">指定された行のフィールドの幅が指定よりも大きいため、その行を解析できません。</span><span class="sxs-lookup"><span data-stu-id="c53e7-104">The specified line cannot be parsed because its fields have widths other than those specified.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c53e7-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c53e7-105">To correct this error</span></span>  
  
- <span data-ttu-id="c53e7-106">行が正しく解析できるように `FieldWidths` を調整するか、またはその行を処理するために例外処理コードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="c53e7-106">Adjust `FieldWidths` so the line can be parsed correctly, or insert exception-handling code in order to handle the line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c53e7-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="c53e7-107">See also</span></span>

- [<span data-ttu-id="c53e7-108">方法: 複数の書式を持つテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="c53e7-108">How to: Read From Text Files with Multiple Formats</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="c53e7-109">My.Computer.FileSystem.OpenTextFieldParser</span><span class="sxs-lookup"><span data-stu-id="c53e7-109">My.Computer.FileSystem.OpenTextFieldParser</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A)
- [<span data-ttu-id="c53e7-110">TextFieldParser オブジェクトによるテキスト ファイルの解析</span><span class="sxs-lookup"><span data-stu-id="c53e7-110">Parsing Text Files with the TextFieldParser Object</span></span>](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="c53e7-111">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="c53e7-111">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
- [<span data-ttu-id="c53e7-112">TextFieldParser.FieldWidths プロパティ</span><span class="sxs-lookup"><span data-stu-id="c53e7-112">TextFieldParser.FieldWidths Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A)
- [<span data-ttu-id="c53e7-113">TextFieldParser.SetFieldWidths メソッド</span><span class="sxs-lookup"><span data-stu-id="c53e7-113">TextFieldParser.SetFieldWidths Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A)
