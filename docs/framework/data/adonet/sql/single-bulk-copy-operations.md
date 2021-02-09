---
description: '詳細情報: バルク コピー操作の単一実行'
title: バルク コピー操作の単一実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: f6b046fbd73ad798f3f9f117eea0b72f46e43b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767480"
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="22004-103">バルク コピー操作の単一実行</span><span class="sxs-lookup"><span data-stu-id="22004-103">Single Bulk Copy Operations</span></span>

<span data-ttu-id="22004-104">SQL Server のバルク コピー操作を実行する簡単な方法は、データベースに対して単一操作を実行することです。</span><span class="sxs-lookup"><span data-stu-id="22004-104">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="22004-105">既定では、一括コピー操作は分離された操作として実行されます。このコピー操作は非トランザクション方式で処理され、ロールバックできません。</span><span class="sxs-lookup"><span data-stu-id="22004-105">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>

> [!NOTE]
> <span data-ttu-id="22004-106">エラーの発生時に、バルク コピー処理の全部または一部をロールバックする必要がある場合は、<xref:System.Data.SqlClient.SqlBulkCopy> が管理するトランザクションを使用するか、または既存のトランザクション内でバルク コピー操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="22004-106">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="22004-107">**SqlBulkCopy** は、**System.Transactions** トランザクションに (明示的または暗黙的に) 接続が参加している場合は <xref:System.Transactions> も使用します。</span><span class="sxs-lookup"><span data-stu-id="22004-107">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>
>
> <span data-ttu-id="22004-108">詳細については、「[トランザクションと一括コピー操作](transaction-and-bulk-copy-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22004-108">For more information, see [Transaction and Bulk Copy Operations](transaction-and-bulk-copy-operations.md).</span></span>

<span data-ttu-id="22004-109">通常、バルク コピー操作の実行手順は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="22004-109">The general steps for performing a bulk copy operation are as follows:</span></span>

1. <span data-ttu-id="22004-110">コピー元のサーバーに接続し、コピーするデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="22004-110">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="22004-111"><xref:System.Data.IDataReader> オブジェクトまたは <xref:System.Data.DataTable> オブジェクトからデータを取得できる場合は、他のソースから取得する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="22004-111">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>

2. <span data-ttu-id="22004-112">コピー先のサーバーに接続します (**SqlBulkCopy** を使用して接続を確立しない場合)。</span><span class="sxs-lookup"><span data-stu-id="22004-112">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>

3. <span data-ttu-id="22004-113"><xref:System.Data.SqlClient.SqlBulkCopy> オブジェクトを作成し、必要なプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="22004-113">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>

4. <span data-ttu-id="22004-114">バルク挿入操作の対象となるテーブルが示されるように **DestinationTableName** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="22004-114">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>

5. <span data-ttu-id="22004-115">**WriteToServer** メソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="22004-115">Call one of the **WriteToServer** methods.</span></span>

6. <span data-ttu-id="22004-116">オプションとして、プロパティを更新したり、必要に応じて **WriteToServer** をもう一度呼び出したりします。</span><span class="sxs-lookup"><span data-stu-id="22004-116">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>

7. <span data-ttu-id="22004-117"><xref:System.Data.SqlClient.SqlBulkCopy.Close%2A> を呼び出すか、一括コピー操作を `Using` ステートメント内にラップします。</span><span class="sxs-lookup"><span data-stu-id="22004-117">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>

> [!CAUTION]
> <span data-ttu-id="22004-118">コピー元とコピー先の列のデータ型を一致させることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="22004-118">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="22004-119">データ型が一致していない場合、**SqlBulkCopy** は、<xref:System.Data.SqlClient.SqlParameter.Value%2A> によって採用されている規則を使用して、コピー元の値をコピー先のデータ型にそれぞれ変換しようとします。</span><span class="sxs-lookup"><span data-stu-id="22004-119">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="22004-120">この変換はパフォーマンスに影響を及ぼし、予期しないエラーが発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="22004-120">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="22004-121">たとえば、`Double` データ型は、多くの場合 `Decimal` データ型に変換されますが、常にというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="22004-121">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>

## <a name="example"></a><span data-ttu-id="22004-122">例</span><span class="sxs-lookup"><span data-stu-id="22004-122">Example</span></span>

<span data-ttu-id="22004-123">次のコンソール アプリケーションは、<xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用してデータを読み込む方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="22004-123">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="22004-124">この例では、<xref:System.Data.SqlClient.SqlDataReader> を使用し、SQL Server の **AdventureWorks** データベースに格納された **Production.Product** テーブルのデータを、同じデータベース内の同等のテーブルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="22004-124">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server **AdventureWorks** database to a similar table in the same database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22004-125">このサンプルは、「[一括コピーのセットアップ例](bulk-copy-example-setup.md)」で説明しているように作業テーブルを作成して取得してからでないと動作しません。</span><span class="sxs-lookup"><span data-stu-id="22004-125">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](bulk-copy-example-setup.md).</span></span> <span data-ttu-id="22004-126">このコードでは、**SqlBulkCopy** だけを使用した構文について説明します。</span><span class="sxs-lookup"><span data-stu-id="22004-126">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="22004-127">コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL `INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="22004-127">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>

[!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
[!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]

## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="22004-128">Transact-SQL および Command クラスを使用したバルク コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="22004-128">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>

<span data-ttu-id="22004-129">次の例では、BULK INSERT ステートメントを実行する <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> メソッドの使用方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="22004-129">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>

> [!NOTE]
> <span data-ttu-id="22004-130">データ ソースのファイル パスはサーバーに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="22004-130">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="22004-131">サーバー プロセスがこのパスにアクセスできないと、バルク コピー操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="22004-131">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>

```vb
Using connection As SqlConnection = New SqlConnection(connectionString)
Dim queryString As String = _
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"
connection.Open()
SqlCommand command = New SqlCommand(queryString, connection);

command.ExecuteNonQuery()
End Using
```

```csharp
using (SqlConnection connection = New SqlConnection(connectionString))
{
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +
    "FROM 'f:\mydata\data.tbl' " +
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";
connection.Open();
SqlCommand command = new SqlCommand(queryString, connection);

command.ExecuteNonQuery();
}
```

## <a name="see-also"></a><span data-ttu-id="22004-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="22004-132">See also</span></span>

- [<span data-ttu-id="22004-133">SQL Server でのバルク コピー操作</span><span class="sxs-lookup"><span data-stu-id="22004-133">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="22004-134">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="22004-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
