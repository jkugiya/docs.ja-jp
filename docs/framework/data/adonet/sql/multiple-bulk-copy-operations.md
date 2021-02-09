---
description: '詳細情報: バルク コピー操作の複数実行'
title: バルク コピー操作の複数実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: dfc694cfb4a993889bed607be71821bb1f9fddf1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767662"
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="53da9-103">バルク コピー操作の複数実行</span><span class="sxs-lookup"><span data-stu-id="53da9-103">Multiple Bulk Copy Operations</span></span>

<span data-ttu-id="53da9-104"><xref:System.Data.SqlClient.SqlBulkCopy> クラスのインスタンスを 1 つ使用すると、バルク コピー操作を複数回実行できます。</span><span class="sxs-lookup"><span data-stu-id="53da9-104">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="53da9-105">コピー元とコピー先で操作パラメーターが変わる場合 (たとえば、コピー先のテーブル名など)、**WriteToServer** メソッドを続けて呼び出す前に、次の例で示すようにパラメーターを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53da9-105">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="53da9-106">明示的に変更されている場合を除き、すべてのプロパティ値は、任意のインスタンスに対する前回のバルク コピー操作の状態のまま残っています。</span><span class="sxs-lookup"><span data-stu-id="53da9-106">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53da9-107">通常、バルク コピー操作を複数回実行する場合は、同じ <xref:System.Data.SqlClient.SqlBulkCopy> のインスタンスを使用する方が各操作ごとに別のインスタンスを使用するよりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="53da9-107">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="53da9-108">同じ <xref:System.Data.SqlClient.SqlBulkCopy> オブジェクトを使用してバルク コピー操作を複数回実行する場合は、コピー元またはコピー先の情報が各操作ごとに一致しているかまたは異なっているかどうかは制限されません。</span><span class="sxs-lookup"><span data-stu-id="53da9-108">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="53da9-109">ただし、サーバーに書き込み処理を行うときは、列の関連情報を毎回正しく設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53da9-109">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="53da9-110">このサンプルは、「[バルク コピー サンプルのセットアップ](bulk-copy-example-setup.md)」で説明されているように作業テーブルを作成してからでないと動作しません。</span><span class="sxs-lookup"><span data-stu-id="53da9-110">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](bulk-copy-example-setup.md).</span></span> <span data-ttu-id="53da9-111">このコードでは、**SqlBulkCopy** だけを使用した構文について説明します。</span><span class="sxs-lookup"><span data-stu-id="53da9-111">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="53da9-112">コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL `INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="53da9-112">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="53da9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="53da9-113">See also</span></span>

- [<span data-ttu-id="53da9-114">SQL Server でのバルク コピー操作</span><span class="sxs-lookup"><span data-stu-id="53da9-114">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="53da9-115">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="53da9-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
