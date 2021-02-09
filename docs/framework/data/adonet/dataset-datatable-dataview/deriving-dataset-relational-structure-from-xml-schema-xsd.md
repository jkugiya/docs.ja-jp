---
description: '詳細情報: XML スキーマ (XSD) からの DataSet リレーショナル構造の派生'
title: XML スキーマ (XSD) からの DataSet リレーショナル構造の派生
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: c2d2dc8ab9c8a1cf77c79fbde38a06de6f120c82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652524"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="ab66e-103">XML スキーマ (XSD) からの DataSet リレーショナル構造の派生</span><span class="sxs-lookup"><span data-stu-id="ab66e-103">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>

<span data-ttu-id="ab66e-104">ここでは、XML スキーマ定義言語 (XSD) スキーマ ドキュメントから `DataSet` のリレーショナル スキーマを生成する方法についての概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="ab66e-104">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="ab66e-105">一般的には、スキーマの要素の各 `complexType` 子要素に対して、テーブルが `DataSet` に生成されます。</span><span class="sxs-lookup"><span data-stu-id="ab66e-105">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="ab66e-106">テーブル構造は、複合型の定義に基づいて決定されます。</span><span class="sxs-lookup"><span data-stu-id="ab66e-106">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="ab66e-107">テーブルは、スキーマのトップレベル要素の `DataSet` に作成されます。</span><span class="sxs-lookup"><span data-stu-id="ab66e-107">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="ab66e-108">ただし、`complexType` 要素が別の `complexType` 要素内で入れ子になっている場合、テーブルはトップレベルの `complexType` 要素にだけ作成されます。その場合、入れ子になった `complexType` 要素は、`DataSet` 内の `DataTable` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ab66e-108">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="ab66e-109">XSD の詳細については、World Wide Web コンソーシアム (W3C) の「[XML スキーマ パート 0: 入門の推奨事項](https://www.w3.org/TR/xmlschema-0/)」、「[XML スキーマ パート 1: 構造に関する推奨事項](https://www.w3.org/TR/xmlschema-1/)」、「[XML スキーマ パート 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/)」 (XML スキーマ第 2 部: データ型の推奨事項) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab66e-109">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="ab66e-110">`customers` 要素が `MyDataSet` 要素の子要素である XML スキーマの例を次に示します。これは **DataSet** 要素です。</span><span class="sxs-lookup"><span data-stu-id="ab66e-110">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="ab66e-111">上記の例では、`customers` 要素は複合型の要素です。</span><span class="sxs-lookup"><span data-stu-id="ab66e-111">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="ab66e-112">したがって、複合型の定義が解析され、割り当て処理によって次のテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ab66e-112">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="ab66e-113">テーブルの各列のデータ型は、それに対応する指定された要素または属性の XML スキーマ型から派生します。</span><span class="sxs-lookup"><span data-stu-id="ab66e-113">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab66e-114">`customers` 要素が **integer** のような単純な XML スキーマ データ型である場合、テーブルは生成されません。</span><span class="sxs-lookup"><span data-stu-id="ab66e-114">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="ab66e-115">テーブルが作成されるのは、複合型のトップレベル要素に対してだけです。</span><span class="sxs-lookup"><span data-stu-id="ab66e-115">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="ab66e-116">次の XML スキーマでは、**Schema** 要素に 2 つの子要素 `InStateCustomers` と `OutOfStateCustomers` があります。</span><span class="sxs-lookup"><span data-stu-id="ab66e-116">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="ab66e-117">`InStateCustomers` と `OutOfStateCustomers` の 2 つの子要素は、複合型の要素です (`customerType`)。</span><span class="sxs-lookup"><span data-stu-id="ab66e-117">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="ab66e-118">したがって、割り当て処理によって `DataSet` に次の 2 つの同じテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ab66e-118">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="ab66e-119">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ab66e-119">In This Section</span></span>  

 [<span data-ttu-id="ab66e-120">XML スキーマ (XSD) 制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="ab66e-120">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="ab66e-121">`DataSet` での一意制約および外部キー制約の作成に使用する XML スキーマの要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab66e-121">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="ab66e-122">XML スキーマ (XSD) からの DataSet リレーションの生成</span><span class="sxs-lookup"><span data-stu-id="ab66e-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="ab66e-123">`DataSet` でのテーブル列間のリレーションの生成に使用する XML スキーマの要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab66e-123">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="ab66e-124">XML スキーマ制約およびリレーションシップ</span><span class="sxs-lookup"><span data-stu-id="ab66e-124">XML Schema Constraints and Relationships</span></span>](xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="ab66e-125">XML スキーマの要素を使用して `DataSet` に制約を作成するときに、リレーションが暗黙的に生成される方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab66e-125">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ab66e-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab66e-126">Related Sections</span></span>  

 [<span data-ttu-id="ab66e-127">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="ab66e-127">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="ab66e-128">`DataSet` のリレーショナル構造とデータを XML データとして読み込んで、永続化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab66e-128">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab66e-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab66e-129">See also</span></span>

- [<span data-ttu-id="ab66e-130">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="ab66e-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
