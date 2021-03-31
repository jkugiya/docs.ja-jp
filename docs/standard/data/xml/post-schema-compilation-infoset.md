---
description: '詳細情報: スキーマのコンパイル後の情報セット'
title: スキーマのコンパイル後の情報セット
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
ms.openlocfilehash: 9c574728b564c69de9574aba551bfb6967cf8488
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783262"
---
# <a name="post-schema-compilation-infoset"></a><span data-ttu-id="55dfd-103">スキーマのコンパイル後の情報セット</span><span class="sxs-lookup"><span data-stu-id="55dfd-103">Post-Schema Compilation Infoset</span></span>

<span data-ttu-id="55dfd-104">W3C 勧告『[XML Schema](https://www.w3.org/XML/Schema)』では、スキーマ検証前とスキーマ コンパイル後に必ず公開する情報セットについて解説されています。</span><span class="sxs-lookup"><span data-stu-id="55dfd-104">The [World Wide Web Consortium (W3C) XML Schema Recommendation](https://www.w3.org/XML/Schema) discusses the information set (infoset) that must be exposed for pre-schema validation and post-schema compilation.</span></span> <span data-ttu-id="55dfd-105">XML スキーマ オブジェクト モデル (SOM) は、<xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッドが呼び出される前と後について、この公開内容を調べます。</span><span class="sxs-lookup"><span data-stu-id="55dfd-105">The XML Schema Object Model (SOM) views this exposure before and after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span>  
  
 <span data-ttu-id="55dfd-106">スキーマの検証前の情報セットは、スキーマの編集時に作成されます。</span><span class="sxs-lookup"><span data-stu-id="55dfd-106">The pre-schema validation infoset is built during the editing of the schema.</span></span> <span data-ttu-id="55dfd-107">スキーマ コンパイル後の情報セットは、<xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッドが呼び出された後、スキーマのコンパイル時に生成され、プロパティとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="55dfd-107">The post-schema compilation infoset is generated after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called, during compilation of the schema, and is exposed as properties.</span></span>  
  
 <span data-ttu-id="55dfd-108">SOM はスキーマ検証前とスキーマ コンパイル後の情報セットを表すオブジェクト モデルです。これは <xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間内のクラスで構成されます。</span><span class="sxs-lookup"><span data-stu-id="55dfd-108">The SOM is the object model that represents the pre-schema validation and post-schema compilation infosets; it consists of the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="55dfd-109"><xref:System.Xml.Schema> 名前空間内のクラスの読み書き可能なプロパティは、すべてスキーマ検証前の情報セットに属し、一方 <xref:System.Xml.Schema> 名前空間のクラスの読み取り専用プロパティは、すべてスキーマ コンパイル後の情報セットに属します。</span><span class="sxs-lookup"><span data-stu-id="55dfd-109">All read and write properties of classes in the <xref:System.Xml.Schema> namespace belong to the pre-schema validation infoset, while all read-only properties of classes in the <xref:System.Xml.Schema> namespace belong to the post-schema compilation infoset.</span></span> <span data-ttu-id="55dfd-110">この規則の例外は、スキーマ検証前の情報セットとスキーマ コンパイル後の情報セットの両方のプロパティである、次のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="55dfd-110">The exception to this rule are the following properties, which are both pre-schema validation infoset and post-schema compilation infoset properties.</span></span>  
  
|<span data-ttu-id="55dfd-111">クラス</span><span class="sxs-lookup"><span data-stu-id="55dfd-111">Class</span></span>|<span data-ttu-id="55dfd-112">プロパティ</span><span class="sxs-lookup"><span data-stu-id="55dfd-112">Property</span></span>|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<span data-ttu-id="55dfd-113"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="55dfd-113"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<span data-ttu-id="55dfd-114"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span><span class="sxs-lookup"><span data-stu-id="55dfd-114"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 <span data-ttu-id="55dfd-115">たとえば、<xref:System.Xml.Schema.XmlSchemaElement> クラスと <xref:System.Xml.Schema.XmlSchemaComplexType> クラスには `BlockResolved` プロパティと `FinalResolved` プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="55dfd-115">For example, the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaComplexType> classes both have `BlockResolved` and `FinalResolved` properties.</span></span> <span data-ttu-id="55dfd-116">これらのプロパティは、スキーマがコンパイルおよび検証された後に、`Block` プロパティと `Final` プロパティの値を格納するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="55dfd-116">These properties are used to hold the values for the `Block` and `Final` properties after the schema has been compiled and validated.</span></span> <span data-ttu-id="55dfd-117">`BlockResolved` プロパティと `FinalResolved` プロパティは、スキーマ コンパイル後の情報セットの一部であり、読み取り専用のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="55dfd-117">`BlockResolved` and `FinalResolved` are read-only properties that are part of the post-schema compilation infoset.</span></span>  
  
 <span data-ttu-id="55dfd-118">スキーマの検証後に設定される <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> クラスの <xref:System.Xml.Schema.XmlSchemaElement> プロパティを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="55dfd-118">The following example shows the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> class set after validating the schema.</span></span> <span data-ttu-id="55dfd-119">検証の前の時点では、このプロパティには `null` 参照が含まれており、<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> には問題の型の名前が設定されています。</span><span class="sxs-lookup"><span data-stu-id="55dfd-119">Before validation, the property contains a `null` reference, and the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is set to the name of the type in question.</span></span> <span data-ttu-id="55dfd-120">検証後、<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> は有効な型に解決され、型オブジェクトは <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> プロパティを通じて利用できます。</span><span class="sxs-lookup"><span data-stu-id="55dfd-120">After validation, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is resolved to a valid type, and the type object is available through the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property.</span></span>  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="55dfd-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="55dfd-121">See also</span></span>

- [<span data-ttu-id="55dfd-122">XML スキーマ オブジェクト モデル (SOM)</span><span class="sxs-lookup"><span data-stu-id="55dfd-122">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)
