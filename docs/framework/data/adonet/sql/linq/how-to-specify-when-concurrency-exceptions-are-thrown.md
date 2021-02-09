---
description: '詳細情報: 方法:コンカレンシー例外をいつスローするかを指定する'
title: '方法: コンカレンシー例外をいつスローするかを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: d445cabfd2498f3599d874c2b7983a86c2c36c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785875"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="7e855-103">方法: コンカレンシー例外をいつスローするかを指定する</span><span class="sxs-lookup"><span data-stu-id="7e855-103">How to: Specify When Concurrency Exceptions are Thrown</span></span>

<span data-ttu-id="7e855-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、オプティミスティック コンカレンシーの競合によってオブジェクトが更新されないときに <xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="7e855-104">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="7e855-105">詳細については、「[オプティミスティック コンカレンシー:概要)](optimistic-concurrency-overview.md) の下のステートメントを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="7e855-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="7e855-106">変更内容をデータベースに送信する前に、コンカレンシー例外をどの時点でスローするかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7e855-106">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
- <span data-ttu-id="7e855-107">例外を最初のエラーの時点でスローします (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>)。</span><span class="sxs-lookup"><span data-stu-id="7e855-107">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
- <span data-ttu-id="7e855-108">更新の再試行を決められた回数繰り返し、すべてのエラー情報を集積してから、この情報を例外で報告します (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>)。</span><span class="sxs-lookup"><span data-stu-id="7e855-108">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="7e855-109"><xref:System.Data.Linq.ChangeConflictException> 例外がスローされると、例外を通じて <xref:System.Data.Linq.ChangeConflictCollection> コレクションにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7e855-109">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="7e855-110">このコレクションを使用して、個々の競合 (それぞれが 1 回の更新失敗に対応する) の詳細情報を取得したり、<xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> コレクションにアクセスしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="7e855-110">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="7e855-111">各メンバー競合は、コンカレンシー チェックでエラーになった更新の 1 つのメンバーに対応します。</span><span class="sxs-lookup"><span data-stu-id="7e855-111">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e855-112">例</span><span class="sxs-lookup"><span data-stu-id="7e855-112">Example</span></span>  

 <span data-ttu-id="7e855-113">両方の値の例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="7e855-113">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7e855-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e855-114">See also</span></span>

- [<span data-ttu-id="7e855-115">方法: 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="7e855-115">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="7e855-116">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="7e855-116">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
