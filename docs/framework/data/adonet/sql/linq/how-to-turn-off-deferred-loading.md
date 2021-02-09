---
description: '詳細情報: 方法:遅延読み込みをオフにする'
title: '方法: 遅延読み込みをオフにする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 739c9b0b65eda73d6c504409395eb805b0c02873
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785836"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="e8009-103">方法: 遅延読み込みをオフにする</span><span class="sxs-lookup"><span data-stu-id="e8009-103">How to: Turn Off Deferred Loading</span></span>

<span data-ttu-id="e8009-104"><xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> を `false` に設定すると、遅延読み込みをオフにできます。</span><span class="sxs-lookup"><span data-stu-id="e8009-104">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="e8009-105">詳細については、「[遅延読み込みと即時読み込み](deferred-versus-immediate-loading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8009-105">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8009-106">遅延読み込みは、オブジェクト トラッキングをオフにすると暗黙でオフになります。</span><span class="sxs-lookup"><span data-stu-id="e8009-106">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="e8009-107">詳細については、[情報を読み取り専用として取得する](how-to-retrieve-information-as-read-only.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8009-107">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8009-108">例</span><span class="sxs-lookup"><span data-stu-id="e8009-108">Example</span></span>  

 <span data-ttu-id="e8009-109"><xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> を `false` に設定して、遅延読み込みをオフにする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="e8009-109">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e8009-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8009-110">See also</span></span>

- [<span data-ttu-id="e8009-111">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="e8009-111">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="e8009-112">データベースに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="e8009-112">Querying the Database</span></span>](querying-the-database.md)
