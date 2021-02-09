---
description: '詳細情報: SQL XML 列値'
title: SQL XML 列値
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 357d55e2ce497c9929b8e7e7459ebf23ccaafede
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767181"
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="18502-103">SQL XML 列値</span><span class="sxs-lookup"><span data-stu-id="18502-103">SQL XML Column Values</span></span>

<span data-ttu-id="18502-104">SQL Server では、`xml` データ型をサポートしています。開発者は、<xref:System.Data.SqlClient.SqlCommand> クラスの標準動作を使用し、この型を含む結果セットを取得できます。</span><span class="sxs-lookup"><span data-stu-id="18502-104">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="18502-105">任意の列が (<xref:System.Data.SqlClient.SqlDataReader> などに) 取得されるように、`xml` 列を取得できますが、列のコンテンツを XML として操作する必要がある場合は、<xref:System.Xml.XmlReader> を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18502-105">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18502-106">例</span><span class="sxs-lookup"><span data-stu-id="18502-106">Example</span></span>  

 <span data-ttu-id="18502-107">次のコンソール アプリケーションでは、**AdventureWorks** データベースの **Sales.Store** テーブルから 2 行を選択し、この行の `xml` 列を <xref:System.Data.SqlClient.SqlDataReader> インスタンスに格納します。</span><span class="sxs-lookup"><span data-stu-id="18502-107">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="18502-108">行ごとに、<xref:System.Data.SqlClient.SqlDataReader> の <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> メソッドを使用して `xml` 列の値が読み取られます。</span><span class="sxs-lookup"><span data-stu-id="18502-108">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="18502-109">この値は <xref:System.Xml.XmlReader> に格納されます。</span><span class="sxs-lookup"><span data-stu-id="18502-109">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="18502-110">コンテンツを <xref:System.Data.SqlTypes.SqlXml> 変数に設定する場合は、<xref:System.Data.IDataRecord.GetValue%2A> メソッドではなく <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> を使用する必要があることに注意してください。<xref:System.Data.IDataRecord.GetValue%2A> は、`xml` 列の値を文字列として返します。</span><span class="sxs-lookup"><span data-stu-id="18502-110">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18502-111">**AdventureWorks** サンプル データベースは、既定では SQL Server のインストール時にはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="18502-111">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="18502-112">SQL Server Setup を実行してインストールします。</span><span class="sxs-lookup"><span data-stu-id="18502-112">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="18502-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="18502-113">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="18502-114">SQL Server における XML データ</span><span class="sxs-lookup"><span data-stu-id="18502-114">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)
- [<span data-ttu-id="18502-115">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="18502-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
