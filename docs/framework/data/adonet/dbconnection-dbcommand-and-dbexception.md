---
description: '詳細情報: DbConnection、DbCommand、および DbException'
title: DbConnection、DbCommand、および DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: b5cb748a8dd5fb06f2f5dc5ab0479a679b2cc07d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651276"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="c75e5-103">DbConnection、DbCommand、および DbException</span><span class="sxs-lookup"><span data-stu-id="c75e5-103">DbConnection, DbCommand and DbException</span></span>

<span data-ttu-id="c75e5-104"><xref:System.Data.Common.DbProviderFactory> および <xref:System.Data.Common.DbConnection> を作成すると、コマンドおよびデータ リーダーを使用してデータ ソースからデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="c75e5-104">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="c75e5-105">データの取得例</span><span class="sxs-lookup"><span data-stu-id="c75e5-105">Retrieving Data Example</span></span>  

 <span data-ttu-id="c75e5-106">次のコード例は、`DbConnection` オブジェクトを引数として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c75e5-106">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="c75e5-107"><xref:System.Data.Common.DbCommand> に SQL SELECT ステートメントを設定することによって、Categories テーブルからデータを検索するための <xref:System.Data.Common.DbCommand.CommandText%2A> を作成します。</span><span class="sxs-lookup"><span data-stu-id="c75e5-107">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="c75e5-108">このコードを実行するには、データ ソースに Categories テーブルが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c75e5-108">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="c75e5-109">接続を開いた後、<xref:System.Data.Common.DbDataReader> を使用してデータが取得されます。</span><span class="sxs-lookup"><span data-stu-id="c75e5-109">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="c75e5-110">コマンド実行例</span><span class="sxs-lookup"><span data-stu-id="c75e5-110">Executing a Command Example</span></span>  

 <span data-ttu-id="c75e5-111">次のコード例は、`DbConnection` オブジェクトを引数として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c75e5-111">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="c75e5-112">`DbConnection` が有効である場合、接続が開かれ、<xref:System.Data.Common.DbCommand> が作成されて実行されます。</span><span class="sxs-lookup"><span data-stu-id="c75e5-112">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="c75e5-113"><xref:System.Data.Common.DbCommand.CommandText%2A> には、Northwind データベースの Categories テーブルへの挿入操作を実行する SQL INSERT ステートメントが設定されています。</span><span class="sxs-lookup"><span data-stu-id="c75e5-113">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="c75e5-114">このコードを実行するには、データ ソースに Northwind データベースが存在すること、および、指定されたプロバイダーの有効な SQL 構文が INSERT ステートメントに使用されていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="c75e5-114">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="c75e5-115">データ ソースで発生したエラーは <xref:System.Data.Common.DbException> コード ブロックで処理され、それ以外のすべての例外は <xref:System.Exception> ブロックで処理されます。</span><span class="sxs-lookup"><span data-stu-id="c75e5-115">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="c75e5-116">DbException でのデータ エラーの処理</span><span class="sxs-lookup"><span data-stu-id="c75e5-116">Handling Data Errors with DbException</span></span>  

 <span data-ttu-id="c75e5-117"><xref:System.Data.Common.DbException> クラスは、データ ソースでスローされるすべての例外の基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="c75e5-117">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="c75e5-118">このクラスを例外処理コードに使用することで、プロバイダーに固有の例外クラスを参照することなく、各種のプロバイダーによってスローされる例外を処理できます。</span><span class="sxs-lookup"><span data-stu-id="c75e5-118">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="c75e5-119">次のコード フラグメントでは、<xref:System.Data.Common.DbException> の各プロパティ (<xref:System.Exception.GetType%2A>、<xref:System.Exception.Source%2A>、<xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>、および <xref:System.Exception.Message%2A>) を使って、データ ソースから返されたエラー情報を表示しています。</span><span class="sxs-lookup"><span data-stu-id="c75e5-119">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="c75e5-120">出力結果には、エラーの種類、エラーの発生元 (プロバイダー名)、エラー コード、および、エラーに関連付けられたメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c75e5-120">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c75e5-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="c75e5-121">See also</span></span>

- [<span data-ttu-id="c75e5-122">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="c75e5-122">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="c75e5-123">DbProviderFactory の取得</span><span class="sxs-lookup"><span data-stu-id="c75e5-123">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="c75e5-124">DbDataAdapter を使用したデータの変更</span><span class="sxs-lookup"><span data-stu-id="c75e5-124">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="c75e5-125">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="c75e5-125">ADO.NET Overview</span></span>](ado-net-overview.md)
