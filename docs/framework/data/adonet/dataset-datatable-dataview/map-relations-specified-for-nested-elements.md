---
description: '詳細情報: 入れ子になっている要素に指定したリレーションシップの割り当て'
title: 入れ子になっている要素に指定したリレーションシップの割り当て
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: a625ad5bfd590794d0362a991dc22f756f043f2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651939"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="dcf88-103">入れ子になっている要素に指定したリレーションシップの割り当て</span><span class="sxs-lookup"><span data-stu-id="dcf88-103">Map Relations Specified for Nested Elements</span></span>

<span data-ttu-id="dcf88-104">スキーマには、その中の 2 つの要素間の割り当てを明示的に指定するために、**msdata:Relationship** 注釈をインクルードすることができます。</span><span class="sxs-lookup"><span data-stu-id="dcf88-104">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="dcf88-105">**msdata:Relationship** で指定されたスキーマの 2 つの要素は、必要に応じて、入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="dcf88-105">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="dcf88-106">割り当て処理では、スキーマの **msdata:Relationship** を使用して 2 つの列間に主キー/外部キーのリレーションシップを生成します。</span><span class="sxs-lookup"><span data-stu-id="dcf88-106">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="dcf88-107">**OrderDetail** 要素が **Order** の子要素であることを示す XML スキーマの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dcf88-107">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="dcf88-108">**msdata:Relationship** はこの親子のリレーションシップを識別し、生成された **Order** テーブルの **OrderNumber** 列と生成された **OrderDetail** テーブルの **OrderNo** 列が関連付けられていることを示します。</span><span class="sxs-lookup"><span data-stu-id="dcf88-108">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
       <xs:element name="OrderNumber" type="xs:string" />  
       <xs:element name="EmpNumber" type="xs:string" />  
       <xs:element name="OrderDetail">  
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"
                                msdata:parent="Order"
                                msdata:child="OrderDetail"
                                msdata:parentkey="OrderNumber"
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
          <xs:complexType>  
            <xs:sequence>  
             <xs:element name="OrderNo" type="xs:string" />  
             <xs:element name="ItemNo" type="xs:string" />  
            </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:sequence>  
    </xs:complexType>  
   </xs:element>  
  </xs:choice>  
 </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="dcf88-109">XML スキーマの割り当て処理によって <xref:System.Data.DataSet> に作成される内容は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dcf88-109">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="dcf88-110">**Order** および **OrderDetail** テーブル。</span><span class="sxs-lookup"><span data-stu-id="dcf88-110">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="dcf88-111">**Order** テーブルと **OrderDetail** テーブルの間のリレーションシップ。</span><span class="sxs-lookup"><span data-stu-id="dcf88-111">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="dcf88-112">スキーマの **Order** 要素と **OrderDetail** 要素が入れ子になっているため、このリレーションシップの **Nested** プロパティは **True** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="dcf88-112">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="dcf88-113">割り当て処理によって制約は作成されません。</span><span class="sxs-lookup"><span data-stu-id="dcf88-113">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf88-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcf88-114">See also</span></span>

- [<span data-ttu-id="dcf88-115">XML スキーマ (XSD) からの DataSet リレーションの生成</span><span class="sxs-lookup"><span data-stu-id="dcf88-115">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="dcf88-116">XML スキーマ (XSD) 制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="dcf88-116">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="dcf88-117">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="dcf88-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
