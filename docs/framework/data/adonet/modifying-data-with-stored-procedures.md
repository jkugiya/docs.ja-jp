---
description: '詳細情報: ストアド プロシージャでのデータの変更'
title: ストアド プロシージャでのデータの変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 66a4aa9577c71605bde0152a142a65dfa81a31d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786226"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="561d2-103">ストアド プロシージャでのデータの変更</span><span class="sxs-lookup"><span data-stu-id="561d2-103">Modifying Data with Stored Procedures</span></span>

<span data-ttu-id="561d2-104">ストアド プロシージャは、入力パラメーターとしてデータを受け取り、出力パラメーター、結果セット、または戻り値としてデータを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="561d2-104">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="561d2-105">以下のサンプルでは、入力パラメーター、出力パラメーター、および戻り値が ADO.NET によってどのようにやり取りされるかを示したものです。</span><span class="sxs-lookup"><span data-stu-id="561d2-105">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="561d2-106">この例では、主キー列が SQL Server データベースの ID 列であるテーブルに新しいレコードを挿入しています。</span><span class="sxs-lookup"><span data-stu-id="561d2-106">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="561d2-107">SQL Server のストアド プロシージャで、<xref:System.Data.SqlClient.SqlDataAdapter> を使用してデータを編集または削除する場合、ストアド プロシージャの定義に SET NOCOUNT ON は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="561d2-107">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="561d2-108">処理された行数がゼロとして返され、`DataAdapter` によってコンカレンシーの競合として解釈されてしまいます。</span><span class="sxs-lookup"><span data-stu-id="561d2-108">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="561d2-109">この場合、<xref:System.Data.DBConcurrencyException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="561d2-109">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="561d2-110">例</span><span class="sxs-lookup"><span data-stu-id="561d2-110">Example</span></span>  

 <span data-ttu-id="561d2-111">この例では、次のストアド プロシージャを使用して、**Northwind** **Categories** テーブルに新しいカテゴリを挿入します。</span><span class="sxs-lookup"><span data-stu-id="561d2-111">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="561d2-112">このストアド プロシージャは、**CategoryName** 列の値を入力パラメーターとして受け取り、SCOPE_IDENTITY() 関数を使用して ID フィールド **CategoryID** の新しい値を取得し、その値を出力パラメーター内に返します。</span><span class="sxs-lookup"><span data-stu-id="561d2-112">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="561d2-113">RETURN ステートメントは、@@ROWCOUNT 関数を使用して、挿入された行の数を返します。</span><span class="sxs-lookup"><span data-stu-id="561d2-113">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="561d2-114">上述の `InsertCategory` ストアド プロシージャを <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> の <xref:System.Data.SqlClient.SqlDataAdapter> のソースとして使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="561d2-114">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="561d2-115">`@Identity` 出力パラメーターは、<xref:System.Data.DataSet> の `Update` メソッドが呼び出され、データベースにレコードが挿入された後で <xref:System.Data.SqlClient.SqlDataAdapter> に反映されます。</span><span class="sxs-lookup"><span data-stu-id="561d2-115">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="561d2-116">戻り値も取得されます。</span><span class="sxs-lookup"><span data-stu-id="561d2-116">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="561d2-117"><xref:System.Data.OleDb.OleDbDataAdapter> を使用するときは、**ReturnValue** の <xref:System.Data.ParameterDirection> を含むパラメーターを、他のパラメーターより先に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="561d2-117">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="561d2-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="561d2-118">See also</span></span>

- [<span data-ttu-id="561d2-119">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="561d2-119">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="561d2-120">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="561d2-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="561d2-121">コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="561d2-121">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="561d2-122">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="561d2-122">ADO.NET Overview</span></span>](ado-net-overview.md)
