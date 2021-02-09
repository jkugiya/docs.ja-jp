---
description: '詳細情報: Oracle BFILE'
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: e1fda4ad4acb225dc9a70c92b2c4f2b1d61ab1d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672492"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="a454a-103">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="a454a-103">Oracle BFILEs</span></span>

<span data-ttu-id="a454a-104">.NET Framework Data Provider for Oracle には、<xref:System.Data.OracleClient.OracleBFile> クラスが含まれています。このクラスは、Oracle <xref:System.Data.OracleClient.OracleType.BFile> データ型で使用されます。</span><span class="sxs-lookup"><span data-stu-id="a454a-104">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="a454a-105">Oracle の **BFILE** データ型は、最大 4 GB までのバイナリ データへの参照を含む Oracle の **LOB** データ型です。</span><span class="sxs-lookup"><span data-stu-id="a454a-105">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="a454a-106">Oracle の **BFILE** は、データがサーバー上にではなくオペレーティング システムの物理ファイルに保存されるという点で、他の Oracle の **LOB** データ型と異なります。</span><span class="sxs-lookup"><span data-stu-id="a454a-106">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="a454a-107">**BFILE** データ型のデータ アクセスは読み取り専用であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a454a-107">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="a454a-108">**LOB** データ型と異なる **BFILE** データ型のその他の特徴としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="a454a-108">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="a454a-109">非構造化データの保持。</span><span class="sxs-lookup"><span data-stu-id="a454a-109">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="a454a-110">サーバー側チャンキングのサポート。</span><span class="sxs-lookup"><span data-stu-id="a454a-110">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="a454a-111">参照コピーのセマンティクスの使用。</span><span class="sxs-lookup"><span data-stu-id="a454a-111">Uses reference copy semantics.</span></span> <span data-ttu-id="a454a-112">たとえば、**BFILE** 上でコピー操作を行う場合、ファイルへの参照である **BFILE** ロケーターだけがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="a454a-112">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="a454a-113">ファイル内のデータはコピーされません。</span><span class="sxs-lookup"><span data-stu-id="a454a-113">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="a454a-114">**BFILE** データ型は、大きいサイズの LOB の参照用として使用してください。データベースへの保存には適しません。</span><span class="sxs-lookup"><span data-stu-id="a454a-114">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="a454a-115">**BFILE** データ型を使用すると、クライアント、サーバー、および通信において、**LOB** データ型よりも、いっそう多くのオーバーヘッドを必要とします。</span><span class="sxs-lookup"><span data-stu-id="a454a-115">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="a454a-116">少量のデータを取得するだけの場合は、**BFILE** へのアクセスがいっそう効果的です。</span><span class="sxs-lookup"><span data-stu-id="a454a-116">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="a454a-117">オブジェクト全体を取得したい場合は、データベースに常駐する LOB へのアクセスがいっそう効果的です。</span><span class="sxs-lookup"><span data-stu-id="a454a-117">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="a454a-118">NULL 以外の **OracleBFile** オブジェクトは、基になる物理ファイルの場所を定義する次の 2 つのエンティティに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="a454a-118">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="a454a-119">Oracle DIRECTORY オブジェクト。ファイル システムのディレクトリに対するデータベースのエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="a454a-119">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="a454a-120">基になる物理ファイルのファイル名。このファイルは、DIRECTORY オブジェクトに関連付けられたディレクトリに配置されています。</span><span class="sxs-lookup"><span data-stu-id="a454a-120">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a454a-121">例</span><span class="sxs-lookup"><span data-stu-id="a454a-121">Example</span></span>  

 <span data-ttu-id="a454a-122">次の C# の例では、Oracle テーブルに **BFILE** を作成し、**OracleBFile** オブジェクトの形式で取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a454a-122">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="a454a-123">この例では、<xref:System.Data.OracleClient.OracleDataReader> オブジェクトと **OracleBFile** の **Seek** および **Read** メソッドを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a454a-123">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="a454a-124">このサンプルを使用するには、はじめに "c:\\\bfiles" というディレクトリと "MyFile.jpg" というファイルを Oracle サーバーに作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a454a-124">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a454a-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a454a-125">See also</span></span>

- [<span data-ttu-id="a454a-126">Oracle および ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a454a-126">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="a454a-127">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="a454a-127">ADO.NET Overview</span></span>](ado-net-overview.md)
