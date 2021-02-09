---
description: '詳細情報: データ ソースのデータの更新'
title: データ ソースのデータの更新
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: a55d6a53f4607908fa279474419803eac3963909
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766570"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="84fdf-103">データ ソースのデータの更新</span><span class="sxs-lookup"><span data-stu-id="84fdf-103">Updating Data in a Data Source</span></span>

<span data-ttu-id="84fdf-104">データを変更する SQL ステートメント (INSERT、UPDATE、DELETE など) は行を返しません。</span><span class="sxs-lookup"><span data-stu-id="84fdf-104">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="84fdf-105">同様に、多くのストアド プロシージャは、アクションを実行しても行を返しません。</span><span class="sxs-lookup"><span data-stu-id="84fdf-105">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="84fdf-106">行を返さないコマンドを実行するには、適切な SQL コマンドを使用して **Command** オブジェクトを作成し、必要な **Parameters** を含む **Connection** を作成します。</span><span class="sxs-lookup"><span data-stu-id="84fdf-106">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="84fdf-107">**Command** オブジェクトの **ExecuteNonQuery** メソッドでコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="84fdf-107">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="84fdf-108">**ExecuteNonQuery** メソッドからは、実行されたステートメントまたはストアド プロシージャの影響を受けた行数を表す整数が返されます。</span><span class="sxs-lookup"><span data-stu-id="84fdf-108">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="84fdf-109">複数のステートメントが実行された場合は、実行された各ステートメントの影響を受けたレコードの合計を示す値が返されます。</span><span class="sxs-lookup"><span data-stu-id="84fdf-109">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84fdf-110">例</span><span class="sxs-lookup"><span data-stu-id="84fdf-110">Example</span></span>  

 <span data-ttu-id="84fdf-111">INSERT ステートメントを実行して、**ExecuteNonQuery** でデータベースにレコードを挿入するコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="84fdf-111">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 <span data-ttu-id="84fdf-112">「[カタログ操作の実行](performing-catalog-operations.md)」と同じコードで作成されたストアド プロシージャを実行するコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="84fdf-112">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="84fdf-113">ストアド プロシージャは行を返さないため **ExecuteNonQuery** メソッドが使用されていますが、ストアド プロシージャは入力パラメーターを受け取り、出力パラメーターと戻り値を返します。</span><span class="sxs-lookup"><span data-stu-id="84fdf-113">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="84fdf-114"><xref:System.Data.OleDb.OleDbCommand> オブジェクトの場合は、最初に **Parameters** コレクションに **ReturnValue** パラメーターを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84fdf-114">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a><span data-ttu-id="84fdf-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="84fdf-115">See also</span></span>

- [<span data-ttu-id="84fdf-116">コマンドを使用したデータ変更</span><span class="sxs-lookup"><span data-stu-id="84fdf-116">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="84fdf-117">DataAdapter によるデータ ソースの更新</span><span class="sxs-lookup"><span data-stu-id="84fdf-117">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="84fdf-118">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="84fdf-118">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="84fdf-119">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="84fdf-119">ADO.NET Overview</span></span>](ado-net-overview.md)
