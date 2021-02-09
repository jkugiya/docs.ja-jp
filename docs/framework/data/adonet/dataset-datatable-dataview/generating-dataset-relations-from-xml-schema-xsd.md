---
description: '詳細情報: XML スキーマ (XSD) からの DataSet リレーションの生成'
title: XML スキーマ (XSD) からの DataSet リレーションの生成
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: e18ae451085f536e7fe35053fadab35e30dbc225
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652459"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="a6f29-103">XML スキーマ (XSD) からの DataSet リレーションの生成</span><span class="sxs-lookup"><span data-stu-id="a6f29-103">Generating DataSet Relations from XML Schema (XSD)</span></span>

<span data-ttu-id="a6f29-104"><xref:System.Data.DataSet> では、親子のリレーションを作成することにより、2 つ以上の列間の関連付けを行います。</span><span class="sxs-lookup"><span data-stu-id="a6f29-104">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="a6f29-105">XML スキーマ定義言語 (XSD) スキーマ内で **DataSet** のリレーションを表すには、次の 3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="a6f29-105">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="a6f29-106">入れ子になった複合型を指定する方法</span><span class="sxs-lookup"><span data-stu-id="a6f29-106">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="a6f29-107">**msdata:Relationship** 注釈を使用します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-107">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="a6f29-108">**msdata:ConstraintOnly** 注釈を使用せずに **xs:keyref** を指定します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-108">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="a6f29-109">入れ子になった複合型</span><span class="sxs-lookup"><span data-stu-id="a6f29-109">Nested Complex Types</span></span>  

 <span data-ttu-id="a6f29-110">スキーマ内で複数の複合型の定義が入れ子になっている場合は、それらの入れ子状の要素間に親子のリレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="a6f29-110">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="a6f29-111">**OrderDetail** が **Order** 要素の子要素であることを示す XML スキーマのフラグメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-111">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>
       <xs:element name="OrderDetail" />  
           <xs:complexType>
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="a6f29-112">XML スキーマの割り当て処理によって、スキーマの入れ子になった複合型に対応する **DataSet** にテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a6f29-112">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="a6f29-113">また、生成されたテーブルの親 **-** 子列として使用される追加列も作成されます。</span><span class="sxs-lookup"><span data-stu-id="a6f29-113">It also creates additional columns that are used as parent **-** child columns for the generated tables.</span></span> <span data-ttu-id="a6f29-114">その親 **-** 子列ではリレーションシップが指定されますが、主キー制約や外部キー制約の指定とは異なるため注意してください。</span><span class="sxs-lookup"><span data-stu-id="a6f29-114">Note that these parent **-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="a6f29-115">msdata:Relationship 注釈</span><span class="sxs-lookup"><span data-stu-id="a6f29-115">msdata:Relationship Annotation</span></span>  

 <span data-ttu-id="a6f29-116">**msdata:Relationship** 注釈を使用すると、入れ子になっていないスキーマの要素間の親子のリレーションシップを明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="a6f29-116">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="a6f29-117">**Relationship** 要素の構造を示す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-117">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 <span data-ttu-id="a6f29-118">**msdata:Relationship** 注釈の属性は、リレーションシップに必要な **parentkey** 要素と **childkey** 要素、および属性と同様に親子のリレーションシップに必要な要素を示します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-118">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="a6f29-119">割り当て処理では、その情報に基づいて **DataSet** にテーブルを作成し、それらのテーブル間に主キーと外部キーのリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-119">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="a6f29-120">たとえば、同じレベルで (入れ子にせずに) **Order** 要素と **OrderDetail** 要素を指定するスキーマのフラグメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-120">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="a6f29-121">スキーマに **msdata:Relationship** 注釈を指定すると、その 2 つの要素間に親子のリレーションシップが指定されます。</span><span class="sxs-lookup"><span data-stu-id="a6f29-121">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="a6f29-122">この場合、**msdata:Relationship** 注釈を使用してリレーションシップを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6f29-122">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 <span data-ttu-id="a6f29-123">割り当て処理では、**Relationship** 要素を使用して、**DataSet** にある **Order** テーブルの **OrderNumber** 列と **OrderDetail** テーブルの **OrderNo** 列に親子のリレーションシップが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a6f29-123">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="a6f29-124">割り当て処理で指定されるのはリレーションシップだけで、リレーショナル データベースにおける主キー制約や外部キー制約の場合とは異なり、該当する列の値に対する制約が自動的に指定されることはありません。</span><span class="sxs-lookup"><span data-stu-id="a6f29-124">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="a6f29-125">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a6f29-125">In This Section</span></span>  

 [<span data-ttu-id="a6f29-126">入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て</span><span class="sxs-lookup"><span data-stu-id="a6f29-126">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="a6f29-127">XML スキーマ内で要素が入れ子になっている場合に、**DataSet** 内に暗黙的に作成される制約とリレーションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-127">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="a6f29-128">入れ子になっている要素に指定したリレーションシップの割り当て</span><span class="sxs-lookup"><span data-stu-id="a6f29-128">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="a6f29-129">XML スキーマで入れ子になっている要素に対して、**DataSet** におけるリレーションを明示的に設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-129">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="a6f29-130">入れ子になっていない要素間のリレーションの指定</span><span class="sxs-lookup"><span data-stu-id="a6f29-130">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="a6f29-131">XML スキーマで入れ子になっていない要素間に、**DataSet** におけるリレーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-131">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="a6f29-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6f29-132">Related Sections</span></span>  

 [<span data-ttu-id="a6f29-133">XML スキーマ (XSD) からの DataSet リレーショナル構造の派生</span><span class="sxs-lookup"><span data-stu-id="a6f29-133">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="a6f29-134">XML スキーマ定義言語 (XSD) スキーマから作成された **DataSet** のリレーショナル構造 (スキーマ) について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-134">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="a6f29-135">XML スキーマ (XSD) 制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="a6f29-135">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="a6f29-136">**DataSet** での一意制約および外部キー制約の作成に使用する XML スキーマの要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6f29-136">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f29-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6f29-137">See also</span></span>

- [<span data-ttu-id="a6f29-138">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="a6f29-138">ADO.NET Overview</span></span>](../ado-net-overview.md)
