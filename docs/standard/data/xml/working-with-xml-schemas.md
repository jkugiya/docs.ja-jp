---
description: '詳細情報: XML スキーマの使用'
title: XML スキーマの使用
ms.date: 03/30/2017
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
ms.openlocfilehash: 41a6aaaa375ffd74bbde2c05bd6e06f1696ffcfe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782807"
---
# <a name="working-with-xml-schemas"></a><span data-ttu-id="594f9-103">XML スキーマの使用</span><span class="sxs-lookup"><span data-stu-id="594f9-103">Working with XML Schemas</span></span>

<span data-ttu-id="594f9-104">XML ドキュメントの構造、その要素間のリレーションシップ、データ型、および内容の制約を定義するには、ドキュメント型定義 (DTD: Document Type Definition) または XML スキーマ定義言語 (XSD) スキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="594f9-104">To define the structure of an XML document, as well as its element relationships, data types, and content constraints, you use a document type definition (DTD) or XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="594f9-105">XML ドキュメントは、W3C (World Wide Web Consortium) 勧告『Extensible Markup Language (XML) 1.0』で定義されている構文要件をすべて満たしている場合には整形式と見なされますが、整形式であると同時に DTD またはスキーマに定義されている制約に準拠していなければ有効とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="594f9-105">Although an XML document is considered to be well-formed if it meets all the syntactical requirements defined by the World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0 Recommendation, it is not considered valid unless it is both well-formed and conforms to the constraints defined by its DTD or schema.</span></span> <span data-ttu-id="594f9-106">したがって、有効な XML ドキュメントはすべて整形式ですが、整形式の XML ドキュメントがすべて有効であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="594f9-106">Therefore, although all valid XML documents are well-formed, not all well-formed XML documents are valid.</span></span>  
  
 <span data-ttu-id="594f9-107">XML の詳細については、[W3C 勧告『XML 1.0』](https://www.w3.org/TR/REC-xml/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="594f9-107">For more information about XML, see the [W3C XML 1.0 Recommendation](https://www.w3.org/TR/REC-xml/).</span></span> <span data-ttu-id="594f9-108">XML スキーマの詳細については、[W3C 勧告『XML Schema Part 1: Structures』](https://www.w3.org/TR/xmlschema-1/)および[『XML Schema Part 2: Datatypes』](https://www.w3.org/TR/xmlschema-2/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="594f9-108">For more information about XML Schema, see the [W3C XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/) and the [W3C XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="594f9-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="594f9-109">In This Section</span></span>  

 [<span data-ttu-id="594f9-110">XML スキーマ オブジェクト モデル (SOM)</span><span class="sxs-lookup"><span data-stu-id="594f9-110">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)  
 <span data-ttu-id="594f9-111"><xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間のスキーマ オブジェクト モデル (SOM) について説明します。SOM は、ファイルからスキーマ定義言語 (XSD) スキーマを読み取ったり、プログラムを使用してメモリ内にスキーマを作成したりできる一連のクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="594f9-111">Discusses the Schema Object Model (SOM) in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that provides a set of classes that allows you to read a Schema definition language (XSD) schema from a file or programmatically create a schema in-memory.</span></span>  
  
 [<span data-ttu-id="594f9-112">スキーマをコンパイルするための XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="594f9-112">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)  
 <span data-ttu-id="594f9-113"><xref:System.Xml.Schema.XmlSchemaSet> クラスについて説明します。このクラスは、XSD スキーマを格納または検証できるキャッシュです。</span><span class="sxs-lookup"><span data-stu-id="594f9-113">Discusses the <xref:System.Xml.Schema.XmlSchemaSet> class that is a cache where XSD schemas can be stored and validated.</span></span>  
  
 [<span data-ttu-id="594f9-114">XmlSchemaValidator のプッシュ ベースの検証</span><span class="sxs-lookup"><span data-stu-id="594f9-114">XmlSchemaValidator Push-Based Validation</span></span>](xmlschemavalidator-push-based-validation.md)  
 <span data-ttu-id="594f9-115"><xref:System.Xml.Schema.XmlSchemaValidator> クラスについて説明します。このクラスは、プッシュ ベース方式で、XSD スキーマを基準として XML データを検証する、効率的かつ高性能なしくみを提供します。</span><span class="sxs-lookup"><span data-stu-id="594f9-115">Discusses the <xref:System.Xml.Schema.XmlSchemaValidator> class that provides an efficient, high-performance mechanism to validate XML data against XSD schemas in a push-based manner.</span></span>  
  
 [<span data-ttu-id="594f9-116">XML スキーマの推論</span><span class="sxs-lookup"><span data-stu-id="594f9-116">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)  
 <span data-ttu-id="594f9-117"><xref:System.Xml.Schema.XmlSchemaInference> クラスを使用して XML ドキュメントの構造から XSD スキーマを推論する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="594f9-117">Discusses how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XSD schema from the structure of an XML document.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="594f9-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="594f9-118">Reference</span></span>  

 <span data-ttu-id="594f9-119"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="594f9-119"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="594f9-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="594f9-120">Related Sections</span></span>  

 [<span data-ttu-id="594f9-121">DOM における XML ドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="594f9-121">Validating an XML Document in the DOM</span></span>](validating-an-xml-document-in-the-dom.md)  
 <span data-ttu-id="594f9-122">ドキュメント オブジェクト モデル (DOM) の XML を検証する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="594f9-122">Discusses how to validate the XML in the Document Object Model (DOM).</span></span> <span data-ttu-id="594f9-123">検証できる XML は、DOM に読み込まれている XML か、または事前に検証されていない DOM の XML ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="594f9-123">You can validate the XML as it is loaded into the DOM, or validate a previously unvalidated XML document in the DOM.</span></span>  
  
 [<span data-ttu-id="594f9-124">XPathNavigator を使用したスキーマ検証</span><span class="sxs-lookup"><span data-stu-id="594f9-124">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="594f9-125"><xref:System.Xml.XPath.XPathNavigator> クラスを使用して操作中および編集中の XML を検証する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="594f9-125">Discusses how to validate XML being navigated and edited using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
