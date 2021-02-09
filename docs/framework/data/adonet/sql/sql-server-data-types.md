---
description: '詳細情報: SQL Server データ型と ADO.NET'
title: SQL Server データ型と ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 841fa5864bf54b5e4fc4dc24dab64e6ac1435c7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767298"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="7fe58-103">SQL Server データ型と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7fe58-103">SQL Server Data Types and ADO.NET</span></span>

<span data-ttu-id="7fe58-104">SQL Server と .NET Framework は異なる型システムに基づいているので、両者間でデータ損失が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7fe58-104">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="7fe58-105">データの整合性を維持するために、.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) では、SQL Server データを処理するための型指定されたアクセサー メソッドが提供されています。</span><span class="sxs-lookup"><span data-stu-id="7fe58-105">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="7fe58-106"><xref:System.Data.SqlDbType> クラスの列挙値を使用して、<xref:System.Data.SqlClient.SqlParameter> データ型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7fe58-106">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="7fe58-107">SQL Server と .NET Framework の間のデータ型マッピングがわかる詳細な説明と表については、「[SQL Server データ型のマッピング](../sql-server-data-type-mappings.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7fe58-107">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="7fe58-108">SQL Server 2008 では、業務上のニーズに対応して、日時データ、構造化データ、半構造化データ、および非構造化データを扱うための新しいデータ型が導入されました。</span><span class="sxs-lookup"><span data-stu-id="7fe58-108">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="7fe58-109">新しいデータ型は、SQL Server 2008 オンライン ブックで説明されています。</span><span class="sxs-lookup"><span data-stu-id="7fe58-109">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="7fe58-110">アプリケーションで使用可能な SQL Server のデータ型は、使用する SQL Server のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="7fe58-110">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="7fe58-111">詳細については、次の表にある各バージョンの SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fe58-111">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="7fe58-112">**SQL Server のドキュメント**</span><span class="sxs-lookup"><span data-stu-id="7fe58-112">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="7fe58-113">データ型 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7fe58-113">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a><span data-ttu-id="7fe58-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7fe58-114">In This Section</span></span>  

 [<span data-ttu-id="7fe58-115">SqlTypes と DataSet</span><span class="sxs-lookup"><span data-stu-id="7fe58-115">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="7fe58-116">`SqlTypes` 内の `DataSet` に対する型のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7fe58-116">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="7fe58-117">null 値の処理</span><span class="sxs-lookup"><span data-stu-id="7fe58-117">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="7fe58-118">null 値と 3 値ロジックの使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="7fe58-118">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="7fe58-119">GUID と uniqueidentifier 値の比較</span><span class="sxs-lookup"><span data-stu-id="7fe58-119">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="7fe58-120">SQL Server と .NET Framework での GUID および uniqueidentifier 値の使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="7fe58-120">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="7fe58-121">日付と時刻のデータ</span><span class="sxs-lookup"><span data-stu-id="7fe58-121">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="7fe58-122">SQL Server 2008 で導入された新しい日付と時刻のデータ型の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7fe58-122">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="7fe58-123">大きな UDT</span><span class="sxs-lookup"><span data-stu-id="7fe58-123">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="7fe58-124">SQL Server 2008 で導入された大きな値の UDT からデータを取り出す方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="7fe58-124">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="7fe58-125">SQL Server における XML データ</span><span class="sxs-lookup"><span data-stu-id="7fe58-125">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="7fe58-126">SQL Server から取得した XML データを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7fe58-126">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7fe58-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fe58-127">Reference</span></span>  

 <xref:System.Data.DataSet>  
 <span data-ttu-id="7fe58-128">`DataSet` クラスおよびそのすべてのメンバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7fe58-128">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="7fe58-129">`SqlTypes` 名前空間およびそのすべてのメンバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7fe58-129">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="7fe58-130">`SqlDbType` 列挙型およびそのすべてのメンバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7fe58-130">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="7fe58-131">`DbType` 列挙型およびそのすべてのメンバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7fe58-131">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe58-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fe58-132">See also</span></span>

- [<span data-ttu-id="7fe58-133">SQL Server データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="7fe58-133">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="7fe58-134">パラメーターおよびパラメーター データ型の構成</span><span class="sxs-lookup"><span data-stu-id="7fe58-134">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="7fe58-135">テーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="7fe58-135">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- [<span data-ttu-id="7fe58-136">SQL Server のバイナリ データと大きな値のデータ</span><span class="sxs-lookup"><span data-stu-id="7fe58-136">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="7fe58-137">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="7fe58-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
