---
description: '詳細情報: 方法:変更セットを表示する'
title: '方法: 変更セットを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: e5ff7aebcc74ded1300433a3bf7b280db3a11b28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786018"
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="e0c73-103">方法: 変更セットを表示する</span><span class="sxs-lookup"><span data-stu-id="e0c73-103">How to: Display a ChangeSet</span></span>

<span data-ttu-id="e0c73-104"><xref:System.Data.Linq.DataContext> によって追跡される変更を <xref:System.Data.Linq.DataContext.GetChangeSet%2A> を使って表示することができます。</span><span class="sxs-lookup"><span data-stu-id="e0c73-104">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0c73-105">例</span><span class="sxs-lookup"><span data-stu-id="e0c73-105">Example</span></span>  

 <span data-ttu-id="e0c73-106">以下の例では、住所がロンドンの顧客を取得し、これをパリに変更してから変更内容をデータベースに送信しています。</span><span class="sxs-lookup"><span data-stu-id="e0c73-106">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="e0c73-107">このコードからの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e0c73-107">Output from this code appears similar to the following.</span></span> <span data-ttu-id="e0c73-108">最後に概要として、8 か所の変更が示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e0c73-108">Note that the summary at the end shows that eight changes were made.</span></span>  

 ```console
CustomerID: AROUT
   Original value: London
   Updated value: Paris
CustomerID: BSBEV
   Original value: London
   Updated value: Paris
CustomerID: CONSH
   Original value: London
   Updated value: Paris
CustomerID: EASTC
   Original value: London
   Updated value: Paris
CustomerID: NORTS
    Original value: London
    Updated value: Paris
CustomerID: PARIS
    Original value: London
    Updated value: Paris
CustomerID: SEVES
    Original value: London
    Updated value: Paris
CustomerID: SPECD
    Original value: London
    Updated value: Paris
Total changes: {Added: 0, Removed: 0, Modified: 8}
```
  
## <a name="see-also"></a><span data-ttu-id="e0c73-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0c73-109">See also</span></span>

- [<span data-ttu-id="e0c73-110">デバッグのサポート</span><span class="sxs-lookup"><span data-stu-id="e0c73-110">Debugging Support</span></span>](debugging-support.md)
