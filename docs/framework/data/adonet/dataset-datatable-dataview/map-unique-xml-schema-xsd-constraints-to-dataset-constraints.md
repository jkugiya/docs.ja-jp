---
description: '詳細情報: XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て'
title: XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 41a6e5424d67b092e57ac61d6e34a1f285fb8d0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651926"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="c73d5-103">XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="c73d5-103">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="c73d5-104">XML スキーマ定義言語 (XSD) スキーマでは、**unique** 要素を使用して要素または属性の一意性制約を指定します。</span><span class="sxs-lookup"><span data-stu-id="c73d5-104">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="c73d5-105">XML スキーマをリレーショナル スキーマに変換する処理では、XML スキーマの要素または属性で指定した UNIQUE 制約が、生成される <xref:System.Data.DataTable> に対応する <xref:System.Data.DataSet> の UNIQUE 制約に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c73d5-105">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="c73d5-106">**unique** 要素で指定できる **msdata** 属性を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c73d5-106">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="c73d5-107">属性名</span><span class="sxs-lookup"><span data-stu-id="c73d5-107">Attribute name</span></span>|<span data-ttu-id="c73d5-108">説明</span><span class="sxs-lookup"><span data-stu-id="c73d5-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c73d5-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="c73d5-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="c73d5-110">この属性を指定した場合、その値が制約名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="c73d5-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="c73d5-111">それ以外の場合は、**name** 属性によって制約名の値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="c73d5-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="c73d5-112">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="c73d5-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="c73d5-113">**unique** 要素が `PrimaryKey="true"` である場合、一意制約は、**IsPrimaryKey** プロパティが **true** に設定された状態で作成されます。</span><span class="sxs-lookup"><span data-stu-id="c73d5-113">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="c73d5-114">**unique** 要素を使用して一意性制約を指定する XML スキーマの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c73d5-114">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
```xml  
<xs:schema id="SampleDataSet"
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="c73d5-115">スキーマの **unique** 要素では、ドキュメント インスタンスのすべての **Customers** 要素に対し、**CustomerID** 子要素の値が一意である必要があることが指定されます。</span><span class="sxs-lookup"><span data-stu-id="c73d5-115">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="c73d5-116">**DataSet** を作成する場合は、割り当て処理によってスキーマが読み込まれ、次のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="c73d5-116">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="c73d5-117">次の **DataSet** に示すように、マッピング プロセスによって **CustomerID** 列に対する一意制約も作成されます。</span><span class="sxs-lookup"><span data-stu-id="c73d5-117">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="c73d5-118">(わかりやすいように、関連するプロパティだけを示します)。</span><span class="sxs-lookup"><span data-stu-id="c73d5-118">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID
      IsPrimaryKey: False  
```  
  
 <span data-ttu-id="c73d5-119">生成される **DataSet** では、一意制約のために **IsPrimaryKey** プロパティが **False** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c73d5-119">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="c73d5-120">列の **unique** プロパティでは、**CustomerID** 列の値が一意であることが示されます (ただし、列の **AllowDBNull** プロパティで指定されているように、null 参照でもかまいません)。</span><span class="sxs-lookup"><span data-stu-id="c73d5-120">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="c73d5-121">スキーマを変更し、オプションの **msdata:PrimaryKey** 属性を **True** に設定すると、一意制約がテーブルに作成されます。</span><span class="sxs-lookup"><span data-stu-id="c73d5-121">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="c73d5-122">**AllowDBNull** 列プロパティが **False** に設定され、制約の **IsPrimaryKey** プロパティが **True** に設定されるため、**CustomerID** 列が主キー列になります。</span><span class="sxs-lookup"><span data-stu-id="c73d5-122">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="c73d5-123">XML スキーマの要素や属性を組み合わせて UNIQUE 制約を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c73d5-123">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="c73d5-124">次の例では、スキーマに別の **xs:field** 要素を追加することにより、**CustomerID** の値と **CompanyName** の値の組み合わせを任意のインスタンスのすべての **Customers** に対して必ず一意になるように指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c73d5-124">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 <span data-ttu-id="c73d5-125">その結果、**DataSet** に作成される制約を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c73d5-125">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="c73d5-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c73d5-126">See also</span></span>

- [<span data-ttu-id="c73d5-127">XML スキーマ (XSD) 制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="c73d5-127">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="c73d5-128">XML スキーマ (XSD) からの DataSet リレーションの生成</span><span class="sxs-lookup"><span data-stu-id="c73d5-128">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="c73d5-129">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="c73d5-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
