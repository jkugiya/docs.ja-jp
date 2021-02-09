---
description: '詳細情報: SQL Server でのアプリケーション ロールの作成'
title: SQL Server でのアプリケーション ロールの作成
ms.date: 03/30/2017
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
ms.openlocfilehash: 20047d12a004230aebca1cf9d42b3893d36f3844
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786161"
---
# <a name="creating-application-roles-in-sql-server"></a><span data-ttu-id="65072-103">SQL Server でのアプリケーション ロールの作成</span><span class="sxs-lookup"><span data-stu-id="65072-103">Creating Application Roles in SQL Server</span></span>

<span data-ttu-id="65072-104">アプリケーション ロールは、データベース ロールやユーザーに対してではなく、アプリケーションに権限を割り当てる手段です。</span><span class="sxs-lookup"><span data-stu-id="65072-104">Application roles provide a way to assign permissions to an application instead of a database role or user.</span></span> <span data-ttu-id="65072-105">ユーザーはデータベースに接続し、アプリケーション ロールをアクティブ化して、そのアプリケーションに付与された権限を使用することになります。</span><span class="sxs-lookup"><span data-stu-id="65072-105">Users can connect to the database, activate the application role, and assume the permissions granted to the application.</span></span> <span data-ttu-id="65072-106">アプリケーション ロールに付与された権限は、接続している間のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="65072-106">The permissions granted to the application role are in force for the duration of the connection.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="65072-107">アプリケーション ロールは、クライアント アプリケーションが接続文字列でアプリケーション ロール名とパスワードを渡すことによってアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="65072-107">Application roles are activated when a client application supplies an application role name and a password in the connection string.</span></span> <span data-ttu-id="65072-108">2 層アプリケーションでは、パスワードをクライアント コンピューターに保存する必要があるため、セキュリティ上の脆弱性を伴います。</span><span class="sxs-lookup"><span data-stu-id="65072-108">They present a security vulnerability in a two-tier application because the password must be stored on the client computer.</span></span> <span data-ttu-id="65072-109">3 層アプリケーションでは、アプリケーションのユーザーがアクセスできないような形でパスワードを保存できます。</span><span class="sxs-lookup"><span data-stu-id="65072-109">In a three-tier application, you can store the password so that it cannot be accessed by users of the application.</span></span>  
  
## <a name="application-role-features"></a><span data-ttu-id="65072-110">アプリケーション ロールの特徴</span><span class="sxs-lookup"><span data-stu-id="65072-110">Application Role Features</span></span>  

 <span data-ttu-id="65072-111">アプリケーション ロールには次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="65072-111">Application roles have the following features:</span></span>  
  
- <span data-ttu-id="65072-112">データベース ロールとは異なり、アプリケーション ロールはメンバーを持ちません。</span><span class="sxs-lookup"><span data-stu-id="65072-112">Unlike database roles, application roles contain no members.</span></span>  
  
- <span data-ttu-id="65072-113">アプリケーション ロールは、アプリケーションが `sp_setapprole` システム ストアド プロシージャにアプリケーション ロール名とパスワードを渡すことによってアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="65072-113">Application roles are activated when an application supplies the application role name and a password to the `sp_setapprole` system stored procedure.</span></span>  
  
- <span data-ttu-id="65072-114">パスワードはクライアント コンピューターに保存しておき、実行時に渡す必要があります。アプリケーション ロールを SQL Server 内からアクティブ化することはできません。</span><span class="sxs-lookup"><span data-stu-id="65072-114">The password must be stored on the client computer and supplied at run time; an application role cannot be activated from inside of SQL Server.</span></span>  
  
- <span data-ttu-id="65072-115">パスワードは暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="65072-115">The password is not encrypted.</span></span> <span data-ttu-id="65072-116">パラメーターのパスワードが一方向のハッシュとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="65072-116">The parameter password is stored as a one-way hash.</span></span>  
  
- <span data-ttu-id="65072-117">アクティブ化後、アプリケーション ロールを使用して取得した権限は、接続している間のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="65072-117">Once activated, permissions acquired through the application role remain in effect for the duration of the connection.</span></span>  
  
- <span data-ttu-id="65072-118">アプリケーション ロールは、`public` ロールに付与された権限を継承します。</span><span class="sxs-lookup"><span data-stu-id="65072-118">The application role inherits permissions granted to the `public` role.</span></span>  
  
- <span data-ttu-id="65072-119">アプリケーション ロールが `sysadmin` 固定サーバー ロールのメンバーによってアクティブ化された場合、セキュリティ コンテキストは、接続している間、アプリケーション ロールのセキュリティ コンテキストに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="65072-119">If a member of the `sysadmin` fixed server role activates an application role, the security context switches to that of the application role for the duration of the connection.</span></span>  
  
- <span data-ttu-id="65072-120">アプリケーション ロールを持ったデータベースに `guest` アカウントを作成した場合、そのアプリケーション ロールまたはそれを呼び出すログインに対するデータベース ユーザー アカウントを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="65072-120">If you create a `guest` account in a database that has an application role, you do not need to create a database user account for the application role or for any of the logins that invoke it.</span></span> <span data-ttu-id="65072-121">別のデータベースに `guest` アカウントが存在する場合は、アプリケーション ロールでそのデータベースに直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="65072-121">Application roles can directly access another database only if a `guest` account exists in the second database</span></span>  
  
- <span data-ttu-id="65072-122">SYSTEM_USER など、ログイン名を返す組み込み関数を実行した場合、アプリケーション ロールを呼び出したログイン名が返されます。</span><span class="sxs-lookup"><span data-stu-id="65072-122">Built-in functions that return login names, such as SYSTEM_USER, return the name of the login that invoked the application role.</span></span> <span data-ttu-id="65072-123">データベース ユーザー名を返す組み込み関数を実行した場合、アプリケーション ロールの名前が返されます。</span><span class="sxs-lookup"><span data-stu-id="65072-123">Built-in functions that return database user names return the name of the application role.</span></span>  
  
### <a name="the-principle-of-least-privilege"></a><span data-ttu-id="65072-124">最小特権の原則</span><span class="sxs-lookup"><span data-stu-id="65072-124">The Principle of Least Privilege</span></span>  

 <span data-ttu-id="65072-125">パスワードが漏洩した場合に備えて、アプリケーション ロールには必要な権限だけを付与してください。</span><span class="sxs-lookup"><span data-stu-id="65072-125">Application roles should be granted only required permissions in case the password is compromised.</span></span> <span data-ttu-id="65072-126">アプリケーション ロールを使ったデータベースでは、`public` ロールに対する権限は取り消す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65072-126">Permissions to the `public` role should be revoked in any database using an application role.</span></span> <span data-ttu-id="65072-127">アプリケーション ロールの呼び出し元が特定のデータベースにアクセスできないようにするには、そのデータベースの `guest` アカウントを無効にします。</span><span class="sxs-lookup"><span data-stu-id="65072-127">Disable the `guest` account in any database you do not want callers of the application role to have access to.</span></span>  
  
### <a name="application-role-enhancements"></a><span data-ttu-id="65072-128">アプリケーション ロールの機能強化</span><span class="sxs-lookup"><span data-stu-id="65072-128">Application Role Enhancements</span></span>  

 <span data-ttu-id="65072-129">アプリケーション ロールをアクティブ化した後で実行コンテキストを元の呼び出し元に戻すことができるため、接続プールを無効にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="65072-129">The execution context can be switched back to the original caller after activating an application role, removing the need to disable connection pooling.</span></span> <span data-ttu-id="65072-130">呼び出し元のコンテキスト情報を格納するクッキーを作成するための新しいオプションが `sp_setapprole` プロシージャに追加されています。</span><span class="sxs-lookup"><span data-stu-id="65072-130">The `sp_setapprole` procedure has a new option that creates a cookie, which contains context information about the caller.</span></span> <span data-ttu-id="65072-131">`sp_unsetapprole` プロシージャにそのクッキーを渡して呼び出すことによって、元のセッションに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="65072-131">You can revert the session by calling the `sp_unsetapprole` procedure, passing it the cookie.</span></span>  
  
## <a name="application-role-alternatives"></a><span data-ttu-id="65072-132">アプリケーション ロールに代わる方法</span><span class="sxs-lookup"><span data-stu-id="65072-132">Application Role Alternatives</span></span>  

 <span data-ttu-id="65072-133">アプリケーション ロールはパスワードのセキュリティに依存する関係上、セキュリティ上の脆弱性を伴います。</span><span class="sxs-lookup"><span data-stu-id="65072-133">Application roles depend on the security of a password, which presents a potential security vulnerability.</span></span> <span data-ttu-id="65072-134">パスワードをアプリケーション コードに組み込んだり、ディスクに保存したりすると、パスワードが漏洩する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65072-134">Passwords may be exposed by being embedded in application code or saved on disk.</span></span>  
  
 <span data-ttu-id="65072-135">以下の代替策を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65072-135">You may want to consider the following alternatives.</span></span>  
  
- <span data-ttu-id="65072-136">EXECUTE AS ステートメントに NO REVERT 句と WITH COOKIE 句を指定してコンテキスト切り替えを行う。</span><span class="sxs-lookup"><span data-stu-id="65072-136">Use context switching with the EXECUTE AS statement with its NO REVERT and WITH COOKIE clauses.</span></span> <span data-ttu-id="65072-137">ログインにマップされていないユーザー アカウントをデータベースに作成し、</span><span class="sxs-lookup"><span data-stu-id="65072-137">You can create a user account in a database that is not mapped to a login.</span></span> <span data-ttu-id="65072-138">このアカウントに権限を割り当てるようにします。</span><span class="sxs-lookup"><span data-stu-id="65072-138">You then assign permissions to this account.</span></span> <span data-ttu-id="65072-139">EXECUTE AS はパスワード ベースではなく、権限ベースであるため、非ログイン ユーザーで使用した方が高いセキュリティを確保できます。</span><span class="sxs-lookup"><span data-stu-id="65072-139">Using EXECUTE AS with a login-less user is more secure because it is permission-based, not password-based.</span></span> <span data-ttu-id="65072-140">詳しくは、「[SQL Server での借用を使用した権限のカスタマイズ](customizing-permissions-with-impersonation-in-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="65072-140">For more information, see [Customizing Permissions with Impersonation in SQL Server](customizing-permissions-with-impersonation-in-sql-server.md).</span></span>  
  
- <span data-ttu-id="65072-141">証明書を使ってストアド プロシージャに署名し、そのプロシージャを実行するのに必要な権限だけを付与する。</span><span class="sxs-lookup"><span data-stu-id="65072-141">Sign stored procedures with certificates, granting only permission to execute the procedures.</span></span> <span data-ttu-id="65072-142">詳しくは、「[SQL Server でのストアド プロシージャの署名](signing-stored-procedures-in-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="65072-142">For more information, see [Signing Stored Procedures in SQL Server](signing-stored-procedures-in-sql-server.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="65072-143">外部リソース</span><span class="sxs-lookup"><span data-stu-id="65072-143">External Resources</span></span>  

 <span data-ttu-id="65072-144">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65072-144">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="65072-145">リソース</span><span class="sxs-lookup"><span data-stu-id="65072-145">Resource</span></span>|<span data-ttu-id="65072-146">説明</span><span class="sxs-lookup"><span data-stu-id="65072-146">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="65072-147">アプリケーション ロール</span><span class="sxs-lookup"><span data-stu-id="65072-147">Application Roles</span></span>](/sql/relational-databases/security/authentication-access/application-roles)|<span data-ttu-id="65072-148">SQL Server 2008 でアプリケーション ロールを作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="65072-148">Describes how to create and use application roles in SQL Server 2008.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65072-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="65072-149">See also</span></span>

- [<span data-ttu-id="65072-150">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="65072-150">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="65072-151">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="65072-151">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="65072-152">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="65072-152">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="65072-153">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="65072-153">ADO.NET Overview</span></span>](../ado-net-overview.md)
