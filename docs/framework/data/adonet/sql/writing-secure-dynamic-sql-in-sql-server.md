---
description: '詳細情報: SQL Server での安全な動的 SQL の作成'
title: SQL Server での安全な動的 SQL の作成
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: 35db22358bae1150a80daa72cf4a86ef8fba9620
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766947"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a><span data-ttu-id="c38e7-103">SQL Server での安全な動的 SQL の作成</span><span class="sxs-lookup"><span data-stu-id="c38e7-103">Writing Secure Dynamic SQL in SQL Server</span></span>

<span data-ttu-id="c38e7-104">SQL インジェクションとは、悪意のあるユーザーによって、有効な入力データの代わりに Transact-SQL ステートメントが入力されることをいいます。</span><span class="sxs-lookup"><span data-stu-id="c38e7-104">SQL Injection is the process by which a malicious user enters Transact-SQL statements instead of valid input.</span></span> <span data-ttu-id="c38e7-105">入力が検証されずにサーバーに直接渡され、挿入されたコードがアプリケーションによって誤って実行された場合に、この攻撃によってデータが破損、または破壊される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-105">If the input is passed directly to the server without being validated and if the application inadvertently executes the injected code, the attack has the potential to damage or destroy data.</span></span>  
  
 <span data-ttu-id="c38e7-106">SQL Server では、構文的に有効であれば受信したクエリがすべて実行されるため、SQL ステートメントを構成するすべてのプロシージャに対して、インジェクションに対する脆弱性をレビューする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-106">Any procedure that constructs SQL statements should be reviewed for injection vulnerabilities because SQL Server will execute all syntactically valid queries that it receives.</span></span> <span data-ttu-id="c38e7-107">高いスキルを持った攻撃者は、その気になればパラメーター化されたデータでさえも操作できます。</span><span class="sxs-lookup"><span data-stu-id="c38e7-107">Even parameterized data can be manipulated by a skilled and determined attacker.</span></span> <span data-ttu-id="c38e7-108">動的 SQL を使用する場合は、必ずコマンドをパラメーター化するようにし、パラメーター値を直接クエリ文字列に追加することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="c38e7-108">If you use dynamic SQL, be sure to parameterize your commands, and never include parameter values directly into the query string.</span></span>  
  
## <a name="anatomy-of-a-sql-injection-attack"></a><span data-ttu-id="c38e7-109">SQL インジェクション攻撃の分析</span><span class="sxs-lookup"><span data-stu-id="c38e7-109">Anatomy of a SQL Injection Attack</span></span>  

 <span data-ttu-id="c38e7-110">インジェクションのプロセスは、テキスト文字列を途中で終了し、新しいコマンドを追加することによって行われます。</span><span class="sxs-lookup"><span data-stu-id="c38e7-110">The injection process works by prematurely terminating a text string and appending a new command.</span></span> <span data-ttu-id="c38e7-111">挿入されたコマンドが実行される前に別の文字列が追加される可能性があるため、攻撃者は挿入する文字列をコメント記号 "--" で終了させます。</span><span class="sxs-lookup"><span data-stu-id="c38e7-111">Because the inserted command may have additional strings appended to it before it is executed, the malefactor terminates the injected string with a comment mark "--".</span></span> <span data-ttu-id="c38e7-112">後続のテキストは実行時には無視されます。</span><span class="sxs-lookup"><span data-stu-id="c38e7-112">Subsequent text is ignored at execution time.</span></span> <span data-ttu-id="c38e7-113">セミコロン (;) 区切り記号を使用して複数のコマンドを挿入できます。</span><span class="sxs-lookup"><span data-stu-id="c38e7-113">Multiple commands can be inserted using a semicolon (;) delimiter.</span></span>  
  
 <span data-ttu-id="c38e7-114">挿入された SQL コードが構文的に正しい限り、改ざんをプログラムによって検出するのは不可能です。</span><span class="sxs-lookup"><span data-stu-id="c38e7-114">As long as injected SQL code is syntactically correct, tampering cannot be detected programmatically.</span></span> <span data-ttu-id="c38e7-115">そのため、すべてのユーザー入力を検証し、使用しているサーバーで作成された SQL コマンドを実行するコードを注意深くレビューする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-115">Therefore, you must validate all user input and carefully review code that executes constructed SQL commands in the server that you are using.</span></span> <span data-ttu-id="c38e7-116">検証されていないユーザー入力は決して連結しないでください。</span><span class="sxs-lookup"><span data-stu-id="c38e7-116">Never concatenate user input that is not validated.</span></span> <span data-ttu-id="c38e7-117">文字列の連結は、スクリプト インジェクションの最初の段階です。</span><span class="sxs-lookup"><span data-stu-id="c38e7-117">String concatenation is the primary point of entry for script injection.</span></span>  
  
 <span data-ttu-id="c38e7-118">有用なガイドラインを次に示します。</span><span class="sxs-lookup"><span data-stu-id="c38e7-118">Here are some helpful guidelines:</span></span>  
  
- <span data-ttu-id="c38e7-119">Transact-SQL ステートメントをユーザー入力から直接作成しないでください。ストアド プロシージャを使用して、ユーザー入力を検証します。</span><span class="sxs-lookup"><span data-stu-id="c38e7-119">Never build Transact-SQL statements directly from user input; use stored procedures to validate user input.</span></span>  
  
- <span data-ttu-id="c38e7-120">ユーザー入力の型、長さ、形式、範囲をテストし、検証してください。</span><span class="sxs-lookup"><span data-stu-id="c38e7-120">Validate user input by testing type, length, format, and range.</span></span> <span data-ttu-id="c38e7-121">Transact-SQL QUOTENAME() 関数を使用してシステム名をエスケープするか、REPLACE() 関数して文字列内の任意の文字をエスケープします。</span><span class="sxs-lookup"><span data-stu-id="c38e7-121">Use the Transact-SQL QUOTENAME() function to escape system names or the REPLACE() function to escape any character in a string.</span></span>  
  
- <span data-ttu-id="c38e7-122">アプリケーションの各層に複数の検証レイヤーを実装します。</span><span class="sxs-lookup"><span data-stu-id="c38e7-122">Implement multiple layers of validation in each tier of your application.</span></span>  
  
- <span data-ttu-id="c38e7-123">入力のサイズとデータ型をテストし、適切な制限を適用します。</span><span class="sxs-lookup"><span data-stu-id="c38e7-123">Test the size and data type of input and enforce appropriate limits.</span></span> <span data-ttu-id="c38e7-124">これは、意図的なバッファー オーバーランを防ぐのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c38e7-124">This can help prevent deliberate buffer overruns.</span></span>  
  
- <span data-ttu-id="c38e7-125">文字列変数の内容をテストし、予測される値のみを受け入れる。</span><span class="sxs-lookup"><span data-stu-id="c38e7-125">Test the content of string variables and accept only expected values.</span></span> <span data-ttu-id="c38e7-126">バイナリ データ、エスケープ シーケンス、およびコメント文字を含む入力は拒否します。</span><span class="sxs-lookup"><span data-stu-id="c38e7-126">Reject entries that contain binary data, escape sequences, and comment characters.</span></span>  
  
- <span data-ttu-id="c38e7-127">XML ドキュメントを扱う場合、入力時にすべてのデータをスキーマに照らして検証します。</span><span class="sxs-lookup"><span data-stu-id="c38e7-127">When you are working with XML documents, validate all data against its schema as it is entered.</span></span>  
  
- <span data-ttu-id="c38e7-128">多層環境では、信頼済みゾーンに入ることを許可する前にすべてのデータを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-128">In multi-tiered environments, all data should be validated before admission to the trusted zone.</span></span>  
  
- <span data-ttu-id="c38e7-129">ファイル名の作成に使用できるフィールドでは、次の文字列を受け付けない:AUX、CLOCK$、COM1 から COM8、CON、CONFIG$、LPT1 から LPT8、NUL、PRN。</span><span class="sxs-lookup"><span data-stu-id="c38e7-129">Do not accept the following strings in fields from which file names can be constructed: AUX, CLOCK$, COM1 through COM8, CON, CONFIG$, LPT1 through LPT8, NUL, and PRN.</span></span>  
  
- <span data-ttu-id="c38e7-130">ストアド プロシージャおよびコマンドで <xref:System.Data.SqlClient.SqlParameter> オブジェクトを使用して、型チェックと長さの検証を行います。</span><span class="sxs-lookup"><span data-stu-id="c38e7-130">Use <xref:System.Data.SqlClient.SqlParameter> objects with stored procedures and commands to provide type checking and length validation.</span></span>  
  
- <span data-ttu-id="c38e7-131">クライアント コードで <xref:System.Text.RegularExpressions.Regex> 式を使用して、無効な文字を排除します。</span><span class="sxs-lookup"><span data-stu-id="c38e7-131">Use <xref:System.Text.RegularExpressions.Regex> expressions in client code to filter invalid characters.</span></span>  
  
## <a name="dynamic-sql-strategies"></a><span data-ttu-id="c38e7-132">動的 SQL を利用した手法</span><span class="sxs-lookup"><span data-stu-id="c38e7-132">Dynamic SQL Strategies</span></span>  

 <span data-ttu-id="c38e7-133">プロシージャ コードで動的に生成された SQL ステートメントを実行することで組み合わせ所有権を破棄すると、SQL Server は動的 SQL によりアクセスされるオブジェクトに対する呼び出し元の権限をチェックします。</span><span class="sxs-lookup"><span data-stu-id="c38e7-133">Executing dynamically created SQL statements in your procedural code breaks the ownership chain, causing SQL Server to check the permissions of the caller against the objects being accessed by the dynamic SQL.</span></span>  
  
 <span data-ttu-id="c38e7-134">SQL Server には、動的 SQL を実行するストアド プロシージャやユーザー定義関数を使用したデータ アクセスをユーザーに許可するための方法があります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-134">SQL Server has methods for granting users access to data using stored procedures and user-defined functions that execute dynamic SQL.</span></span>  
  
- <span data-ttu-id="c38e7-135">Transact-SQL EXECUTE AS 句による偽装を利用する。詳細は、[SQL Server で偽装を利用してアクセス許可をカスタマイズする](customizing-permissions-with-impersonation-in-sql-server.md)方法に関するページにあります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-135">Using impersonation with the Transact-SQL EXECUTE AS clause, as described in [Customizing Permissions with Impersonation in SQL Server](customizing-permissions-with-impersonation-in-sql-server.md).</span></span>  
  
- <span data-ttu-id="c38e7-136">証明書を利用してストアド プロシージャに署名する。詳細は、[SQL Server でストアド プロシージャに署名する](signing-stored-procedures-in-sql-server.md)方法に関するページにあります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-136">Signing stored procedures with certificates, as described in [Signing Stored Procedures in SQL Server](signing-stored-procedures-in-sql-server.md).</span></span>  
  
### <a name="execute-as"></a><span data-ttu-id="c38e7-137">EXECUTE AS</span><span class="sxs-lookup"><span data-stu-id="c38e7-137">EXECUTE AS</span></span>  

 <span data-ttu-id="c38e7-138">EXECUTE AS 句では、呼び出し元のアクセス許可を、EXECUTE AS 句に指定されたユーザーのアクセス許可で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c38e7-138">The EXECUTE AS clause replaces the permissions of the caller with that of the user specified in the EXECUTE AS clause.</span></span> <span data-ttu-id="c38e7-139">入れ子になったストアド プロシージャまたはトリガーは、プロキシ ユーザーのセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="c38e7-139">Nested stored procedures or triggers execute under the security context of the proxy user.</span></span> <span data-ttu-id="c38e7-140">これにより、行レベルのセキュリティに依存する、または監査を必要とするアプリケーションが中断される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-140">This can break applications that rely on row-level security or require auditing.</span></span> <span data-ttu-id="c38e7-141">ユーザーの ID を返す一部の関数では、元の呼び出し元ではなく、EXECUTE AS 句に指定されたユーザーを返します。</span><span class="sxs-lookup"><span data-stu-id="c38e7-141">Some functions that return the identity of the user return the user specified in the EXECUTE AS clause, not the original caller.</span></span> <span data-ttu-id="c38e7-142">プロシージャの実行後、または REVERT ステートメントが発行されたときにのみ、実行コンテキストが最初の呼び出し元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-142">Execution context is reverted to the original caller only after execution of the procedure or when a REVERT statement is issued.</span></span>  
  
### <a name="certificate-signing"></a><span data-ttu-id="c38e7-143">証明書署名</span><span class="sxs-lookup"><span data-stu-id="c38e7-143">Certificate Signing</span></span>  

 <span data-ttu-id="c38e7-144">証明書により署名されているストアド プロシージャが実行されると、証明書ユーザーに許可される権限が呼び出し元の権限にマージされます。</span><span class="sxs-lookup"><span data-stu-id="c38e7-144">When a stored procedure that has been signed with a certificate executes, the permissions granted to the certificate user are merged with those of the caller.</span></span> <span data-ttu-id="c38e7-145">実行コンテキストはそのままです。証明書ユーザーが呼び出し元を偽装することはありません。</span><span class="sxs-lookup"><span data-stu-id="c38e7-145">The execution context remains the same; the certificate user does not impersonate the caller.</span></span> <span data-ttu-id="c38e7-146">ストアド プロシージャに署名するには、いくつかの手順を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-146">Signing stored procedures requires several steps to implement.</span></span> <span data-ttu-id="c38e7-147">プロシージャが変更されるたびに、再度署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-147">Each time the procedure is modified, it must be re-signed.</span></span>  
  
### <a name="cross-database-access"></a><span data-ttu-id="c38e7-148">複数のデータベースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="c38e7-148">Cross Database Access</span></span>  

 <span data-ttu-id="c38e7-149">動的に生成された SQL ステートメントを実行する場合、複数データベースの組み合わせ所有権は機能しません。</span><span class="sxs-lookup"><span data-stu-id="c38e7-149">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed.</span></span> <span data-ttu-id="c38e7-150">SQL Server では、別のデータベースのデータにアクセスするストアド プロシージャを作成し、両方のデータベースに存在する証明書でそのプロシージャに署名することによって、この制限を回避できます。</span><span class="sxs-lookup"><span data-stu-id="c38e7-150">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="c38e7-151">これにより、ユーザーは、データベースへのアクセス許可が付与されていなくても、そのプロシージャによって使用されるデータベース リソースにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="c38e7-151">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="c38e7-152">外部リソース</span><span class="sxs-lookup"><span data-stu-id="c38e7-152">External Resources</span></span>  

 <span data-ttu-id="c38e7-153">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c38e7-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="c38e7-154">リソース</span><span class="sxs-lookup"><span data-stu-id="c38e7-154">Resource</span></span>|<span data-ttu-id="c38e7-155">説明</span><span class="sxs-lookup"><span data-stu-id="c38e7-155">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="c38e7-156">「[ストアド プロシージャ](/sql/relational-databases/stored-procedures/stored-procedures-database-engine)」と「[SQL インジェクション](/sql/relational-databases/security/sql-injection)」 (SQL Server オンライン ブック)</span><span class="sxs-lookup"><span data-stu-id="c38e7-156">[Stored Procedures](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) and [SQL Injection](/sql/relational-databases/security/sql-injection) in SQL Server Books Online</span></span>|<span data-ttu-id="c38e7-157">ストアド プロシージャの作成方法と SQL インジェクションのしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c38e7-157">Topics describe how to create stored procedures and how SQL Injection works.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c38e7-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="c38e7-158">See also</span></span>

- [<span data-ttu-id="c38e7-159">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="c38e7-159">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="c38e7-160">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="c38e7-160">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="c38e7-161">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="c38e7-161">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="c38e7-162">SQL Server でのストアド プロシージャを使用したアクセス許可の管理</span><span class="sxs-lookup"><span data-stu-id="c38e7-162">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="c38e7-163">SQL Server でのストアド プロシージャの署名</span><span class="sxs-lookup"><span data-stu-id="c38e7-163">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="c38e7-164">SQL Server での借用を使用したアクセス許可のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="c38e7-164">Customizing Permissions with Impersonation in SQL Server</span></span>](customizing-permissions-with-impersonation-in-sql-server.md)
- [<span data-ttu-id="c38e7-165">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="c38e7-165">ADO.NET Overview</span></span>](../ado-net-overview.md)
