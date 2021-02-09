---
description: '詳細情報: トランザクションのサポート'
title: トランザクションのサポート
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 97c076fadacde01c7d14e5d51b000839b3d014a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681176"
---
# <a name="transaction-support"></a><span data-ttu-id="890ac-103">トランザクションのサポート</span><span class="sxs-lookup"><span data-stu-id="890ac-103">Transaction Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="890ac-104">では、3 種類のトランザクション モデルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="890ac-104">supports three distinct transaction models.</span></span> <span data-ttu-id="890ac-105">チェックが行われる順に、これらのモデルを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="890ac-105">The following lists these models in the order of checks performed.</span></span>  
  
## <a name="explicit-local-transaction"></a><span data-ttu-id="890ac-106">明示的なローカル トランザクション</span><span class="sxs-lookup"><span data-stu-id="890ac-106">Explicit Local Transaction</span></span>  

 <span data-ttu-id="890ac-107"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> が呼び出されたときに <xref:System.Data.Linq.DataContext.Transaction%2A> プロパティが (`IDbTransaction`) トランザクションに設定されている場合、同じトランザクションのコンテキストで <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼び出しが実行されます。</span><span class="sxs-lookup"><span data-stu-id="890ac-107">When <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called, if the <xref:System.Data.Linq.DataContext.Transaction%2A> property is set to a (`IDbTransaction`) transaction, the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> call is executed in the context of the same transaction.</span></span>  
  
 <span data-ttu-id="890ac-108">トランザクションの実行が終了したら、ユーザーがトランザクションをコミットまたはロールバックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="890ac-108">It is your responsibility to commit or rollback the transaction after successful execution of the transaction.</span></span> <span data-ttu-id="890ac-109">トランザクションに対応する接続は、<xref:System.Data.Linq.DataContext> を構築するのに使用した接続に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="890ac-109">The connection corresponding to the transaction must match the connection used for constructing the <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="890ac-110">異なる接続が使用されると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="890ac-110">An exception is thrown if a different connection is used.</span></span>  
  
## <a name="explicit-distributable-transaction"></a><span data-ttu-id="890ac-111">明示的な分散トランザクション</span><span class="sxs-lookup"><span data-stu-id="890ac-111">Explicit Distributable Transaction</span></span>  

 <span data-ttu-id="890ac-112">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API (<xref:System.Data.Linq.DataContext.SubmitChanges%2A> など) は、アクティブな <xref:System.Transactions.Transaction> のスコープ内で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="890ac-112">You can call [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (including but not limited to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) in the scope of an active <xref:System.Transactions.Transaction>.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="890ac-113">によって呼び出しがトランザクションのスコープ内であることが検出されて、新しいトランザクションは作成されません。</span><span class="sxs-lookup"><span data-stu-id="890ac-113">detects that the call is in the scope of a transaction and does not create a new transaction.</span></span> <span data-ttu-id="890ac-114">この場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では接続の終了も回避されます。</span><span class="sxs-lookup"><span data-stu-id="890ac-114">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] also avoids closing the connection in this case.</span></span> <span data-ttu-id="890ac-115">このようなトランザクションのコンテキストで、クエリと <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の実行が可能です。</span><span class="sxs-lookup"><span data-stu-id="890ac-115">You can perform query and <xref:System.Data.Linq.DataContext.SubmitChanges%2A> executions in the context of such a transaction.</span></span>  
  
## <a name="implicit-transaction"></a><span data-ttu-id="890ac-116">暗黙のトランザクション</span><span class="sxs-lookup"><span data-stu-id="890ac-116">Implicit Transaction</span></span>  

 <span data-ttu-id="890ac-117"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すと、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって、呼び出しが <xref:System.Transactions.Transaction> のスコープにあるかどうか、または `Transaction` プロパティ (`IDbTransaction`) がユーザーによって開始されたローカル トランザクションに設定されているかどうかがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="890ac-117">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] checks to see whether the call is in the scope of a <xref:System.Transactions.Transaction> or if the `Transaction` property (`IDbTransaction`) is set to a user-started local transaction.</span></span> <span data-ttu-id="890ac-118">どちらのトランザクションも見つからない場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によってローカル トランザクション (`IDbTransaction`) が開始され、それを使用して、生成された SQL コマンドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="890ac-118">If it finds neither transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a local transaction (`IDbTransaction`) and uses it to execute the generated SQL commands.</span></span> <span data-ttu-id="890ac-119">すべての SQL コマンドが終了すると、ローカル トランザクションがコミットされて [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] から戻ります。</span><span class="sxs-lookup"><span data-stu-id="890ac-119">When all SQL commands have been successfully completed, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] commits the local transaction and returns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="890ac-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="890ac-120">See also</span></span>

- [<span data-ttu-id="890ac-121">背景情報</span><span class="sxs-lookup"><span data-stu-id="890ac-121">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="890ac-122">方法: データ送信をトランザクションで囲む</span><span class="sxs-lookup"><span data-stu-id="890ac-122">How to: Bracket Data Submissions by Using Transactions</span></span>](how-to-bracket-data-submissions-by-using-transactions.md)
