---
description: '詳細情報: XML スキーマの作成'
title: XML スキーマの作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: a748560b128ff16ea3cceb9be37e427396ec9dfd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642618"
---
# <a name="building-xml-schemas"></a><span data-ttu-id="ced61-103">XML スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="ced61-103">Building XML Schemas</span></span>

<span data-ttu-id="ced61-104"><xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間のクラスは、W3C (World Wide Web Consortium) 勧告『XML Schema』で定義された構造に割り当てられ、メモリ内に XML スキーマを作成する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ced61-104">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="ced61-105">XML スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="ced61-105">Building an XML Schema</span></span>  

 <span data-ttu-id="ced61-106">以下のコード サンプルでは、SOM API を使用してカスタム XML スキーマをメモリ内に作成します。</span><span class="sxs-lookup"><span data-stu-id="ced61-106">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="ced61-107">要素と属性の作成</span><span class="sxs-lookup"><span data-stu-id="ced61-107">Creating Element and Attributes</span></span>  

 <span data-ttu-id="ced61-108">このコード サンプルでは、カスタム スキーマを最初から作成するため、子要素、属性、およびそれらに対応する型を作成した後で最上位要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="ced61-108">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="ced61-109">以下のコード サンプルでは、SOM の `FirstName` クラスおよび `LastName` クラスを使用して、カスタム スキーマの `CustomerId` 属性に加え、<xref:System.Xml.Schema.XmlSchemaElement> 要素および <xref:System.Xml.Schema.XmlSchemaAttribute> 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="ced61-109">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="ced61-110">XML スキーマの <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> 要素および <xref:System.Xml.Schema.XmlSchemaElement> 要素の name 属性に対応する <xref:System.Xml.Schema.XmlSchemaAttribute> クラスおよび `<xs:element />` クラスの `<xs:attribute />` プロパティを除いて、このスキーマで使用できる他のすべての属性 (`defaultValue`、`fixedValue`、`form` など) には、<xref:System.Xml.Schema.XmlSchemaElement> クラスおよび <xref:System.Xml.Schema.XmlSchemaAttribute> クラスに対応するプロパティが存在します。</span><span class="sxs-lookup"><span data-stu-id="ced61-110">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="ced61-111">スキーマの型の作成</span><span class="sxs-lookup"><span data-stu-id="ced61-111">Creating Schema Types</span></span>  

 <span data-ttu-id="ced61-112">要素および属性のコンテンツは、その型によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="ced61-112">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="ced61-113">組み込みのスキーマの型を持つ要素と属性を作成するには、<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> クラスを使用する組み込みの修飾名を使用して、<xref:System.Xml.Schema.XmlSchemaElement> クラスまたは <xref:System.Xml.Schema.XmlSchemaAttribute> クラスの <xref:System.Xml.XmlQualifiedName> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="ced61-113">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="ced61-114">要素と属性のユーザー定義型を作成するには、<xref:System.Xml.Schema.XmlSchemaSimpleType> または <xref:System.Xml.Schema.XmlSchemaComplexType> クラスを使用して単純型または複合型を新しく作成します。</span><span class="sxs-lookup"><span data-stu-id="ced61-114">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ced61-115">要素または属性の匿名の子である名前のない単純型または複合型 (属性に適用されるのは単純型のみ) を作成するには、<xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> クラスまたは <xref:System.Xml.Schema.XmlSchemaElement> クラスの <xref:System.Xml.Schema.XmlSchemaAttribute> プロパティではなく、<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> クラスまたは <xref:System.Xml.Schema.XmlSchemaElement> クラスの <xref:System.Xml.Schema.XmlSchemaAttribute> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="ced61-115">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="ced61-116">XML スキーマを使用すると、匿名の単純型と名前付きの単純型の両方を、他の単純型 (組み込み型またはユーザー定義型) から制限付きで派生させるか、または、他の単純型のリストまたは和集合として作成することができます。</span><span class="sxs-lookup"><span data-stu-id="ced61-116">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="ced61-117"><xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> クラスを使用して単純型を作成する場合には、組み込みの `xs:string` 型を制限します。</span><span class="sxs-lookup"><span data-stu-id="ced61-117">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="ced61-118">また、<xref:System.Xml.Schema.XmlSchemaSimpleTypeList> または <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> クラスを使用すると、リストまたは和集合の型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ced61-118">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="ced61-119"><xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> プロパティは、単純型の制限、リスト、または和集合を表します。</span><span class="sxs-lookup"><span data-stu-id="ced61-119">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="ced61-120">以下のコード サンプルでは、`FirstName` 要素の型は組み込み型の `xs:string`、`LastName` 要素の型は組み込み型 `xs:string` の制限となる名前付き単純型 (`MaxLength` ファセット値 20)、`CustomerId` 属性の型は組み込み型 `xs:positiveInteger` です。</span><span class="sxs-lookup"><span data-stu-id="ced61-120">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="ced61-121">`Customer` 要素は匿名の複合型で、そのパーティクルは `FirstName` 要素および `LastName` 要素のシーケンスとなり、その属性には `CustomerId` 属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ced61-121">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ced61-122">また、複合型のパーティクルとして <xref:System.Xml.Schema.XmlSchemaChoice> クラスまたは <xref:System.Xml.Schema.XmlSchemaAll> クラスを使用して、`<xs:choice />` または `<xs:all />` セマンティクスをレプリケートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ced61-122">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="ced61-123">スキーマの作成とコンパイル</span><span class="sxs-lookup"><span data-stu-id="ced61-123">Creating and Compiling Schemas</span></span>  

 <span data-ttu-id="ced61-124">この時点で、子要素と属性 (それらに対応する型) および最上位の `Customer` 要素が SOM API を使用してメモリ内に作成されています。</span><span class="sxs-lookup"><span data-stu-id="ced61-124">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="ced61-125">以下のコード サンプルでは、<xref:System.Xml.Schema.XmlSchema> クラスを使用してスキーマ要素が作成され、<xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> プロパティを使用して最上位の要素と型が追加されます。また、<xref:System.Xml.Schema.XmlSchemaSet> クラスを使用して完全なスキーマがコンパイルされて、コンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="ced61-125">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="ced61-126"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> メソッドは、XML スキーマの規則を基準としてカスタム スキーマを検証し、スキーマ コンパイル後のプロパティを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ced61-126">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ced61-127">SOM API のスキーマ コンパイル後のプロパティは、スキーマ検証後の情報セットとは異なります。</span><span class="sxs-lookup"><span data-stu-id="ced61-127">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="ced61-128"><xref:System.Xml.Schema.ValidationEventHandler> に追加される <xref:System.Xml.Schema.XmlSchemaSet> は、コールバック メソッド `ValidationCallback` を呼び出してスキーマ検証時の警告およびエラーを処理するデリゲートになります。</span><span class="sxs-lookup"><span data-stu-id="ced61-128">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="ced61-129">以下に、完全なコード サンプルおよびコンソールに出力されるカスタム スキーマを示します。</span><span class="sxs-lookup"><span data-stu-id="ced61-129">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
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
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ced61-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="ced61-130">See also</span></span>

- [<span data-ttu-id="ced61-131">XML スキーマ オブジェクト モデルの概要</span><span class="sxs-lookup"><span data-stu-id="ced61-131">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="ced61-132">XML スキーマの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="ced61-132">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="ced61-133">XML スキーマの走査</span><span class="sxs-lookup"><span data-stu-id="ced61-133">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="ced61-134">XML スキーマの編集</span><span class="sxs-lookup"><span data-stu-id="ced61-134">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="ced61-135">XML スキーマのインクルードまたはインポート</span><span class="sxs-lookup"><span data-stu-id="ced61-135">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="ced61-136">スキーマをコンパイルするための XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="ced61-136">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="ced61-137">スキーマのコンパイル後の情報セット</span><span class="sxs-lookup"><span data-stu-id="ced61-137">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
