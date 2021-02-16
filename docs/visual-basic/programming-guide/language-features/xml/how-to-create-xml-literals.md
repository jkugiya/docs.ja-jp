---
description: '詳細情報: 方法:XML リテラルを作成する (Visual Basic)'
title: '方法: XML リテラルを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 0e57b037d0567002fd570025e147771c4fab38f4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433292"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="b3ac1-103">方法: XML リテラルを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3ac1-103">How to: Create XML Literals (Visual Basic)</span></span>

<span data-ttu-id="b3ac1-104">XML リテラルを使用して、XML ドキュメント、フラグメント、または要素をコード内で直接作成できます。</span><span class="sxs-lookup"><span data-stu-id="b3ac1-104">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="b3ac1-105">このトピックの例では、3 つの子要素を持つ XML 要素を作成する方法と、XML ドキュメントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b3ac1-105">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="b3ac1-106">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API を使用して、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] オブジェクトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b3ac1-106">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="b3ac1-107">詳細については、「<xref:System.Xml.Linq.XElement>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3ac1-107">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="b3ac1-108">XML 要素を作成するには</span><span class="sxs-lookup"><span data-stu-id="b3ac1-108">To create an XML element</span></span>  
  
- <span data-ttu-id="b3ac1-109">XML リテラル構文を使用して XML インラインを作成します。これは、実際の XML 構文と同じです。</span><span class="sxs-lookup"><span data-stu-id="b3ac1-109">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="b3ac1-110">コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="b3ac1-110">Run the code.</span></span> <span data-ttu-id="b3ac1-111">このコードの出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b3ac1-111">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="b3ac1-112">XML ドキュメントを作成するには</span><span class="sxs-lookup"><span data-stu-id="b3ac1-112">To create an XML document</span></span>  
  
- <span data-ttu-id="b3ac1-113">XML ドキュメントをインラインで作成します。</span><span class="sxs-lookup"><span data-stu-id="b3ac1-113">Create the XML document inline.</span></span> <span data-ttu-id="b3ac1-114">次のコードでは、リテラル構文、XML 宣言、処理命令、コメント、および別の要素を含む要素を持つ XML ドキュメントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b3ac1-114">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="b3ac1-115">コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="b3ac1-115">Run the code.</span></span> <span data-ttu-id="b3ac1-116">このコードの出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b3ac1-116">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="b3ac1-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3ac1-117">See also</span></span>

- [<span data-ttu-id="b3ac1-118">XML</span><span class="sxs-lookup"><span data-stu-id="b3ac1-118">XML</span></span>](index.md)
- [<span data-ttu-id="b3ac1-119">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="b3ac1-119">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="b3ac1-120">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="b3ac1-120">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="b3ac1-121">XML ドキュメント リテラル</span><span class="sxs-lookup"><span data-stu-id="b3ac1-121">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
