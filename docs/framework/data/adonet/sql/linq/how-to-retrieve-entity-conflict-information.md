---
description: '詳細情報: 方法:エンティティの競合情報を取得する'
title: '方法: エンティティの競合情報を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: dde11a431ae977595b9845444e48705a4552fb23
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767753"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="d9c5e-103">方法: エンティティの競合情報を取得する</span><span class="sxs-lookup"><span data-stu-id="d9c5e-103">How to: Retrieve Entity Conflict Information</span></span>

<span data-ttu-id="d9c5e-104"><xref:System.Data.Linq.ObjectChangeConflict> クラスのオブジェクトを使用して、<xref:System.Data.Linq.ChangeConflictException> 例外によって発生する競合に関する情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="d9c5e-104">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="d9c5e-105">詳しくは、「[オプティミスティック コンカレンシー: 概要)](optimistic-concurrency-overview.md) の下のステートメントを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="d9c5e-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9c5e-106">例</span><span class="sxs-lookup"><span data-stu-id="d9c5e-106">Example</span></span>  

 <span data-ttu-id="d9c5e-107">次の例では、累積した競合のリストを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="d9c5e-107">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d9c5e-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9c5e-108">See also</span></span>

- [<span data-ttu-id="d9c5e-109">方法: 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="d9c5e-109">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
