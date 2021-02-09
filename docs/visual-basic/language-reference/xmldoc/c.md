---
description: '詳細情報: <c> (Visual Basic)'
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 350a5dbf2dee2911c356a7c76a9bafbab35fd71e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787514"
---
# <a name="c-visual-basic"></a><span data-ttu-id="befa2-102">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="befa2-102">\<c> (Visual Basic)</span></span>

<span data-ttu-id="befa2-103">説明内のテキストがコードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="befa2-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="befa2-104">構文</span><span class="sxs-lookup"><span data-stu-id="befa2-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="befa2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="befa2-105">Parameters</span></span>  
  
|<span data-ttu-id="befa2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="befa2-106">Parameter</span></span>|<span data-ttu-id="befa2-107">説明</span><span class="sxs-lookup"><span data-stu-id="befa2-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="befa2-108">コードとして指定するテキストです。</span><span class="sxs-lookup"><span data-stu-id="befa2-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="befa2-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="befa2-109">Remarks</span></span>  

 <span data-ttu-id="befa2-110">`<c>` タグを使用すると、説明内のテキストをコードとしてマークする必要があることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="befa2-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="befa2-111">複数行をコードとして示す場合は、[\<code>](code.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="befa2-111">Use [\<code>](code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="befa2-112">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="befa2-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="befa2-113">例</span><span class="sxs-lookup"><span data-stu-id="befa2-113">Example</span></span>  

 <span data-ttu-id="befa2-114">この例では、summary セクションで `<c>` タグを使用して、`Counter` がコードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="befa2-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="befa2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="befa2-115">See also</span></span>

- [<span data-ttu-id="befa2-116">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="befa2-116">XML Comment Tags</span></span>](index.md)
