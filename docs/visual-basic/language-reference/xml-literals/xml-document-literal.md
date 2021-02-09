---
description: '詳細情報: XML ドキュメント リテラル (Visual Basic)'
title: XML ドキュメント リテラル
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: d268f205c9357598a631216879b424dd8155268a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700313"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="f5eae-103">XML ドキュメント リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5eae-103">XML Document Literal (Visual Basic)</span></span>

<span data-ttu-id="f5eae-104"><xref:System.Xml.Linq.XDocument> オブジェクトを表すリテラル。</span><span class="sxs-lookup"><span data-stu-id="f5eae-104">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5eae-105">構文</span><span class="sxs-lookup"><span data-stu-id="f5eae-105">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="f5eae-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="f5eae-106">Parts</span></span>  
  
|<span data-ttu-id="f5eae-107">用語</span><span class="sxs-lookup"><span data-stu-id="f5eae-107">Term</span></span>|<span data-ttu-id="f5eae-108">定義</span><span class="sxs-lookup"><span data-stu-id="f5eae-108">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="f5eae-109">任意。</span><span class="sxs-lookup"><span data-stu-id="f5eae-109">Optional.</span></span> <span data-ttu-id="f5eae-110">ドキュメントが使用するエンコードを宣言するリテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="f5eae-110">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="f5eae-111">任意。</span><span class="sxs-lookup"><span data-stu-id="f5eae-111">Optional.</span></span> <span data-ttu-id="f5eae-112">リテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="f5eae-112">Literal text.</span></span> <span data-ttu-id="f5eae-113">"yes" または "no" にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5eae-113">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="f5eae-114">任意。</span><span class="sxs-lookup"><span data-stu-id="f5eae-114">Optional.</span></span> <span data-ttu-id="f5eae-115">XML 処理命令と XML コメントのリスト。</span><span class="sxs-lookup"><span data-stu-id="f5eae-115">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="f5eae-116">次の形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="f5eae-116">Takes the following format:</span></span><br /><br /> <span data-ttu-id="f5eae-117">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="f5eae-117">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="f5eae-118">各 `piComment` に次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f5eae-118">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="f5eae-119">-   [XML 処理命令リテラル](xml-processing-instruction-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="f5eae-119">-   [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="f5eae-120">-   [XML コメント リテラル](xml-comment-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="f5eae-120">-   [XML Comment Literal](xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="f5eae-121">必須です。</span><span class="sxs-lookup"><span data-stu-id="f5eae-121">Required.</span></span> <span data-ttu-id="f5eae-122">ドキュメントのルート要素。</span><span class="sxs-lookup"><span data-stu-id="f5eae-122">Root element of the document.</span></span> <span data-ttu-id="f5eae-123">形式は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="f5eae-123">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="f5eae-124">[XML 要素リテラル](xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="f5eae-124">[XML Element Literal](xml-element-literal.md).</span></span></li><li><span data-ttu-id="f5eae-125">`<%=` `elementExp` `%>` 形式の埋め込み式。</span><span class="sxs-lookup"><span data-stu-id="f5eae-125">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="f5eae-126">`elementExp` は次のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="f5eae-126">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="f5eae-127"><xref:System.Xml.Linq.XElement> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f5eae-127">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="f5eae-128">1 つの <xref:System.Xml.Linq.XElement> オブジェクトと、任意の数の <xref:System.Xml.Linq.XProcessingInstruction> および <xref:System.Xml.Linq.XComment> オブジェクトを含むコレクション。</span><span class="sxs-lookup"><span data-stu-id="f5eae-128">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="f5eae-129">詳細については、「[XML での埋め込み式](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5eae-129">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="f5eae-130">戻り値</span><span class="sxs-lookup"><span data-stu-id="f5eae-130">Return Value</span></span>  

 <span data-ttu-id="f5eae-131"><xref:System.Xml.Linq.XDocument> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f5eae-131">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5eae-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="f5eae-132">Remarks</span></span>  

 <span data-ttu-id="f5eae-133">リテラルの先頭にある XML 宣言によって、XML ドキュメント リテラルが特定されます。</span><span class="sxs-lookup"><span data-stu-id="f5eae-133">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="f5eae-134">各 XML ドキュメント リテラルにルート XML 要素が 1 つ必要ですが、XML 処理命令と XML コメントは任意の数を挿入できます。</span><span class="sxs-lookup"><span data-stu-id="f5eae-134">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="f5eae-135">XML ドキュメント リテラルは、XML 要素には記述できません。</span><span class="sxs-lookup"><span data-stu-id="f5eae-135">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5eae-136">XML リテラルは、行連結文字を使用せずに、複数行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="f5eae-136">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="f5eae-137">これにより、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="f5eae-137">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="f5eae-138">XML ドキュメント リテラルは、Visual Basic コンパイラによって、<xref:System.Xml.Linq.XDocument.%23ctor%2A> コンストラクターおよび <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> コンストラクターへの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="f5eae-138">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5eae-139">例</span><span class="sxs-lookup"><span data-stu-id="f5eae-139">Example</span></span>  

 <span data-ttu-id="f5eae-140">次の例で作成する XML ドキュメントには、XML 宣言、処理命令、コメント、および別の要素を含む要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f5eae-140">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="f5eae-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5eae-141">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="f5eae-142">XML 処理命令リテラル</span><span class="sxs-lookup"><span data-stu-id="f5eae-142">XML Processing Instruction Literal</span></span>](xml-processing-instruction-literal.md)
- [<span data-ttu-id="f5eae-143">XML コメント リテラル</span><span class="sxs-lookup"><span data-stu-id="f5eae-143">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="f5eae-144">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="f5eae-144">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="f5eae-145">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="f5eae-145">XML Literals</span></span>](index.md)
- [<span data-ttu-id="f5eae-146">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="f5eae-146">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="f5eae-147">XML での埋め込み式</span><span class="sxs-lookup"><span data-stu-id="f5eae-147">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
