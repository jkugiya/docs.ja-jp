---
description: 詳細については、EscapeQuotes が True に設定されている場合、二重引用符が有効な区切り記号ではないため、区切られたフィールドを読み取ることができません。
title: EscapeQuotes が True に設定されている場合、二重引用符は有効な区切り記号でないため、区切り記号で分けられたフィールドを読み取れません
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 066b5110eaddad74b64f1d86683d7ca2a0a619f7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474396"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="3b878-103">EscapeQuotes が True に設定されている場合、二重引用符は有効な区切り記号でないため、区切り記号で分けられたフィールドを読み取れません</span><span class="sxs-lookup"><span data-stu-id="3b878-103">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>

<span data-ttu-id="3b878-104">引用符 (") が区切り文字として指定されており、 `TextFieldParser` が `EscapeQuotes` に設定されているため、 `True`はファイルからの読み取りができません。</span><span class="sxs-lookup"><span data-stu-id="3b878-104">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3b878-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3b878-105">To correct this error</span></span>  
  
- <span data-ttu-id="3b878-106">`EscapeQuotes` を `False` に設定します。</span><span class="sxs-lookup"><span data-stu-id="3b878-106">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b878-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b878-107">See also</span></span>

- [<span data-ttu-id="3b878-108">TextFieldParser.SetDelimiters メソッド</span><span class="sxs-lookup"><span data-stu-id="3b878-108">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [<span data-ttu-id="3b878-109">TextFieldParser.Delimiters プロパティ</span><span class="sxs-lookup"><span data-stu-id="3b878-109">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [<span data-ttu-id="3b878-110">方法: コンマ区切りのテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="3b878-110">How to: Read From Comma-Delimited Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="3b878-111">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="3b878-111">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
