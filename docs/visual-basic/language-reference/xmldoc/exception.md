---
description: '詳細情報: <exception> (Visual Basic)'
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 14b7f78dd2521f7d5b3d62f635baa5b50969afa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787475"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="85717-102">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85717-102">\<exception> (Visual Basic)</span></span>

<span data-ttu-id="85717-103">スローできる例外を指定します。</span><span class="sxs-lookup"><span data-stu-id="85717-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85717-104">構文</span><span class="sxs-lookup"><span data-stu-id="85717-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="85717-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="85717-105">Parameters</span></span>  

 `member`  
 <span data-ttu-id="85717-106">現在のコンパイル環境から使用できる例外の参照。</span><span class="sxs-lookup"><span data-stu-id="85717-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="85717-107">コンパイラは、指定された例外が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="85717-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="85717-108">`member` は、二重引用符 (" ") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="85717-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="85717-109">説明です。</span><span class="sxs-lookup"><span data-stu-id="85717-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85717-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="85717-110">Remarks</span></span>  

 <span data-ttu-id="85717-111">`<exception>` タグを使用して、スローできる例外を指定します。</span><span class="sxs-lookup"><span data-stu-id="85717-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="85717-112">このタグは、メソッドの定義に適用されます。</span><span class="sxs-lookup"><span data-stu-id="85717-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="85717-113">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="85717-113">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85717-114">例</span><span class="sxs-lookup"><span data-stu-id="85717-114">Example</span></span>  

 <span data-ttu-id="85717-115">この例では、`<exception>` タグを使用して、`IntDivide` 関数がスローできる例外を記述します。</span><span class="sxs-lookup"><span data-stu-id="85717-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="85717-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="85717-116">See also</span></span>

- [<span data-ttu-id="85717-117">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="85717-117">XML Comment Tags</span></span>](index.md)
