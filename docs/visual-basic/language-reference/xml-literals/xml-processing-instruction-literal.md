---
description: '詳細情報: XML 処理命令リテラル (Visual Basic)'
title: XML 処理命令リテラル
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 5037aab343cbe50ebc48614991e96da8198a481f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787527"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="bf71e-103">XML 処理命令リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf71e-103">XML Processing Instruction Literal (Visual Basic)</span></span>

<span data-ttu-id="bf71e-104"><xref:System.Xml.Linq.XProcessingInstruction> オブジェクトを表すリテラル。</span><span class="sxs-lookup"><span data-stu-id="bf71e-104">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf71e-105">構文</span><span class="sxs-lookup"><span data-stu-id="bf71e-105">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="bf71e-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="bf71e-106">Parts</span></span>  

 `<?`  
 <span data-ttu-id="bf71e-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="bf71e-107">Required.</span></span> <span data-ttu-id="bf71e-108">XML 処理命令リテラルの先頭を表します。</span><span class="sxs-lookup"><span data-stu-id="bf71e-108">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="bf71e-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="bf71e-109">Required.</span></span> <span data-ttu-id="bf71e-110">処理命令の対象となるアプリケーションを示す名前。</span><span class="sxs-lookup"><span data-stu-id="bf71e-110">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="bf71e-111">"xml" または "XML" では開始できません。</span><span class="sxs-lookup"><span data-stu-id="bf71e-111">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="bf71e-112">任意。</span><span class="sxs-lookup"><span data-stu-id="bf71e-112">Optional.</span></span> <span data-ttu-id="bf71e-113">`piName` の対象となるアプリケーションが XML ドキュメントを処理する方法を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="bf71e-113">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="bf71e-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="bf71e-114">Required.</span></span> <span data-ttu-id="bf71e-115">処理命令の末尾を表します。</span><span class="sxs-lookup"><span data-stu-id="bf71e-115">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf71e-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="bf71e-116">Return Value</span></span>  

 <span data-ttu-id="bf71e-117"><xref:System.Xml.Linq.XProcessingInstruction> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bf71e-117">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf71e-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="bf71e-118">Remarks</span></span>  

 <span data-ttu-id="bf71e-119">XML 処理命令リテラルは、アプリケーションが XML ドキュメントを処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bf71e-119">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="bf71e-120">アプリケーションは XML ドキュメントを読み込むとき、XML 処理命令を確認して、そのドキュメントの処理方法を判断します。</span><span class="sxs-lookup"><span data-stu-id="bf71e-120">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="bf71e-121">アプリケーションによって解釈されるのは、`piName` と `piData` の意味です。</span><span class="sxs-lookup"><span data-stu-id="bf71e-121">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="bf71e-122">XML ドキュメント リテラルでは、XML 処理命令と似た構文が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf71e-122">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="bf71e-123">詳細については、「[XML ドキュメント リテラル](xml-document-literal.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf71e-123">For more information, see [XML Document Literal](xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf71e-124">`piName` 要素の先頭に "xml" または "XML" 文字列を使用することはできません。これらの識別子は、XML 1.0 仕様で予約されているためです。</span><span class="sxs-lookup"><span data-stu-id="bf71e-124">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="bf71e-125">XML 処理命令リテラルは、変数に代入するか、XML ドキュメント リテラルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bf71e-125">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf71e-126">XML リテラルは、行連結文字なしで複数行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="bf71e-126">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="bf71e-127">これにより、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="bf71e-127">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="bf71e-128">XML 処理命令リテラルは、Visual Basic コンパイラによって、<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> コンストラクターへの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="bf71e-128">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf71e-129">例</span><span class="sxs-lookup"><span data-stu-id="bf71e-129">Example</span></span>  

 <span data-ttu-id="bf71e-130">次の例では、XML ドキュメントのスタイルシートを特定する処理命令を作成します。</span><span class="sxs-lookup"><span data-stu-id="bf71e-130">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="bf71e-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf71e-131">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="bf71e-132">XML ドキュメント リテラル</span><span class="sxs-lookup"><span data-stu-id="bf71e-132">XML Document Literal</span></span>](xml-document-literal.md)
- [<span data-ttu-id="bf71e-133">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="bf71e-133">XML Literals</span></span>](index.md)
- [<span data-ttu-id="bf71e-134">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="bf71e-134">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
