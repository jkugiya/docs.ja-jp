---
description: '詳細情報: データベース スキーマ情報の取得'
title: データベース スキーマ情報の取得
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 84ac94a72b23d0b1d6924600f2fd33b2a285eab8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663405"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="05c8c-103">データベース スキーマ情報の取得</span><span class="sxs-lookup"><span data-stu-id="05c8c-103">Retrieving Database Schema Information</span></span>

<span data-ttu-id="05c8c-104">データベースからのスキーマ情報の取得は、スキーマの検出プロセスによって行われます。</span><span class="sxs-lookup"><span data-stu-id="05c8c-104">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="05c8c-105">スキーマの検出により、アプリケーションでは、特定のデータベースのデータベース スキーマ ("*メタデータ*" とも呼ばれます) に関する情報を検索して返すように、マネージド プロバイダーに要求できます。</span><span class="sxs-lookup"><span data-stu-id="05c8c-105">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="05c8c-106">テーブル、列、ストアド プロシージャなどの各種のデータベース スキーマ要素は、スキーマ コレクションを通じて公開されます。</span><span class="sxs-lookup"><span data-stu-id="05c8c-106">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="05c8c-107">各スキーマ コレクションには、使用されているプロバイダーに固有の各種のスキーマ情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="05c8c-107">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="05c8c-108">各 .NET Framework マネージド プロバイダーでは、**Connection** クラスの **GetSchema** メソッドが実装されていて、**GetSchema** メソッドから返されるスキーマ情報は、<xref:System.Data.DataTable> という形式になります。</span><span class="sxs-lookup"><span data-stu-id="05c8c-108">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="05c8c-109">**GetSchema** メソッドはオーバーロードされたメソッドであり、オプションのパラメーターで、取得するスキーマ コレクションを指定し、返される情報の量を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="05c8c-109">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="05c8c-110">OLE DB、ODBC、Oracle、SqlClient 用の .NET Framework データ プロバイダーで提供されている **GetSchemaTable** メソッドでは、**DataReader** の列のメタデータを表す DataTable が返されます。</span><span class="sxs-lookup"><span data-stu-id="05c8c-110">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="05c8c-111">.NET Framework Data Provider for OLE DB では、<xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> オブジェクトの <xref:System.Data.OleDb.OleDbConnection> メソッドを使ってスキーマ情報を公開します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-111">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="05c8c-112">**GetOleDbSchemaTable** は、引数として、返すスキーマ情報を識別する <xref:System.Data.OleDb.OleDbSchemaGuid> と、返された列に対する制限の配列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="05c8c-112">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="05c8c-113">**GetOleDbSchemaTable** では、要求したスキーマ情報が格納されている <xref:System.Data.DataTable> が返されます。</span><span class="sxs-lookup"><span data-stu-id="05c8c-113">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05c8c-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="05c8c-114">In This Section</span></span>  

 [<span data-ttu-id="05c8c-115">GetSchema およびスキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="05c8c-115">GetSchema and Schema Collections</span></span>](getschema-and-schema-collections.md)  
 <span data-ttu-id="05c8c-116">**GetSchema** メソッドと、このメソッドを使ってデータベースからスキーマ情報を取得して制限する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-116">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="05c8c-117">スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="05c8c-117">Schema Restrictions</span></span>  
 <span data-ttu-id="05c8c-118">**GetSchema** で使用できるスキーマの制限について説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-118">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="05c8c-119">共通のスキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="05c8c-119">Common Schema Collections</span></span>](common-schema-collections.md)  
 <span data-ttu-id="05c8c-120">すべての .NET Framework マネージド プロバイダーでサポートされる共通のスキーマ コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-120">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="05c8c-121">SQL Server スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="05c8c-121">SQL Server Schema Collections</span></span>](sql-server-schema-collections.md)  
 <span data-ttu-id="05c8c-122">.NET Framework Provider for SQL Server でサポートされるスキーマ コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-122">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="05c8c-123">Oracle スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="05c8c-123">Oracle Schema Collections</span></span>](oracle-schema-collections.md)  
 <span data-ttu-id="05c8c-124">.NET Framework Provider for Oracle でサポートされるスキーマ コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-124">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="05c8c-125">ODBC スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="05c8c-125">ODBC Schema Collections</span></span>](odbc-schema-collections.md)  
 <span data-ttu-id="05c8c-126">ODBC ドライバーのスキーマ コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-126">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="05c8c-127">OLE DB スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="05c8c-127">OLE DB Schema Collections</span></span>](ole-db-schema-collections.md)  
 <span data-ttu-id="05c8c-128">OLE DB プロバイダーのスキーマ コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-128">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="05c8c-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="05c8c-129">Reference</span></span>  

 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="05c8c-130"><xref:System.Data.Common.DbConnection> クラスの **GetSchema** メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-130">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="05c8c-131"><xref:System.Data.Odbc.OdbcConnection> クラスの **GetSchema** メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-131">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="05c8c-132"><xref:System.Data.OleDb.OleDbConnection> クラスの **GetSchema** メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-132">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="05c8c-133"><xref:System.Data.OracleClient.OracleConnection> クラスの **GetSchema** メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-133">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="05c8c-134"><xref:System.Data.SqlClient.SqlConnection> クラスの **GetSchema** メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-134">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="05c8c-135"><xref:System.Data.Common.DbDataReader> クラスの **GetSchemaTable** メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="05c8c-136"><xref:System.Data.Odbc.OdbcDataReader> クラスの **GetSchemaTable** メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-136">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="05c8c-137"><xref:System.Data.OleDb.OleDbDataReader> クラスの **GetSchemaTable** メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="05c8c-138"><xref:System.Data.OracleClient.OracleDataReader> クラスの **GetSchemaTable** メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-138">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="05c8c-139"><xref:System.Data.SqlClient.SqlDataReader> クラスの **GetSchemaTable** メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="05c8c-139">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c8c-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="05c8c-140">See also</span></span>

- [<span data-ttu-id="05c8c-141">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="05c8c-141">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="05c8c-142">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="05c8c-142">ADO.NET Overview</span></span>](ado-net-overview.md)
