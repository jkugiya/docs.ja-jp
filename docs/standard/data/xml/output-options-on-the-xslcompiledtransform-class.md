---
description: '詳細情報: XslCompiledTransform クラスの出力オプション'
title: XslCompiledTransform クラスの出力オプション
ms.date: 03/30/2017
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
ms.openlocfilehash: 8f16de929ba196eddb6ebb4b8b251668820b4d91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783301"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a><span data-ttu-id="f70fa-103">XslCompiledTransform クラスの出力オプション</span><span class="sxs-lookup"><span data-stu-id="f70fa-103">Output Options on the XslCompiledTransform Class</span></span>

<span data-ttu-id="f70fa-104">このトピックでは、XSLT で使用できる出力オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-104">This topic discusses the available XSLT output options.</span></span> <span data-ttu-id="f70fa-105">出力オプションは、スタイル シート内で、または <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドで指定できます。</span><span class="sxs-lookup"><span data-stu-id="f70fa-105">You can specify output options in the style sheet, or on the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="xsloutput-element"></a><span data-ttu-id="f70fa-106">xsl:output 要素</span><span class="sxs-lookup"><span data-stu-id="f70fa-106">xsl:output Element</span></span>  

 <span data-ttu-id="f70fa-107">`xsl:output` 要素は出力のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-107">The `xsl:output` element specifies options for the output.</span></span> <span data-ttu-id="f70fa-108"><xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドで指定する出力の種類により、`xsl:output` オプションの動作が決定されます。</span><span class="sxs-lookup"><span data-stu-id="f70fa-108">The output type specified by the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method determines the behavior of the `xsl:output` options.</span></span>  
  
 <span data-ttu-id="f70fa-109">次の表では、出力の種類がストリームか `xsl:output` の場合に <xref:System.IO.TextWriter> 要素で使用できる各属性の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-109">The following table describes the behavior for each of the attributes available on the `xsl:output` element when the output type is a stream or a <xref:System.IO.TextWriter>.</span></span>  
  
|<span data-ttu-id="f70fa-110">属性名</span><span class="sxs-lookup"><span data-stu-id="f70fa-110">Attribute name</span></span>|<span data-ttu-id="f70fa-111">動作</span><span class="sxs-lookup"><span data-stu-id="f70fa-111">Behavior</span></span>|  
|--------------------|--------------|  
|<span data-ttu-id="f70fa-112">メソッド</span><span class="sxs-lookup"><span data-stu-id="f70fa-112">method</span></span>|<span data-ttu-id="f70fa-113">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="f70fa-113">Supported.</span></span>|  
|<span data-ttu-id="f70fa-114">version</span><span class="sxs-lookup"><span data-stu-id="f70fa-114">version</span></span>|<span data-ttu-id="f70fa-115">無視されます。</span><span class="sxs-lookup"><span data-stu-id="f70fa-115">Ignored.</span></span> <span data-ttu-id="f70fa-116">バージョンは常に XML では 1.0、そして HTML では 4.0 です。</span><span class="sxs-lookup"><span data-stu-id="f70fa-116">The version is always 1.0 for XML and 4.0 for HTML.</span></span>|  
|<span data-ttu-id="f70fa-117">encoding</span><span class="sxs-lookup"><span data-stu-id="f70fa-117">encoding</span></span>|<span data-ttu-id="f70fa-118"><xref:System.IO.TextWriter> への出力時には無視されます。</span><span class="sxs-lookup"><span data-stu-id="f70fa-118">Ignored when outputting to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="f70fa-119"><xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> プロパティが代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f70fa-119">The <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> property is used instead.</span></span>|  
|<span data-ttu-id="f70fa-120">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="f70fa-120">omit-xml-declaration</span></span>|<span data-ttu-id="f70fa-121">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="f70fa-121">Supported.</span></span>|  
|<span data-ttu-id="f70fa-122">スタンドアロン</span><span class="sxs-lookup"><span data-stu-id="f70fa-122">standalone</span></span>|<span data-ttu-id="f70fa-123">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="f70fa-123">Supported.</span></span>|  
|<span data-ttu-id="f70fa-124">doctype-public</span><span class="sxs-lookup"><span data-stu-id="f70fa-124">doctype-public</span></span>|<span data-ttu-id="f70fa-125">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="f70fa-125">Supported.</span></span>|  
|<span data-ttu-id="f70fa-126">doctype-system</span><span class="sxs-lookup"><span data-stu-id="f70fa-126">doctype-system</span></span>|<span data-ttu-id="f70fa-127">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="f70fa-127">Supported.</span></span>|  
|<span data-ttu-id="f70fa-128">cdata-section-elements</span><span class="sxs-lookup"><span data-stu-id="f70fa-128">cdata-section-elements</span></span>|<span data-ttu-id="f70fa-129">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="f70fa-129">Supported.</span></span>|  
|<span data-ttu-id="f70fa-130">indent</span><span class="sxs-lookup"><span data-stu-id="f70fa-130">indent</span></span>|<span data-ttu-id="f70fa-131">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="f70fa-131">Supported.</span></span>|  
|<span data-ttu-id="f70fa-132">media-type</span><span class="sxs-lookup"><span data-stu-id="f70fa-132">media-type</span></span>|<span data-ttu-id="f70fa-133">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="f70fa-133">Supported.</span></span>|  
  
#### <a name="sending-output-to-an-xmlwriter"></a><span data-ttu-id="f70fa-134">XmlWriter への出力の送出</span><span class="sxs-lookup"><span data-stu-id="f70fa-134">Sending Output to an XmlWriter</span></span>  

 <span data-ttu-id="f70fa-135">スタイル シートで `xsl:output` 要素が使用され、出力の種類が <xref:System.Xml.XmlWriter> オブジェクトの場合は、<xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> オブジェクトを作成する際に <xref:System.Xml.XmlWriter> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-135">If your style sheet uses the `xsl:output` element and the output type is an <xref:System.Xml.XmlWriter> object, you should use the <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> property when you create the <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="f70fa-136"><xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> プロパティは、コンパイル済みスタイル シートの <xref:System.Xml.XmlWriterSettings> 要素から派生した情報を含む `xsl:output` オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-136">The <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> property returns an <xref:System.Xml.XmlWriterSettings> object that contains information derived from the `xsl:output` element of a compiled style sheet.</span></span> <span data-ttu-id="f70fa-137">この <xref:System.Xml.XmlWriterSettings> オブジェクトを <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> メソッドに渡して、正しい設定の <xref:System.Xml.XmlWriter> オブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="f70fa-137">This <xref:System.Xml.XmlWriterSettings> object can be passed to the <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> method to create an <xref:System.Xml.XmlWriter> object with the correct settings.</span></span>  
  
## <a name="output-types"></a><span data-ttu-id="f70fa-138">出力の種類</span><span class="sxs-lookup"><span data-stu-id="f70fa-138">Output Types</span></span>  

 <span data-ttu-id="f70fa-139">次の一覧では、<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> コマンドで使用できる出力の種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-139">The following list describes the output types available on the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> command.</span></span>  
  
#### <a name="xmlwriter"></a><span data-ttu-id="f70fa-140">XmlWriter</span><span class="sxs-lookup"><span data-stu-id="f70fa-140">XmlWriter</span></span>  

 <span data-ttu-id="f70fa-141"><xref:System.Xml.XmlWriter> クラスは XML ストリームまたはファイルを書き出します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-141">The <xref:System.Xml.XmlWriter> class writes out XML streams or files.</span></span> <span data-ttu-id="f70fa-142"><xref:System.Xml.XmlWriter> クラスを使用して、出力オプションも含め、<xref:System.Xml.XmlWriterSettings> オブジェクトでサポートする機能を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f70fa-142">You can specify the features to support on the <xref:System.Xml.XmlWriter> object, including output options, by using the <xref:System.Xml.XmlWriterSettings> class.</span></span> <span data-ttu-id="f70fa-143"><xref:System.Xml.XmlWriter> クラスは <xref:System.Xml> フレームワークの重要な一部分です。</span><span class="sxs-lookup"><span data-stu-id="f70fa-143">The <xref:System.Xml.XmlWriter> class is an integral part of the <xref:System.Xml> framework.</span></span> <span data-ttu-id="f70fa-144">出力結果を別の XML プロセスにパイプラインして送るには、この出力を使用します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-144">Use this output type to pipeline the output results into another XML process.</span></span>  
  
#### <a name="string"></a><span data-ttu-id="f70fa-145">String</span><span class="sxs-lookup"><span data-stu-id="f70fa-145">String</span></span>  

 <span data-ttu-id="f70fa-146">出力ファイルの URI を指定するには、この出力を使用します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-146">Use this output type to specify the URI of the output file.</span></span>  
  
#### <a name="stream"></a><span data-ttu-id="f70fa-147">ストリーム</span><span class="sxs-lookup"><span data-stu-id="f70fa-147">Stream</span></span>  

 <span data-ttu-id="f70fa-148">ストリームとは、ファイル、入出力デバイス、プロセス間通信のパイプ、または TCP/IP ソケットなどのバイト シーケンスを抽象化したものです。</span><span class="sxs-lookup"><span data-stu-id="f70fa-148">A stream is an abstraction of a sequence of bytes, such as a file, an input/output device, an inter-process communication pipe, or a TCP/IP socket.</span></span> <span data-ttu-id="f70fa-149"><xref:System.IO.Stream> クラスとその派生クラスは、これら各種の入出力にジェネリックな視点を提供し、プログラマがオペレーティング システムや下位のデバイスに固有の詳細を考慮する必要をなくします。</span><span class="sxs-lookup"><span data-stu-id="f70fa-149">The <xref:System.IO.Stream> class and its derived classes provide a generic view of these different types of input and output, isolating the programmer from the specific details of the operating system and the underlying devices.</span></span>  
  
 <span data-ttu-id="f70fa-150"><xref:System.IO.FileStream>、<xref:System.IO.MemoryStream>、または出力ストリーム (`Response.OutputStream`) にデータを送るには、この出力の種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-150">Use this output type to send data to a <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, or an output stream (`Response.OutputStream`).</span></span>  
  
#### <a name="textwriter"></a><span data-ttu-id="f70fa-151">TextWriter</span><span class="sxs-lookup"><span data-stu-id="f70fa-151">TextWriter</span></span>  

 <span data-ttu-id="f70fa-152"><xref:System.IO.TextWriter> は、文字シーケンスを書き出します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-152">The <xref:System.IO.TextWriter> writes sequential characters.</span></span> <span data-ttu-id="f70fa-153">これは <xref:System.IO.StringWriter> クラスおよび <xref:System.IO.StreamWriter> クラスに実装され、それぞれ文字を文字列に、またはストリームに書き出します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-153">It is implemented in the <xref:System.IO.StringWriter> and <xref:System.IO.StreamWriter> classes, which write characters to strings or streams, respectively.</span></span> <span data-ttu-id="f70fa-154">文字列に出力する場合は、この出力の種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="f70fa-154">Use this output type when you want to output to a string.</span></span>  
  
## <a name="notes"></a><span data-ttu-id="f70fa-155">メモ</span><span class="sxs-lookup"><span data-stu-id="f70fa-155">Notes</span></span>  
  
- <span data-ttu-id="f70fa-156">空要素タグを書き出すとき、要素名の最後の文字とバック主ラッシュとの間に 1 つのスペースが書かれます。たとえば `<myElement />` です。</span><span class="sxs-lookup"><span data-stu-id="f70fa-156">When writing out empty tags, a space is written between the last character of the element name and the backslash, `<myElement />` for example.</span></span> <span data-ttu-id="f70fa-157">これにより、生成された HTML ページが古いブラウザーで正しく表示されます。</span><span class="sxs-lookup"><span data-stu-id="f70fa-157">This lets older browsers display the generated HTML pages correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f70fa-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="f70fa-158">See also</span></span>

- [<span data-ttu-id="f70fa-159">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="f70fa-159">XSLT Transformations</span></span>](xslt-transformations.md)
