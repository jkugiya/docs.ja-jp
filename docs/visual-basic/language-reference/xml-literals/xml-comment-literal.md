---
description: '詳細情報: XML コメント リテラル (Visual Basic)'
title: XML コメント リテラル
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: f44d2e132236d74d312910921fabb3a85afd82d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768741"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="2fcfb-103">XML コメント リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fcfb-103">XML Comment Literal (Visual Basic)</span></span>

<span data-ttu-id="2fcfb-104"><xref:System.Xml.Linq.XComment> オブジェクトを表すリテラル。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-104">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fcfb-105">構文</span><span class="sxs-lookup"><span data-stu-id="2fcfb-105">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="2fcfb-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="2fcfb-106">Parts</span></span>  
  
|<span data-ttu-id="2fcfb-107">用語</span><span class="sxs-lookup"><span data-stu-id="2fcfb-107">Term</span></span>|<span data-ttu-id="2fcfb-108">定義</span><span class="sxs-lookup"><span data-stu-id="2fcfb-108">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="2fcfb-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-109">Required.</span></span> <span data-ttu-id="2fcfb-110">XML コメントの先頭を表します。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-110">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="2fcfb-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-111">Required.</span></span> <span data-ttu-id="2fcfb-112">XML コメントに表示されるテキスト。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-112">Text to appear in the XML comment.</span></span> <span data-ttu-id="2fcfb-113">連続する 2 つのハイフン (--) を含めたり、終了タグに隣接するハイフンを末尾に使用したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-113">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="2fcfb-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-114">Required.</span></span> <span data-ttu-id="2fcfb-115">XML コメントの末尾を表します。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-115">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="2fcfb-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="2fcfb-116">Return Value</span></span>  

 <span data-ttu-id="2fcfb-117"><xref:System.Xml.Linq.XComment> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-117">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fcfb-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="2fcfb-118">Remarks</span></span>  

 <span data-ttu-id="2fcfb-119">XML コメント リテラルにはドキュメントのコンテンツではなく、ドキュメントに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-119">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="2fcfb-120">XML コメント セクションの末尾には "-->" シーケンスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-120">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="2fcfb-121">これは以下を意味します。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-121">This implies the following points:</span></span>  
  
- <span data-ttu-id="2fcfb-122">埋め込み式の区切り記号は有効な XML コメント コンテンツであるため、XML コメント リテラルでは埋め込み式を使用できません。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-122">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="2fcfb-123">`content` には値 "-->" を含めることができないため、XML コメント セクションを入れ子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-123">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="2fcfb-124">XML コメント リテラルは、変数に代入するか、XML 要素リテラルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-124">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fcfb-125">XML リテラルは、行連結文字を使用せずに、複数行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-125">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="2fcfb-126">この機能を使用すると、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-126">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="2fcfb-127">XML コメント リテラルは、Visual Basic コンパイラによって、<xref:System.Xml.Linq.XComment.%23ctor%2A> コンストラクターへの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-127">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fcfb-128">例</span><span class="sxs-lookup"><span data-stu-id="2fcfb-128">Example</span></span>  

 <span data-ttu-id="2fcfb-129">次の例では、"This is a comment" というテキストを含む XML コメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2fcfb-129">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="2fcfb-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="2fcfb-130">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="2fcfb-131">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="2fcfb-131">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="2fcfb-132">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="2fcfb-132">XML Literals</span></span>](index.md)
- [<span data-ttu-id="2fcfb-133">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="2fcfb-133">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
