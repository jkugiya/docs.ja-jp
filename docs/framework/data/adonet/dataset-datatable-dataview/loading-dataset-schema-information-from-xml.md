---
description: '詳細情報: XML の DataSet スキーマ情報の読み込み'
title: XML の DataSet スキーマ情報の読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: dd3a327270d6f8e3086d7206dd6f44290415c55e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652108"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="b7fd4-103">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="b7fd4-103">Loading DataSet Schema Information from XML</span></span>

<span data-ttu-id="b7fd4-104"><xref:System.Data.DataSet> のスキーマ (テーブル、列、リレーション、および制約) は、プログラムを使用して定義され、<xref:System.Data.Common.DataAdapter> の **Fill** メソッドまたは **FillSchema** メソッドによって作成されるか、あるいは XML ドキュメントから読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-104">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="b7fd4-105">XML ドキュメントから **DataSet** スキーマ情報を読み込むには、**DataSet** の **ReadXmlSchema** メソッドまたは **InferXmlSchema** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-105">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="b7fd4-106">**ReadXmlSchema** を使用すると、XML スキーマ定義言語 (XSD) スキーマが含まれているドキュメントまたはインライン XML スキーマが含まれている XML ドキュメントから、**DataSet** スキーマ情報を読み込むかまたは推論できます。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-106">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="b7fd4-107">**InferXmlSchema** を使用すると、XML ドキュメントからスキーマを推論できます。このとき、指定した特定の XML 名前空間は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-107">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7fd4-108">XSD の構造 (入れ子になったリレーションなど) を使用してメモリ内で作成された **DataSet** を、Web サービスまたは XML シリアル化を使って転送した場合、**DataSet** 内のテーブルの順序が維持されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-108">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="b7fd4-109">この場合、**DataSet** の受け取り側はテーブルの順序に依存していないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-109">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="b7fd4-110">ただし、メモリ内で作成するのではなく、転送する **DataSet** のスキーマを XSD ファイルから読み取った場合は、テーブルの順序が常に維持されます。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-110">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="b7fd4-111">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="b7fd4-111">ReadXmlSchema</span></span>  

 <span data-ttu-id="b7fd4-112">XML ドキュメントから **DataSet** のスキーマだけを読み込み、データを読み込まないようにするには、**DataSet** の **ReadXmlSchema** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-112">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="b7fd4-113">**ReadXmlSchema** では、XML スキーマ定義言語 (XSD) スキーマを使用して定義されている **DataSet** が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-113">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="b7fd4-114">**ReadXmlSchema** メソッドは、ファイル名、ストリーム、または読み込む XML ドキュメントが格納されている **XmlReader** のいずれか 1 つを引数として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-114">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="b7fd4-115">この XML ドキュメントには、スキーマだけが含まれているか、またはデータのある XML 要素と共にスキーマがインラインで含まれています。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-115">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="b7fd4-116">インライン スキーマを XML スキーマとして記述する方法の詳細については、「[XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-116">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="b7fd4-117">**ReadXmlSchema** に渡された XML ドキュメントに、インライン スキーマ情報が含まれていない場合、**ReadXmlSchema** は XML ドキュメントの要素からスキーマを推論します。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-117">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="b7fd4-118">**DataSet** に既にスキーマが含まれている場合、テーブルが存在しなければ新しいテーブルを追加することによって現在のスキーマが拡張されます。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-118">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="b7fd4-119">既存のテーブルには新しい列は追加されません。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-119">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="b7fd4-120">**DataSet** に既に追加される列が存在していますが、XML で検出された列の型と矛盾する場合には、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-120">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="b7fd4-121">**ReadXmlSchema** によって XML ドキュメントからスキーマが推論される方法の詳細については、「[XML からの DataSet リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-121">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="b7fd4-122">**ReadXmlSchema** では **DataSet** スキーマの読み込みまたは推論のいずれかが実行されますが、**DataSet** の **ReadXml** メソッドでは、スキーマと XML ドキュメントのデータの両方の読み込みまたは推論が実行されます。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-122">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="b7fd4-123">詳しくは、「[XML からの DataSet の読み込み](loading-a-dataset-from-xml.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-123">For more information, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="b7fd4-124">XML ドキュメントまたは XML ストリームから **DataSet** スキーマを読み込む方法のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-124">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="b7fd4-125">1 番目の例では、XML スキーマ ファイル名が **ReadXmlSchema** メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-125">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="b7fd4-126">2 番目の例では、**System.IO.StreamReader** が示されています。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-126">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a><span data-ttu-id="b7fd4-127">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="b7fd4-127">InferXmlSchema</span></span>  

 <span data-ttu-id="b7fd4-128">**DataSet** に対し、**DataSet** の **InferXmlSchema** メソッドを使用して XML ドキュメントのスキーマを推論するように指示できます。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-128">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="b7fd4-129">**InferXmlSchema** は、**XmlReadMode** を **InferSchema** に設定した **ReadXml** (データの読み込みとスキーマの推論) と、読み取られるドキュメントにインライン スキーマが含まれていない場合の **ReadXmlSchema** の両方と同様の機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-129">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="b7fd4-130">ただし **InferXmlSchema** には、スキーマを推論するときに無視する特定の XML 名前空間を指定できる追加機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-130">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="b7fd4-131">**InferXmlSchema** に必要な 2 つの引数は、XML ドキュメントの位置と、この操作によって無視される XML 名前空間の文字列配列です。XML ドキュメントの位置は、ファイル名、ストリーム、または **XmlReader** によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-131">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="b7fd4-132">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-132">For example, consider the following XML:</span></span>  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>
  <Description od:adotype="203">Soft drinks and teas</Description>
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>
  <ReorderLevel od:adotype="3">10</ReorderLevel>
  <Discontinued od:adotype="11">0</Discontinued>
</Products>  
</NewDataSet>  
```  
  
 <span data-ttu-id="b7fd4-133">前述の XML ドキュメントの要素に対して指定されている属性により、**XmlReadMode** が **InferSchema** の **ReadXmlSchema** メソッドと **ReadXml** メソッドでは、すべての要素 に対するテーブルが作成されます: **Categories**、**CategoryID**、**CategoryName**、**Description**、**Products**、**ProductID**、**ReorderLevel**、**Discontinued**。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-133">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="b7fd4-134">(詳細については、「[XML からの DataSet リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)」を参照してください)。ただし、これより適切な方法としては、最初に **Categories** テーブルと **Products** テーブルだけを作成し、次に **Categories** テーブルの **CategoryID**、**CategoryName**、**Description** 列を作成し、**Products** テーブルの **ProductID**、**ReorderLevel**、**Discontinued** 列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-134">(For more information, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="b7fd4-135">推論されたスキーマが、XML 要素に指定されている属性を無視するようにするには、**InferXmlSchema** メソッドを使用して **officedata** の XML 名前空間を無視するように指定します。この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b7fd4-135">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7fd4-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7fd4-136">See also</span></span>

- [<span data-ttu-id="b7fd4-137">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="b7fd4-137">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="b7fd4-138">XML スキーマ (XSD) からの DataSet リレーショナル構造の派生</span><span class="sxs-lookup"><span data-stu-id="b7fd4-138">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="b7fd4-139">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="b7fd4-139">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="b7fd4-140">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="b7fd4-140">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="b7fd4-141">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="b7fd4-141">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="b7fd4-142">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="b7fd4-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
