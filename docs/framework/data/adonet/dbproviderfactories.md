---
description: '詳細情報: DbProviderFactories'
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 735c78a846fc8df31a922acf90e587c6d96f4995
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651263"
---
# <a name="dbproviderfactories"></a><span data-ttu-id="9c55a-103">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="9c55a-103">DbProviderFactories</span></span>

<span data-ttu-id="9c55a-104"><xref:System.Data.Common> 名前空間には、特定のデータ ソースを使用するための <xref:System.Data.Common.DbProviderFactory> インスタンスを作成するクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9c55a-104">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="9c55a-105"><xref:System.Data.Common.DbProviderFactory> インスタンスを作成し、データ プロバイダーに関する情報をそのインスタンスに渡すと、`DbProviderFactory` はあらかじめ提供された情報に基づいて厳密に型指定された正しいオブジェクトを判断して返すことができます。</span><span class="sxs-lookup"><span data-stu-id="9c55a-105">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="9c55a-106">.NET Framework バージョン 4 以降では、<xref:System.Data.Odbc>、<xref:System.Data.OleDb>、<xref:System.Data.SqlClient>、および <xref:System.Data.OracleClient> などのデータ プロバイダーは machine.config ファイルに表示されなくなりますが、カスタム プロバイダーは表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c55a-106">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c55a-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9c55a-107">In This Section</span></span>  

 [<span data-ttu-id="9c55a-108">ファクトリ モデルの概要</span><span class="sxs-lookup"><span data-stu-id="9c55a-108">Factory Model Overview</span></span>](factory-model-overview.md)  
 <span data-ttu-id="9c55a-109">ファクトリ デザイン パターンとプログラミング インターフェイスの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="9c55a-109">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="9c55a-110">DbProviderFactory の取得</span><span class="sxs-lookup"><span data-stu-id="9c55a-110">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="9c55a-111">インストールされているデータ プロバイダーの一覧を取得したり、<xref:System.Data.Common.DbConnection> から `DbProviderFactory` を作成したりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c55a-111">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="9c55a-112">DbConnection、DbCommand、および DbException</span><span class="sxs-lookup"><span data-stu-id="9c55a-112">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="9c55a-113"><xref:System.Data.Common.DbCommand> と <xref:System.Data.Common.DbDataReader> の作成方法のほか、<xref:System.Data.Common.DbException> を使ったデータ エラーの処理方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c55a-113">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="9c55a-114">DbDataAdapter を使用したデータの変更</span><span class="sxs-lookup"><span data-stu-id="9c55a-114">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="9c55a-115"><xref:System.Data.Common.DbCommandBuilder> と <xref:System.Data.Common.DbDataAdapter> を使用して、データを取得したり変更したりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c55a-115">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c55a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c55a-116">See also</span></span>

- [<span data-ttu-id="9c55a-117">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="9c55a-117">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="9c55a-118">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="9c55a-118">ADO.NET Overview</span></span>](ado-net-overview.md)
