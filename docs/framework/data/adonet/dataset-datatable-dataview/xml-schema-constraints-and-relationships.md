---
description: '詳細情報: XML スキーマ制約およびリレーションシップ'
title: XML スキーマ制約およびリレーションシップ
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: c7847691537c4b754abcbacdeb367b1d92365ef3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651315"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="86bf8-103">XML スキーマ制約およびリレーションシップ</span><span class="sxs-lookup"><span data-stu-id="86bf8-103">XML Schema Constraints and Relationships</span></span>

<span data-ttu-id="86bf8-104">XML スキーマ定義言語 (XSD) スキーマでは、制約 (UNIQUE、キー、キー参照) およびリレーションシップ (**msdata:Relationship** 注釈を使用した) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="86bf8-104">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="86bf8-105">このトピックでは、XML スキーマで指定した制約およびリレーションシップを解釈して <xref:System.Data.DataSet> を生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="86bf8-105">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="86bf8-106">一般的に、XML スキーマでは **DataSet** にリレーションシップだけを生成する場合に、**msdata:Relationship** 注釈を指定します。</span><span class="sxs-lookup"><span data-stu-id="86bf8-106">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="86bf8-107">詳細については、「[XML スキーマ (XSD) からの DataSet リレーションの生成](generating-dataset-relations-from-xml-schema-xsd.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86bf8-107">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="86bf8-108">**DataSet** に制約を生成する場合は、制約 (UNIQUE、キー、およびキー参照) を指定します。</span><span class="sxs-lookup"><span data-stu-id="86bf8-108">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="86bf8-109">このトピックの後に説明されているように、リレーションシップを生成するにはキー制約とキー参照制約も使用するので注意してください。</span><span class="sxs-lookup"><span data-stu-id="86bf8-109">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="86bf8-110">キー制約およびキー参照制約によるリレーションシップの生成</span><span class="sxs-lookup"><span data-stu-id="86bf8-110">Generating a Relationship from key and keyref Constraints</span></span>  

 <span data-ttu-id="86bf8-111">**msdata:Relationship** 注釈を指定する代わりに、XML スキーマの割り当て処理時に使用するキー制約とキー参照制約を指定し、制約だけでなく、**DataSet** のリレーションシップも生成することができます。</span><span class="sxs-lookup"><span data-stu-id="86bf8-111">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="86bf8-112">ただし、**keyref** 要素で `msdata:ConstraintOnly="true"` を指定した場合、**DataSet** には制約だけが作成され、リレーションシップは生成されません。</span><span class="sxs-lookup"><span data-stu-id="86bf8-112">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="86bf8-113">入れ子になっていない **Order** 要素と **OrderDetail** 要素を含む XML スキーマの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="86bf8-113">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="86bf8-114">スキーマでは、キー制約とキー参照制約も指定します。</span><span class="sxs-lookup"><span data-stu-id="86bf8-114">The schema also specifies key and keyref constraints.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="86bf8-115">XML スキーマの割り当て処理時に生成される **DataSet** には、**Order** テーブルと **OrderDetail** テーブルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="86bf8-115">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="86bf8-116">さらに、**DataSet** にはリレーションシップと制約も含まれます。</span><span class="sxs-lookup"><span data-stu-id="86bf8-116">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="86bf8-117">そのリレーションシップと制約の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="86bf8-117">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="86bf8-118">スキーマでは、**msdata:Relationship** 注釈が指定されないことに注意してください。代わりに、キー制約とキー参照制約を使用してリレーションが生成されます。</span><span class="sxs-lookup"><span data-stu-id="86bf8-118">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
```text
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 <span data-ttu-id="86bf8-119">上記のスキーマの例では、**Order** 要素と **OrderDetail** 要素は入れ子になっていません。</span><span class="sxs-lookup"><span data-stu-id="86bf8-119">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="86bf8-120">入れ子になっている Order 要素と OrderDetail 要素を含むスキーマの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="86bf8-120">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="86bf8-121">ただし、**msdata:Relationship** 注釈が指定されていないため、暗黙のリレーションが適用されます。</span><span class="sxs-lookup"><span data-stu-id="86bf8-121">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="86bf8-122">詳細については、「[入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て](map-implicit-relations-between-nested-schema-elements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86bf8-122">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="86bf8-123">スキーマでは、キー制約とキー参照制約も指定します。</span><span class="sxs-lookup"><span data-stu-id="86bf8-123">The schema also specifies key and keyref constraints.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="86bf8-124">XML スキーマの割り当て処理によって生成された **DataSet** には、次の 2 つのテーブルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="86bf8-124">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="86bf8-125">さらに、**DataSet** には 2 つのリレーションシップ (1 つは **msdata:relationship** 注釈に基づいた、もう 1 つはキー制約とキー参照制約に基づいた) およびさまざまな制約も含まれます。</span><span class="sxs-lookup"><span data-stu-id="86bf8-125">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="86bf8-126">リレーションおよび制約の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="86bf8-126">The following example shows the relations and constraints.</span></span>  
  
```text
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 <span data-ttu-id="86bf8-127">入れ子になっているテーブルを参照するキー参照制約に **msdata:IsNested="true"** 注釈が含まれている場合は、**DataSet** により、そのキー参照制約と関連する UNIQUE/ キー制約に基づいて、1 つの入れ子になったリレーションシップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="86bf8-127">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86bf8-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="86bf8-128">See also</span></span>

- [<span data-ttu-id="86bf8-129">XML スキーマ (XSD) からの DataSet リレーショナル構造の派生</span><span class="sxs-lookup"><span data-stu-id="86bf8-129">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="86bf8-130">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="86bf8-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
