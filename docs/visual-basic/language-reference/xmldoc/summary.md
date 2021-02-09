---
description: 詳細については、以下をご覧ください。 <summary> (Visual Basic)
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 4d4b1ecf0fa054eb625c1a3cf09c1cab4e661ef2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640291"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="05711-103">\<summary> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05711-103">\<summary> (Visual Basic)</span></span>

<span data-ttu-id="05711-104">メンバーの概要を指定します。</span><span class="sxs-lookup"><span data-stu-id="05711-104">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05711-105">構文</span><span class="sxs-lookup"><span data-stu-id="05711-105">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="05711-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05711-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="05711-107">オブジェクトの概要。</span><span class="sxs-lookup"><span data-stu-id="05711-107">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05711-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="05711-108">Remarks</span></span>  

 <span data-ttu-id="05711-109">`<summary>` タグを使用して、型または型メンバーを記述します。</span><span class="sxs-lookup"><span data-stu-id="05711-109">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="05711-110">型の説明に補足情報を追加するには、[\<remarks>](remarks.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="05711-110">Use [\<remarks>](remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="05711-111">`<summary>` タグのテキストは、IntelliSense での型に関する唯一のソースで、オブジェクト ブラウザーにも表示されます。</span><span class="sxs-lookup"><span data-stu-id="05711-111">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="05711-112">オブジェクト ブラウザーについては、「[コードの構造の表示](/visualstudio/ide/viewing-the-structure-of-code)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05711-112">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="05711-113">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="05711-113">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05711-114">例</span><span class="sxs-lookup"><span data-stu-id="05711-114">Example</span></span>  

 <span data-ttu-id="05711-115">この例では、`<summary>` タグを使用して `ResetCounter` メソッドと `Counter` プロパティを記述します。</span><span class="sxs-lookup"><span data-stu-id="05711-115">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="05711-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="05711-116">See also</span></span>

- [<span data-ttu-id="05711-117">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="05711-117">XML Comment Tags</span></span>](index.md)
