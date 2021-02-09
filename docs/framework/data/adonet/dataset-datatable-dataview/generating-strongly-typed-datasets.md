---
description: '詳細情報: 厳密に型指定された DataSet の生成'
title: 厳密に型指定された DataSet の生成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: c69aecc5a0a541c868dac3037c9dd0dbc3fe8383
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652433"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="ce568-103">厳密に型指定された DataSet の生成</span><span class="sxs-lookup"><span data-stu-id="ce568-103">Generating Strongly Typed DataSets</span></span>

<span data-ttu-id="ce568-104">XML スキーマ定義言語 (XSD) 標準に準拠する XML スキーマがあれば、Windows ソフトウェア開発キット (SDK) に付属する XSD.exe ツールを使用して、厳密に型指定された <xref:System.Data.DataSet> を生成できます。</span><span class="sxs-lookup"><span data-stu-id="ce568-104">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the Windows Software Development Kit (SDK).</span></span>  
  
 <span data-ttu-id="ce568-105">(データベース テーブルから xsd を作成するには、<xref:System.Data.DataSet.WriteXmlSchema%2A> に関するトピック、または「[Visual Studio でのデータセットの操作](/visualstudio/data-tools/dataset-tools-in-visual-studio)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="ce568-105">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span></span>  
  
 <span data-ttu-id="ce568-106">次のコードでは、このツールを使用して **DataSet** を生成する構文を示します。</span><span class="sxs-lookup"><span data-stu-id="ce568-106">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```console  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="ce568-107">この構文の `/d` ディレクティブでは、**DataSet** を生成することをツールに指示し、`/l:` では使用する言語 (C#、Visual Basic .NET など) をツールに指示します。</span><span class="sxs-lookup"><span data-stu-id="ce568-107">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="ce568-108">オプションの `/eld` ディレクティブを指定すると、生成された **DataSet** に対し、LINQ to DataSet を使用してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ce568-108">The optional `/eld` directive specifies that you can use LINQ to DataSet to query against the generated **DataSet.**</span></span> <span data-ttu-id="ce568-109">このオプションは、`/d` オプションと組み合わせて指定します。</span><span class="sxs-lookup"><span data-stu-id="ce568-109">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="ce568-110">詳しくは、「[型指定された DataSet のクエリ](../querying-typed-datasets.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ce568-110">For more information, see [Querying Typed DataSets](../querying-typed-datasets.md).</span></span> <span data-ttu-id="ce568-111">オプションの `/n:` ディレクティブでは、**XSDSchema.Namespace** という名前の名前空間も **DataSet** に対して生成することをツールに指示します。</span><span class="sxs-lookup"><span data-stu-id="ce568-111">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="ce568-112">コマンドの出力は XSDSchemaFileName.cs で、ADO.NET アプリケーションでコンパイルおよび使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce568-112">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="ce568-113">生成されたコードをライブラリまたはモジュールとしてコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="ce568-113">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="ce568-114">C# コンパイラ (csc.exe) を使用して、生成されたコードをライブラリとしてコンパイルする構文を次のコードで示します。</span><span class="sxs-lookup"><span data-stu-id="ce568-114">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```console  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="ce568-115">`/t:` ディレクティブはライブラリとしてコンパイルすることをツールに知らせ、`/r:` ディレクティブはコンパイルに必要な依存ライブラリを指定します。</span><span class="sxs-lookup"><span data-stu-id="ce568-115">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="ce568-116">コマンドの出力は XSDSchemaFileName.dll で、`/r:` ディレクティブによる ADO.NET アプリケーションのコンパイル時にコンパイラに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="ce568-116">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="ce568-117">ADO.NET アプリケーションの XSD.exe に渡された名前空間にアクセスする構文を次のコードで示します。</span><span class="sxs-lookup"><span data-stu-id="ce568-117">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="ce568-118">次のコード例では、**CustomerDataSet** という名前の型指定された **DataSet** を使用して、**Northwind** データベースから顧客リストを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="ce568-118">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="ce568-119">**Fill** メソッドを使用してデータを読み込んだ後、例では、型指定された **CustomersRow** (**DataRow**) オブジェクトを使用して、**Customers** テーブルの各顧客をループします。</span><span class="sxs-lookup"><span data-stu-id="ce568-119">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="ce568-120">このようにすると、**DataColumnCollection** による場合とは異なり、**CustomerID** 列に直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ce568-120">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 <span data-ttu-id="ce568-121">例に使用された XML スキーマを次に示します。</span><span class="sxs-lookup"><span data-stu-id="ce568-121">The following is the XML Schema used for the example:</span></span>
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce568-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce568-122">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="ce568-123">型指定されたデータセット</span><span class="sxs-lookup"><span data-stu-id="ce568-123">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="ce568-124">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="ce568-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="ce568-125">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="ce568-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
