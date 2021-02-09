---
description: '詳細情報: Oracle 分散トランザクション'
title: Oracle 分散トランザクション
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: d0c41920f18e0f56ebdf57e3cb82cf829a59c450
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786174"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="e212b-103">Oracle 分散トランザクション</span><span class="sxs-lookup"><span data-stu-id="e212b-103">Oracle Distributed Transactions</span></span>

<span data-ttu-id="e212b-104"><xref:System.Data.OracleClient.OracleConnection> オブジェクトはトランザクションがアクティブであると判断した場合、既存の分散トランザクションに自動的に参加します。</span><span class="sxs-lookup"><span data-stu-id="e212b-104">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="e212b-105">自動トランザクション参加は、接続が開かれた場合または接続プールから取得された場合に行われます。</span><span class="sxs-lookup"><span data-stu-id="e212b-105">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="e212b-106">既存のトランザクションへの自動参加を無効にするには、</span><span class="sxs-lookup"><span data-stu-id="e212b-106">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```csharp  
Enlist=false  
```  
  
 <span data-ttu-id="e212b-107">を <xref:System.Data.OracleClient.OracleConnection> の接続文字列パラメーターとして指定します。</span><span class="sxs-lookup"><span data-stu-id="e212b-107">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e212b-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="e212b-108">See also</span></span>

- [<span data-ttu-id="e212b-109">Oracle および ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e212b-109">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="e212b-110">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="e212b-110">ADO.NET Overview</span></span>](ado-net-overview.md)
