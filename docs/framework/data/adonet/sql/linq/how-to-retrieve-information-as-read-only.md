---
description: '詳細情報: 方法:情報を読み取り専用として取得する'
title: '方法: 情報を読み取り専用として取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 7743e555bcc3f6371ca601d02313e30895e57961
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723453"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="f3e1c-103">方法: 情報を読み取り専用として取得する</span><span class="sxs-lookup"><span data-stu-id="f3e1c-103">How to: Retrieve Information As Read-Only</span></span>

<span data-ttu-id="f3e1c-104">データを変更する予定がない場合は、読み取り専用の結果を取得することでクエリのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="f3e1c-104">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="f3e1c-105">読み取り専用の処理を実装するには、<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f3e1c-105">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3e1c-106"><xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> を `false` に設定すると、<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> が暗黙的に `false` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f3e1c-106">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3e1c-107">例</span><span class="sxs-lookup"><span data-stu-id="f3e1c-107">Example</span></span>  

 <span data-ttu-id="f3e1c-108">次のコード例は、従業員の入社日の読み取り専用コレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="f3e1c-108">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f3e1c-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3e1c-109">See also</span></span>

- [<span data-ttu-id="f3e1c-110">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="f3e1c-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="f3e1c-111">データベースに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="f3e1c-111">Querying the Database</span></span>](querying-the-database.md)
- [<span data-ttu-id="f3e1c-112">遅延読み込みと即時読み込み</span><span class="sxs-lookup"><span data-stu-id="f3e1c-112">Deferred versus Immediate Loading</span></span>](deferred-versus-immediate-loading.md)
