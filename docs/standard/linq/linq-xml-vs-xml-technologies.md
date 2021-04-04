---
title: LINQ to XML とその他の XML テクノロジ
description: より良いテクノロジを選択できるようにするため、LINQ to XML を XSLT、MSXML、および XmlLite と比較する方法について説明します。
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: ac118543bd1101e50edfcf99a609a715b885bfbd
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412046"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a><span data-ttu-id="d2c38-103">LINQ to XML とその他の XML テクノロジ</span><span class="sxs-lookup"><span data-stu-id="d2c38-103">LINQ to XML vs. other XML technologies</span></span>

<span data-ttu-id="d2c38-104">この記事では、LINQ to XML を他の XML テクノロジ (<xref:System.Xml.XmlReader>、XSLT、MSXML、および XmlLite) と比較します。</span><span class="sxs-lookup"><span data-stu-id="d2c38-104">This article compares LINQ to XML to the following XML technologies: <xref:System.Xml.XmlReader>, XSLT, MSXML, and XmlLite.</span></span> <span data-ttu-id="d2c38-105">この情報は、使用するテクノロジを決定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-105">This information can help you decide which technologies to use.</span></span>

<span data-ttu-id="d2c38-106">LINQ to XML とドキュメント オブジェクト モデル (DOM) の比較については、「[LINQ to XML とDOM](linq-xml-vs-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2c38-106">For a comparison of LINQ to XML to the Document Object Model (DOM), see [LINQ to XML vs. DOM](linq-xml-vs-dom.md).</span></span>

## <a name="linq-to-xml-vs-xmlreader"></a><span data-ttu-id="d2c38-107">LINQ to XML およびXmlReader</span><span class="sxs-lookup"><span data-stu-id="d2c38-107">LINQ to XML vs. XmlReader</span></span>

<span data-ttu-id="d2c38-108"><xref:System.Xml.XmlReader> は、高速、前方参照専用、非キャッシュのパーサーです。</span><span class="sxs-lookup"><span data-stu-id="d2c38-108"><xref:System.Xml.XmlReader> is a fast, forward-only, non-caching parser.</span></span>

<span data-ttu-id="d2c38-109">LINQ to XML は <xref:System.Xml.XmlReader> の上位に実装され、緊密に統合されています。</span><span class="sxs-lookup"><span data-stu-id="d2c38-109">LINQ to XML is implemented on top of <xref:System.Xml.XmlReader>, and they're tightly integrated.</span></span> <span data-ttu-id="d2c38-110">ただし、<xref:System.Xml.XmlReader> を直接使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-110">However, you can also use <xref:System.Xml.XmlReader> directly.</span></span>

<span data-ttu-id="d2c38-111">たとえば、1 秒間に何百もの XML ドキュメントを解析する Web サービスを構築する際に、これらのドキュメントの構造が同じであるため、XML を解析するために実装するコードの作成が 1 つだけで済む場合は、</span><span class="sxs-lookup"><span data-stu-id="d2c38-111">For example, suppose you're building a Web service that will parse hundreds of XML documents per second, and the documents have the same structure, meaning that you only have to write one implementation of the code to parse the XML.</span></span> <span data-ttu-id="d2c38-112"><xref:System.Xml.XmlReader> を直接使用することが考えられます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-112">In this case, you'd probably want to use <xref:System.Xml.XmlReader> directly.</span></span>

<span data-ttu-id="d2c38-113">一方、多数の小さい XML ドキュメントを解析するシステムを構築する際に、ドキュメントがそれぞれ異なる場合は、生産性の向上という観点から LINQ to XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2c38-113">In contrast, if you're building a system that parses many smaller XML documents, and each one is different, you'd want to take advantage of the productivity improvements that LINQ to XML provides.</span></span>

## <a name="linq-to-xml-vs-xslt"></a><span data-ttu-id="d2c38-114">LINQ to XML およびXSLT</span><span class="sxs-lookup"><span data-stu-id="d2c38-114">LINQ to XML vs. XSLT</span></span>

<span data-ttu-id="d2c38-115">LINQ to XML と XSLT は、どちらも広範な XML ドキュメント変換機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="d2c38-115">Both LINQ to XML and XSLT provide extensive XML document transformation capabilities.</span></span> <span data-ttu-id="d2c38-116">XSLT は、ルール ベースの宣言型の方法です。</span><span class="sxs-lookup"><span data-stu-id="d2c38-116">XSLT is a rule-based, declarative approach.</span></span> <span data-ttu-id="d2c38-117">高度な XSLT プログラミングでは、ステートレスな方法が重視される関数型のプログラミング スタイルで XSLT を記述します。</span><span class="sxs-lookup"><span data-stu-id="d2c38-117">Advanced XSLT programmers write XSLT in a functional programming style that emphasizes a stateless approach.</span></span> <span data-ttu-id="d2c38-118">変換は、副作用なしで実装される純粋関数を使用して記述できます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-118">Transformations can be written using pure functions that are implemented without side effects.</span></span> <span data-ttu-id="d2c38-119">このルール ベース (関数型) の方法に精通している開発者は多くありません。また、修得するのは難しく、相当の学習時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d2c38-119">This rule-based or functional approach is unfamiliar to many developers, and can be difficult and time-consuming to learn.</span></span>

<span data-ttu-id="d2c38-120">XSLT は、パフォーマンスの高いアプリケーションを生成する、生産性の高いシステムとして利用できます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-120">XSLT can be a productive system that yields high-performance applications.</span></span> <span data-ttu-id="d2c38-121">たとえば、Web 関連の大企業の中には、さまざまな種類のデータ ソースを基に取得した XML から HTML を生成するための手段として XSLT を使用している企業もあります。</span><span class="sxs-lookup"><span data-stu-id="d2c38-121">For example, some large Web companies use XSLT as a way to generate HTML from XML that has been pulled from different kinds of data stores.</span></span> <span data-ttu-id="d2c38-122">XSLT を共通言語ランタイム (CLR) コードにコンパイルするマネージド XSLT エンジンは、一部のシナリオではネイティブ XSLT エンジンより高いパフォーマンスを発揮します。</span><span class="sxs-lookup"><span data-stu-id="d2c38-122">The managed XSLT engine compiles XSLT to common language runtime (CLR) code, and performs even better in some scenarios than the native XSLT engine.</span></span>

<span data-ttu-id="d2c38-123">ただし、XSLT では、多くの開発者が持っている C# や Visual Basic の知識は活かされません。</span><span class="sxs-lookup"><span data-stu-id="d2c38-123">However, XSLT doesn't take advantage of the C# and Visual Basic knowledge that many developers have.</span></span> <span data-ttu-id="d2c38-124">開発者は、別の複雑なプログラミング言語でコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2c38-124">It requires developers to write code in a different and complex programming language.</span></span> <span data-ttu-id="d2c38-125">C# (または Visual Basic) と XSLT など、統合されていない 2 つの開発システムを使用すると、ソフトウェア システムの開発や保守が困難になります。</span><span class="sxs-lookup"><span data-stu-id="d2c38-125">Using two non-integrated development systems such as C# (or Visual Basic) and XSLT results in software systems that are more difficult to develop and maintain.</span></span>

<span data-ttu-id="d2c38-126">LINQ to XML クエリ式を習得すると、LINQ to XML 変換は使いやすい強力なテクノロジになります。</span><span class="sxs-lookup"><span data-stu-id="d2c38-126">After you've mastered LINQ to XML query expressions, LINQ to XML transformations are a powerful technology that's easy to use.</span></span> <span data-ttu-id="d2c38-127">基本的には、関数型構築を使用して、さまざまなソースからデータを取り込んで <xref:System.Xml.Linq.XElement> オブジェクトを動的に構築し、全体をまとめて新しい XML ツリーを作成することによって XML ドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="d2c38-127">Basically, you form your XML document by using functional construction, pulling in data from various sources, constructing <xref:System.Xml.Linq.XElement> objects dynamically, and assembling the whole into a new XML tree.</span></span> <span data-ttu-id="d2c38-128">変換では、まったく新しいドキュメントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-128">The transformation can generate a completely new document.</span></span> <span data-ttu-id="d2c38-129">LINQ to XML を使用すると、変換を比較的簡単かつ直感的に構築でき、結果のコードも読みやすいものになります。</span><span class="sxs-lookup"><span data-stu-id="d2c38-129">Constructing transformations in LINQ to XML is relatively easy and intuitive, and the resulting code is readable.</span></span> <span data-ttu-id="d2c38-130">このため、開発と保守のコストを削減できます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-130">This reduces development and maintenance costs.</span></span>

<span data-ttu-id="d2c38-131">LINQ to XML は、XSLT に置き換わることを目的としていません。</span><span class="sxs-lookup"><span data-stu-id="d2c38-131">LINQ to XML isn't intended to replace XSLT.</span></span> <span data-ttu-id="d2c38-132">複雑なドキュメント中心の XML 変換 (特に、ドキュメントの構造が明確に定義されていない場合) では、引き続き XSLT が最適なツールになります。</span><span class="sxs-lookup"><span data-stu-id="d2c38-132">XSLT is still the tool of choice for complicated and document-centric XML transformations, especially if the structure of the document isn't well defined.</span></span>

<span data-ttu-id="d2c38-133">XSLT には、W3C (World Wide Web Consortium) 標準という利点があります。</span><span class="sxs-lookup"><span data-stu-id="d2c38-133">XSLT has the advantage of being a World Wide Web Consortium (W3C) standard.</span></span> <span data-ttu-id="d2c38-134">標準となっている技術を使用するだけで十分な場合は、XSLT の方が適切といえます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-134">If you have a requirement that you use only technologies that are standards, XSLT might be more appropriate.</span></span>

<span data-ttu-id="d2c38-135">XSLT は XML であるため、プログラムで操作できます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-135">XSLT is XML, and that's why it can be programmatically manipulated.</span></span>

## <a name="linq-to-xml-vs-msxml"></a><span data-ttu-id="d2c38-136">LINQ to XML およびMSXML</span><span class="sxs-lookup"><span data-stu-id="d2c38-136">LINQ to XML vs. MSXML</span></span>

<span data-ttu-id="d2c38-137">MSXML は、Microsoft Windows に付属する、XML 処理のための COM ベース テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="d2c38-137">MSXML is the COM-based technology for processing XML that's included with Microsoft Windows.</span></span> <span data-ttu-id="d2c38-138">MSXML は DOM をネイティブで実装し、XPath と XSLT をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d2c38-138">MSXML provides a native implementation of the DOM with support for XPath and XSLT.</span></span> <span data-ttu-id="d2c38-139">MSXML には、非キャッシュの SAX2 イベントベース パーサーも含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2c38-139">It also contains the SAX2 non-caching, event-based parser.</span></span>

<span data-ttu-id="d2c38-140">MSXML はパフォーマンスが高く、セキュリティもほとんどのシナリオで既定で確保されます。また、Internet Explorer でアクセスできるため、AJAX スタイルのアプリケーションでクライアント側での XML の処理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-140">MSXML performs well, is secure by default in most scenarios, and can be accessed in Internet Explorer for doing client-side XML processing in AJAX-style applications.</span></span> <span data-ttu-id="d2c38-141">MSXML は、C++、JavaScript、Visual Basic 6.0 など、COM をサポートするすべてのプログラミング言語から使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-141">MSXML can be used from any programming language that supports COM, including C++, JavaScript, and Visual Basic 6.0.</span></span>

<span data-ttu-id="d2c38-142">MSXML を CLR に基づくマネージド コードで使用することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="d2c38-142">MSXML isn't recommended for use in managed code based on the CLR.</span></span>

## <a name="linq-to-xml-vs-xmllite"></a><span data-ttu-id="d2c38-143">LINQ to XML およびXmlLite</span><span class="sxs-lookup"><span data-stu-id="d2c38-143">LINQ to XML vs. XmlLite</span></span>

<span data-ttu-id="d2c38-144">XmlLite は、非キャッシュ、前方参照専用のプル パーサーで、</span><span class="sxs-lookup"><span data-stu-id="d2c38-144">XmlLite is a non-caching, forward only, pull parser.</span></span> <span data-ttu-id="d2c38-145">主に C++ で使用されます。</span><span class="sxs-lookup"><span data-stu-id="d2c38-145">Developers primarily use XmlLite with C++.</span></span> <span data-ttu-id="d2c38-146">マネージド コードで XmlLite を使用することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="d2c38-146">It's not recommended for developers to use XmlLite with managed code.</span></span>

<span data-ttu-id="d2c38-147">XmlLite の最大の利点は、ほとんどのシナリオで、軽量かつ高速で安全な XML パーサーとして利用できることです。</span><span class="sxs-lookup"><span data-stu-id="d2c38-147">The main advantage of XmlLite is that it's a lightweight, fast XML parser that's secure in most scenarios.</span></span> <span data-ttu-id="d2c38-148">脅威の対象となる要素がほとんどないため、</span><span class="sxs-lookup"><span data-stu-id="d2c38-148">Its threat surface area is small.</span></span> <span data-ttu-id="d2c38-149">信頼されていないドキュメントを解析し、サービス拒否攻撃やデータ漏洩攻撃などからの保護が必要な場合は、優れた方法となります。</span><span class="sxs-lookup"><span data-stu-id="d2c38-149">If you have to parse untrusted documents and you want to protect against attacks such as denial of service or exposure of data, XmlLite might be a good option.</span></span>

<span data-ttu-id="d2c38-150">XmlLite は、統合言語クエリ (LINQ) と統合されていません。</span><span class="sxs-lookup"><span data-stu-id="d2c38-150">XmlLite isn't integrated with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="d2c38-151">LINQ の利用動機となるプログラミングの生産性の向上はもたらされません。</span><span class="sxs-lookup"><span data-stu-id="d2c38-151">It doesn't yield the programmer productivity improvements that are the motivating force behind LINQ.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2c38-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2c38-152">See also</span></span>

- [<span data-ttu-id="d2c38-153">LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="d2c38-153">LINQ to XML overview</span></span>](linq-xml-overview.md)