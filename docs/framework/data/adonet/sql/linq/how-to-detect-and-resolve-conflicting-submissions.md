---
description: '詳細情報: 方法:送信の競合を検出および解決する'
title: '方法: 送信の競合を検出および解決する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 7ccfc9aeba8a21c3f5e950569d7650af087416a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739041"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="b5744-103">方法: 送信の競合を検出および解決する</span><span class="sxs-lookup"><span data-stu-id="b5744-103">How to: Detect and Resolve Conflicting Submissions</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b5744-104">には、複数のユーザーがデータベースを変更するために生じる競合を、検出および解決するための多くのリソースが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b5744-104">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="b5744-105">詳細については、[変更の競合を管理する](how-to-manage-change-conflicts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5744-105">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5744-106">例</span><span class="sxs-lookup"><span data-stu-id="b5744-106">Example</span></span>  

 <span data-ttu-id="b5744-107"><xref:System.Data.Linq.ChangeConflictException> 例外をキャッチする `try`/`catch` ブロックの例を次にします。</span><span class="sxs-lookup"><span data-stu-id="b5744-107">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="b5744-108">各競合のエンティティおよびメンバー情報が、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b5744-108">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5744-109">情報の取得をサポートするには、`using System.Reflection` ディレクティブ (Visual Basic の場合は `Imports System.Reflection`) を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5744-109">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="b5744-110">詳細については、「<xref:System.Reflection>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5744-110">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b5744-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5744-111">See also</span></span>

- [<span data-ttu-id="b5744-112">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="b5744-112">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="b5744-113">方法: 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="b5744-113">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
