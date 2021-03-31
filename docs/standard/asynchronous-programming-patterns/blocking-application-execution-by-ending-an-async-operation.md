---
description: '詳細情報: 非同期操作の終了によるアプリケーション実行のブロック'
title: 非同期操作の終了によるアプリケーション実行のブロック
ms.date: 03/30/2017
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
dev_langs:
- csharp
- vb
ms.openlocfilehash: e726bad3c9fe78d8e4fafadc3d10975bb9c17750
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642813"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="e27ce-103">非同期操作の終了によるアプリケーション実行のブロック</span><span class="sxs-lookup"><span data-stu-id="e27ce-103">Blocking Application Execution by Ending an Async Operation</span></span>

<span data-ttu-id="e27ce-104">非同期操作の結果の待機中に、他の作業を継続できないアプリケーションは、操作が完了するまでブロックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e27ce-104">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="e27ce-105">次のオプションのいずれかを使用して、非同期操作が完了するまでの待機中に、アプリケーションのメイン スレッドをブロックします。</span><span class="sxs-lookup"><span data-stu-id="e27ce-105">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="e27ce-106">非同期操作の **End**_OperationName_ メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e27ce-106">Call the asynchronous operations **End**_OperationName_ method.</span></span> <span data-ttu-id="e27ce-107">このトピックでは、この方法のデモが実行されます。</span><span class="sxs-lookup"><span data-stu-id="e27ce-107">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="e27ce-108">非同期操作の **Begin**_OperationName_ メソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.AsyncWaitHandle%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="e27ce-108">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="e27ce-109">この方法をデモの例については、「[AsyncWaitHandle の使用によるアプリケーション実行のブロック](blocking-application-execution-using-an-asyncwaithandle.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e27ce-109">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="e27ce-110">非同期操作が完了するまでブロックするために **End**_OperationName_ メソッドを使用するアプリケーションは、通常は **Begin**_OperationName_ メソッドを呼び出し、操作の結果なしで実行できる任意の作業を実行して、**End**_OperationName_ を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e27ce-110">Applications that use the **End**_OperationName_ method to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then call **End**_OperationName_.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e27ce-111">例</span><span class="sxs-lookup"><span data-stu-id="e27ce-111">Example</span></span>  

 <span data-ttu-id="e27ce-112">次のコード例は、ユーザー指定のコンピューターのドメイン ネーム システム情報を取得するために、<xref:System.Net.Dns> クラスの非同期メソッドを使用してデモを実行します。</span><span class="sxs-lookup"><span data-stu-id="e27ce-112">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="e27ce-113">この方法を使用する場合はこれらの引数は必要ないため、`null` (Visual Basic の場合は `Nothing`) は、<xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` と `stateObject` パラメーターに渡されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e27ce-113">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e27ce-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e27ce-114">See also</span></span>

- [<span data-ttu-id="e27ce-115">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="e27ce-115">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="e27ce-116">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="e27ce-116">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
