---
description: '詳細情報: 複数のキャンセル要求を待機する方法'
title: '方法: 複数のキャンセル要求を待機する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
ms.openlocfilehash: 7b04a1451338544a35dbae22bbd2d1848b50c69e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666785"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="f9610-103">方法: 複数のキャンセル要求を待機する</span><span class="sxs-lookup"><span data-stu-id="f9610-103">How to: Listen for Multiple Cancellation Requests</span></span>

<span data-ttu-id="f9610-104">この例では、2 つのキャンセル トークンを同時にリッスンして、いずれかのトークンからキャンセルが要求された場合に操作を取り消す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f9610-104">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9610-105">[マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="f9610-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="f9610-106">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="f9610-106">This error is benign.</span></span> <span data-ttu-id="f9610-107">F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="f9610-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="f9610-108">Visual Studio による処理が最初のエラーで中断しないようにするには、 **[ツール] メニューの [オプション]、[デバッグ] 、[全般]** の順にクリックし、[マイ コードのみ] チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="f9610-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9610-109">例</span><span class="sxs-lookup"><span data-stu-id="f9610-109">Example</span></span>  

 <span data-ttu-id="f9610-110">次の例では、<xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> メソッドを使用して 2 つのトークンを 1 つのトークンに結合します。</span><span class="sxs-lookup"><span data-stu-id="f9610-110">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="f9610-111">これで、1 つのキャンセル トークンのみを引数として受け取るメソッドにトークンを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f9610-111">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="f9610-112">この例では、クラスの外部から渡されたトークンと、クラス内部で生成されたトークンの両方をメソッドで観察する必要がある一般的なシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="f9610-112">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="f9610-113">リンクされたトークンから <xref:System.OperationCanceledException> がスローされる場合、例外に渡されるトークンは先行トークンではなくリンクされたトークンです。</span><span class="sxs-lookup"><span data-stu-id="f9610-113">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="f9610-114">取り消されたトークンを特定するには、先行トークンの状態を直接確認します。</span><span class="sxs-lookup"><span data-stu-id="f9610-114">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="f9610-115">この例で <xref:System.AggregateException> がスローされることはまずありませんが、実際のシナリオでは、タスクのデリゲートからスローされた <xref:System.OperationCanceledException> 以外の例外はすべて <xref:System.AggregateException> にラップされるので、ここでキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="f9610-115">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9610-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9610-116">See also</span></span>

- [<span data-ttu-id="f9610-117">マネージド スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="f9610-117">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
