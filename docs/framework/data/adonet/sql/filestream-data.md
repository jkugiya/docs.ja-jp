---
description: '詳細情報: FILESTREAM データ'
title: FILESTREAM データ
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 0110be6b867a07ec1cd204e2a3de371367bbfa36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802048"
---
# <a name="filestream-data"></a><span data-ttu-id="c1893-103">FILESTREAM データ</span><span class="sxs-lookup"><span data-stu-id="c1893-103">FILESTREAM Data</span></span>

<span data-ttu-id="c1893-104">FILESTREAM ストレージ属性は、varbinary(max) 列に格納されるバイナリ (BLOB) データに対応しています。</span><span class="sxs-lookup"><span data-stu-id="c1893-104">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="c1893-105">FILESTREAM 以前は、バイナリデータの格納に特別な処理が必要でした。</span><span class="sxs-lookup"><span data-stu-id="c1893-105">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="c1893-106">テキスト ドキュメント、イメージ、ビデオなどの非構造化データはデータベース外に保存されることが多く、そのために管理が困難でした。</span><span class="sxs-lookup"><span data-stu-id="c1893-106">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>

> [!NOTE]
> <span data-ttu-id="c1893-107">SqlClient を使用して FILESTREAM データを操作するには、.NET Framework 3.5 SP1 以降をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1893-107">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>

<span data-ttu-id="c1893-108">varbinary(max) 列に FILESTREAM 属性を指定すると、SQL Server ではデータはデータベース ファイルではなくローカルの NTFS ファイル システムに保存されます。</span><span class="sxs-lookup"><span data-stu-id="c1893-108">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="c1893-109">データは個別に保存されますが、データベースに保存されている varbinary(max) データの操作をサポートする同じ Transact-SQL ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c1893-109">Although it is stored separately, you can use the same Transact-SQL statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>

## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="c1893-110">FILESTREAM の SqlClient サポート</span><span class="sxs-lookup"><span data-stu-id="c1893-110">SqlClient Support for FILESTREAM</span></span>

<span data-ttu-id="c1893-111">.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) では、<xref:System.Data.SqlTypes> 名前空間で定義されている <xref:System.Data.SqlTypes.SqlFileStream> クラスを使用して、FILESTREAM のデータの読み取りと書き込みがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c1893-111">The .NET Framework Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="c1893-112">`SqlFileStream` は <xref:System.IO.Stream> クラスを継承します。このクラスは、データのストリームへの読み込みと書き込みを行うためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c1893-112">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="c1893-113">ストリームからの読み取りでは、データをストリームからバイト配列などのデータ構造に転送します。</span><span class="sxs-lookup"><span data-stu-id="c1893-113">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="c1893-114">書き込みを行うと、データはデータ構造からストリームに転送されます。</span><span class="sxs-lookup"><span data-stu-id="c1893-114">Writing transfers the data from the data structure into a stream.</span></span>

### <a name="creating-the-sql-server-table"></a><span data-ttu-id="c1893-115">SQL Server テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="c1893-115">Creating the SQL Server Table</span></span>

<span data-ttu-id="c1893-116">次の Transact-SQL ステートメントによって、従業員の名前の付いたテーブルが作成され、データ行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="c1893-116">The following Transact-SQL statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="c1893-117">FILESTREAM ストレージを有効にしたら、このテーブルを以下のコード例と組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="c1893-117">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="c1893-118">SQL Server オンライン ブックの関連トピックへのリンクは、このトピックの終わりにあります。</span><span class="sxs-lookup"><span data-stu-id="c1893-118">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>

```sql
CREATE TABLE employees
(
  EmployeeId INT  NOT NULL  PRIMARY KEY,
  Photo VARBINARY(MAX) FILESTREAM  NULL,
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL
  UNIQUE DEFAULT NEWID()
)
GO
Insert into employees
Values(1, 0x00, default)
GO
```

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="c1893-119">例:FILESTREAM データの読み取り、上書き、挿入</span><span class="sxs-lookup"><span data-stu-id="c1893-119">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>

<span data-ttu-id="c1893-120">次のサンプルでは、FILESTREAM からデータを読み取る方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1893-120">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="c1893-121">このコードでは、ファイルへの論理パスを取得し、`FileAccess` を `Read` に、`FileOptions` を `SequentialScan` に設定します。</span><span class="sxs-lookup"><span data-stu-id="c1893-121">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="c1893-122">次に、コードが SqlFileStream からバッファーにバイトを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="c1893-122">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="c1893-123">次に、バイトがコンソール ウィンドウに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="c1893-123">The bytes are then written to the console window.</span></span>

<span data-ttu-id="c1893-124">さらに、このサンプルでは、既存のすべてのデータが上書きされる FILESTREAM にデータを書き込む方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="c1893-124">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="c1893-125">このコードでは、ファイルへの論理パスを取得し、`SqlFileStream` を作成して、`FileAccess` を `Write` に、`FileOptions` を `SequentialScan` に設定します。</span><span class="sxs-lookup"><span data-stu-id="c1893-125">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="c1893-126">1 バイトが `SqlFileStream` に書き込まれ、ファイル内のすべてのデータが置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="c1893-126">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>

<span data-ttu-id="c1893-127">このサンプルでは、Seek メソッドを使用してファイルの末尾にデータを追加することによって、データを FILESTREAM に書き込む方法も示します。</span><span class="sxs-lookup"><span data-stu-id="c1893-127">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="c1893-128">このコードでは、ファイルへの論理パスを取得し、`SqlFileStream` を作成して、`FileAccess` を `ReadWrite` に、`FileOptions` を `SequentialScan` に設定します。</span><span class="sxs-lookup"><span data-stu-id="c1893-128">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="c1893-129">このコードは、Seek メソッドを使用してファイルの末尾までシークし、既存のファイルに 1 バイトを追加します。</span><span class="sxs-lookup"><span data-stu-id="c1893-129">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Data.SqlTypes;
using System.Data;
using System.IO;

namespace FileStreamTest
{
    class Program
    {
        static void Main(string[] args)
        {
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for the file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Read the contents as bytes and write them to the console
                            for (long index = 0; index < fileStream.Length; index++)
                            {
                                Console.WriteLine(fileStream.ReadByte());
                            }
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Write a single byte to the file. This will
                            // replace any data in the file.
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Seek to the end of the file
                            fileStream.Seek(0, SeekOrigin.End);

                            // Append a single byte
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }

        }
    }
}
```

<span data-ttu-id="c1893-130">別のサンプルについては、「[ファイル ストリーム列にバイナリ データをフェッチおよび格納する方法](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1893-130">For another sample, see [How to store and fetch binary data into a file stream column](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>

## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="c1893-131">SQL Server オンライン ブックのリソース</span><span class="sxs-lookup"><span data-stu-id="c1893-131">Resources in SQL Server Books Online</span></span>

<span data-ttu-id="c1893-132">FILESTREAM の詳細なドキュメントは、SQL Server オンライン ブックの次のセクションにあります。</span><span class="sxs-lookup"><span data-stu-id="c1893-132">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>

|<span data-ttu-id="c1893-133">トピック</span><span class="sxs-lookup"><span data-stu-id="c1893-133">Topic</span></span>|<span data-ttu-id="c1893-134">説明</span><span class="sxs-lookup"><span data-stu-id="c1893-134">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="c1893-135">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c1893-135">FILESTREAM (SQL Server)</span></span>](/sql/relational-databases/blob/filestream-sql-server)|<span data-ttu-id="c1893-136">FILESTREAM ストレージを使用するタイミングと、SQL Server データベース エンジンと NTFS ファイル システムを統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1893-136">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|
|[<span data-ttu-id="c1893-137">FILESTREAM データ用のクライアント アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="c1893-137">Create Client Applications for FILESTREAM Data</span></span>](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|<span data-ttu-id="c1893-138">FILESTREAM データを操作するための Windows API 関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1893-138">Describes the Windows API functions for working with FILESTREAM data.</span></span>|
|[<span data-ttu-id="c1893-139">FILESTREAM と SQL Server のその他の機能</span><span class="sxs-lookup"><span data-stu-id="c1893-139">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="c1893-140">FILESTREAM データを SQL Server の他の機能と共に使用する際の注意事項、ガイドライン、および制限事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1893-140">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c1893-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1893-141">See also</span></span>

- [<span data-ttu-id="c1893-142">SQL Server データ型と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c1893-142">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="c1893-143">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="c1893-143">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="c1893-144">コード アクセス セキュリティと ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c1893-144">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="c1893-145">SQL Server のバイナリ データと大きな値のデータ</span><span class="sxs-lookup"><span data-stu-id="c1893-145">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="c1893-146">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="c1893-146">ADO.NET Overview</span></span>](../ado-net-overview.md)
