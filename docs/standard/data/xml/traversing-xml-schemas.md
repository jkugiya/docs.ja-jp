---
description: '詳細情報: XML スキーマの走査'
title: XML スキーマの走査
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
ms.openlocfilehash: d860235fb8d4414a465a931438701ace5ed1e08c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782911"
---
# <a name="traversing-xml-schemas"></a><span data-ttu-id="a2a54-103">XML スキーマの走査</span><span class="sxs-lookup"><span data-stu-id="a2a54-103">Traversing XML Schemas</span></span>

<span data-ttu-id="a2a54-104">スキーマ オブジェクト モデル (SOM) API を使用して XML スキーマを走査すると、SOM に格納されている要素、属性、および型にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a2a54-104">Traversing an XML schema using the Schema Object Model (SOM) API provides access to the elements, attributes, and types stored in the SOM.</span></span> <span data-ttu-id="a2a54-105">また、SOM API を使用して XML スキーマを編集する際には、最初に SOM に読み込まれた XML スキーマを走査します。</span><span class="sxs-lookup"><span data-stu-id="a2a54-105">Traversing an XML schema loaded into the SOM is also the first step in editing an XML schema using the SOM API.</span></span>

## <a name="traversing-an-xml-schema"></a><span data-ttu-id="a2a54-106">XML スキーマの走査</span><span class="sxs-lookup"><span data-stu-id="a2a54-106">Traversing an XML Schema</span></span>

<span data-ttu-id="a2a54-107"><xref:System.Xml.Schema.XmlSchema> クラスの次のプロパティを使用すると、XML スキーマに追加されたすべてのグローバル要素のコレクションにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a2a54-107">The following properties of the <xref:System.Xml.Schema.XmlSchema> class provide access to the collection of all global items added to the XML schema.</span></span>

|<span data-ttu-id="a2a54-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a2a54-108">Property</span></span>|<span data-ttu-id="a2a54-109">コレクションまたは配列に格納されているオブジェクトの型</span><span class="sxs-lookup"><span data-stu-id="a2a54-109">Object type stored in the collection or array</span></span>|
|--------------|---------------------------------------------------|
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<span data-ttu-id="a2a54-110"><xref:System.Xml.Schema.XmlSchemaExternal>、<xref:System.Xml.Schema.XmlSchemaInclude>、<xref:System.Xml.Schema.XmlSchemaImport>、または <xref:System.Xml.Schema.XmlSchemaRedefine></span><span class="sxs-lookup"><span data-stu-id="a2a54-110"><xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport>, or <xref:System.Xml.Schema.XmlSchemaRedefine></span></span>|
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<span data-ttu-id="a2a54-111"><xref:System.Xml.Schema.XmlSchemaObject> (グローバル レベルのすべての要素、属性、および型にアクセスできる)</span><span class="sxs-lookup"><span data-stu-id="a2a54-111"><xref:System.Xml.Schema.XmlSchemaObject> (provides access to all global level elements, attributes, and types).</span></span>|
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<span data-ttu-id="a2a54-112"><xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType></span><span class="sxs-lookup"><span data-stu-id="a2a54-112"><xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType></span></span>|
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<span data-ttu-id="a2a54-113"><xref:System.Xml.XmlAttribute> (スキーマの名前空間に属さない属性にアクセスできる)</span><span class="sxs-lookup"><span data-stu-id="a2a54-113"><xref:System.Xml.XmlAttribute> (provides access to attributes that do not belong to the schema namespace)</span></span>|

> [!NOTE]
> <span data-ttu-id="a2a54-114">上記の表に記載されているすべてのプロパティ (<xref:System.Xml.Schema.XmlSchema.Items%2A> プロパティを除く) は、スキーマのコンパイル後の情報セット (PSCI) プロパティで、スキーマがコンパイルされるまで使用できません。</span><span class="sxs-lookup"><span data-stu-id="a2a54-114">All of the properties listed in the table above, except for the <xref:System.Xml.Schema.XmlSchema.Items%2A> property, are Post-Schema-Compilation-Infoset (PSCI) properties that are not available until the schema has been compiled.</span></span> <span data-ttu-id="a2a54-115"><xref:System.Xml.Schema.XmlSchema.Items%2A> プロパティは、スキーマのコンパイル前のプロパティで、スキーマがコンパイルされる前に使用できます。このプロパティを使用すると、グローバル レベルのすべての要素、属性、および型にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a2a54-115">The <xref:System.Xml.Schema.XmlSchema.Items%2A> property is a pre-schema-compilation property that can be used before the schema has been compiled to access and edit all global level elements, attributes, and types.</span></span>
>
> <span data-ttu-id="a2a54-116"><xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> プロパティを使用すると、スキーマの名前空間に属さないすべての属性にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a2a54-116">The <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> property provides access to all the attributes that do not belong to the schema namespace.</span></span> <span data-ttu-id="a2a54-117">これらの属性はスキーマ プロセッサで処理されません。</span><span class="sxs-lookup"><span data-stu-id="a2a54-117">These attributes are not processed by the schema processor.</span></span>

<span data-ttu-id="a2a54-118">以下のコード サンプルでは、「[XML スキーマの作成](building-xml-schemas.md)」トピックで作成されたカスタム スキーマの走査の例を示します。</span><span class="sxs-lookup"><span data-stu-id="a2a54-118">The code example that follows demonstrates traversing the customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span> <span data-ttu-id="a2a54-119">このコード サンプルは、上記のコレクションを使用してスキーマを走査し、スキーマのすべての要素と属性をコンソールに出力する例を示します。</span><span class="sxs-lookup"><span data-stu-id="a2a54-119">The code example demonstrates traversing the schema using the collections described above and writes all the elements and attributes in the schema to the console.</span></span>

<span data-ttu-id="a2a54-120">このサンプルでは、次の手順でカスタム スキーマの走査を行います。</span><span class="sxs-lookup"><span data-stu-id="a2a54-120">The sample traverses the customer schema in the following steps.</span></span>

1. <span data-ttu-id="a2a54-121">カスタム スキーマを新しい <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトに追加し、コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="a2a54-121">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="a2a54-122">スキーマの読み取りまたはコンパイル時に発生するスキーマ検証に関する警告とエラーは、<xref:System.Xml.Schema.ValidationEventHandler> デリゲートで処理されます。</span><span class="sxs-lookup"><span data-stu-id="a2a54-122">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="a2a54-123"><xref:System.Xml.Schema.XmlSchema> プロパティを反復処理して、<xref:System.Xml.Schema.XmlSchemaSet> からコンパイルされた <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="a2a54-123">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="a2a54-124">スキーマはコンパイルされているため、スキーマのコンパイル後の情報セット (PSCI) プロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a2a54-124">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="a2a54-125">各要素の名前をコンソールに出力するスキーマ コンパイル後の <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> コレクションの <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> コレクションで、各 <xref:System.Xml.Schema.XmlSchemaElement> を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="a2a54-125">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection writing the name of each element to the console.</span></span>

4. <span data-ttu-id="a2a54-126">`Customer` クラスを使用して <xref:System.Xml.Schema.XmlSchemaComplexType> 要素の複合型を取得します。</span><span class="sxs-lookup"><span data-stu-id="a2a54-126">Gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>

5. <span data-ttu-id="a2a54-127">複合型に何らかの属性がある場合、それぞれの <xref:System.Collections.IDictionaryEnumerator> を列挙する <xref:System.Xml.Schema.XmlSchemaAttribute> を取得して、その名前をコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="a2a54-127">If the complex type has any attributes, gets an <xref:System.Collections.IDictionaryEnumerator> to enumerate over each <xref:System.Xml.Schema.XmlSchemaAttribute> and writes its name to the console.</span></span>

6. <span data-ttu-id="a2a54-128"><xref:System.Xml.Schema.XmlSchemaSequence> クラスを使用して、複合型の sequence のパーティクルを取得します。</span><span class="sxs-lookup"><span data-stu-id="a2a54-128">Gets the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

7. <span data-ttu-id="a2a54-129">各子要素の名前をコンソールに出力する <xref:System.Xml.Schema.XmlSchemaElement> コレクション内で、それぞれの <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="a2a54-129">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection writing the name of each child element to the console.</span></span>

<span data-ttu-id="a2a54-130">完全なコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a2a54-130">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
[!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
[!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]

<span data-ttu-id="a2a54-131"><xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> プロパティには、<xref:System.Xml.Schema.XmlSchemaSimpleType> (ユーザー定義の単純型または複合型の場合は <xref:System.Xml.Schema.XmlSchemaComplexType>) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a2a54-131">The <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> property can be <xref:System.Xml.Schema.XmlSchemaSimpleType>, or <xref:System.Xml.Schema.XmlSchemaComplexType> if it is a user-defined simple type or a complex type.</span></span> <span data-ttu-id="a2a54-132">また、W3C 勧告『XML Schema』で定義されている組み込みデータ型の場合には、<xref:System.Xml.Schema.XmlSchemaDatatype> を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a2a54-132">It can also be <xref:System.Xml.Schema.XmlSchemaDatatype> if it is one of the built-in datatypes defined in the W3C XML Schema Recommendation.</span></span> <span data-ttu-id="a2a54-133">カスタム スキーマの場合、<xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> 要素の `Customer` は <xref:System.Xml.Schema.XmlSchemaComplexType> で、`FirstName` 要素および `LastName` 要素は <xref:System.Xml.Schema.XmlSchemaSimpleType> です。</span><span class="sxs-lookup"><span data-stu-id="a2a54-133">In the customer schema, the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> of the `Customer` element is <xref:System.Xml.Schema.XmlSchemaComplexType>, and the `FirstName` and `LastName` elements are <xref:System.Xml.Schema.XmlSchemaSimpleType>.</span></span>

<span data-ttu-id="a2a54-134">「[XML スキーマの作成](building-xml-schemas.md)」のコード サンプルでは、<xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> コレクションを使用して、`Customer` 要素に属性 `CustomerId` を追加しました。</span><span class="sxs-lookup"><span data-stu-id="a2a54-134">The code example in the [Building XML Schemas](building-xml-schemas.md) topic used the <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> collection to add the attribute `CustomerId` to the `Customer` element.</span></span> <span data-ttu-id="a2a54-135">これは、スキーマのコンパイル前のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="a2a54-135">This is a pre-schema-compilation property.</span></span> <span data-ttu-id="a2a54-136">対応するスキーマのコンパイル後の情報セット プロパティは、<xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> コレクションで、複合型のすべての属性 (型の派生を通じて継承される属性を含む) を持っています。</span><span class="sxs-lookup"><span data-stu-id="a2a54-136">The corresponding Post-Schema-Compilation-Infoset property is the <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> collection, which holds all the attributes of the complex type, including the ones that are inherited through type derivation.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2a54-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2a54-137">See also</span></span>

- [<span data-ttu-id="a2a54-138">XML スキーマ オブジェクト モデルの概要</span><span class="sxs-lookup"><span data-stu-id="a2a54-138">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="a2a54-139">XML スキーマの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="a2a54-139">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="a2a54-140">XML スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="a2a54-140">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="a2a54-141">XML スキーマの編集</span><span class="sxs-lookup"><span data-stu-id="a2a54-141">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="a2a54-142">XML スキーマのインクルードまたはインポート</span><span class="sxs-lookup"><span data-stu-id="a2a54-142">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="a2a54-143">スキーマをコンパイルするための XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="a2a54-143">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="a2a54-144">スキーマのコンパイル後の情報セット</span><span class="sxs-lookup"><span data-stu-id="a2a54-144">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
