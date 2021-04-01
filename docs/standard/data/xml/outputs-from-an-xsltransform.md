---
description: '詳細情報: XslTransform からの出力'
title: XslTransform からの出力
ms.date: 03/30/2017
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 103334274daafc7de2e7cadab7191bc5b90a34d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783275"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="9e415-103">XslTransform からの出力</span><span class="sxs-lookup"><span data-stu-id="9e415-103">Outputs from an XslTransform</span></span>

<span data-ttu-id="9e415-104">スタイル シートは、`<xsl:output>` ステートメントと `method` 属性を使って出力形式を決定できます。次の表では、<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを使用して出力を書き出し、出力形式を <xref:System.IO.Stream> または <xref:System.IO.TextWriter> として宣言した場合に出力形式がどうなるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="9e415-104">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e415-105">.NET Framework 2.0 では <xref:System.Xml.Xsl.XslTransform> クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="9e415-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="9e415-106"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="9e415-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="9e415-107">詳しくは、「[XslCompiledTransform クラスの使用](using-the-xslcompiledtransform-class.md)」および「[XslTransform クラスからの移行](migrating-from-the-xsltransform-class.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9e415-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="9e415-108">スタイル シートは、`<xsl:output>` ステートメントと `method` 属性を使って出力形式を決定できます。次の表では、<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを使用して出力を書き出し、出力形式を <xref:System.IO.Stream> または <xref:System.IO.TextWriter> として宣言した場合に出力形式がどうなるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="9e415-108">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="9e415-109"><xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを `<xsl:output>` ステートメントと共に使用して出力の種類を宣言した場合に得られる結果を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="9e415-109">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="9e415-110">\<xsl:output method = > 属性</span><span class="sxs-lookup"><span data-stu-id="9e415-110">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="9e415-111">結果の形式</span><span class="sxs-lookup"><span data-stu-id="9e415-111">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="9e415-112">method="xml"</span><span class="sxs-lookup"><span data-stu-id="9e415-112">method="xml"</span></span>|<span data-ttu-id="9e415-113">XML</span><span class="sxs-lookup"><span data-stu-id="9e415-113">XML</span></span>|  
|<span data-ttu-id="9e415-114">method="html"</span><span class="sxs-lookup"><span data-stu-id="9e415-114">method="html"</span></span>|<span data-ttu-id="9e415-115">HTML</span><span class="sxs-lookup"><span data-stu-id="9e415-115">HTML</span></span>|  
|<span data-ttu-id="9e415-116">method="text"</span><span class="sxs-lookup"><span data-stu-id="9e415-116">method="text"</span></span>|<span data-ttu-id="9e415-117">テキスト</span><span class="sxs-lookup"><span data-stu-id="9e415-117">Text</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="9e415-118">メモ:<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドの出力が <xref:System.Xml.XmlReader> または <xref:System.Xml.XmlWriter> である場合、`<xsl:output>` ステートメントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="9e415-118">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="9e415-119"><xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドの出力が <xref:System.IO.Stream> または <xref:System.IO.TextWriter> である場合は、次の属性がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9e415-119">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="9e415-120">encoding\*</span><span class="sxs-lookup"><span data-stu-id="9e415-120">encoding\*</span></span>  
  
- <span data-ttu-id="9e415-121">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="9e415-121">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="9e415-122">スタンドアロン</span><span class="sxs-lookup"><span data-stu-id="9e415-122">standalone</span></span>  
  
- <span data-ttu-id="9e415-123">doctype-public</span><span class="sxs-lookup"><span data-stu-id="9e415-123">doctype-public</span></span>  
  
- <span data-ttu-id="9e415-124">doctype-system</span><span class="sxs-lookup"><span data-stu-id="9e415-124">doctype-system</span></span>  
  
- <span data-ttu-id="9e415-125">cdata-section-elements</span><span class="sxs-lookup"><span data-stu-id="9e415-125">cdata-section-elements</span></span>  
  
- <span data-ttu-id="9e415-126">indent</span><span class="sxs-lookup"><span data-stu-id="9e415-126">indent</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9e415-127">\*<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドがその出力を <xref:System.IO.TextWriter> に送信する場合、encoding 属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="9e415-127">\*The encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="9e415-128">その場合は、encoding 属性の代わりに <xref:System.IO.TextWriter> の encoding プロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9e415-128">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>
  
 <span data-ttu-id="9e415-129"><xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドの出力が <xref:System.IO.Stream> の場合、次の属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="9e415-129">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="9e415-130">version : バージョンは常に 1.0 です。</span><span class="sxs-lookup"><span data-stu-id="9e415-130">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="9e415-131">media-type : メディア タイプです。</span><span class="sxs-lookup"><span data-stu-id="9e415-131">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="9e415-132">特殊文字のエスケープ</span><span class="sxs-lookup"><span data-stu-id="9e415-132">Escaping Special Characters</span></span>  

 <span data-ttu-id="9e415-133">`<xsl:text disable-output-escaping>` 記号の代わりに `<&lt>` を使用するなど、特殊文字を XML 形式にエスケープする必要があるかどうかを示すには、`"<"` タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="9e415-133">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="9e415-134">`disable-output-escaping` オブジェクトまたは <xref:System.Xml.XmlReader> オブジェクトへの変換では <xref:System.Xml.XmlWriter> 属性が無視されるため、特殊文字はこのタグの影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="9e415-134">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e415-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e415-135">See also</span></span>

- [<span data-ttu-id="9e415-136">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="9e415-136">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
