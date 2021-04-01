---
description: '詳細情報: XML スキーマの編集'
title: XML スキーマの編集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: 19f757f537281b16d30dfc831e0dc8f0f4735987
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783340"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="1ab53-103">XML スキーマの編集</span><span class="sxs-lookup"><span data-stu-id="1ab53-103">Editing XML Schemas</span></span>

<span data-ttu-id="1ab53-104">XML スキーマの編集は、スキーマ オブジェクト モデル (SOM) の最も重要な機能の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="1ab53-104">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="1ab53-105">XML スキーマの既存の値を変更する場合、SOM のスキーマ コンパイル前のすべてのプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1ab53-105">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="1ab53-106">その後、XML スキーマを再コンパイルすると、変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="1ab53-106">The XML schema can then be recompiled to reflect the changes.</span></span>

<span data-ttu-id="1ab53-107">SOM に読み込まれたスキーマを編集する場合、最初にスキーマの走査を行います。</span><span class="sxs-lookup"><span data-stu-id="1ab53-107">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="1ab53-108">スキーマを編集する際には、事前に SOM API を使用したスキーマの走査をよく理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ab53-108">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="1ab53-109">また、スキーマのコンパイル後の情報セット (PSCI) のうち、スキーマのコンパイル前のプロパティとコンパイル後のプロパティについてもよく理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ab53-109">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>

## <a name="editing-an-xml-schema"></a><span data-ttu-id="1ab53-110">XML スキーマの編集</span><span class="sxs-lookup"><span data-stu-id="1ab53-110">Editing an XML Schema</span></span>

<span data-ttu-id="1ab53-111">このセクションには、2 種類のコード サンプルが用意されています。これらはいずれも「[XML スキーマの作成](building-xml-schemas.md)」トピックで作成したカスタム スキーマを編集します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-111">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span> <span data-ttu-id="1ab53-112">最初のコード サンプルは、`PhoneNumber` 要素に新しい `Customer` 要素を追加します。2 番目のコード サンプルは、`Title` 要素に新しい `FirstName` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-112">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="1ab53-113">また、最初のサンプルは、スキーマのコンパイル前の <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> コレクションをカスタム スキーマを走査する手段として使用しますが、2 番目のコード サンプルはスキーマのコンパイル後の <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> コレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-113">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

### <a name="phonenumber-element-example"></a><span data-ttu-id="1ab53-114">PhoneNumber 要素の例</span><span class="sxs-lookup"><span data-stu-id="1ab53-114">PhoneNumber Element Example</span></span>

<span data-ttu-id="1ab53-115">この最初のコード サンプルでは、カスタム スキーマの `PhoneNumber` 要素に新しい `Customer` 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-115">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="1ab53-116">このコード サンプルでは、次の手順でカスタム スキーマの編集を行います。</span><span class="sxs-lookup"><span data-stu-id="1ab53-116">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="1ab53-117">カスタム スキーマを新しい <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトに追加し、コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="1ab53-117">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="1ab53-118">スキーマの読み取りまたはコンパイル時に発生するスキーマ検証に関する警告とエラーは、<xref:System.Xml.Schema.ValidationEventHandler> デリゲートで処理されます。</span><span class="sxs-lookup"><span data-stu-id="1ab53-118">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="1ab53-119"><xref:System.Xml.Schema.XmlSchema> プロパティを反復処理して、<xref:System.Xml.Schema.XmlSchemaSet> からコンパイルされた <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-119">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="1ab53-120">スキーマはコンパイルされているため、スキーマのコンパイル後の情報セット (PSCI) プロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1ab53-120">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="1ab53-121">`PhoneNumber` クラスを使用する <xref:System.Xml.Schema.XmlSchemaElement> 要素を作成し、`xs:string` クラスおよび <xref:System.Xml.Schema.XmlSchemaSimpleType> クラスを使用する <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> 単純型の制限を作成し、制限の <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> プロパティに pattern ファセットを追加し、単純型の <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> プロパティに制限を追加して、<xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> 要素の `PhoneNumber` に単純型を追加します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-121">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>

4. <span data-ttu-id="1ab53-122">スキーマ コンパイル後の <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> コレクションの <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> コレクションで、それぞれの <xref:System.Xml.Schema.XmlSchemaElement> を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-122">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>

5. <span data-ttu-id="1ab53-123">要素の <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> が `"Customer"` である場合、`Customer` クラスを使用する複合型の <xref:System.Xml.Schema.XmlSchemaComplexType> 要素と <xref:System.Xml.Schema.XmlSchemaSequence> クラスを使用する複合型の sequence のパーティクルを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-123">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

6. <span data-ttu-id="1ab53-124">シーケンスのスキーマ コンパイル前の <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> コレクションを使用する既存の `FirstName` 要素および `LastName` 要素を格納するシーケンスに、新しい `PhoneNumber` 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-124">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>

7. <span data-ttu-id="1ab53-125">最後に、<xref:System.Xml.Schema.XmlSchema> クラスの <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> および <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> メソッドを使用して、変更された <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトの再処理とコンパイルを行って、コンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-125">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="1ab53-126">完全なコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-126">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

<span data-ttu-id="1ab53-127">変更後のカスタム スキーマ (「[XML スキーマの作成](building-xml-schemas.md)」トピックで作成) を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-127">The following is the modified customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="xs:string" />
        <xs:element name="LastName" type="tns:LastNameType" />
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>
      </xs:sequence>
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />
    </xs:complexType>
  </xs:element>
  <xs:simpleType name="LastNameType">
    <xs:restriction base="xs:string">
      <xs:maxLength value="20" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

### <a name="title-attribute-example"></a><span data-ttu-id="1ab53-128">Title 属性の例</span><span class="sxs-lookup"><span data-stu-id="1ab53-128">Title Attribute Example</span></span>

<span data-ttu-id="1ab53-129">この 2 番目のコード サンプルでは、カスタム スキーマの `Title` 要素に新しい `FirstName` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-129">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="1ab53-130">最初のコード サンプルでは、`FirstName` 要素の型が `xs:string` になっています。</span><span class="sxs-lookup"><span data-stu-id="1ab53-130">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="1ab53-131">`FirstName` 要素が文字列のコンテンツと同時に属性を持つには、単純なコンテンツの拡張コンテンツ モデルを使用してこの要素の型を複合型に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ab53-131">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>

<span data-ttu-id="1ab53-132">このコード サンプルでは、次の手順でカスタム スキーマの編集を行います。</span><span class="sxs-lookup"><span data-stu-id="1ab53-132">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="1ab53-133">カスタム スキーマを新しい <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトに追加し、コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="1ab53-133">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="1ab53-134">スキーマの読み取りまたはコンパイル時に発生するスキーマ検証に関する警告とエラーは、<xref:System.Xml.Schema.ValidationEventHandler> デリゲートで処理されます。</span><span class="sxs-lookup"><span data-stu-id="1ab53-134">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="1ab53-135"><xref:System.Xml.Schema.XmlSchema> プロパティを反復処理して、<xref:System.Xml.Schema.XmlSchemaSet> からコンパイルされた <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-135">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="1ab53-136">スキーマはコンパイルされているため、スキーマのコンパイル後の情報セット (PSCI) プロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1ab53-136">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="1ab53-137">`FirstName` クラスを使用して <xref:System.Xml.Schema.XmlSchemaComplexType> 要素に対する複合型を新しく作成します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-137">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>

4. <span data-ttu-id="1ab53-138">`xs:string` および <xref:System.Xml.Schema.XmlSchemaSimpleContent> クラスを使用して、<xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> の基本型を使った単純なコンテンツの拡張型を新しく作成します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-138">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>

5. <span data-ttu-id="1ab53-139">`Title` の <xref:System.Xml.Schema.XmlSchemaAttribute> を使用して、<xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> クラスを使用する `xs:string` 属性を新しく作成し、その属性を単純なコンテンツの拡張型に追加します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-139">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>

6. <span data-ttu-id="1ab53-140">単純なコンテンツのコンテンツ モデルを単純なコンテンツの拡張型に設定し、複合型のコンテンツ モデルを単純なコンテンツに設定します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-140">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>

7. <span data-ttu-id="1ab53-141">スキーマ コンパイル前の <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> コレクションに、新しい複合型を追加します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-141">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

8. <span data-ttu-id="1ab53-142">スキーマのコンパイル前の <xref:System.Xml.Schema.XmlSchemaObject> コレクションで、それぞれの <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-142">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

> [!NOTE]
> <span data-ttu-id="1ab53-143">`FirstName` 要素はスキーマのグローバル要素ではないため、<xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> または <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> コレクションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="1ab53-143">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="1ab53-144">コード サンプルでは、`FirstName` 要素を検索するために、最初に `Customer` 要素の検索を行います。</span><span class="sxs-lookup"><span data-stu-id="1ab53-144">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>
>
> <span data-ttu-id="1ab53-145">最初のコード サンプルでは、スキーマ コンパイル後の <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> コレクションを使用してスキーマを走査しました。</span><span class="sxs-lookup"><span data-stu-id="1ab53-145">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="1ab53-146">このサンプルでは、スキーマ コンパイル前の <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> コレクションを使用してスキーマを走査します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-146">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="1ab53-147">どちらのコレクションでもスキーマのグローバル要素にアクセスできますが、<xref:System.Xml.Schema.XmlSchema.Items%2A> コレクションで反復処理を行う場合、スキーマ内のすべてのグローバル要素に対して反復処理を行う必要があり、スキーマに PSCI プロパティが存在しないため、処理時間が長くなります。</span><span class="sxs-lookup"><span data-stu-id="1ab53-147">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="1ab53-148">PSCI コレクション (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>、<xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>、<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType> など) では、グローバルな要素、属性、型、および PSCI プロパティに直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1ab53-148">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>

1. <span data-ttu-id="1ab53-149"><xref:System.Xml.Schema.XmlSchemaObject> が要素 (その <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> が `"Customer"`) である場合、`Customer` クラスを使用する複合型の <xref:System.Xml.Schema.XmlSchemaComplexType> 要素と <xref:System.Xml.Schema.XmlSchemaSequence> クラスを使用する複合型の sequence のパーティクルを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-149">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

2. <span data-ttu-id="1ab53-150">スキーマのコンパイル前の <xref:System.Xml.Schema.XmlSchemaParticle> コレクションで、それぞれの <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-150">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="1ab53-151"><xref:System.Xml.Schema.XmlSchemaParticle> が要素 (その <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> が `"FirstName"`) である場合、<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 要素の `FirstName` を新しい `FirstName` 複合型に設定します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-151">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>

4. <span data-ttu-id="1ab53-152">最後に、<xref:System.Xml.Schema.XmlSchema> クラスの <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> および <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> メソッドを使用して、変更された <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトの再処理とコンパイルを行って、コンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-152">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="1ab53-153">完全なコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-153">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

<span data-ttu-id="1ab53-154">変更後のカスタム スキーマ (「[XML スキーマの作成](building-xml-schemas.md)」トピックで作成) を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1ab53-154">The following is the modified customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span>

```xml
<?xml version="1.0" encoding=" utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />
        <xs:element name="LastName" type="tns:LastNameType" />
      </xs:sequence>
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />
    </xs:complexType>
  </xs:element>
  <xs:simpleType name="LastNameType">
    <xs:restriction base="xs:string">
      <xs:maxLength value="20" />
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="1ab53-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ab53-155">See also</span></span>

- [<span data-ttu-id="1ab53-156">XML スキーマ オブジェクト モデルの概要</span><span class="sxs-lookup"><span data-stu-id="1ab53-156">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="1ab53-157">XML スキーマの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="1ab53-157">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="1ab53-158">XML スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="1ab53-158">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="1ab53-159">XML スキーマの走査</span><span class="sxs-lookup"><span data-stu-id="1ab53-159">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="1ab53-160">XML スキーマのインクルードまたはインポート</span><span class="sxs-lookup"><span data-stu-id="1ab53-160">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="1ab53-161">スキーマをコンパイルするための XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="1ab53-161">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="1ab53-162">スキーマのコンパイル後の情報セット</span><span class="sxs-lookup"><span data-stu-id="1ab53-162">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
