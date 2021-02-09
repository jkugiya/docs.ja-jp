---
description: 詳細については、以下をご覧ください。 <remarks> (Visual Basic)
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 4b0584abbe85a7ecc73e25dd1f6ec321962b88a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640408"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="eed95-103">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eed95-103">\<remarks> (Visual Basic)</span></span>

<span data-ttu-id="eed95-104">メンバーの解説セクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="eed95-104">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eed95-105">構文</span><span class="sxs-lookup"><span data-stu-id="eed95-105">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="eed95-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eed95-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="eed95-107">メンバーの説明。</span><span class="sxs-lookup"><span data-stu-id="eed95-107">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eed95-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="eed95-108">Remarks</span></span>  

 <span data-ttu-id="eed95-109">`<remarks>` タグを使用して、型の情報を追加し、[\<summary>](summary.md) で指定された情報を補足します。</span><span class="sxs-lookup"><span data-stu-id="eed95-109">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="eed95-110">この情報はオブジェクト ブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="eed95-110">This information appears in the Object Browser.</span></span> <span data-ttu-id="eed95-111">オブジェクト ブラウザーについては、「[コードの構造の表示](/visualstudio/ide/viewing-the-structure-of-code)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed95-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="eed95-112">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="eed95-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eed95-113">例</span><span class="sxs-lookup"><span data-stu-id="eed95-113">Example</span></span>  

 <span data-ttu-id="eed95-114">この例では、`<remarks>` タグを使用して `UpdateRecord` メソッドの動作を説明します。</span><span class="sxs-lookup"><span data-stu-id="eed95-114">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="eed95-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="eed95-115">See also</span></span>

- [<span data-ttu-id="eed95-116">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="eed95-116">XML Comment Tags</span></span>](index.md)
