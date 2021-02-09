---
description: '詳細情報: 接続の確立'
title: 接続の確立
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: e7f8c837476a678f003eb0477934bb8bd08fd896
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724337"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="ec41b-103">接続の確立</span><span class="sxs-lookup"><span data-stu-id="ec41b-103">Establishing the Connection</span></span>

<span data-ttu-id="ec41b-104">Microsoft SQL Server に接続する場合は、.NET Framework Data Provider for SQL Server の <xref:System.Data.SqlClient.SqlConnection> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-104">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="ec41b-105">OLE DB データ ソースに接続する場合は、.NET Framework Data Provider for OLE DB の <xref:System.Data.OleDb.OleDbConnection> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-105">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="ec41b-106">ODBC データ ソースに接続する場合は、.NET Framework Data Provider for ODBC の <xref:System.Data.Odbc.OdbcConnection> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-106">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="ec41b-107">Oracle データ ソースに接続する場合は、.NET Framework Data Provider for Oracle の <xref:System.Data.OracleClient.OracleConnection> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-107">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="ec41b-108">安全な接続文字列の格納および取得については、「[接続情報の保護](protecting-connection-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-108">For securely storing and retrieving connection strings, see [Protecting Connection Information](protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="ec41b-109">接続の終了</span><span class="sxs-lookup"><span data-stu-id="ec41b-109">Closing Connections</span></span>  

 <span data-ttu-id="ec41b-110">接続がプールに返されるようにするために、接続を使い終えたら必ず接続を終了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec41b-110">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="ec41b-111">Visual Basic または C# の `Using` ブロックは、コードがこのブロックを終了したときに接続を破棄します。これは、未処理の例外の場合でも実行されます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-111">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="ec41b-112">詳しくは、「[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)」および「[Using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-112">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) and [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="ec41b-113">また、使用しているプロバイダーの接続オブジェクトの `Close` または `Dispose` メソッドを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-113">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="ec41b-114">明示的に終了されていない接続は、プールに追加したり返したりすることができないことがあります。</span><span class="sxs-lookup"><span data-stu-id="ec41b-114">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="ec41b-115">たとえば、スコープ外に出ても、明示的に終了されていない接続は、最大プール サイズに達した時点でその接続がまだ有効である場合にだけ接続プールに返されます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-115">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="ec41b-116">詳しくは、「[OLE DB、ODBC、および Oracle 接続プール](ole-db-odbc-and-oracle-connection-pooling.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-116">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec41b-117">クラスの `Finalize` メソッド内で、**Connection**、**DataReader**、またはその他のマネージド オブジェクトの `Close` または `Dispose` を呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-117">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="ec41b-118">終了処理では、クラスに直接所有されているアンマネージ リソースだけを解放してください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-118">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="ec41b-119">クラスがアンマネージ リソースを所有していない場合は、クラス定義に `Finalize` メソッドを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-119">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="ec41b-120">詳しくは、「[ガベージ コレクション](../../../standard/garbage-collection/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-120">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec41b-121">接続が接続プールからフェッチされたり接続プールに返されたりしたとき、ログイン イベントとログアウト イベントはサーバーで発生しません。これは、接続プールに返されても接続は実際には終了していないためです。</span><span class="sxs-lookup"><span data-stu-id="ec41b-121">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="ec41b-122">詳しくは、「[SQL Server の接続プール (ADO.NET)](sql-server-connection-pooling.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-122">For more information, see [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="ec41b-123">SQL Server への接続</span><span class="sxs-lookup"><span data-stu-id="ec41b-123">Connecting to SQL Server</span></span>  

 <span data-ttu-id="ec41b-124">.NET Framework Data Provider for SQL Server は、OLE DB (ADO) 接続文字列フォーマットに似た接続文字列フォーマットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="ec41b-124">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="ec41b-125">有効な文字列フォーマットの名前および値については、<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> プロパティを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-125">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="ec41b-126">また、<xref:System.Data.SqlClient.SqlConnectionStringBuilder> クラスを使用すると、構文的に正しい接続文字列を実行時に作成できます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-126">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="ec41b-127">詳細については、「[接続文字列ビルダー](connection-string-builders.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-127">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="ec41b-128">SQL Server のデータベースへの接続を開いて確立する方法を次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-128">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="ec41b-129">統合セキュリティと ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ec41b-129">Integrated Security and ASP.NET</span></span>  

 <span data-ttu-id="ec41b-130">SQL Server 統合セキュリティ (信頼関係接続とも呼ばれます) は、SQL Server への接続を保護します。接続文字列でユーザー ID とパスワードを公開することがなく、接続の認証用に推奨されている方法でもあるためです。</span><span class="sxs-lookup"><span data-stu-id="ec41b-130">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="ec41b-131">統合セキュリティでは、実行中のプロセスの現在のセキュリティ ID またはトークンを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-131">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="ec41b-132">これは、デスクトップ アプリケーションでは通常、現在ログオンしているユーザーの ID です。</span><span class="sxs-lookup"><span data-stu-id="ec41b-132">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="ec41b-133">ASP.NET アプリケーションのセキュリティ ID は、他のオプションのうちのいずれかに設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-133">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="ec41b-134">SQL Server に接続するときに ASP.NET アプリケーションが使用するセキュリティ ID の詳細については、「[ASP.NET の偽装](/previous-versions/aspnet/xh507fc5(v=vs.100))」、「[ASP.NET の認証](/previous-versions/aspnet/eeyk640h(v=vs.100))」、および「[方法: Windows 統合セキュリティを使用して SQL Server にアクセスする](/previous-versions/aspnet/bsz5788z(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-134">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="ec41b-135">OLE DB データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="ec41b-135">Connecting to an OLE DB Data Source</span></span>  

 <span data-ttu-id="ec41b-136">.NET Framework Data Provider for OLE DB では、**OleDbConnection** オブジェクトを使用して、OLE DB によって公開されているデータ ソースへの接続が (SQLOLEDB: OLE DB Provider for SQL Server を通じて) 提供されます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-136">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="ec41b-137">.NET Framework Data Provider for OLE DB で使用される接続文字列フォーマットは ADO で使用される接続文字列フォーマットと同じですが、次の例外があります。</span><span class="sxs-lookup"><span data-stu-id="ec41b-137">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
- <span data-ttu-id="ec41b-138">**Provider** キーワードは必須です。</span><span class="sxs-lookup"><span data-stu-id="ec41b-138">The **Provider** keyword is required.</span></span>  
  
- <span data-ttu-id="ec41b-139">**URL**、**Remote Provider**、**Remote Server** キーワードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ec41b-139">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="ec41b-140">OLE DB 接続文字列の詳細については、「<xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-140">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="ec41b-141">また、<xref:System.Data.OleDb.OleDbConnectionStringBuilder> を使用すると、接続文字列を実行時に作成できます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-141">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec41b-142">**OleDbConnection** オブジェクトでは、OLE DB プロバイダー固有の動的プロパティの設定または取得はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ec41b-142">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="ec41b-143">OLE DB プロバイダーに接続文字列で渡すことができるプロパティだけがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ec41b-143">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="ec41b-144">OLE DB データ ソースへの接続を作成し確立する方法を次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-144">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="ec41b-145">Universal Data Link ファイルは使用しない</span><span class="sxs-lookup"><span data-stu-id="ec41b-145">Do Not Use Universal Data Link Files</span></span>  

 <span data-ttu-id="ec41b-146">**OleDbConnection** の接続情報は、UDL (Universal Data Link) ファイルを使用して提供できますが、このファイルは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-146">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="ec41b-147">UDL ファイルは暗号化されないため、接続文字列をテキスト形式で表現してしまいます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-147">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="ec41b-148">UDL ファイルは、アプリケーションにとって外部ファイルをベースにしたリソースであるため、.NET Framework でセキュリティ保護できません。</span><span class="sxs-lookup"><span data-stu-id="ec41b-148">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="ec41b-149">ODBC データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="ec41b-149">Connecting to an ODBC Data Source</span></span>  

 <span data-ttu-id="ec41b-150">.NET Framework Data Provider for ODBC では、**OdbcConnection** オブジェクトを通じて、ODBC によって公開されているデータ ソースへの接続が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-150">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="ec41b-151">.NET Framework Data Provider for ODBC で使用される接続文字列フォーマットは、できるだけ ODBC の接続文字列フォーマットと一致するようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="ec41b-151">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="ec41b-152">ODBC データ ソース名 (DSN) を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-152">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="ec41b-153">**OdbcConnection** の詳細については、「<xref:System.Data.Odbc.OdbcConnection>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-153">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="ec41b-154">ODBC データ ソースへの接続を作成し確立する方法を次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-154">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="ec41b-155">Oracle データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="ec41b-155">Connecting to an Oracle Data Source</span></span>  

 <span data-ttu-id="ec41b-156">.NET Framework Data Provider for Oracle では、**OracleConnection** オブジェクトを通じて、Oracle データ ソースへの接続が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ec41b-156">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="ec41b-157">.NET Framework Data Provider for Oracle で使用される接続文字列フォーマットは、できるだけ MSDAORA (OLE DB Provider for Oracle) の接続文字列フォーマットと一致するようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="ec41b-157">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="ec41b-158">**OracleConnection** の詳細については、「<xref:System.Data.OracleClient.OracleConnection>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec41b-158">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="ec41b-159">Oracle データ ソースへの接続を作成し確立する方法を次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="ec41b-159">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec41b-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec41b-160">See also</span></span>

- [<span data-ttu-id="ec41b-161">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="ec41b-161">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="ec41b-162">接続文字列</span><span class="sxs-lookup"><span data-stu-id="ec41b-162">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="ec41b-163">OLE DB、ODBC、および Oracle 接続プール</span><span class="sxs-lookup"><span data-stu-id="ec41b-163">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="ec41b-164">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="ec41b-164">ADO.NET Overview</span></span>](ado-net-overview.md)
