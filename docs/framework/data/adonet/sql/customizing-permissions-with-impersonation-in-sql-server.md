---
description: '詳細情報: SQL Server での借用を使用した権限のカスタマイズ'
title: SQL Server での借用を使用した権限のカスタマイズ
ms.date: 03/30/2017
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
ms.openlocfilehash: 1c2cada004b8f604ccbb9448f40e00bea472771f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786122"
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a><span data-ttu-id="4f57b-103">SQL Server での借用を使用した権限のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="4f57b-103">Customizing Permissions with Impersonation in SQL Server</span></span>

<span data-ttu-id="4f57b-104">多くのアプリケーションでは、ベース テーブルへのアクセスを制限する組み合わせ所有権を利用して、ストアド プロシージャを使ってデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4f57b-104">Many applications use stored procedures to access data, relying on ownership chaining to restrict access to base tables.</span></span> <span data-ttu-id="4f57b-105">ストアド プロシージャに対して EXECUTE 権限を付与するとき、ベース テーブルに対する権限を取り消したり拒否したりできます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-105">You can grant EXECUTE permissions on stored procedures, revoking or denying permissions on the base tables.</span></span> <span data-ttu-id="4f57b-106">ストアド プロシージャとテーブルの所有者が同じ場合、SQL Server では呼び出し元の権限をチェックしません。</span><span class="sxs-lookup"><span data-stu-id="4f57b-106">SQL Server does not check the permissions of the caller if the stored procedure and tables have the same owner.</span></span> <span data-ttu-id="4f57b-107">ただし、オブジェクトの所有者が異なる場合や、動的 SQL の場合には、組み合わせ所有権が無効になります。</span><span class="sxs-lookup"><span data-stu-id="4f57b-107">However, ownership chaining doesn't work if objects have different owners or in the case of dynamic SQL.</span></span>  
  
 <span data-ttu-id="4f57b-108">参照先オブジェクトに対する権限が呼び出し元になくても、ストアド プロシージャで EXECUTE AS 句を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-108">You can use the EXECUTE AS clause in a stored procedure when the caller doesn't have permissions on the referenced database objects.</span></span> <span data-ttu-id="4f57b-109">EXECUTE AS 句の効果は、実行コンテキストがプロキシ ユーザーに切り替えられることです。</span><span class="sxs-lookup"><span data-stu-id="4f57b-109">The effect of the EXECUTE AS clause is that the execution context is switched to the proxy user.</span></span> <span data-ttu-id="4f57b-110">入れ子になったストアド プロシージャやトリガーへの呼び出しを含め、すべてのコードがプロキシ ユーザーのセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-110">All code, as well as any calls to nested stored procedures or triggers, executes under the security context of the proxy user.</span></span> <span data-ttu-id="4f57b-111">プロシージャの実行後、または REVERT ステートメントが発行されたときにのみ、実行コンテキストが最初の呼び出し元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="4f57b-111">Execution context is reverted to the original caller only after execution of the procedure or when a REVERT statement is issued.</span></span>  
  
## <a name="context-switching-with-the-execute-as-statement"></a><span data-ttu-id="4f57b-112">EXECUTE AS ステートメントを使用したコンテキスト切り替え</span><span class="sxs-lookup"><span data-stu-id="4f57b-112">Context Switching with the EXECUTE AS Statement</span></span>  

 <span data-ttu-id="4f57b-113">Transact-SQL の EXECUTE AS ステートメントを使用して、別のログインまたはデータベース ユーザーの権限を借用することで、ステートメントの実行コンテキストを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-113">The Transact-SQL EXECUTE AS statement allows you to switch the execution context of a statement by impersonating another login or database user.</span></span> <span data-ttu-id="4f57b-114">これは、クエリとプロシージャを別のユーザーとしてテストできる便利な手法です。</span><span class="sxs-lookup"><span data-stu-id="4f57b-114">This is a useful technique for testing queries and procedures as another user.</span></span>  
  
```sql  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 <span data-ttu-id="4f57b-115">権限を借用するログインまたはユーザーに対する IMPERSONATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4f57b-115">You must have IMPERSONATE permissions on the login or user you are impersonating.</span></span> <span data-ttu-id="4f57b-116">この権限は、`sysadmin` にはすべてのデータベースに対して与えられ、`db_owner` ロールのメンバーには所有するデータベースに対して与えられます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-116">This permission is implied for `sysadmin` for all databases, and `db_owner` role members in databases that they own.</span></span>  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a><span data-ttu-id="4f57b-117">EXECUTE AS 句を使用した権限の許可</span><span class="sxs-lookup"><span data-stu-id="4f57b-117">Granting Permissions with the EXECUTE AS Clause</span></span>  

 <span data-ttu-id="4f57b-118">EXECUTE AS 句は、ストアド プロシージャ、トリガー、ユーザー定義関数 (インライン テーブル値関数を除く) の定義ヘッダーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-118">You can use the EXECUTE AS clause in the definition header of a stored procedure, trigger, or user-defined function (except for inline table-valued functions).</span></span> <span data-ttu-id="4f57b-119">そのため、EXECUTE AS 句で指定されたユーザー名またはキーワードのコンテキストでプロシージャが実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-119">This causes the procedure to execute in the context of the user name or keyword specified in the EXECUTE AS clause.</span></span> <span data-ttu-id="4f57b-120">データベースに、ログインに割り当てられないプロキシ ユーザーを作成し、プロシージャがアクセスするオブジェクトに対して必要な権限のみを許可することができます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-120">You can create a proxy user in the database that is not mapped to a login, granting it only the necessary permissions on the objects accessed by the procedure.</span></span> <span data-ttu-id="4f57b-121">EXECUTE AS 句で指定されたプロキシ ユーザーのみが、モジュールからアクセスされるすべてのオブジェクトに対する権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f57b-121">Only the proxy user specified in the EXECUTE AS clause must have permissions on all objects accessed by the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f57b-122">TRUNCATE TABLE など、許可する権限のない操作もあります。</span><span class="sxs-lookup"><span data-stu-id="4f57b-122">Some actions, such as TRUNCATE TABLE, do not have grantable permissions.</span></span> <span data-ttu-id="4f57b-123">プロシージャ内にステートメントを組み込み、ALTER TABLE 権限を持つプロキシ ユーザーを指定することで、プロシージャに対する EXECUTE 権限のみを持つ呼び出し元に、テーブルを切り捨てる権限を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-123">By incorporating the statement within a procedure and specifying a proxy user who has ALTER TABLE permissions, you can extend the permissions to truncate the table to callers who have only EXECUTE permissions on the procedure.</span></span>  
  
 <span data-ttu-id="4f57b-124">EXECUTE AS 句で指定されたコンテキストは、入れ子になったプロシージャやトリガーを含むプロシージャの実行中に有効となります。</span><span class="sxs-lookup"><span data-stu-id="4f57b-124">The context specified in the EXECUTE AS clause is valid for the duration of the procedure, including nested procedures and triggers.</span></span> <span data-ttu-id="4f57b-125">実行が完了したとき、または REVERT ステートメントが発行されたときに、コンテキストが呼び出し元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="4f57b-125">Context reverts to the caller when execution is complete or the REVERT statement is issued.</span></span>  
  
 <span data-ttu-id="4f57b-126">プロシージャで EXECUTE AS 句を使用する際には、次の 3 つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4f57b-126">There are three steps involved in using the EXECUTE AS clause in a procedure.</span></span>  
  
1. <span data-ttu-id="4f57b-127">ログインに割り当てられていないプロキシ ユーザーをデータベースに作成します。</span><span class="sxs-lookup"><span data-stu-id="4f57b-127">Create a proxy user in the database that is not mapped to a login.</span></span> <span data-ttu-id="4f57b-128">この操作は必須ではありませんが、権限を管理するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-128">This is not required, but it helps when managing permissions.</span></span>  
  
```sql
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1. <span data-ttu-id="4f57b-129">プロキシ ユーザーに必要な権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-129">Grant the proxy user the necessary permissions.</span></span>  
  
2. <span data-ttu-id="4f57b-130">ストアド プロシージャまたはユーザー定義関数に EXECUTE AS 句を追加します。</span><span class="sxs-lookup"><span data-stu-id="4f57b-130">Add the EXECUTE AS clause to the stored procedure or user-defined function.</span></span>  
  
```sql
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
> <span data-ttu-id="4f57b-131">呼び出し元の元のセキュリティ コンテキストが保持されないため、監査の必要なアプリケーションはブレークされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f57b-131">Applications that require auditing can break because the original security context of the caller is not retained.</span></span> <span data-ttu-id="4f57b-132">SESSION_USER、USER、USER_NAME など、現在のユーザーの識別情報を返す組み込み関数では、最初の呼び出し元ではなく EXECUTE AS 句に関連付けられているユーザーが返されます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-132">Built-in functions that return the identity of the current user, such as SESSION_USER, USER, or USER_NAME, return the user associated with the EXECUTE AS clause, not the original caller.</span></span>  
  
### <a name="using-execute-as-with-revert"></a><span data-ttu-id="4f57b-133">REVERT での EXECUTE AS の使用</span><span class="sxs-lookup"><span data-stu-id="4f57b-133">Using EXECUTE AS with REVERT</span></span>  

 <span data-ttu-id="4f57b-134">Transact-SQL REVERT ステートメントを使用して、元の実行コンテキストに戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-134">You can use the Transact-SQL REVERT statement to revert to the original execution context.</span></span>  
  
 <span data-ttu-id="4f57b-135">オプションの句である WITH NO REVERT COOKIE = @variableName を使用すると、@variableName 変数に正しい値が含まれていれば、実行コンテキストを呼び出し元に切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-135">The optional clause, WITH NO REVERT COOKIE = @variableName, allows you switch the execution context back to the caller if the @variableName variable contains the correct value.</span></span> <span data-ttu-id="4f57b-136">これにより、接続プールが使用されている環境では実行コンテキストを呼び出し元に切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-136">This allows you to switch the execution context back to the caller in environments where connection pooling is used.</span></span> <span data-ttu-id="4f57b-137">@variableName の値は、EXECUTE AS ステートメントの呼び出し元のみが把握しているため、実行コンテキストがアプリケーションを呼び出したエンド ユーザーによって変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="4f57b-137">Because the value of @variableName is known only to the caller of the EXECUTE AS statement, the caller can guarantee that the execution context cannot be changed by the end user that invokes the application.</span></span> <span data-ttu-id="4f57b-138">接続は、閉じられるとプールに返されます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-138">When the connection is closed, it is returned to the pool.</span></span> <span data-ttu-id="4f57b-139">ADO.NET での接続プールについて詳しくは、「[SQL Server の接続プール (ADO.NET)](../sql-server-connection-pooling.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4f57b-139">For more information on connection pooling in ADO.NET, see [SQL Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md).</span></span>  
  
### <a name="specifying-the-execution-context"></a><span data-ttu-id="4f57b-140">実行コンテキストの指定</span><span class="sxs-lookup"><span data-stu-id="4f57b-140">Specifying the Execution Context</span></span>  

 <span data-ttu-id="4f57b-141">EXECUTE AS は、ユーザーを指定するだけでなく、次のキーワードを指定して使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-141">In addition to specifying a user, you can also use EXECUTE AS with any of the following keywords.</span></span>  
  
- <span data-ttu-id="4f57b-142">CALLER : </span><span class="sxs-lookup"><span data-stu-id="4f57b-142">CALLER.</span></span> <span data-ttu-id="4f57b-143">既定で、CALLER として実行されます。他にオプションが指定されていない場合、プロシージャは呼び出し元のセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-143">Executing as CALLER is the default; if no other option is specified, then the procedure executes in the security context of the caller.</span></span>  
  
- <span data-ttu-id="4f57b-144">OWNER : </span><span class="sxs-lookup"><span data-stu-id="4f57b-144">OWNER.</span></span> <span data-ttu-id="4f57b-145">OWNER として実行すると、プロシージャがプロシージャ所有者のコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-145">Executing as OWNER executes the procedure in the context of the procedure owner.</span></span> <span data-ttu-id="4f57b-146">`dbo` すなわちデータベース所有者が所有するスキーマでプロシージャが作成されている場合、プロシージャは権限無制限で実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-146">If the procedure is created in a schema owned by `dbo` or the database owner, the procedure will execute with unrestricted permissions.</span></span>  
  
- <span data-ttu-id="4f57b-147">SELF : </span><span class="sxs-lookup"><span data-stu-id="4f57b-147">SELF.</span></span> <span data-ttu-id="4f57b-148">SELF として実行すると、ストアド プロシージャの作成者のセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f57b-148">Executing as SELF executes in the security context of the creator of the stored procedure.</span></span> <span data-ttu-id="4f57b-149">これは、指定されたユーザーとして実行することと同じです。指定されたユーザーとは、プロシージャを作成または変更した人物です。</span><span class="sxs-lookup"><span data-stu-id="4f57b-149">This is equivalent to executing as a specified user, where the specified user is the person creating or altering the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f57b-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f57b-150">See also</span></span>

- [<span data-ttu-id="4f57b-151">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="4f57b-151">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="4f57b-152">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="4f57b-152">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="4f57b-153">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="4f57b-153">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="4f57b-154">SQL Server でのストアド プロシージャを使用したアクセス許可の管理</span><span class="sxs-lookup"><span data-stu-id="4f57b-154">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="4f57b-155">SQL Server での安全な動的 SQL の作成</span><span class="sxs-lookup"><span data-stu-id="4f57b-155">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="4f57b-156">SQL Server でのストアド プロシージャの署名</span><span class="sxs-lookup"><span data-stu-id="4f57b-156">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="4f57b-157">ストアド プロシージャでのデータの変更</span><span class="sxs-lookup"><span data-stu-id="4f57b-157">Modifying Data with Stored Procedures</span></span>](../modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="4f57b-158">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="4f57b-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
