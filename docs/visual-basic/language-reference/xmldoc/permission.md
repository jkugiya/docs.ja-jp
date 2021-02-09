---
description: 詳細については、以下をご覧ください。 <permission> (Visual Basic)
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 7a227e97051002c834c96297d3028f08e3ed07ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700261"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="42ff9-103">\<permission> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42ff9-103">\<permission> (Visual Basic)</span></span>

<span data-ttu-id="42ff9-104">メンバーの必要な権限を指定します。</span><span class="sxs-lookup"><span data-stu-id="42ff9-104">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42ff9-105">構文</span><span class="sxs-lookup"><span data-stu-id="42ff9-105">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="42ff9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42ff9-106">Parameters</span></span>  

 `member`  
 <span data-ttu-id="42ff9-107">現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。</span><span class="sxs-lookup"><span data-stu-id="42ff9-107">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="42ff9-108">コンパイラは、指定されたコード要素が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="42ff9-108">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="42ff9-109">`member` を引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="42ff9-109">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="42ff9-110">メンバーへのアクセスの説明です。</span><span class="sxs-lookup"><span data-stu-id="42ff9-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42ff9-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="42ff9-111">Remarks</span></span>  

 <span data-ttu-id="42ff9-112">`<permission>` タグを使用して、メンバーのアクセスを文書化します。</span><span class="sxs-lookup"><span data-stu-id="42ff9-112">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="42ff9-113"><xref:System.Security.PermissionSet> クラスを使用して、メンバーへのアクセスを指定します。</span><span class="sxs-lookup"><span data-stu-id="42ff9-113">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="42ff9-114">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="42ff9-114">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42ff9-115">例</span><span class="sxs-lookup"><span data-stu-id="42ff9-115">Example</span></span>  

 <span data-ttu-id="42ff9-116">この例では、`<permission>` タグを使用して、<xref:System.Security.Permissions.FileIOPermission> が `ReadFile` メソッドに必要であることを記述します。</span><span class="sxs-lookup"><span data-stu-id="42ff9-116">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="42ff9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="42ff9-117">See also</span></span>

- [<span data-ttu-id="42ff9-118">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="42ff9-118">XML Comment Tags</span></span>](index.md)
