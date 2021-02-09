---
description: 詳細については、以下をご覧ください。 <example> (Visual Basic)
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 643e06fd24e38123dd2693d671b9ab33da5b413e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787488"
---
# <a name="example-visual-basic"></a><span data-ttu-id="de794-103">\<example> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de794-103">\<example> (Visual Basic)</span></span>

<span data-ttu-id="de794-104">メンバーの例を指定します。</span><span class="sxs-lookup"><span data-stu-id="de794-104">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de794-105">構文</span><span class="sxs-lookup"><span data-stu-id="de794-105">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="de794-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de794-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="de794-107">コード例の説明です。</span><span class="sxs-lookup"><span data-stu-id="de794-107">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de794-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="de794-108">Remarks</span></span>  

 <span data-ttu-id="de794-109">`<example>` タグを使用すると、メソッドまたは他のライブラリ メンバーの使用例を指定できます。</span><span class="sxs-lookup"><span data-stu-id="de794-109">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="de794-110">一般的に、[\<code>](code.md) タグが使用されます。</span><span class="sxs-lookup"><span data-stu-id="de794-110">This commonly involves using the [\<code>](code.md) tag.</span></span>  
  
 <span data-ttu-id="de794-111">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="de794-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de794-112">例</span><span class="sxs-lookup"><span data-stu-id="de794-112">Example</span></span>  

 <span data-ttu-id="de794-113">この例では、`<example>` タグを使用して、`ID` フィールドを使用する例を組み込みます。</span><span class="sxs-lookup"><span data-stu-id="de794-113">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="de794-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="de794-114">See also</span></span>

- [<span data-ttu-id="de794-115">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="de794-115">XML Comment Tags</span></span>](index.md)
