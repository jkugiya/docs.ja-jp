---
description: '詳細情報: XML スキーマ (XSD) のキー制約の DataSet 制約への割り当て'
title: XML スキーマ (XSD) のキー制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 0c07b53e06dc6b80395764b2bdd76045ee80bffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651991"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="e74d4-103">XML スキーマ (XSD) のキー制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="e74d4-103">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="e74d4-104">スキーマでは、**key** 要素を使用して要素または属性のキー制約を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e74d4-104">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="e74d4-105">キー制約を指定する要素または属性の値は、スキーマ インスタンス内で一意になる必要があります。また、null 値にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e74d4-105">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="e74d4-106">キー制約を定義する列の値を null 値にできない点を除くと、キー制約は UNIQUE 制約と同じです。</span><span class="sxs-lookup"><span data-stu-id="e74d4-106">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="e74d4-107">**key** 要素に指定できる **msdata** 属性を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e74d4-107">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="e74d4-108">属性名</span><span class="sxs-lookup"><span data-stu-id="e74d4-108">Attribute name</span></span>|<span data-ttu-id="e74d4-109">説明</span><span class="sxs-lookup"><span data-stu-id="e74d4-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e74d4-110">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="e74d4-110">**msdata:ConstraintName**</span></span>|<span data-ttu-id="e74d4-111">この属性を指定した場合、その値が制約名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="e74d4-111">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="e74d4-112">それ以外の場合は、**name** 属性によって制約名の値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="e74d4-112">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="e74d4-113">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="e74d4-113">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="e74d4-114">`PrimaryKey="true"` が指定されている場合、**IsPrimaryKey** 制約のプロパティを **true** に設定することによって、主キーになります。</span><span class="sxs-lookup"><span data-stu-id="e74d4-114">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="e74d4-115">主キーの値は null 値にできないため、**AllowDBNull** 列のプロパティが **false** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e74d4-115">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="e74d4-116">キー制約を指定するスキーマの変換では、割り当て処理により、制約の列ごとに **AllowDBNull** 列のプロパティが **false** に設定された状態でテーブルに一意制約が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e74d4-116">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="e74d4-117">**key** 要素で `msdata:PrimaryKey="true"` を指定しない限り、一意制約の **IsPrimaryKey** プロパティも **false** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e74d4-117">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="e74d4-118">これは、スキーマに `PrimaryKey="true"` が指定される UNIQUE 制約と同じです。</span><span class="sxs-lookup"><span data-stu-id="e74d4-118">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="e74d4-119">**key** 要素を使用して **CustomerID** 要素のキー制約を指定するスキーマの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e74d4-119">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 <span data-ttu-id="e74d4-120">**key** 要素は、**Customers** 要素の **CustomerID** 子要素の値を一意の値にし、null 値を許可しないように指定します。</span><span class="sxs-lookup"><span data-stu-id="e74d4-120">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="e74d4-121">XML スキーマ定義言語 (XSD) スキーマの変換では、割り当て処理によって次のテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e74d4-121">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="e74d4-122">また、次の <xref:System.Data.DataSet> に示すように、XML スキーマの割り当てによって **CustomerID** 列の **UniqueConstraint** を作成することもできます</span><span class="sxs-lookup"><span data-stu-id="e74d4-122">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e74d4-123">(わかりやすいように、関連するプロパティだけを示します)。</span><span class="sxs-lookup"><span data-stu-id="e74d4-123">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 <span data-ttu-id="e74d4-124">生成される **DataSet** では、スキーマの **Key** 要素で `msdata:PrimaryKey="true"` が指定されるため、**UniqueConstraint** の **IsPrimaryKey** プロパティが **true** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e74d4-124">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="e74d4-125">**DataSet** にある **UniqueConstraint** の **ConstraintName** プロパティの値は、スキーマの **key** 要素で指定した **msdata:ConstraintName** 属性の値です。</span><span class="sxs-lookup"><span data-stu-id="e74d4-125">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e74d4-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="e74d4-126">See also</span></span>

- [<span data-ttu-id="e74d4-127">XML スキーマ (XSD) 制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="e74d4-127">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="e74d4-128">XML スキーマ (XSD) からの DataSet リレーションの生成</span><span class="sxs-lookup"><span data-stu-id="e74d4-128">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="e74d4-129">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="e74d4-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
