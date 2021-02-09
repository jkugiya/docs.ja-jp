---
description: '詳細情報: XSD としての DataSet スキーマ情報の書き込み'
title: XSD としての DataSet スキーマ情報の書き込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: e05188c74ca21e73ee5151da817e143102640a13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651354"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="c4453-103">XSD としての DataSet スキーマ情報の書き込み</span><span class="sxs-lookup"><span data-stu-id="c4453-103">Writing DataSet Schema Information as XSD</span></span>

<span data-ttu-id="c4453-104"><xref:System.Data.DataSet> のスキーマを XML スキーマ定義言語 (XSD) スキーマとして書き込むと、このスキーマを XML ドキュメントに転送できます。このとき関連データを含む定義、または関連データを含まない定義ができます。</span><span class="sxs-lookup"><span data-stu-id="c4453-104">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="c4453-105">XML スキーマはファイル、ストリーム、<xref:System.Xml.XmlWriter>、または文字列に書き込むことができるため、厳密に型指定された **DataSet** を生成するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c4453-105">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="c4453-106">厳密に型指定された **DataSet** オブジェクトの詳細については、「[型指定されたデータセット](typed-datasets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4453-106">For more information about strongly typed **DataSet** objects, see [Typed DataSets](typed-datasets.md).</span></span>  
  
 <span data-ttu-id="c4453-107">テーブルの列を XML スキーマで表す方法を指定するには、<xref:System.Data.DataColumn> オブジェクトの **ColumnMapping** プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4453-107">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="c4453-108">詳細については、「[DataSet 内容の XML データとしての書き込み](writing-dataset-contents-as-xml-data.md)」の「XML 要素、属性、およびテキストへの列の割り当て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4453-108">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="c4453-109">**DataSet** のスキーマを XML スキーマとしてファイル、ストリーム、または **XmlWriter** に書き込むには、**DataSet** の **WriteXmlSchema** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4453-109">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="c4453-110">**WriteXmlSchema** は、XML スキーマの書き込み先を指定するパラメーターを 1 つ受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c4453-110">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="c4453-111">次のコード例では、ファイル名が含まれる文字列と <xref:System.IO.StreamWriter> オブジェクトを渡して **DataSet** の XML スキーマをファイルに書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c4453-111">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 <span data-ttu-id="c4453-112">**DataSet** のスキーマを取得し、XML スキーマ文字列として書き込むには、次の例に示すように、**GetXmlSchema** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4453-112">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4453-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4453-113">See also</span></span>

- [<span data-ttu-id="c4453-114">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="c4453-114">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="c4453-115">DataSet 内容の XML データとしての書き込み</span><span class="sxs-lookup"><span data-stu-id="c4453-115">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)
- [<span data-ttu-id="c4453-116">型指定されたデータセット</span><span class="sxs-lookup"><span data-stu-id="c4453-116">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="c4453-117">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="c4453-117">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="c4453-118">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="c4453-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
