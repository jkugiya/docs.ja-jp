---
description: '詳細情報: コンテキスト接続'
title: コンテキスト接続
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: caea829464ae19a8944f02c4edb38ec41b9bde48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767012"
---
# <a name="the-context-connection"></a><span data-ttu-id="763aa-103">コンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="763aa-103">The Context Connection</span></span>

<span data-ttu-id="763aa-104">内部データ アクセスの問題は、非常に一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="763aa-104">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="763aa-105">つまり、共通言語ランタイム (CLR) ストアド プロシージャまたは関数を実行しているサーバーにアクセスする場合の問題です。</span><span class="sxs-lookup"><span data-stu-id="763aa-105">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="763aa-106">1 つの解決方法は、<xref:System.Data.SqlClient.SqlConnection> を使用して接続文字列を作成し、ローカル サーバーをポイントするように接続文字列で指定して、接続を開くことです。</span><span class="sxs-lookup"><span data-stu-id="763aa-106">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="763aa-107">これを行うには、ログインするための資格情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="763aa-107">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="763aa-108">接続がストアド プロシージャまたは関数とは別のデータベース セッションにある場合や、異なる `SET` オプションが指定されている場合があります。また、別のトランザクション内にある場合や、一時テーブルを参照していない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="763aa-108">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="763aa-109">マネージド ストアド プロシージャまたは関数コードが SQL Server プロセス内で実行されている場合、別のユーザーがサーバーに接続して、そのマネージド ストアド プロシージャまたは関数コードを起動する SQL ステートメントを実行していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="763aa-109">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="763aa-110">接続のコンテキスト内で、ストアド プロシージャまたは関数をトランザクションや `SET` オプションなどと共に実行する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="763aa-110">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="763aa-111">これは、コンテキスト接続と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="763aa-111">This is called the context connection.</span></span>  
  
 <span data-ttu-id="763aa-112">コンテキスト接続を使用すると、コードが初めに起動されたコンテキスト内で Transact-SQL ステートメントを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="763aa-112">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="763aa-113">詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="763aa-113">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="763aa-114">**SQL Server のドキュメント**</span><span class="sxs-lookup"><span data-stu-id="763aa-114">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="763aa-115">コンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="763aa-115">The Context Connection</span></span>](/sql/relational-databases/clr-integration/data-access/context-connection)  
  
## <a name="see-also"></a><span data-ttu-id="763aa-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="763aa-116">See also</span></span>

- [<span data-ttu-id="763aa-117">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="763aa-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
