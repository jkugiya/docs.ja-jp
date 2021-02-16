---
description: '詳細情報: 方法:XML リテラルに式を埋め込む (Visual Basic)'
title: '方法: XML リテラルに式を埋め込む'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 18bc6164c4466532956f1a5df70c1ff2a8dbbfd5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480051"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="1a00c-103">方法: XML リテラルに式を埋め込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a00c-103">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>

<span data-ttu-id="1a00c-104">XML リテラルと埋め込み式を組み合わせて、実行時に作成される内容を含む XML ドキュメント、フラグメント、または要素を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1a00c-104">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="1a00c-105">次の例では、埋め込み式を使用して、実行時に要素の内容、属性、および要素名を設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1a00c-105">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="1a00c-106">埋め込み式の構文は `<%=` `exp` `%>` となります。これは ASP.NET で使用される構文と同じです。</span><span class="sxs-lookup"><span data-stu-id="1a00c-106">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span></span> <span data-ttu-id="1a00c-107">詳細については、「[XML での埋め込み式](embedded-expressions-in-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a00c-107">For more information, see [Embedded Expressions in XML](embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="1a00c-108">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API を使用して、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] オブジェクトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1a00c-108">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="1a00c-109">詳細については、「<xref:System.Xml.Linq.XElement>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a00c-109">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="1a00c-110">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="1a00c-110">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="1a00c-111">要素の内容としてテキストを挿入するには</span><span class="sxs-lookup"><span data-stu-id="1a00c-111">To insert text as element content</span></span>  
  
- <span data-ttu-id="1a00c-112">次の例は、名前の開始要素と終了要素の間に `contactName` 変数に含まれるテキストを挿入する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1a00c-112">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="1a00c-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1a00c-113">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="1a00c-114">属性値としてテキストを挿入するには</span><span class="sxs-lookup"><span data-stu-id="1a00c-114">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="1a00c-115">次の例は、`phoneType` 変数に含まれるテキストを `type` 属性の値として挿入する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1a00c-115">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="1a00c-116">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1a00c-116">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="1a00c-117">要素名のテキストを挿入するには</span><span class="sxs-lookup"><span data-stu-id="1a00c-117">To insert text for an element name</span></span>  
  
- <span data-ttu-id="1a00c-118">次の例は、`elementName` 変数に含まれるテキストを要素の名前として挿入する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1a00c-118">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="1a00c-119">この手法を使用して要素を作成する場合は、\</> タグで終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a00c-119">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="1a00c-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1a00c-120">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1a00c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a00c-121">See also</span></span>

- [<span data-ttu-id="1a00c-122">方法: XML リテラルを作成する</span><span class="sxs-lookup"><span data-stu-id="1a00c-122">How to: Create XML Literals</span></span>](how-to-create-xml-literals.md)
- [<span data-ttu-id="1a00c-123">XML での埋め込み式</span><span class="sxs-lookup"><span data-stu-id="1a00c-123">Embedded Expressions in XML</span></span>](embedded-expressions-in-xml.md)
- [<span data-ttu-id="1a00c-124">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="1a00c-124">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="1a00c-125">XML</span><span class="sxs-lookup"><span data-stu-id="1a00c-125">XML</span></span>](index.md)
