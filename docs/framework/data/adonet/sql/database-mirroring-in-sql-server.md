---
description: '詳細情報: SQL Server のデータベース ミラーリング'
title: SQL Server のデータベース ミラーリング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: 663f0a2a016a3f6c449c1d2694bc6c2d77eb6157
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695893"
---
# <a name="database-mirroring-in-sql-server"></a><span data-ttu-id="ba2cb-103">SQL Server のデータベース ミラーリング</span><span class="sxs-lookup"><span data-stu-id="ba2cb-103">Database Mirroring in SQL Server</span></span>

<span data-ttu-id="ba2cb-104">SQL Server のデータベース ミラーリング機能を使用すると、スタンバイ サーバー上に SQL Server データベースのコピー (ミラー) を保持できます。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-104">Database mirroring in SQL Server allows you to keep a copy, or mirror, of a SQL Server database on a standby server.</span></span> <span data-ttu-id="ba2cb-105">ミラーリングは、常にデータのコピーが 2 つ別々に存在することを保証し、高可用性とデータの完全な冗長性をもたらします。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-105">Mirroring ensures that two separate copies of the data exist at all times, providing high availability and complete data redundancy.</span></span> <span data-ttu-id="ba2cb-106">.NET Data Provider for SQL Server では、データベース ミラーリングが暗黙的にサポートされているため、SQL Server データベース用に構成されている場合は、開発者が操作を行ったり、コードを作成したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-106">The .NET Data Provider for SQL Server provides implicit support for database mirroring, so that the developer does not need to take any action or write any code once it has been configured for a SQL Server database.</span></span> <span data-ttu-id="ba2cb-107">さらに、<xref:System.Data.SqlClient.SqlConnection> オブジェクトは、<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 内のフェールオーバー パートナー サーバーの名前を指定できる明示的な接続モードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-107">In addition, the <xref:System.Data.SqlClient.SqlConnection> object supports an explicit connection mode that allows supplying the name of a failover partner server in the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="ba2cb-108">簡略化された次の一連のイベントは、ミラーリング用に構成されたデータベースをターゲットにする <xref:System.Data.SqlClient.SqlConnection> オブジェクトに対して発生します。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-108">The following simplified sequence of events occurs for a <xref:System.Data.SqlClient.SqlConnection> object that targets a database configured for mirroring:</span></span>  
  
1. <span data-ttu-id="ba2cb-109">クライアント アプリケーションがプリンシパル データベースに正常に接続し、サーバーがパートナー サーバーの名前を送り返します。その後、その名前がクライアントでキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-109">The client application successfully connects to the principal database, and the server sends back the name of the partner server, which is then cached on the client.</span></span>  
  
2. <span data-ttu-id="ba2cb-110">プリンシパル データベースを含むサーバーに障害が発生、または接続が中断された場合、接続およびトランザクション状態は失われます。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-110">If the server containing the principal database fails or connectivity is interrupted, connection and transaction state is lost.</span></span> <span data-ttu-id="ba2cb-111">クライアント アプリケーションがプリンシパル データベースへの接続を再確立しようとして失敗します。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-111">The client application attempts to re-establish a connection to the principal database and fails.</span></span>  
  
3. <span data-ttu-id="ba2cb-112">次に、クライアント アプリケーションがパートナー サーバー上のミラー データベースへの接続を透過的に確立しようとします。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-112">The client application then transparently attempts to establish a connection to the mirror database on the partner server.</span></span> <span data-ttu-id="ba2cb-113">この処理に成功すると、新しいプリンシパル データベースとなるミラー データベースに、接続がリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-113">If it succeeds, the connection is redirected to the mirror database, which then becomes the new principal database.</span></span>  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a><span data-ttu-id="ba2cb-114">接続文字列でのフェールオーバー パートナーの指定</span><span class="sxs-lookup"><span data-stu-id="ba2cb-114">Specifying the Failover Partner in the Connection String</span></span>  

 <span data-ttu-id="ba2cb-115">接続文字列でフェールオーバー パートナー サーバーの名前を指定すると、クライアント アプリケーションが最初に接続するときにプリンシパル データベースを使用できない場合、クライアントはフェールオーバー パートナーへの接続を透過的に試行します。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-115">If you supply the name of a failover partner server in the connection string, the client will transparently attempt a connection with the failover partner if the principal database is unavailable when the client application first connects.</span></span>  
  
```csharp
";Failover Partner=PartnerServerName"  
```  
  
 <span data-ttu-id="ba2cb-116">フェールオーバー パートナー サーバーの名前を省略すると、クライアント アプリケーションの最初の接続時にプリンシパル データベースが使用できない場合、<xref:System.Data.SqlClient.SqlException> が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-116">If you omit the name of the failover partner server and the principal database is unavailable when the client application first connects then a <xref:System.Data.SqlClient.SqlException> is raised.</span></span>  
  
 <span data-ttu-id="ba2cb-117"><xref:System.Data.SqlClient.SqlConnection> が正常に開かれた場合は、サーバーからフェールオーバー パートナー名が返され、接続文字列で指定されたすべての値と置き換わります。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-117">When a <xref:System.Data.SqlClient.SqlConnection> is successfully opened, the failover partner name is returned by the server and supersedes any values supplied in the connection string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba2cb-118">データベース ミラーリングのシナリオでは、接続文字列で初期カタログまたはデータベース名を明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-118">You must explicitly specify the initial catalog or database name in the connection string for database mirroring scenarios.</span></span> <span data-ttu-id="ba2cb-119">クライアントが、初期カタログやデータベースが明示的に指定されていない接続に関するフェールオーバー情報を受信する場合は、このフェールオーバー情報はキャッシュされず、アプリケーションはプリンシパル サーバーでの障害発生時にフェールオーバーを試行しません。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-119">If the client receives failover information on a connection that doesn't have an explicitly specified initial catalog or database, the failover information is not cached and the application does not attempt to fail over if the principal server fails.</span></span> <span data-ttu-id="ba2cb-120">接続文字列にフェールオーバー パートナーの値が含まれていても、初期カタログまたはデータベースの値が含まれていない場合、`InvalidArgumentException` が発生します。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-120">If a connection string has a value for the failover partner, but no value for the initial catalog or database, an `InvalidArgumentException` is raised.</span></span>  
  
## <a name="retrieving-the-current-server-name"></a><span data-ttu-id="ba2cb-121">現在のサーバー名の取得</span><span class="sxs-lookup"><span data-stu-id="ba2cb-121">Retrieving the Current Server Name</span></span>  

 <span data-ttu-id="ba2cb-122">フェールオーバーの場合には、<xref:System.Data.SqlClient.SqlConnection.DataSource%2A> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> プロパティを使って、現在の接続が実際に接続されているサーバーの名前を取得できます。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-122">In the event of a failover, you can retrieve the name of the server to which the current connection is actually connected by using the <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> property of a <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="ba2cb-123">次のコード フラグメントでは、接続変数が開いている <xref:System.Data.SqlClient.SqlConnection> を参照していることを前提として、アクティブなサーバーの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-123">The following code fragment retrieves the name of the active server, assuming that the connection variable references an open <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
 <span data-ttu-id="ba2cb-124">フェールオーバー イベントが発生し、接続がミラー サーバーに切り替えられた場合は、**DataSource** プロパティがそのミラー名を反映するように更新されます。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-124">When a failover event occurs and the connection is switched to the mirror server, the **DataSource** property is updated to reflect the mirror name.</span></span>  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a><span data-ttu-id="ba2cb-125">SqlClient ミラーリングの動作</span><span class="sxs-lookup"><span data-stu-id="ba2cb-125">SqlClient Mirroring Behavior</span></span>  

 <span data-ttu-id="ba2cb-126">クライアントは、常に現在のプリンシパル サーバーに接続しようとします。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-126">The client always tries to connect to the current principal server.</span></span> <span data-ttu-id="ba2cb-127">それが失敗すると、フェールオーバー パートナーを試します。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-127">If it fails, it tries the failover partner.</span></span> <span data-ttu-id="ba2cb-128">ミラー データベースが既にパートナー サーバー上のプリンシパル ロールに切り替えられている場合、接続は成功し、新しいプリンシパル/ミラーのマッピングがクライアントに送信され、<xref:System.AppDomain> の呼び出しが有効な間はキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-128">If the mirror database has already been switched to the principal role on the partner server, the connection succeeds and the new principal-mirror mapping is sent to the client and cached for the lifetime of the calling <xref:System.AppDomain>.</span></span> <span data-ttu-id="ba2cb-129">このマッピングは永続ストレージには格納されないため、別の **AppDomain** 内またはプロセス内で次回の接続に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-129">It is not stored in persistent storage and is not available for subsequent connections in a different **AppDomain** or process.</span></span> <span data-ttu-id="ba2cb-130">ただし、同一の **AppDomain** 内では次回の接続に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-130">However, it is available for subsequent connections within the same **AppDomain**.</span></span> <span data-ttu-id="ba2cb-131">同一または別のコンピューター上で実行されている、別の **AppDomain** またはプロセスには常に接続のプールがあり、これらの接続はリセットされません。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-131">Note that another **AppDomain** or process running on the same or a different computer always has its pool of connections, and those connections are not reset.</span></span> <span data-ttu-id="ba2cb-132">このとき、プライマリ データベースがダウンし、各プロセスまたは **AppDomain** が失敗した場合、プールは自動的に消去されます。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-132">In that case, if the primary database goes down, each process or **AppDomain** fails once, and the pool is automatically cleared.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba2cb-133">サーバー上のミラーリングのサポートは、データベースごとに構成されます。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-133">Mirroring support on the server is configured on a per-database basis.</span></span> <span data-ttu-id="ba2cb-134">マルチパート名を使用するか、または現在のデータベースを変更し、プリンシパル/ミラー セットに含まれていない他のデータベースに対してデータ操作が行われた場合、障害が発生したときは、これらの他のデータベースへの変更は伝播されません。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-134">If data manipulation operations are executed against other databases not included in the principal/mirror set, either by using multipart names or by changing the current database, the changes to these other databases do not propagate in the event of failure.</span></span> <span data-ttu-id="ba2cb-135">ミラー化されていないデータベースでデータが変更されても、エラーは生成されません。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-135">No error is generated when data is modified in a database that is not mirrored.</span></span> <span data-ttu-id="ba2cb-136">開発者は、このような操作の考えられる影響を評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-136">The developer must evaluate the possible impact of such operations.</span></span>  
  
## <a name="database-mirroring-resources"></a><span data-ttu-id="ba2cb-137">データベース ミラーリングに関するリソース</span><span class="sxs-lookup"><span data-stu-id="ba2cb-137">Database Mirroring Resources</span></span>  

 <span data-ttu-id="ba2cb-138">ミラーリングの構成、配置、管理の概念に関するドキュメントや情報については、SQL Server ドキュメントの次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-138">For conceptual documentation and information on configuring, deploying and administering mirroring, see the following resources in SQL Server documentation.</span></span>  
  
|<span data-ttu-id="ba2cb-139">リソース</span><span class="sxs-lookup"><span data-stu-id="ba2cb-139">Resource</span></span>|<span data-ttu-id="ba2cb-140">説明</span><span class="sxs-lookup"><span data-stu-id="ba2cb-140">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="ba2cb-141">データベース ミラーリング</span><span class="sxs-lookup"><span data-stu-id="ba2cb-141">Database Mirroring</span></span>](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|<span data-ttu-id="ba2cb-142">SQL Server でのミラーリングの設定と構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba2cb-142">Describes how to set up and configure mirroring in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba2cb-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba2cb-143">See also</span></span>

- [<span data-ttu-id="ba2cb-144">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="ba2cb-144">ADO.NET Overview</span></span>](../ado-net-overview.md)
