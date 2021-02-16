---
description: '詳細情報: 方法:XML 子要素にアクセスする (Visual Basic)'
title: '方法: XML 子要素にアクセスする'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: fad4d45853006762bc319b0ff8f9143ef13058da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433240"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="8e11c-103">方法: XML 子要素にアクセスする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e11c-103">How to: Access XML Child Elements (Visual Basic)</span></span>

<span data-ttu-id="8e11c-104">この例では、子軸プロパティを使用して、XML 要素内で指定した名前を持つすべての XML 子要素にアクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8e11c-104">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="8e11c-105">特に、<xref:System.Xml.Linq.XElement.Value%2A> プロパティを使用して、`name` 子軸プロパティによって返されるコレクション内の最初の要素の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="8e11c-105">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="8e11c-106">子軸プロパティ `name` では、`contact` オブジェクト内の `phone` という名前のすべての子要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="8e11c-106">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="8e11c-107">また、この例では、`phone` 子軸プロパティを使用して、`contact` オブジェクトに含まれている `phone` という名前のすべての子要素にアクセスしています。</span><span class="sxs-lookup"><span data-stu-id="8e11c-107">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e11c-108">例</span><span class="sxs-lookup"><span data-stu-id="8e11c-108">Example</span></span>  

 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="8e11c-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="8e11c-109">Compile the code</span></span>  

 <span data-ttu-id="8e11c-110">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8e11c-110">This example requires:</span></span>  
  
- <span data-ttu-id="8e11c-111"><xref:System.Xml.Linq> 名前空間への参照</span><span class="sxs-lookup"><span data-stu-id="8e11c-111">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e11c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e11c-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8e11c-113">XML 子軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="8e11c-113">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="8e11c-114">XML Value プロパティ</span><span class="sxs-lookup"><span data-stu-id="8e11c-114">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="8e11c-115">Visual Basic での XML へのアクセス</span><span class="sxs-lookup"><span data-stu-id="8e11c-115">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="8e11c-116">XML</span><span class="sxs-lookup"><span data-stu-id="8e11c-116">XML</span></span>](index.md)
