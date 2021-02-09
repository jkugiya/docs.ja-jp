---
description: '詳細情報: ADO.NET でのデータ型のマッピング'
title: データ型のマップ
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: c1829fdc2ebc053d1fd3a76e827a81e582572233
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786447"
---
# <a name="data-type-mappings-in-adonet"></a><span data-ttu-id="76736-103">ADO.NET でのデータ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="76736-103">Data Type Mappings in ADO.NET</span></span>

<span data-ttu-id="76736-104">.NET Framework は共通型システムを基にしています。このシステムは実行時の型の宣言、使用、および管理方法を定義するものです。</span><span class="sxs-lookup"><span data-stu-id="76736-104">The .NET Framework is based on the common type system, which defines how types are declared, used, and managed in the runtime.</span></span> <span data-ttu-id="76736-105">値型と参照型の両方から構成されており、これらはすべて <xref:System.Object> 基本型から派生します。</span><span class="sxs-lookup"><span data-stu-id="76736-105">It consists of both value types and reference types, which all derive from the <xref:System.Object> base type.</span></span> <span data-ttu-id="76736-106">データ ソースを操作するときは、データ型が明示的に指定されていない場合はデータ プロバイダーから推論されます。</span><span class="sxs-lookup"><span data-stu-id="76736-106">When working with a data source, the data type is inferred from the data provider if it is not explicitly specified.</span></span> <span data-ttu-id="76736-107">たとえば、<xref:System.Data.DataSet> オブジェクトは、特定のデータ ソースには依存しません。</span><span class="sxs-lookup"><span data-stu-id="76736-107">For example, a <xref:System.Data.DataSet> object is independent of any specific data source.</span></span> <span data-ttu-id="76736-108">`DataSet` 内のデータはデータ ソースから取得され、変更は `DataAdapter` によってデータ ソースに反映されます。</span><span class="sxs-lookup"><span data-stu-id="76736-108">Data in a `DataSet` is retrieved from a data source, and changes are persisted back to the data source by using a `DataAdapter`.</span></span> <span data-ttu-id="76736-109">つまり、`DataAdapter` によって `DataSet` 内の <xref:System.Data.DataTable> に、データ ソースからの値が格納されると、`DataTable` 内の列の結果のデータ型は、データ ソースへの接続に使用された .NET Framework データ プロバイダーに固有の型ではなく、.NET Framework の型になります。</span><span class="sxs-lookup"><span data-stu-id="76736-109">This means that when a `DataAdapter` fills a <xref:System.Data.DataTable> in a `DataSet` with values from a data source, the resulting data types of the columns in the `DataTable` are .NET Framework types, instead of types specific to the .NET Framework data provider that is used to connect to the data source.</span></span>  
  
 <span data-ttu-id="76736-110">同様に、`DataReader` によってデータ ソースから値が返されるとき、結果の値は .NET Framework 型のローカル変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="76736-110">Likewise, when a `DataReader` returns a value from a data source, the resulting value is stored in a local variable that has a .NET Framework type.</span></span> <span data-ttu-id="76736-111">`DataAdapter` の `Fill` 操作と `DataReader` の `Get` メソッドのどちらの場合も、.NET Framework の型は .NET Framework データ プロバイダーから返された値から推論されます。</span><span class="sxs-lookup"><span data-stu-id="76736-111">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the value returned from the .NET Framework data provider.</span></span>  
  
 <span data-ttu-id="76736-112">返される値の型がわかっている場合は、推論されるデータ型を使用するのではなく、`DataReader` の型指定されたアクセサー メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="76736-112">Instead of relying on the inferred data type, you can use the typed accessor methods of the `DataReader` when you know the specific type of the value being returned.</span></span> <span data-ttu-id="76736-113">型指定されたアクセサー メソッドを使用して .NET Framework の特定の型として値を返すと、追加の型変換が不要になるため、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="76736-113">Typed accessor methods give you better performance by returning a value as a specific .NET Framework type, which eliminates the need for additional type conversion.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76736-114">.NET Framework データ プロバイダーのデータ型の null 値は、`DBNull.Value` で表されます。</span><span class="sxs-lookup"><span data-stu-id="76736-114">Null values for .NET Framework data provider data types are represented by `DBNull.Value`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76736-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="76736-115">In This Section</span></span>  

 [<span data-ttu-id="76736-116">SQL Server データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="76736-116">SQL Server Data Type Mappings</span></span>](sql-server-data-type-mappings.md)  
 <span data-ttu-id="76736-117">推論されたデータ型マッピングおよび <xref:System.Data.SqlClient> のデータ アクセサー メソッドを一覧で示します。</span><span class="sxs-lookup"><span data-stu-id="76736-117">Lists inferred data type mappings and data accessor methods for <xref:System.Data.SqlClient>.</span></span>  
  
 [<span data-ttu-id="76736-118">OLE DB データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="76736-118">OLE DB Data Type Mappings</span></span>](ole-db-data-type-mappings.md)  
 <span data-ttu-id="76736-119">推論されたデータ型マッピングおよび <xref:System.Data.OleDb> のデータ アクセサー メソッドを一覧で示します。</span><span class="sxs-lookup"><span data-stu-id="76736-119">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OleDb>.</span></span>  
  
 [<span data-ttu-id="76736-120">ODBC データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="76736-120">ODBC Data Type Mappings</span></span>](odbc-data-type-mappings.md)  
 <span data-ttu-id="76736-121">推論されたデータ型マッピングおよび <xref:System.Data.Odbc> のデータ アクセサー メソッドを一覧で示します。</span><span class="sxs-lookup"><span data-stu-id="76736-121">Lists inferred data type mappings and data accessor methods for <xref:System.Data.Odbc>.</span></span>  
  
 [<span data-ttu-id="76736-122">Oracle データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="76736-122">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="76736-123">推論されたデータ型マッピングおよび <xref:System.Data.OracleClient> のデータ アクセサー メソッドを一覧で示します。</span><span class="sxs-lookup"><span data-stu-id="76736-123">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OracleClient>.</span></span>  
  
 [<span data-ttu-id="76736-124">浮動小数点数</span><span class="sxs-lookup"><span data-stu-id="76736-124">Floating-Point Numbers</span></span>](floating-point-numbers.md)  
 <span data-ttu-id="76736-125">開発者が浮動小数点数を扱う際の発生頻度の高い問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="76736-125">Describes issues that developers frequently encounter when working with floating-point numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76736-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="76736-126">See also</span></span>

- [<span data-ttu-id="76736-127">SQL Server データ型と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="76736-127">SQL Server Data Types and ADO.NET</span></span>](./sql/sql-server-data-types.md)
- [<span data-ttu-id="76736-128">パラメーターおよびパラメーター データ型の構成</span><span class="sxs-lookup"><span data-stu-id="76736-128">Configuring Parameters and Parameter Data Types</span></span>](configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="76736-129">データベース スキーマ情報の取得</span><span class="sxs-lookup"><span data-stu-id="76736-129">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="76736-130">共通型システム</span><span class="sxs-lookup"><span data-stu-id="76736-130">Common Type System</span></span>](../../../standard/base-types/common-type-system.md)
- <span data-ttu-id="76736-131">[型の変換](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="76736-131">[Converting Types](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))</span></span>
- [<span data-ttu-id="76736-132">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="76736-132">ADO.NET Overview</span></span>](ado-net-overview.md)
