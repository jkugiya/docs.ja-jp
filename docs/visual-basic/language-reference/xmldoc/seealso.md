---
description: 詳細については、以下をご覧ください。 <seealso> (Visual Basic)
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 0bf6fa69ad63db016b42e31f717f521f82bbe20e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640317"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="f295e-103">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f295e-103">\<seealso> (Visual Basic)</span></span>

<span data-ttu-id="f295e-104">関連項目セクションに表示されるリンクを指定します。</span><span class="sxs-lookup"><span data-stu-id="f295e-104">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f295e-105">構文</span><span class="sxs-lookup"><span data-stu-id="f295e-105">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="f295e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f295e-106">Parameters</span></span>  

 `member`  
 <span data-ttu-id="f295e-107">現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。</span><span class="sxs-lookup"><span data-stu-id="f295e-107">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="f295e-108">コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。</span><span class="sxs-lookup"><span data-stu-id="f295e-108">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="f295e-109">`member` は、二重引用符 (" ") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="f295e-109">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f295e-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="f295e-110">Remarks</span></span>  

 <span data-ttu-id="f295e-111">`<seealso>` タグを使用して、関連項目セクションに表示するテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="f295e-111">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="f295e-112">[\<see>](see.md) を使用すると、テキスト内からリンクを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f295e-112">Use [\<see>](see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="f295e-113">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="f295e-113">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f295e-114">例</span><span class="sxs-lookup"><span data-stu-id="f295e-114">Example</span></span>  

 <span data-ttu-id="f295e-115">この例では、`DoesRecordExist` 解説セクションの `<seealso>` タグを使用して、`UpdateRecord` メソッドを参照します。</span><span class="sxs-lookup"><span data-stu-id="f295e-115">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="f295e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f295e-116">See also</span></span>

- [<span data-ttu-id="f295e-117">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="f295e-117">XML Comment Tags</span></span>](index.md)
