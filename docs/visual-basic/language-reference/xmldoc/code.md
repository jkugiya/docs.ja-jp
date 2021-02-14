---
description: '詳細情報: <code> (Visual Basic)'
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 80fc0988f60d9d82b9c88734f86b20ebccc80b7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787501"
---
# <a name="code-visual-basic"></a><span data-ttu-id="ea19f-102">\<code> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea19f-102">\<code> (Visual Basic)</span></span>

<span data-ttu-id="ea19f-103">テキストが複数コード行であることを示します。</span><span class="sxs-lookup"><span data-stu-id="ea19f-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea19f-104">構文</span><span class="sxs-lookup"><span data-stu-id="ea19f-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea19f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea19f-105">Parameters</span></span>  

 `content`  
 <span data-ttu-id="ea19f-106">コードとしてマークするテキスト。</span><span class="sxs-lookup"><span data-stu-id="ea19f-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea19f-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="ea19f-107">Remarks</span></span>  

 <span data-ttu-id="ea19f-108">`<code>` タグを使用して、複数行をコードとして指定します。</span><span class="sxs-lookup"><span data-stu-id="ea19f-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="ea19f-109">説明内のテキストをコードとしてマークする場合は、[\<c>](c.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea19f-109">Use [\<c>](c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="ea19f-110">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="ea19f-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea19f-111">例</span><span class="sxs-lookup"><span data-stu-id="ea19f-111">Example</span></span>  

 <span data-ttu-id="ea19f-112">この例では、\<code> タグを使用して、`ID` フィールドを使用するためのコード例を追加します。</span><span class="sxs-lookup"><span data-stu-id="ea19f-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ea19f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea19f-113">See also</span></span>

- [<span data-ttu-id="ea19f-114">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="ea19f-114">XML Comment Tags</span></span>](index.md)
