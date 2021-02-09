---
description: '詳細情報: SQL Server での複数データベースにまたがるアクセスの有効化'
title: SQL Server での複数データベースにまたがるアクセスの有効化
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 4e818b4f0294fdc7edd351a1e60203357579a320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695867"
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="3df1d-103">SQL Server での複数データベースにまたがるアクセスの有効化</span><span class="sxs-lookup"><span data-stu-id="3df1d-103">Enabling Cross-Database Access in SQL Server</span></span>

<span data-ttu-id="3df1d-104">複数データベースの組み合わせ所有権は、あるデータベースのプロシージャが、別のデータベースのオブジェクトに依存している場合に作用します。</span><span class="sxs-lookup"><span data-stu-id="3df1d-104">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="3df1d-105">複数データベースの組み合わせ所有権は、単一データベースの組み合わせ所有権とほぼ同じように機能しますが、所有権の連鎖性を保つために、すべてのオブジェクトの所有者が同じログイン アカウントにマップされていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="3df1d-105">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="3df1d-106">ソース データベース内のソース オブジェクトおよびターゲット データベース内のターゲット オブジェクトが同じログイン アカウントによって所有されている場合、ターゲット オブジェクトに対する権限は SQL Server によってチェックされません。</span><span class="sxs-lookup"><span data-stu-id="3df1d-106">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="3df1d-107">既定で無効の機能</span><span class="sxs-lookup"><span data-stu-id="3df1d-107">Off By Default</span></span>  

 <span data-ttu-id="3df1d-108">複数データベースにまたがる組み合わせ所有権は、既定では無効になっています。</span><span class="sxs-lookup"><span data-stu-id="3df1d-108">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="3df1d-109">次に示したように、複数データベースの組み合わせ所有権はセキュリティ上のリスクを伴うため無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3df1d-109">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
- <span data-ttu-id="3df1d-110">`db_ddladmin` データベース ロールまたは `db_owners` データベース ロールのデータベース所有者およびメンバーは、他のユーザーによって所有されたオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3df1d-110">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="3df1d-111">これらのオブジェクトが、他のデータベースのオブジェクトに依存している可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="3df1d-111">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="3df1d-112">これは、複数データベースの組み合わせ所有権を有効にした場合、すべてのデータベースのデータについて、これらのユーザーを完全に信頼する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="3df1d-112">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
- <span data-ttu-id="3df1d-113">CREATE DATABASE 権限を持つユーザーは、新しいデータベースを作成したり、既存のデータベースをアタッチしたりできます。</span><span class="sxs-lookup"><span data-stu-id="3df1d-113">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="3df1d-114">複数データベースの組み合わせ所有権を有効にした場合、これらのユーザーが、新たに作成したデータベースから (または、アタッチしたデータベースから)、権限を持たない他のデータベース内のオブジェクトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3df1d-114">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="3df1d-115">複数データベースの組み合わせ所有権の有効化</span><span class="sxs-lookup"><span data-stu-id="3df1d-115">Enabling Cross-database Ownership Chaining</span></span>  

 <span data-ttu-id="3df1d-116">高い権限が与えられたユーザーを完全に信頼できる環境であれば、複数データベースの組み合わせ所有権を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3df1d-116">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="3df1d-117">複数データベースの組み合わせ所有権は、セットアップ時にすべてのデータベースを対象に構成できるほか、Transact-SQL コマンドの `sp_configure` および `ALTER DATABASE` を使用することで、特定のデータベースを対象に構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3df1d-117">It can be configured during setup for all databases, or selectively for specific databases using the Transact-SQL commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="3df1d-118">複数データベースの組み合わせ所有権を個別に構成するには、`sp_configure` を使用し、サーバーに対してこの機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="3df1d-118">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="3df1d-119">次に、ALTER DATABASE コマンドで SET DB_CHAINING ON を指定し、必要なデータベースに対してのみ、複数データベースの組み合わせ所有権を構成します。</span><span class="sxs-lookup"><span data-stu-id="3df1d-119">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="3df1d-120">次のサンプルでは、すべてのデータベースに対して複数データベースの組み合わせ所有権を有効にします。</span><span class="sxs-lookup"><span data-stu-id="3df1d-120">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```sql
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="3df1d-121">次のサンプルでは、特定のデータベースに対して複数データベースの組み合わせ所有権を有効にします。</span><span class="sxs-lookup"><span data-stu-id="3df1d-121">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```sql
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="3df1d-122">動的 SQL</span><span class="sxs-lookup"><span data-stu-id="3df1d-122">Dynamic SQL</span></span>  

 <span data-ttu-id="3df1d-123">動的に生成された SQL ステートメントの実行では、同じユーザーが両方のデータベースに存在しない限り、複数データベースの組み合わせ所有権は機能しません。</span><span class="sxs-lookup"><span data-stu-id="3df1d-123">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="3df1d-124">SQL Server では、別のデータベースのデータにアクセスするストアド プロシージャを作成し、両方のデータベースに存在する証明書でそのプロシージャに署名することによって、この制限を回避できます。</span><span class="sxs-lookup"><span data-stu-id="3df1d-124">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="3df1d-125">これにより、ユーザーは、データベースへのアクセス許可が付与されていなくても、そのプロシージャによって使用されるデータベース リソースにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="3df1d-125">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="3df1d-126">外部リソース</span><span class="sxs-lookup"><span data-stu-id="3df1d-126">External Resources</span></span>  

 <span data-ttu-id="3df1d-127">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3df1d-127">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="3df1d-128">リソース</span><span class="sxs-lookup"><span data-stu-id="3df1d-128">Resource</span></span>|<span data-ttu-id="3df1d-129">説明</span><span class="sxs-lookup"><span data-stu-id="3df1d-129">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3df1d-130">「[EXECUTE AS の使用によるデータベースの権限借用の拡張](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105))」および「[cross db ownership chaining サーバー構成オプション](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option)」。</span><span class="sxs-lookup"><span data-stu-id="3df1d-130">[Extending Database Impersonation by Using EXECUTE AS](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) and [Cross DB Ownership Chaining Option](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).</span></span>|<span data-ttu-id="3df1d-131">SQL Server のインスタンスに対して、複数データベースの組み合わせ所有権を構成する方法が説明されています。</span><span class="sxs-lookup"><span data-stu-id="3df1d-131">Articles describe how to configure cross-database ownership chaining for an instance of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3df1d-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="3df1d-132">See also</span></span>

- [<span data-ttu-id="3df1d-133">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="3df1d-133">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="3df1d-134">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="3df1d-134">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="3df1d-135">SQL Server でのストアド プロシージャを使用したアクセス許可の管理</span><span class="sxs-lookup"><span data-stu-id="3df1d-135">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="3df1d-136">SQL Server での安全な動的 SQL の作成</span><span class="sxs-lookup"><span data-stu-id="3df1d-136">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="3df1d-137">SQL Server でのストアド プロシージャの署名</span><span class="sxs-lookup"><span data-stu-id="3df1d-137">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="3df1d-138">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="3df1d-138">ADO.NET Overview</span></span>](../ado-net-overview.md)
