---
description: '詳細情報: 方法:SQL コマンドを直接実行する'
title: '方法: SQL コマンドを直接実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 9dd53b3582b6099bae51dc008debd8cb3142e386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786031"
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="fd934-103">方法: SQL コマンドを直接実行する</span><span class="sxs-lookup"><span data-stu-id="fd934-103">How to: Directly Execute SQL Commands</span></span>

<span data-ttu-id="fd934-104"><xref:System.Data.Linq.DataContext> 接続を使用すると仮定して、オブジェクトを返さない SQL コマンドを実行するために <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd934-104">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd934-105">例</span><span class="sxs-lookup"><span data-stu-id="fd934-105">Example</span></span>  

 <span data-ttu-id="fd934-106">SQL Server で UnitPrice の値を 1.00 増やす方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fd934-106">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="fd934-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd934-107">See also</span></span>

- [<span data-ttu-id="fd934-108">方法: SQL クエリを直接実行する</span><span class="sxs-lookup"><span data-stu-id="fd934-108">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)
- [<span data-ttu-id="fd934-109">データベースとの通信</span><span class="sxs-lookup"><span data-stu-id="fd934-109">Communicating with the Database</span></span>](communicating-with-the-database.md)
