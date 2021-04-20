---
description: '詳細情報: TextFieldParser はスペース文字を含むコメント トークンをサポートしていません'
title: TextFieldParser はスペース文字を含むコメント トークンをサポートしていません
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 27ca19f0a901ca1644d4b121951ed9fdf4d553bd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455341"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a><span data-ttu-id="876c3-103">TextFieldParser はスペース文字を含むコメント トークンをサポートしていません</span><span class="sxs-lookup"><span data-stu-id="876c3-103">TextFieldParser does not support comment tokens that contain white space</span></span>

<span data-ttu-id="876c3-104">空白を含むコメント トークンが指定されています。</span><span class="sxs-lookup"><span data-stu-id="876c3-104">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="876c3-105">トークンの先頭に空白がある場合を除き、 `TextFieldParser` は空白を含むコメント トークンをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="876c3-105">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="876c3-106">トークンの先頭にある空白は無視されます。</span><span class="sxs-lookup"><span data-stu-id="876c3-106">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="876c3-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="876c3-107">To correct this error</span></span>  
  
- <span data-ttu-id="876c3-108">適切なコメント トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="876c3-108">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="876c3-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="876c3-109">See also</span></span>

- [<span data-ttu-id="876c3-110">TextFieldParser.CommentTokens プロパティ</span><span class="sxs-lookup"><span data-stu-id="876c3-110">TextFieldParser.CommentTokens Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [<span data-ttu-id="876c3-111">TextFieldParser オブジェクトによるテキスト ファイルの解析</span><span class="sxs-lookup"><span data-stu-id="876c3-111">Parsing Text Files with the TextFieldParser Object</span></span>](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="876c3-112">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="876c3-112">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
