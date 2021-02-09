---
description: '詳細情報: Oracle LOB'
title: Oracle LOB
ms.date: 03/30/2017
ms.assetid: 272e8e1e-a31f-475a-8c2a-ae8e1286bdab
ms.openlocfilehash: f59e2326852233648b15cf6aa56ebed905fcb598
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723687"
---
# <a name="oracle-lobs"></a><span data-ttu-id="d3e5c-103">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="d3e5c-103">Oracle LOBs</span></span>

<span data-ttu-id="d3e5c-104">.NET Framework Data Provider for Oracle には、<xref:System.Data.OracleClient.OracleLob> クラスが含まれています。このクラスは、Oracle の **LOB** データ型を操作するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-104">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle **LOB** data types.</span></span>  
  
 <span data-ttu-id="d3e5c-105">**OracleLob** は、これらの <xref:System.Data.OracleClient.OracleType> データ型の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-105">An **OracleLob** may be one of these <xref:System.Data.OracleClient.OracleType> data types:</span></span>  
  
|<span data-ttu-id="d3e5c-106">データの種類</span><span class="sxs-lookup"><span data-stu-id="d3e5c-106">Data type</span></span>|<span data-ttu-id="d3e5c-107">説明</span><span class="sxs-lookup"><span data-stu-id="d3e5c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3e5c-108">**BLOB**</span><span class="sxs-lookup"><span data-stu-id="d3e5c-108">**Blob**</span></span>|<span data-ttu-id="d3e5c-109">最大 4 GB までのバイナリ データを含む Oracle の **BLOB** データ型です。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-109">An Oracle **BLOB** data type that contains binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="d3e5c-110">**Byte** 型の **Array** にマップします。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-110">This maps to an **Array** of type **Byte**.</span></span>|  
|<span data-ttu-id="d3e5c-111">**Clob**</span><span class="sxs-lookup"><span data-stu-id="d3e5c-111">**Clob**</span></span>|<span data-ttu-id="d3e5c-112">Oracle の **CLOB** データ型です。サーバーの既定の文字セットに基づいて最大 4 GB までの文字データを含みます。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-112">An Oracle **CLOB** data type that contains character data, based on the default character set on the server, with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="d3e5c-113">**String** にマップします。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-113">This maps to **String**.</span></span>|  
|<span data-ttu-id="d3e5c-114">**NClob**</span><span class="sxs-lookup"><span data-stu-id="d3e5c-114">**NClob**</span></span>|<span data-ttu-id="d3e5c-115">Oracle の **NCLOB** データ型です。サーバーの各国語文字セットに基づいて最大 4 GB までの文字データを含みます。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-115">An Oracle **NCLOB** data type that contains character data, based on the national character set on the server with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="d3e5c-116">**String** にマップします。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-116">This maps to **String**.</span></span>|  
  
 <span data-ttu-id="d3e5c-117">**OracleLob** は、データがオペレーティング システムの物理ファイルにではなくサーバーに格納されるという点で、<xref:System.Data.OracleClient.OracleBFile> とは異なります。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-117">An **OracleLob** differs from an <xref:System.Data.OracleClient.OracleBFile> in that the data is stored on the server instead of in a physical file in the operating system.</span></span> <span data-ttu-id="d3e5c-118">また、常に読み取り専用になっている **OracleBFile** とは異なり、読み書き可能なオブジェクトにもなります。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-118">It can also be a read-write object, unlike an **OracleBFile**, which is always read-only.</span></span>  
  
## <a name="creating-retrieving-and-writing-to-a-lob"></a><span data-ttu-id="d3e5c-119">LOB の作成、取得、および書き込み</span><span class="sxs-lookup"><span data-stu-id="d3e5c-119">Creating, Retrieving, and Writing to a LOB</span></span>  

 <span data-ttu-id="d3e5c-120">次の C# の例では、Oracle テーブルに LOB を作成し、それらを取得して **OracleLob** オブジェクトの形式で書き込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-120">The following C# example demonstrates how you can create LOBs in an Oracle table, and then retrieve and write to them in the form of **OracleLob** objects.</span></span> <span data-ttu-id="d3e5c-121">この例では、<xref:System.Data.OracleClient.OracleDataReader> オブジェクトと **OracleLob** の **Read** および **Write** メソッドを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-121">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleLob** **Read** and **Write** methods.</span></span> <span data-ttu-id="d3e5c-122">Oracle の **BLOB**、**CLOB**、**NCLOB** データ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-122">The example uses Oracle **BLOB**, **CLOB**, and **NCLOB** data types.</span></span>  
  
```csharp  
using System;  
using System.IO;
using System.Text;
using System.Data;
using System.Data.OracleClient;  
  
// LobExample  
public class LobExample  
{  
   public static int Main(string[] args)  
   {  
      //Create a connection.  
      OracleConnection conn = new OracleConnection(  
         "Data Source=Oracle8i;Integrated Security=yes");  
      using(conn)  
      {  
         //Open a connection.  
         conn.Open();  
         OracleCommand cmd = conn.CreateCommand();  
  
         //Create the table and schema.  
         CreateTable(cmd);  
  
         //Read example.  
         ReadLobExample(cmd);  
  
         //Write example  
         WriteLobExample(cmd);  
      }  
  
      return 1;  
   }  
  
   // ReadLobExample  
   public static void ReadLobExample(OracleCommand cmd)  
   {  
      int actual = 0;  
  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs values (1, 'AA', 'AAA', N'AAAA')";  
      // Select some data.  
      cmd.CommandText = "SELECT * FROM tablewithlobs";  
      OracleDataReader reader = cmd.ExecuteReader();  
      using(reader)  
      {  
         //Obtain the first row of data.  
         reader.Read();  
  
         //Obtain the LOBs (all 3 varieties).  
         OracleLob blob = reader.GetOracleLob(1);  
         OracleLob clob = reader.GetOracleLob(2);  
         OracleLob nclob = reader.GetOracleLob(3);  
  
         //Example - Reading binary data (in chunks).  
         byte[] buffer = new byte[100];  
         while((actual = blob.Read(buffer, 0, buffer.Length)) >0)  
            Console.WriteLine(blob.LobType + ".Read(" + buffer + ", " +
              buffer.Length + ") => " + actual);  
  
         // Example - Reading CLOB/NCLOB data (in chunks).  
         // Note: You can read character data as raw Unicode bytes
         // (using OracleLob.Read as in the above example).  
         // However, because the OracleLob object inherits directly
         // from the .NET stream object,
         // all the existing classes that manipluate streams can
         // also be used. For example, the
         // .NET StreamReader makes it easier to convert the raw bytes
         // into actual characters.  
         StreamReader streamreader =
           new StreamReader(clob, Encoding.Unicode);  
         char[] cbuffer = new char[100];  
         while((actual = streamreader.Read(cbuffer,
           0, cbuffer.Length)) >0)  
            Console.WriteLine(clob.LobType + ".Read(  
              " + new string(cbuffer, 0, actual) + ", " +
              cbuffer.Length + ") => " + actual);  
  
         // Example - Reading data (all at once).  
         // You could use StreamReader.ReadToEnd to obtain
         // all the string data, or simply  
         // call OracleLob.Value to obtain a contiguous allocation
         // of all the data.  
         Console.WriteLine(nclob.LobType + ".Value => " + nclob.Value);  
      }  
   }  
  
   // WriteLobExample  
   public static void WriteLobExample(OracleCommand cmd)  
   {  
      //Note: Updating LOB data requires a transaction.  
      cmd.Transaction = cmd.Connection.BeginTransaction();  
  
      // Select some data.  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs values (1, 'AA', 'AAA', N'AAAA')";  
      cmd.CommandText = "SELECT * FROM tablewithlobs FOR UPDATE";  
      OracleDataReader reader = cmd.ExecuteReader();  
      using(reader)  
      {  
         // Obtain the first row of data.  
         reader.Read();  
  
         // Obtain a LOB.  
         OracleLob blob = reader.GetOracleLob(1/*0:based ordinal*/);  
  
         // Perform any desired operations on the LOB
         // (read, position, and so on).  
  
         // Example - Writing binary data (directly to the backend).  
         // To write, you can use any of the stream classes, or write  
         // raw binary data using
         // the OracleLob write method. Writing character vs. binary
         // is the same;  
         // however note that character is always in terms of
         // Unicode byte counts  
         // (for example, even number of bytes - 2 bytes for every  
         // Unicode character).  
         byte[] buffer = new byte[100];  
         buffer[0] = 0xCC;  
         buffer[1] = 0xDD;  
         blob.Write(buffer, 0, 2);  
         blob.Position = 0;  
         Console.WriteLine(blob.LobType + ".Write(  
           " + buffer + ", 0, 2) => " + blob.Value);  
  
         // Example - Obtaining a temp LOB and copying data
         // into it from another LOB.  
         OracleLob templob = CreateTempLob(cmd, blob.LobType);  
         long actual = blob.CopyTo(templob);  
         Console.WriteLine(blob.LobType + ".CopyTo(  
            " + templob.Value + ") => " + actual);  
  
         // Commit the transaction now that everything succeeded.  
         // Note: On error, Transaction.Dispose is called
         // (from the using statement)  
         // and will automatically roll back the pending transaction.  
         cmd.Transaction.Commit();  
      }  
   }  
  
   // CreateTempLob  
   public static OracleLob CreateTempLob(  
     OracleCommand cmd, OracleType lobtype)  
   {  
      //Oracle server syntax to obtain a temporary LOB.  
      cmd.CommandText = "DECLARE A " + lobtype + "; "+  
                     "BEGIN "+  
                        "DBMS_LOB.CREATETEMPORARY(A, FALSE); "+  
                        ":LOC := A; "+  
                     "END;";  
  
      //Bind the LOB as an output parameter.  
      OracleParameter p = cmd.Parameters.Add("LOC", lobtype);  
      p.Direction = ParameterDirection.Output;  
  
      //Execute (to receive the output temporary LOB).  
      cmd.ExecuteNonQuery();  
  
      //Return the temporary LOB.  
      return (OracleLob)p.Value;  
   }  
  
   // CreateTable  
   public static void CreateTable(OracleCommand cmd)  
   {  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs VALUES (1, 'AA', 'AAA', N'AAAA')";  
      try  
      {  
         cmd.CommandText   = "DROP TABLE tablewithlobs";  
         cmd.ExecuteNonQuery();  
      }  
      catch(Exception)  
      {  
      }  
  
      cmd.CommandText =
        "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText =
        "INSERT INTO tablewithlobs VALUES (1, 'AA', 'AAA', N'AAAA')";  
      cmd.ExecuteNonQuery();  
   }  
}  
```  
  
## <a name="creating-a-temporary-lob"></a><span data-ttu-id="d3e5c-123">一時 LOB の作成</span><span class="sxs-lookup"><span data-stu-id="d3e5c-123">Creating a Temporary LOB</span></span>  

 <span data-ttu-id="d3e5c-124">次の C# の例では、一時 LOB の作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3e5c-124">The following C# example demonstrates how to create a temporary LOB.</span></span>  
  
```csharp  
OracleConnection conn = new OracleConnection(  
  "server=test8172; integrated security=yes;");  
conn.Open();  
  
OracleTransaction tx = conn.BeginTransaction();  
  
OracleCommand cmd = conn.CreateCommand();  
cmd.Transaction = tx;  
cmd.CommandText =
  "declare xx blob; begin dbms_lob.createtemporary(  
  xx, false, 0); :tempblob := xx; end;";  
cmd.Parameters.Add(new OracleParameter("tempblob",  
  OracleType.Blob)).Direction = ParameterDirection.Output;  
cmd.ExecuteNonQuery();  
OracleLob tempLob = (OracleLob)cmd.Parameters[0].Value;  
tempLob.BeginBatch(OracleLobOpenMode.ReadWrite);  
tempLob.Write(tempbuff,0,tempbuff.Length);  
tempLob.EndBatch();  
cmd.Parameters.Clear();  
cmd.CommandText = "myTable.myProc";  
cmd.CommandType = CommandType.StoredProcedure;
cmd.Parameters.Add(new OracleParameter(  
  "ImportDoc", OracleType.Blob)).Value = tempLob;  
cmd.ExecuteNonQuery();  
  
tx.Commit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3e5c-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3e5c-125">See also</span></span>

- [<span data-ttu-id="d3e5c-126">Oracle および ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d3e5c-126">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="d3e5c-127">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="d3e5c-127">ADO.NET Overview</span></span>](ado-net-overview.md)
