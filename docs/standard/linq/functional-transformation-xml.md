---
title: XML の関数型変換 - LINQ to XML
description: XML ドキュメントを変更するための純粋関数型変換の方法と、手続き型の方法との違いについて学習します。
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: b23288e013a4104b21523e17e1f266a9f712c451
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412182"
---
# <a name="functional-transformation-of-xml-linq-to-xml"></a><span data-ttu-id="72a74-103">XML の関数型変換 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="72a74-103">Functional transformation of XML (LINQ to XML)</span></span>

<span data-ttu-id="72a74-104">この記事では、XML ドキュメントを変更するための純粋関数型変換の方法について説明し、手続き型の方法と比較します。</span><span class="sxs-lookup"><span data-stu-id="72a74-104">This article discusses the pure functional transformation approach to modifying XML documents, and contrasts it with a procedural approach.</span></span>

## <a name="modifying-an-xml-document"></a><span data-ttu-id="72a74-105">XML ドキュメントの変更</span><span class="sxs-lookup"><span data-stu-id="72a74-105">Modifying an XML document</span></span>

<span data-ttu-id="72a74-106">XML プログラマにとって最も一般的なタスクの 1 つが、XML の形式の変換です。</span><span class="sxs-lookup"><span data-stu-id="72a74-106">One of the most common tasks for an XML programmer is transforming XML from one shape to another.</span></span> <span data-ttu-id="72a74-107">XML ドキュメントの形式とはドキュメントの構造のことで、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="72a74-107">The shape of an XML document is the structure of the document, which includes the following:</span></span>

- <span data-ttu-id="72a74-108">ドキュメントによって表される階層。</span><span class="sxs-lookup"><span data-stu-id="72a74-108">The hierarchy expressed by the document.</span></span>
- <span data-ttu-id="72a74-109">要素名および属性名。</span><span class="sxs-lookup"><span data-stu-id="72a74-109">The element and attribute names.</span></span>
- <span data-ttu-id="72a74-110">要素と属性のデータ型。</span><span class="sxs-lookup"><span data-stu-id="72a74-110">The data types of the elements and attributes.</span></span>

<span data-ttu-id="72a74-111">一般に、XML の形式を変換するために最も効果的なのは、純粋関数型変換の方法です。</span><span class="sxs-lookup"><span data-stu-id="72a74-111">In general, the most effective approach to transforming XML from one shape to another is that of pure functional transformation.</span></span> <span data-ttu-id="72a74-112">この方法におけるプログラマの主なタスクは、XML ドキュメント全体 (または 1 つ以上の厳密に定義されたノード) に適用する変換を作成することです。</span><span class="sxs-lookup"><span data-stu-id="72a74-112">In this approach, the primary programmer task is to create a transformation which is applied to the entire XML document (or to one or more strictly defined nodes).</span></span> <span data-ttu-id="72a74-113">関数型変換は、(プログラマがこの方法をいったん理解すれば) コードの記述が最も簡単で、最も保守しやすいコードが得られ、多くの場合、その他の方法よりもコンパクトです。</span><span class="sxs-lookup"><span data-stu-id="72a74-113">Functional transformation is arguably the easiest to code (after a programmer is familiar with the approach), yields the most maintainable code, and is often more compact than alternative approaches.</span></span>

### <a name="xml-functional-transformational-technologies"></a><span data-ttu-id="72a74-114">XML の関数型変換のテクノロジ</span><span class="sxs-lookup"><span data-stu-id="72a74-114">XML functional transformational technologies</span></span>

<span data-ttu-id="72a74-115">Microsoft では、XML ドキュメントで使用する関数型変換のテクノロジを 2 つ用意しています。XSLT と LINQ to XML です。</span><span class="sxs-lookup"><span data-stu-id="72a74-115">Microsoft offers two functional transformation technologies for use on XML documents: XSLT and LINQ to XML.</span></span> <span data-ttu-id="72a74-116">XSLT は、<xref:System.Xml.Xsl> マネージド名前空間と、MSXML のネイティブな COM 実装でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="72a74-116">XSLT is supported in the <xref:System.Xml.Xsl> managed namespace and in the native COM implementation of MSXML.</span></span> <span data-ttu-id="72a74-117">XSLT は XML ドキュメントを操作するための堅牢なテクノロジですが、XSLT 言語とそれに対応する API に関する専門知識を必要とします。</span><span class="sxs-lookup"><span data-stu-id="72a74-117">Although XSLT is a robust technology for manipulating XML documents, it requires expertise in a specialized domain, namely the XSLT language and its supporting APIs.</span></span>

<span data-ttu-id="72a74-118">LINQ to XML には、純粋関数型変換のコードを C# または Visual Basic のコード内にさまざまな表現で効果的に記述できるツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="72a74-118">LINQ to XML provides the tools necessary to code pure functional transformations in an expressive and powerful way, within C# or Visual Basic code.</span></span> <span data-ttu-id="72a74-119">たとえば、LINQ to XML のドキュメントに記載されている多くの例で、純粋関数型の方法が使用されています。</span><span class="sxs-lookup"><span data-stu-id="72a74-119">For example, many of the examples in the LINQ to XML documentation use a pure functional approach.</span></span> <span data-ttu-id="72a74-120">また、[チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作](xml-shape-wordprocessingml-documents.md)に関するチュートリアルでは、Microsoft Word 文書の情報を操作するために、LINQ to XML を関数型の方法も使用されています。</span><span class="sxs-lookup"><span data-stu-id="72a74-120">Also, in the [Tutorial: Manipulating Content in a WordprocessingML Document](xml-shape-wordprocessingml-documents.md) tutorial, we use LINQ to XML in a functional approach to manipulate information in a Microsoft Word document.</span></span>

<span data-ttu-id="72a74-121">LINQ to XML とその他の Microsoft XML テクノロジのより完全な比較については、「[LINQ to XML とその他の XML テクノロジ](linq-xml-vs-xml-technologies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72a74-121">For a more complete comparison of LINQ to XML with other Microsoft XML technologies, see [LINQ to XML vs. other XML technologies](linq-xml-vs-xml-technologies.md).</span></span>

<span data-ttu-id="72a74-122">ソース ドキュメントの構造が標準的でない場合、ドキュメント中心の変換には XSLT を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="72a74-122">XSLT is the recommended tool for  document-centric transformations when the source document has an irregular structure.</span></span> <span data-ttu-id="72a74-123">ただし、LINQ to XML でもドキュメント中心の変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="72a74-123">However, LINQ to XML can also perform document-centric transforms.</span></span> <span data-ttu-id="72a74-124">詳細については、[注釈を使用して XSLT スタイルの LINQ to XML ツリーを変換する方法](use-annotations-transform-linq-xml-trees-xslt-style.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="72a74-124">For more information, see [How to use annotations to transform LINQ to XML trees in an XSLT style](use-annotations-transform-linq-xml-trees-xslt-style.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="72a74-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="72a74-125">See also</span></span>

- [<span data-ttu-id="72a74-126">純粋関数型変換の概要</span><span class="sxs-lookup"><span data-stu-id="72a74-126">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)
- [<span data-ttu-id="72a74-127">チュートリアル: WordprocessingML ドキュメント内のコンテンツを操作する</span><span class="sxs-lookup"><span data-stu-id="72a74-127">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
- [<span data-ttu-id="72a74-128">LINQ to XML とその他の XML テクノロジ</span><span class="sxs-lookup"><span data-stu-id="72a74-128">LINQ to XML vs. other XML technologies</span></span>](linq-xml-vs-xml-technologies.md)
