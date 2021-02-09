---
description: '詳細情報: LINQ to SQL におけるセキュリティ'
title: LINQ to SQL におけるセキュリティ
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: 3d53def25aed83d96e0d32dfc964d9b49458fad7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662937"
---
# <a name="security-in-linq-to-sql"></a><span data-ttu-id="8a4e2-103">LINQ to SQL におけるセキュリティ</span><span class="sxs-lookup"><span data-stu-id="8a4e2-103">Security in LINQ to SQL</span></span>

<span data-ttu-id="8a4e2-104">データベースに接続するときは、常にセキュリティのリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-104">Security risks are always present when you connect to a database.</span></span> <span data-ttu-id="8a4e2-105">LINQ to SQL には SQL Server のデータを操作する新しい方法が含まれていますが、セキュリティ メカニズムは追加されていません。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-105">Although LINQ to SQL may include some new ways to work with data in SQL Server, it does not provide any additional security mechanisms.</span></span>  
  
## <a name="access-control-and-authentication"></a><span data-ttu-id="8a4e2-106">アクセス制御と認証</span><span class="sxs-lookup"><span data-stu-id="8a4e2-106">Access Control and Authentication</span></span>  

 <span data-ttu-id="8a4e2-107">LINQ to SQL には独自のユーザー モデルや認証メカニズムがありません。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-107">LINQ to SQL does not have its own user model or authentication mechanisms.</span></span> <span data-ttu-id="8a4e2-108">オブジェクト モデルにマッピングされるデータベース、データベースのテーブル、ビュー、ストアド プロシージャなどへのアクセス制御には SQL Server のセキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-108">Use SQL Server Security to control access to the database, database tables, views, and stored procedures that are mapped to your object model.</span></span> <span data-ttu-id="8a4e2-109">ユーザーには必要最小限のアクセス権を与え、ユーザー認証には強力なパスワードを要求してください。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-109">Grant the minimally required access to users and require strong passwords for user authentication.</span></span>  
  
## <a name="mapping-and-schema-information"></a><span data-ttu-id="8a4e2-110">マッピングとスキーマ情報</span><span class="sxs-lookup"><span data-stu-id="8a4e2-110">Mapping and Schema Information</span></span>  

 <span data-ttu-id="8a4e2-111">オブジェクト モデルまたは外部マッピング ファイルにある、SQL-CLR 型マッピングとデータベース スキーマ情報は、ファイル システムでこれらのファイルに対してアクセス権を持つ全ユーザーに公開されます。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-111">SQL-CLR type mapping and database schema information in your object model or external mapping file is available for all with access to those files in the file system.</span></span> <span data-ttu-id="8a4e2-112">オブジェクト モデルまたは外部マッピング ファイルにアクセスできるすべてのユーザーがスキーマ情報を使用できることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-112">Assume that schema information will be available to all who can access the object model or external mapping file.</span></span> <span data-ttu-id="8a4e2-113">より広範囲にスキーマ情報をアクセス可能にするには、ファイル セキュリティ メカニズムを使用して、ソース ファイルとマッピング ファイルをセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-113">To prevent more widespread access to schema information, use file security mechanisms to secure source files and mapping files.</span></span>  
  
## <a name="connection-strings"></a><span data-ttu-id="8a4e2-114">接続文字列</span><span class="sxs-lookup"><span data-stu-id="8a4e2-114">Connection Strings</span></span>  

 <span data-ttu-id="8a4e2-115">接続文字列にパスワードを使用することは、できるだけ避けてください。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-115">Using passwords in connection strings should be avoided whenever possible.</span></span> <span data-ttu-id="8a4e2-116">接続文字列自体がセキュリティのリスクであるうえに、接続文字列はオブジェクト リレーショナル デザイナーまたは SQLMetal コマンド ライン ツールの使用時にオブジェクト モデルや外部マッピング ファイルにクリア テキストで追加できます。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-116">Not only is a connection string a security risk in its own right, but the connection string may also be added in clear text to the object model or external mapping file when using the Object Relational Designer or SQLMetal command-line tool.</span></span> <span data-ttu-id="8a4e2-117">ファイル システムでオブジェクト モデルまたは外部マッピング ファイルに対してアクセス権があれば、どのユーザーでも接続パスワードを見ることができます (パスワードが接続文字列に含まれている場合)。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-117">Anyone with access to the object model or external mapping file via the file system could see the connection password (if it is included in the connection string).</span></span>  
  
 <span data-ttu-id="8a4e2-118">このようなリスクを最小限に抑えるには、統合セキュリティを使用して SQL Server との信頼関係接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-118">To minimize such risks, use integrated security to make a trusted connection with SQL Server.</span></span> <span data-ttu-id="8a4e2-119">この方法を使用すると、接続文字列にパスワードを含める必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-119">By using this approach, you do not have to store a password in the connection string.</span></span> <span data-ttu-id="8a4e2-120">詳細については、「[SQL Server のセキュリティ](../sql-server-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-120">For more information, see [SQL Server Security](../sql-server-security.md).</span></span>  
  
 <span data-ttu-id="8a4e2-121">統合セキュリティがない場合は、接続文字列にクリア テキストのパスワードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-121">In the absence of integrated security, a clear-text password will be needed in the connection string.</span></span> <span data-ttu-id="8a4e2-122">以下は、接続文字列のセキュリティ保護に最も有効な手段です。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-122">The best way to help secure your connection string, in increasing order of risk, is as follows:</span></span>  
  
- <span data-ttu-id="8a4e2-123">統合セキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-123">Use integrated security.</span></span>  
  
- <span data-ttu-id="8a4e2-124">接続文字列をパスワードで保護し、接続文字列の配布を最小限にします。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-124">Secure connection strings with passwords and minimize passing around connection strings.</span></span>  
  
- <span data-ttu-id="8a4e2-125">接続文字列の代わりに、表示時間に制限のある <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-125">Use a <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> class instead of a connection string since it limits the duration of exposure.</span></span> <span data-ttu-id="8a4e2-126">LINQ to SQL の <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> クラスは <xref:System.Data.SqlClient.SqlConnection> を使用してインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-126">The LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> class can be instantiated using a <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
- <span data-ttu-id="8a4e2-127">すべての接続文字列の期限と接触点を最小限にします。</span><span class="sxs-lookup"><span data-stu-id="8a4e2-127">Minimize lifetimes and touch points for all connection strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a4e2-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a4e2-128">See also</span></span>

- [<span data-ttu-id="8a4e2-129">背景情報</span><span class="sxs-lookup"><span data-stu-id="8a4e2-129">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="8a4e2-130">よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="8a4e2-130">Frequently Asked Questions</span></span>](frequently-asked-questions.md)
