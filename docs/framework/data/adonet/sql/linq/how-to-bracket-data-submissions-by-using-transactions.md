---
description: '詳細情報: 方法:データ送信をトランザクションで囲む'
title: '方法: データ送信をトランザクションで囲む'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: a1bbebfcdb4b65e83c4ac6dc9b87b06f33f2cb41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739028"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="4dd31-103">方法: データ送信をトランザクションで囲む</span><span class="sxs-lookup"><span data-stu-id="4dd31-103">How to: Bracket Data Submissions by Using Transactions</span></span>

<span data-ttu-id="4dd31-104">データベースへの送信を <xref:System.Transactions.TransactionScope> で囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="4dd31-104">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="4dd31-105">詳しくは、「[トランザクションのサポート](transaction-support.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4dd31-105">For more information, see [Transaction Support](transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dd31-106">例</span><span class="sxs-lookup"><span data-stu-id="4dd31-106">Example</span></span>  

 <span data-ttu-id="4dd31-107">次のコードでは、データベース送信を <xref:System.Transactions.TransactionScope> で囲みます。</span><span class="sxs-lookup"><span data-stu-id="4dd31-107">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="4dd31-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="4dd31-108">See also</span></span>

- [<span data-ttu-id="4dd31-109">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="4dd31-109">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="4dd31-110">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="4dd31-110">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="4dd31-111">トランザクションのサポート</span><span class="sxs-lookup"><span data-stu-id="4dd31-111">Transaction Support</span></span>](transaction-support.md)
