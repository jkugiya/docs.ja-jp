---
description: '詳細情報: SQL Server でのストアド プロシージャの署名'
title: SQL Server でのストアド プロシージャの署名
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 1189f3ac24c8499cd8fb3ff9e6b6263a71fcc3a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767506"
---
# <a name="signing-stored-procedures-in-sql-server"></a><span data-ttu-id="31d18-103">SQL Server でのストアド プロシージャの署名</span><span class="sxs-lookup"><span data-stu-id="31d18-103">Signing Stored Procedures in SQL Server</span></span>

<span data-ttu-id="31d18-104">デジタル署名は、署名者の秘密キーで暗号化されたデータ ダイジェストです。</span><span class="sxs-lookup"><span data-stu-id="31d18-104">A digital signature is a data digest encrypted with the private key of the signer.</span></span> <span data-ttu-id="31d18-105">秘密キーにより、デジタル署名がその保持者または所有者に固有であることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="31d18-105">The private key ensures that the digital signature is unique to its bearer or owner.</span></span> <span data-ttu-id="31d18-106">ストアド プロシージャ、関数 (インライン テーブル値関数を除く)、トリガー、アセンブリに署名できます。</span><span class="sxs-lookup"><span data-stu-id="31d18-106">You can sign stored procedures, functions (except for inline table-valued functions), triggers, and assemblies.</span></span>

<span data-ttu-id="31d18-107">証明書や非対称キーを使用してストアド プロシージャに署名することができます。</span><span class="sxs-lookup"><span data-stu-id="31d18-107">You can sign a stored procedure with a certificate or an asymmetric key.</span></span> <span data-ttu-id="31d18-108">この機能は、動的 SQL などのように、組み合わせ所有権によって権限を継承できない場合や、組み合わせ所有権が壊れている場合を想定して用意されています。</span><span class="sxs-lookup"><span data-stu-id="31d18-108">This is designed for scenarios when permissions cannot be inherited through ownership chaining or when the ownership chain is broken, such as dynamic SQL.</span></span> <span data-ttu-id="31d18-109">証明書にマップされたユーザーを作成し、その証明書ユーザーに、ストアド プロシージャがアクセスする必要があるオブジェクトへのアクセス許可を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="31d18-109">You can then create a user mapped to the certificate, granting the certificate user permissions on the objects the stored procedure needs to access.</span></span>

<span data-ttu-id="31d18-110">同じ証明書にマップされたログインを作成し、必要なサーバー レベルのアクセス許可をそのログインに付与したり、1 つ以上の固定サーバー ロールにログインを追加したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="31d18-110">You can also create a login mapped to the same certificate, and then grant any necessary server-level permissions to that login, or add the login to one or more of the fixed server roles.</span></span> <span data-ttu-id="31d18-111">これは、高いレベルのアクセス許可が必要なシナリオで、`TRUSTWORTHY` のデータベース設定を有効にしなくて済むように設計されています。</span><span class="sxs-lookup"><span data-stu-id="31d18-111">This is designed to avoid enabling the `TRUSTWORTHY` database setting for scenarios in which higher level permissions are needed.</span></span>

<span data-ttu-id="31d18-112">ストアド プロシージャが実行されるときに、SQL Server によって証明書ユーザーやログインのアクセス許可が、呼び出し元のアクセス許可と組み合わされます。</span><span class="sxs-lookup"><span data-stu-id="31d18-112">When the stored procedure is executed, SQL Server combines the permissions of the certificate user and/or login with those of the caller.</span></span> <span data-ttu-id="31d18-113">`EXECUTE AS` 句とは異なり、プロシージャの実行コンテキストは変更されません。</span><span class="sxs-lookup"><span data-stu-id="31d18-113">Unlike the `EXECUTE AS` clause, it does not change the execution context of the procedure.</span></span> <span data-ttu-id="31d18-114">ログイン名とユーザー名を返す組み込み関数を実行すると、証明書ユーザーの名前ではなく、呼び出し元の名前が返されます。</span><span class="sxs-lookup"><span data-stu-id="31d18-114">Built-in functions that return login and user names return the name of the caller, not the certificate user name.</span></span>

## <a name="creating-certificates"></a><span data-ttu-id="31d18-115">証明書の作成</span><span class="sxs-lookup"><span data-stu-id="31d18-115">Creating Certificates</span></span>

<span data-ttu-id="31d18-116">証明書または非対称キーを使用してストアド プロシージャに署名すると、ストアド プロシージャのコードの暗号化ハッシュで構成されたデータ ダイジェストが、実行ユーザーと共に、秘密キーを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="31d18-116">When you sign a stored procedure with a certificate or asymmetric key, a data digest consisting of the encrypted hash of the stored procedure code, along with the execute-as user, is created using the private key.</span></span> <span data-ttu-id="31d18-117">実行時に、このデータ ダイジェストが公開キーを使用して復号化され、ストアド プロシージャのハッシュ値と比較されます。</span><span class="sxs-lookup"><span data-stu-id="31d18-117">At run time, the data digest is decrypted with the public key and compared with the hash value of the stored procedure.</span></span> <span data-ttu-id="31d18-118">実行ユーザーを変更するとハッシュ値が無効になり、デジタル署名が一致しなくなります。</span><span class="sxs-lookup"><span data-stu-id="31d18-118">Changing the execute-as user invalidates the hash value so that the digital signature no longer matches.</span></span> <span data-ttu-id="31d18-119">ストアド プロシージャを変更すると、署名が完全に削除され、これにより、秘密キーへのアクセス権を持たないユーザーは、ストアド プロシージャのコードを変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="31d18-119">Modifying the stored procedure drops the signature entirely, which prevents someone who does not have access to the private key from changing the stored procedure code.</span></span> <span data-ttu-id="31d18-120">どちらの場合も、コードまたは実行ユーザーを変更するたびに、プロシージャに再署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31d18-120">In either case, you must re-sign the procedure each time you change the code or the execute-as user.</span></span>

<span data-ttu-id="31d18-121">モジュールに署名するには、次の 2 つのステップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31d18-121">There are two required steps involved in signing a module:</span></span>

1. <span data-ttu-id="31d18-122">Transact-SQL ステートメント `CREATE CERTIFICATE [certificateName]` を使用して、証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="31d18-122">Create a certificate using the Transact-SQL `CREATE CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="31d18-123">このステートメントには、開始日、終了日、パスワードを設定するためのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="31d18-123">This statement has several options for setting a start and end date and a password.</span></span> <span data-ttu-id="31d18-124">既定の有効期限は 1 年間です。</span><span class="sxs-lookup"><span data-stu-id="31d18-124">The default expiration date is one year.</span></span>

1. <span data-ttu-id="31d18-125">Transact-SQL ステートメント `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` を使用して、証明書によってプロシージャに署名します。</span><span class="sxs-lookup"><span data-stu-id="31d18-125">Sign the procedure with the certificate using the Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` statement.</span></span>

<span data-ttu-id="31d18-126">モジュールに署名したら、証明書に関連付ける必要がある追加のアクセス許可を保持するため、1 つ以上のプリンシパルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31d18-126">Once the module has been signed, one or more principals needs to be created in order to hold the additional permissions that should be associated with the certificate.</span></span>

<span data-ttu-id="31d18-127">モジュールにデータベース レベルのアクセス許可を追加する必要がある場合:</span><span class="sxs-lookup"><span data-stu-id="31d18-127">If the module needs additional database-level permissions:</span></span>

1. <span data-ttu-id="31d18-128">Transact-SQL ステートメント `CREATE USER [userName] FROM CERTIFICATE [certificateName]` を使用して、証明書に関連付けられたデータベース ユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="31d18-128">Create a database user associated with that certificate using the Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="31d18-129">このユーザーはデータベースにのみ存在し、ログインも同じ証明書から作成されている場合を除き、ログインには関連付けられません。</span><span class="sxs-lookup"><span data-stu-id="31d18-129">This user exists in the database only and is not associated with a login unless a login has also been created from that same certificate.</span></span>

1. <span data-ttu-id="31d18-130">証明書ユーザーに、必要なデータベース レベルのアクセス許可を与えます。</span><span class="sxs-lookup"><span data-stu-id="31d18-130">Grant the certificate user the required database-level permissions.</span></span>

<span data-ttu-id="31d18-131">モジュールにサーバー レベルのアクセス許可を追加する必要がある場合:</span><span class="sxs-lookup"><span data-stu-id="31d18-131">If the module needs additional server-level permissions:</span></span>

1. <span data-ttu-id="31d18-132">証明書を `master` データベースにコピーします。</span><span class="sxs-lookup"><span data-stu-id="31d18-132">Copy the certificate to the `master` database.</span></span>

1. <span data-ttu-id="31d18-133">Transact-SQL のステートメント `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` を使用して、その証明書に関連付けられたログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="31d18-133">Create a login associated with that certificate using the Transact-SQL `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` statement.</span></span>

1. <span data-ttu-id="31d18-134">証明書ログインに、必要なサーバー レベルのアクセス許可を与えます。</span><span class="sxs-lookup"><span data-stu-id="31d18-134">Grant the certificate login the required server-level permissions.</span></span>

> [!NOTE]
> <span data-ttu-id="31d18-135">証明書では、DENY ステートメントを使用して権限が取り消されているユーザーに権限を与えることはできません。</span><span class="sxs-lookup"><span data-stu-id="31d18-135">A certificate cannot grant permissions to a user that has had permissions revoked using the DENY statement.</span></span> <span data-ttu-id="31d18-136">DENY は常に GRANT よりも優先されるため、証明書ユーザーに許可された権限を呼び出し元が継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="31d18-136">DENY always takes precedence over GRANT, preventing the caller from inheriting permissions granted to the certificate user.</span></span>

## <a name="external-resources"></a><span data-ttu-id="31d18-137">外部リソース</span><span class="sxs-lookup"><span data-stu-id="31d18-137">External Resources</span></span>

<span data-ttu-id="31d18-138">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="31d18-138">For more information, see the following resources.</span></span>

|<span data-ttu-id="31d18-139">リソース</span><span class="sxs-lookup"><span data-stu-id="31d18-139">Resource</span></span>|<span data-ttu-id="31d18-140">説明</span><span class="sxs-lookup"><span data-stu-id="31d18-140">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="31d18-141">[モジュール署名](/previous-versions/sql/sql-server-2008/ms345102(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="31d18-141">[Module Signing](/previous-versions/sql/sql-server-2008/ms345102(v=sql.100))</span></span>|<span data-ttu-id="31d18-142">モジュールの署名について説明し、サンプル シナリオと、関連する Transact-SQL の記事へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="31d18-142">Describes module signing, providing a sample scenario and links to the relevant Transact-SQL articles.</span></span>|
|[<span data-ttu-id="31d18-143">証明書を使用したストアド プロシージャへの署名</span><span class="sxs-lookup"><span data-stu-id="31d18-143">Signing Stored Procedures with a Certificate</span></span>](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate)|<span data-ttu-id="31d18-144">証明書を使用したストアド プロシージャの署名のチュートリアルです。</span><span class="sxs-lookup"><span data-stu-id="31d18-144">Provides a tutorial for signing a stored procedure with a certificate.</span></span>|

## <a name="see-also"></a><span data-ttu-id="31d18-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="31d18-145">See also</span></span>

- [<span data-ttu-id="31d18-146">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="31d18-146">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="31d18-147">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="31d18-147">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="31d18-148">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="31d18-148">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="31d18-149">SQL Server でのストアド プロシージャを使用したアクセス許可の管理</span><span class="sxs-lookup"><span data-stu-id="31d18-149">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="31d18-150">SQL Server での安全な動的 SQL の作成</span><span class="sxs-lookup"><span data-stu-id="31d18-150">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="31d18-151">SQL Server での借用を使用したアクセス許可のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="31d18-151">Customizing Permissions with Impersonation in SQL Server</span></span>](customizing-permissions-with-impersonation-in-sql-server.md)
- [<span data-ttu-id="31d18-152">ストアド プロシージャでのデータの変更</span><span class="sxs-lookup"><span data-stu-id="31d18-152">Modifying Data with Stored Procedures</span></span>](../modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="31d18-153">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="31d18-153">ADO.NET Overview</span></span>](../ado-net-overview.md)
