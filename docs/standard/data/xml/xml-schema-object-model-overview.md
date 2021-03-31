---
description: '詳細情報: XML スキーマ オブジェクト モデルの概要'
title: XML スキーマ オブジェクト モデルの概要
ms.date: 03/30/2017
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
ms.openlocfilehash: 7c780cf2a1b23c39b8c1051dbebcbb9d96fec22d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782729"
---
# <a name="xml-schema-object-model-overview"></a><span data-ttu-id="f30f8-103">XML スキーマ オブジェクト モデルの概要</span><span class="sxs-lookup"><span data-stu-id="f30f8-103">XML Schema Object Model Overview</span></span>

<span data-ttu-id="f30f8-104">Microsoft .NET Framework のスキーマ オブジェクト モデル (SOM) は豊富な機能を備えた API で、スキーマの作成、編集、および検証をプログラムで実行できます。</span><span class="sxs-lookup"><span data-stu-id="f30f8-104">The Schema Object Model (SOM) in the Microsoft .NET Framework is a rich API that allows you to create, edit, and validate schemas programmatically.</span></span> <span data-ttu-id="f30f8-105">SOM は、ドキュメント オブジェクト モデル (DOM) が XML ドキュメント上で機能するのと同様に、XML スキーマ ドキュメント上で機能します。</span><span class="sxs-lookup"><span data-stu-id="f30f8-105">The SOM operates on XML schema documents similarly to the way the Document Object Model (DOM) operates on XML documents.</span></span> <span data-ttu-id="f30f8-106">XML スキーマ ドキュメントは有効な XML ファイルで、SOM に読み込まれると、スキーマに準拠した他の XML ドキュメントの構造および有効性に関する情報を伝えます。</span><span class="sxs-lookup"><span data-stu-id="f30f8-106">XML schema documents are valid XML files that, once loaded into the SOM, convey meaning about the structure and validity of other XML documents which conform to the schema.</span></span>  
  
 <span data-ttu-id="f30f8-107">スキーマは、特定のスキーマに対して XML ドキュメントの構造またはモデルを指定することによって XML ドキュメントのクラスを定義する、XML ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="f30f8-107">A schema is an XML document that defines a class of XML documents by specifying the structure or model of XML documents for a particular schema.</span></span> <span data-ttu-id="f30f8-108">スキーマは、XML ドキュメントの内容に対する制約を指定し、特定のスキーマと照合して有効と見なされるように、規定に準拠した XML ドキュメントが従う表現形式 (規則または文法) を記述します。</span><span class="sxs-lookup"><span data-stu-id="f30f8-108">A schema identifies the constraints on the content of the XML documents, and describes the vocabulary (rules or grammar) that compliant XML documents must follow in order to be considered schema-valid with that particular schema.</span></span> <span data-ttu-id="f30f8-109">XML ドキュメントの検証は、ドキュメントがスキーマによって指定された文法に準拠しているかどうかを確認するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="f30f8-109">Validation of an XML document is the process that ensures that the document conforms to the grammar specified by the schema.</span></span>  
  
 <span data-ttu-id="f30f8-110">.NET Framework の SOM API を使用すると、スキーマの作成、編集、および検証に関する次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f30f8-110">The following are ways the SOM API in the .NET Framework enables you to create, edit, and validate schemas.</span></span>  
  
- <span data-ttu-id="f30f8-111">有効なスキーマをファイルから読み込み、ファイルへ保存します。</span><span class="sxs-lookup"><span data-stu-id="f30f8-111">Load and save valid schemas to and from files.</span></span>  
  
- <span data-ttu-id="f30f8-112">厳密に型指定されたクラスを使用し、メモリ内にスキーマを作成します。</span><span class="sxs-lookup"><span data-stu-id="f30f8-112">Create in-memory schemas using strongly typed classes.</span></span>  
  
- <span data-ttu-id="f30f8-113"><xref:System.Xml.Schema.XmlSchemaSet> クラスと対話し、スキーマのキャッシュ、コンパイル、および取得を行います。</span><span class="sxs-lookup"><span data-stu-id="f30f8-113">Interact with the <xref:System.Xml.Schema.XmlSchemaSet> class to cache, compile, and retrieve schemas.</span></span>  
  
- <span data-ttu-id="f30f8-114"><xref:System.Xml.XmlReader.Create%2A> クラスの <xref:System.Xml.XmlReader> メソッドと対話し、スキーマを基準として XML インスタンス ドキュメントを検証します。</span><span class="sxs-lookup"><span data-stu-id="f30f8-114">Interact with the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to validate XML instance documents against schemas.</span></span>  
  
- <span data-ttu-id="f30f8-115">スキーマの作成および保守に使用するエディターを作成します。</span><span class="sxs-lookup"><span data-stu-id="f30f8-115">Build editors for creating and maintaining schemas.</span></span>  
  
- <span data-ttu-id="f30f8-116">XML インスタンス ドキュメントの検証で使用するためにコンパイルと保存が可能なスキーマを動的に編集します。</span><span class="sxs-lookup"><span data-stu-id="f30f8-116">Dynamically edit a schema that can be complied and saved for use in the validation of XML instance documents.</span></span>  
  
## <a name="the-schema-object-model"></a><span data-ttu-id="f30f8-117">スキーマ オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="f30f8-117">The Schema Object Model</span></span>  

 <span data-ttu-id="f30f8-118">SOM は、XML スキーマの要素に相当する <xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間の広範囲にわたるクラスで構成されています。</span><span class="sxs-lookup"><span data-stu-id="f30f8-118">The SOM consists of an extensive set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace corresponding to the elements in an XML schema.</span></span> <span data-ttu-id="f30f8-119">たとえば、`<xsd:schema>...</xsd:schema>` 要素は <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> クラスにマップしているため、`<xsd:schema/>` 要素に格納できる情報はすべて <xref:System.Xml.Schema.XmlSchema> クラスを使って表すことができます。</span><span class="sxs-lookup"><span data-stu-id="f30f8-119">For example, the `<xsd:schema>...</xsd:schema>` element maps to the <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> class, and all the information that can be contained within an `<xsd:schema/>` element can be represented using the <xref:System.Xml.Schema.XmlSchema> class.</span></span> <span data-ttu-id="f30f8-120">同様に、`<xsd:element>...</xsd:element>` 要素と `<xsd:attribute>...</xsd:attribute>` 要素は、それぞれ <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> クラスと <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> クラスにマップしています。</span><span class="sxs-lookup"><span data-stu-id="f30f8-120">Similarly, the `<xsd:element>...</xsd:element>` and `<xsd:attribute>...</xsd:attribute>` elements map to the <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> and <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> classes respectively.</span></span> <span data-ttu-id="f30f8-121">このマッピングは、次の図に示す <xref:System.Xml.Schema> 名前空間の XML スキーマ オブジェクト モデルを作成する XML スキーマのすべての要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="f30f8-121">This mapping continues for all the elements of an XML schema creating an XML schema object model in the <xref:System.Xml.Schema> namespace illustrated in the diagram that follows.</span></span>  
  
 ![System.Xml.Schema オブジェクト モデル](./media/xml-schema-object-model-overview/xml-schema-object-model.gif)  
  
 <span data-ttu-id="f30f8-123"><xref:System.Xml.Schema> 名前空間の各クラスの詳細については、.NET Framework クラス ライブラリの <xref:System.Xml.Schema> 名前空間のリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f30f8-123">For more information about each class in the <xref:System.Xml.Schema> namespace, see the <xref:System.Xml.Schema> namespace reference documentation in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f30f8-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f30f8-124">See also</span></span>

- [<span data-ttu-id="f30f8-125">XML スキーマの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="f30f8-125">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="f30f8-126">XML スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="f30f8-126">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="f30f8-127">XML スキーマの走査</span><span class="sxs-lookup"><span data-stu-id="f30f8-127">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="f30f8-128">XML スキーマの編集</span><span class="sxs-lookup"><span data-stu-id="f30f8-128">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="f30f8-129">XML スキーマのインクルードまたはインポート</span><span class="sxs-lookup"><span data-stu-id="f30f8-129">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="f30f8-130">スキーマをコンパイルするための XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="f30f8-130">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="f30f8-131">スキーマのコンパイル後の情報セット</span><span class="sxs-lookup"><span data-stu-id="f30f8-131">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
