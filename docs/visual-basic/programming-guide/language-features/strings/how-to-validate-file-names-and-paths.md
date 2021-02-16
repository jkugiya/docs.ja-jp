---
description: '詳細情報: 方法:Visual Basic でファイル名とパスを検証する'
title: '方法: ファイル名とパスを検証する'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: 02a48ea7cbf3291cb2fe1c64c4e636a273842546
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429741"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="490c0-103">方法: Visual Basic でファイル名とパスを検証する</span><span class="sxs-lookup"><span data-stu-id="490c0-103">How to: Validate File Names and Paths in Visual Basic</span></span>

<span data-ttu-id="490c0-104">この例では、文字列がファイル名とパスのどちらを表すかを示す `Boolean` 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="490c0-104">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="490c0-105">この検証では、ファイル システムで許可されていない文字が名前に含まれているかどうかがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="490c0-105">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="490c0-106">例</span><span class="sxs-lookup"><span data-stu-id="490c0-106">Example</span></span>  

 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="490c0-107">この例では、名前にコロンが正しく配置されていないか、名前のないディレクトリがあるか、または名前の長さがシステム定義の最大長を超えているかどうかはチェックされません。</span><span class="sxs-lookup"><span data-stu-id="490c0-107">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="490c0-108">また、アプリケーションが指定された名前のファイル システム リソースにアクセスするアクセス許可を持っているかどうかもチェックされません。</span><span class="sxs-lookup"><span data-stu-id="490c0-108">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="490c0-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="490c0-109">See also</span></span>

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="490c0-110">Visual Basic における文字列の検証</span><span class="sxs-lookup"><span data-stu-id="490c0-110">Validating Strings in Visual Basic</span></span>](validating-strings.md)
