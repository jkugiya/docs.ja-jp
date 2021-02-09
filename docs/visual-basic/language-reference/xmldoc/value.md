---
description: 詳細については、以下をご覧ください。 <value> (Visual Basic)
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 80a3ef875eea4418d28d60dac1818f3390c361ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640252"
---
# <a name="value-visual-basic"></a><span data-ttu-id="b2340-103">\<value> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2340-103">\<value> (Visual Basic)</span></span>

<span data-ttu-id="b2340-104">プロパティの説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="b2340-104">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2340-105">構文</span><span class="sxs-lookup"><span data-stu-id="b2340-105">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2340-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b2340-106">Parameters</span></span>  

 `property-description`  
 <span data-ttu-id="b2340-107">プロパティの説明。</span><span class="sxs-lookup"><span data-stu-id="b2340-107">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2340-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="b2340-108">Remarks</span></span>  

 <span data-ttu-id="b2340-109">`<value>` タグを使用して、プロパティを記述します。</span><span class="sxs-lookup"><span data-stu-id="b2340-109">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="b2340-110">Visual Studio 開発環境では、コード ウィザードを使用してプロパティを追加するときに、新しいプロパティの [\<summary>](summary.md) タグが追加されることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="b2340-110">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](summary.md) tag for the new property.</span></span> <span data-ttu-id="b2340-111">その後、手動で `<value>` タグを追加してプロパティが表す値を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2340-111">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="b2340-112">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="b2340-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2340-113">例</span><span class="sxs-lookup"><span data-stu-id="b2340-113">Example</span></span>  

 <span data-ttu-id="b2340-114">この例では、`<value>` タグを使用して、`Counter` プロパティに保持されている値を記述します。</span><span class="sxs-lookup"><span data-stu-id="b2340-114">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b2340-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2340-115">See also</span></span>

- [<span data-ttu-id="b2340-116">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="b2340-116">XML Comment Tags</span></span>](index.md)
