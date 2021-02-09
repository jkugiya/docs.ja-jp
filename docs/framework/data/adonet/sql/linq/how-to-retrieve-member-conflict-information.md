---
description: '詳細情報: 方法:メンバーの競合情報を取得する'
title: '方法: メンバーの競合情報を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 2a33aba1a113bdfd66bdc341bfc9ae59406f2c40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723401"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="bcd73-103">方法: メンバーの競合情報を取得する</span><span class="sxs-lookup"><span data-stu-id="bcd73-103">How to: Retrieve Member Conflict Information</span></span>

<span data-ttu-id="bcd73-104"><xref:System.Data.Linq.MemberChangeConflict> クラスを使用すると、競合する個々のメンバーに関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="bcd73-104">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="bcd73-105">この同じコンテキストで、メンバーの競合の処理をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="bcd73-105">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="bcd73-106">詳しくは、「[オプティミスティック コンカレンシー: 概要)](optimistic-concurrency-overview.md) の下のステートメントを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="bcd73-106">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcd73-107">例</span><span class="sxs-lookup"><span data-stu-id="bcd73-107">Example</span></span>  

 <span data-ttu-id="bcd73-108">次のコードでは、<xref:System.Data.Linq.ObjectChangeConflict> オブジェクトを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="bcd73-108">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="bcd73-109">オブジェクトごとに、次に <xref:System.Data.Linq.MemberChangeConflict> オブジェクトを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="bcd73-109">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcd73-110"><xref:System.Reflection> 情報を提供するには、<xref:System.Data.Linq.MemberChangeConflict.Member%2A> を含めます。</span><span class="sxs-lookup"><span data-stu-id="bcd73-110">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bcd73-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcd73-111">See also</span></span>

- [<span data-ttu-id="bcd73-112">方法: 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="bcd73-112">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
