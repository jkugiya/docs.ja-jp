---
description: '詳細情報: DataSet への XSLT 変換の適用'
title: DataSet への XSLT 変換の適用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: c7fc25441091112f7fbb7e4c1f8dd210d8cd0c5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725117"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a><span data-ttu-id="054e1-103">DataSet への XSLT 変換の適用</span><span class="sxs-lookup"><span data-stu-id="054e1-103">Applying an XSLT Transform to a DataSet</span></span>

<span data-ttu-id="054e1-104"><xref:System.Data.DataSet> の **WriteXml** メソッドを使用すると、**DataSet** の内容を XML データとして書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="054e1-104">The **WriteXml** method of the <xref:System.Data.DataSet> enables you to write the contents of a **DataSet** as XML data.</span></span> <span data-ttu-id="054e1-105">一般的な作業は、XSLT (XSL Transformation) を使用してこの XML を別の形式へ変換する操作です。</span><span class="sxs-lookup"><span data-stu-id="054e1-105">A common task is to then transform that XML to another format using XSL transformations (XSLT).</span></span> <span data-ttu-id="054e1-106">ただし **DataSet** を <xref:System.Xml.XmlDataDocument> と同期することで、最初に **WriteXml** を使用して **DataSet** の内容を XML データとして書き込む操作を実行せずに、**DataSet** の内容に XSLT スタイルシートを適用できます。</span><span class="sxs-lookup"><span data-stu-id="054e1-106">However, synchronizing a **DataSet** with an <xref:System.Xml.XmlDataDocument> enables you to apply an XSLT stylesheet to the contents of a **DataSet** without having to first write the contents of the **DataSet** as XML data using **WriteXml**.</span></span>  
  
 <span data-ttu-id="054e1-107">**DataSet** にテーブルとリレーションシップを格納し、**DataSet** を **XmlDataDocument** と同期し、XSLT スタイルシートを使用して **DataSet** の一部を HTML ファイルとして書き込む例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="054e1-107">The following example populates a **DataSet** with tables and relationships, synchronizes the **DataSet** with an **XmlDataDocument**, and writes a portion of the **DataSet** as an HTML file using an XSLT stylesheet.</span></span> <span data-ttu-id="054e1-108">次に示すのは、XSLT スタイルシートの内容です。</span><span class="sxs-lookup"><span data-stu-id="054e1-108">The following are the contents of the XSLT stylesheet:</span></span>
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
<xsl:template match="CustomerOrders">  
  <HTML>  
  <STYLE>  
  BODY {font-family:verdana;font-size:9pt}  
  TD   {font-size:8pt}  
  </STYLE>  
    <BODY>  
    <TABLE BORDER="1">  
      <xsl:apply-templates select="Customers"/>  
    </TABLE>  
    </BODY>  
  </HTML>  
</xsl:template>  
  
<xsl:template match="Customers">  
    <TR><TD>  
      <xsl:value-of select="ContactName"/>, <xsl:value-of select="Phone"/><BR/>  
    </TD></TR>  
      <xsl:apply-templates select="Orders"/>  
</xsl:template>  
  
<xsl:template match="Orders">  
  <TABLE BORDER="1">  
    <TR><TD valign="top"><B>Order:</B></TD><TD valign="top"><xsl:value-of select="OrderID"/></TD></TR>  
    <TR><TD valign="top"><B>Date:</B></TD><TD valign="top"><xsl:value-of select="OrderDate"/></TD></TR>  
    <TR><TD valign="top"><B>Ship To:</B></TD>  
        <TD valign="top"><xsl:value-of select="ShipName"/><BR/>  
        <xsl:value-of select="ShipAddress"/><BR/>  
        <xsl:value-of select="ShipCity"/>, <xsl:value-of select="ShipRegion"/>  <xsl:value-of select="ShipPostalCode"/><BR/>  
        <xsl:value-of select="ShipCountry"/></TD></TR>  
  </TABLE>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="054e1-109">次のコードは、**DataSet** にデータを格納し、XSLT スタイル シートを適用します。</span><span class="sxs-lookup"><span data-stu-id="054e1-109">The following code fills the **DataSet** and applies the XSLT style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="054e1-110">リレーションシップが含まれている **DataSet** に XSLT スタイル シートを適用する場合は、入れ子になっているリレーションシップごとに <xref:System.Data.DataRelation> の **Nested** プロパティを **true** に設定すると、パフォーマンスが最大になります。</span><span class="sxs-lookup"><span data-stu-id="054e1-110">If you are applying an XSLT style sheet to a **DataSet** that contains relations, you achieve best performance if you set the **Nested** property of the <xref:System.Data.DataRelation> to **true** for each nested relation.</span></span> <span data-ttu-id="054e1-111">これにより、階層を自然な順番で上から下へと進みながらデータを変換する XSLT スタイル シートを利用できるようになります。パフォーマンスに大きく影響する XPath ロケーション軸 (たとえば、スタイル シートのノード テスト式での preceding-sibling や following-sibling) を使用して階層をたどる必要はなくなります。</span><span class="sxs-lookup"><span data-stu-id="054e1-111">This allows you to use XSLT style sheets that implement natural top-down processing to navigate the hierarchy and transform the data, as opposed to using performance-intensive XPath location axes (for example, preceding-sibling and following-sibling in style sheet node test expressions) to navigate it.</span></span> <span data-ttu-id="054e1-112">入れ子になったリレーションの詳細については、「[DataRelation の入れ子化](nesting-datarelations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="054e1-112">For more information on nested relations, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)
  
Dim xslTran As XslTransform = New XslTransform  
xslTran.Load("transform.xsl")  
  
Dim writer As XmlTextWriter = New XmlTextWriter( _  
  "xslt_output.html", System.Text.Encoding.UTF8)  
  
xslTran.Transform(xmlDoc, Nothing, writer)  
writer.Close()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
DataSet custDS = new DataSet("CustomerDataSet");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(custDS, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(custDS, "Orders");  
  
connection.Close();  
  
custDS.Relations.Add("CustOrders",  
  custDS.Tables["Customers"].Columns["CustomerID"],  
                     custDS.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(custDS);
  
XslTransform xslTran = new XslTransform();  
xslTran.Load("transform.xsl");  
  
XmlTextWriter writer = new XmlTextWriter("xslt_output.html",
  System.Text.Encoding.UTF8);  
  
xslTran.Transform(xmlDoc, null, writer);  
writer.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="054e1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="054e1-113">See also</span></span>

- [<span data-ttu-id="054e1-114">DataSet と XmlDataDocument の同期</span><span class="sxs-lookup"><span data-stu-id="054e1-114">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="054e1-115">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="054e1-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
